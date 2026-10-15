# Comprendre l’architecture du projet

Le projet automatise une partie des échanges nécessaires à la préparation d’un site : recevoir un mail, comprendre le besoin, demander des précisions, préparer une maquette et faire valider sa livraison.

Le Raspberry Pi fait tourner les automatisations. Gmail transporte les mails. Telegram permet à une personne d’intervenir. Les services d’IA aident à analyser et rédiger. Un hébergement externe reçoit les maquettes.

Le [guide des workflows](WORKFLOWS-PIPELINE-PRINCIPAL.md) explique les étapes du traitement. Cette page explique les machines, les services et les documents qui permettent à ce traitement de fonctionner.

Version du texte : 15 octobre 2026. Le parcours applicatif décrit correspond aux observations du 14 octobre. Les interventions encore en cours ne sont pas présentées comme terminées. Les adresses, chemins privés et identifiants restent dans les références d’exploitation sur le Pi.

## Le rôle de chaque machine

| Élément | Son rôle concret | Ce qu’il faut comprendre |
| --- | --- | --- |
| PC Windows | Sert à piloter le projet, préparer des changements et rédiger la documentation avec Codex. | Les automatisations du Pi peuvent continuer quand le PC est éteint. |
| VM Kali personnelle de Yanis | Sert à préparer et appliquer des changements d’administration avec Ansible. Une VM est un ordinateur virtuel. | Son arrêt ne coupe pas n8n. Ce n’est pas un espace partagé avec Ilyes ou les agents. |
| Raspberry Pi | Héberge n8n, les services d’accès et les services qui relient les automatisations à Telegram et OpenCode. | C’est la machine de production : les services actifs et leurs données y sont conservés. |
| GitHub | Conserve les sources et la documentation versionnée. | Un fichier publié sur GitHub n’est pas automatiquement installé sur le Pi. |
| Services externes | Fournissent la messagerie, les modèles d’IA et l’hébergement des sites. | Ils restent nécessaires aux étapes qui les utilisent, même si le Pi fonctionne. |

**Kali reste personnelle à Yanis.** Ilyes et les agents ne doivent pas s’y connecter ni sonder son accès sans demande explicite de Yanis visant cette machine. Mentionner son rôle dans ce document ne donne pas une autorisation d’accès.

## Les services qui tournent sur le Pi

### n8n organise les étapes

n8n exécute les workflows. Il reçoit les événements, appelle les services nécessaires, enregistre des résultats et choisit la suite prévue par le parcours.

n8n et ses outils d’exécution utilisent **Docker**, qui permet de faire fonctionner des applications dans des environnements séparés appelés conteneurs. **Docker Compose** décrit les conteneurs à lancer et leurs liens.

Les **task runners** exécutent les étapes de code dans un conteneur séparé. Ils ne disposent pas du même accès au stockage des identifiants que n8n. Cette séparation limite les accès ; elle ne dispense pas de vérifier le code et ses permissions.

Les données durables sont conservées dans un **volume Docker** : un espace de stockage qui existe indépendamment du conteneur. Recréer un conteneur n’est donc pas la même opération qu’effacer ses données.

### Caddy reçoit les connexions HTTPS

Caddy est placé devant n8n. Il reçoit la connexion sécurisée du navigateur et la transmet à n8n sur le Pi. C’est ce qu’on appelle un **proxy inverse**.

HTTPS chiffre la connexion et utilise un certificat pour vérifier l’identité du service. Le renouvellement du certificat utilise une preuve sur le nom de domaine, appelée **DNS-01**. Il n’exige pas de rendre l’éditeur n8n public sur Internet.

### Le VPN et le DNS permettent l’accès privé

Le **VPN** crée un accès réseau privé pour les personnes autorisées. L’éditeur n8n est accessible depuis les réseaux autorisés, notamment le réseau local ou le VPN ; il n’est pas ouvert librement à Internet.

Le **DNS** traduit un nom de service en adresse réseau. Les réglages du réseau local et du VPN permettent d’atteindre le bon service avec son nom. Un problème de DNS ne justifie pas d’ouvrir n8n publiquement.

Le VPN ne doit donner que les accès prévus. Disposer d’une connexion VPN ne signifie pas que l’on peut administrer tous les services du Pi.

### Le service Telegram reçoit les réponses humaines

Un service dédié récupère les événements du bot Telegram et transmet les décisions aux traitements concernés. Il interroge Telegram depuis le Pi ; ce fonctionnement ne nécessite pas une nouvelle ouverture publique de n8n.

Un seul service doit récupérer les réponses de ce bot. En lancer un deuxième risquerait de perturber leur traitement.

### Le bridge OpenCode transmet les demandes de construction

Le **bridge**, ou passerelle, relie le workflow n8n au mécanisme de construction OpenCode. Il reçoit une demande, suit le travail et expose le résultat nécessaire à la suite du parcours.

Son API est privée et réservée au réseau applicatif autorisé. Une **API** est une interface par laquelle deux programmes échangent des demandes et des résultats.

Les services persistants de l’hôte sont gérés par **systemd**, le gestionnaire de services Linux. Modifier un fichier de service ne signifie pas à lui seul que le programme actif a chargé ce changement.

## Les services utilisés à l’extérieur

| Service | Ce qui lui est demandé |
| --- | --- |
| Gmail | Lire les messages autorisés et envoyer les réponses prévues par le parcours. |
| Telegram | Montrer les demandes de décision et recevoir les actions humaines. |
| GPT | Aider au tri, au conseil et à la rédaction. |
| Jev | Appuyer la décision sur des passages du client et indiquer si le dialogue doit continuer, peut produire une maquette ou doit demander de l’aide. |
| Hébergement N0C | Conserver et servir les maquettes créées dans la cible autorisée. |
| Services de nom de domaine et de certificat | Permettre de retrouver le service et de sécuriser sa connexion HTTPS. |
| GitHub | Conserver les versions des sources et des documents. |

Les maquettes sont hébergées chez N0C, pas sur le Pi. Le Pi organise leur construction et leur livraison. Un environnement isolé utilisé par l’assistant, tel que Daytona dans la configuration documentée, a aussi son rôle propre : ce n’est pas l’hébergement du site.

Une connexion enregistrée auprès d’un service ne prouve pas que toutes ses fonctions sont intégrées au parcours. Par exemple, un lecteur Drive en développement ne devient pas une capacité de production parce qu’un accès Google existe.

## Le trajet du mail jusqu’à la maquette

Voici le parcours principal. Certains mails s’arrêtent plus tôt, par exemple s’ils sont ignorés ou nécessitent des précisions.

1. **Gmail vers la réception n8n.** Le message est vérifié, mis en attente puis réservé pour éviter deux traitements simultanés.
2. **Réception vers le dialogue.** Le système relit la conversation, vérifie le projet et rassemble les demandes du client.
3. **Dialogue avec GPT et Jev.** Les services d’IA aident à comprendre et décider. Si le besoin est incomplet, le système pose des questions. S’il est incertain, une personne intervient sur Telegram.
4. **Brief suffisant vers la construction.** Le système peut lancer automatiquement une première maquette sur la cible de test autorisée. Le brief est le résumé du besoin du client.
5. **Construction puis contrôle.** Le résultat construit et le contenu réellement accessible sont comparés. La revue et la version du travail sont prises en compte.
6. **Maquette puis validation humaine.** Une personne examine le résultat et autorise ou refuse la livraison de cette version précise.
7. **Approbation puis Gmail.** Le système réserve l’envoi du lien et vérifie ensuite sa confirmation.

La première maquette peut donc exister avant le clic humain final. La validation qui protège sa livraison intervient après sa construction. Une mise en production de site complet reste une autre opération, qui exige sa propre autorisation.

## Les deux interventions humaines du parcours

Il existe deux interventions différentes dans le parcours décrit :

- **Répondre à un mail bloqué.** La personne reçoit le mail sur Telegram, choisit Stop ou Continuer, rédige une réponse puis confirme son aperçu avant envoi.
- **Valider la livraison d’une maquette.** La personne examine un résultat déjà construit et approuve l’envoi du lien correspondant à cette version.

Une notification ne signifie pas qu’une action a été confirmée. Un clic ancien ne vaut pas approbation d’un nouveau résultat. Une autorisation d’envoyer une réponse commerciale ne vaut pas autorisation de construire ou de publier un site complet.

Telegram reste utilisable via sa connexion Internet habituelle. L’accès à l’éditeur n8n, lui, reste privé. Ce sont deux accès différents.

## Les sources et les données de fonctionnement

Il faut distinguer quatre choses :

| Élément | Ce qu’il contient | Ce que prouve sa présence |
| --- | --- | --- |
| Sources applicatives | Les fichiers qui définissent le comportement des services et des intégrations. | Le code existe ; cela ne prouve pas que cette version est installée. |
| Configuration installée et workflows publiés | Les réglages et définitions retenus pour les services actifs. | Ils décrivent la version installée ou publiée ; leur lecture ne remplace pas un test réel. |
| Données de fonctionnement | Conversations autorisées, travaux en attente, décisions, historique des envois et autres états durables. | Elles permettent de suivre et de reprendre le travail ; elles ne sont pas remplacées par un dépôt de sources. |
| Documentation | Explications, procédures et rapports datés. | Elle décrit ce qui a été observé ou réalisé, avec ses limites. |

Les fichiers d’exploitation comprennent notamment la description Docker Compose, la configuration Caddy et les définitions de services systemd. Chacun est lu par un programme précis. Pour connaître son chemin exact, son consommateur, son effet et sa couverture de sauvegarde, il faut consulter la documentation privée d’exploitation.

Un **commit** enregistre une version dans Git. Une **sauvegarde** conserve ce qu’il faut pour récupérer un système ou des données. Un commit du code ne sauvegarde pas la base n8n, les envois en cours ou tous les réglages installés.

## La coopération entre personnes et agents

Trois espaces ont des usages différents :

- **L’espace partagé machine** contient les règles de coopération, les annonces de début et de fin et les copies de travail autorisées.
- **Ce dépôt public** contient les explications et rapports que tout le monde peut lire.
- **L’espace sensible du Pi** contient les références privées utiles à l’exploitation et à la coopération autorisée.

Les valeurs secrètes restent dans les stockages privés prévus à cet effet. Elles ne vont pas dans Git, même dans un dépôt privé. Les clés et identités personnelles ne sont pas partagées simplement parce que des personnes travaillent sur le même projet.

Avant de modifier des fichiers partagés, un agent consulte les annonces récentes et indique ce qu’il va toucher. Avant d’écrire, il vérifie qu’un autre agent n’a pas modifié ou réservé les mêmes fichiers. À la fin, il décrit le résultat et libère sa réservation.

Cette annonce évite les conflits si les agents respectent le protocole. Elle n’empêche pas techniquement deux écritures simultanées : ce n’est pas un verrou automatique.

Pour les implémentations importantes sur le Pi, le travail est normalement réparti entre planification, réalisation et revue. Codex conserve la responsabilité de l’intégration et du contrôle final. Les rapports distinguent un agent lancé, son travail terminé et un résultat effectivement intégré et vérifié.

## Les changements d’administration avec Ansible

**Ansible** décrit des changements d’administration de façon reproductible : quels fichiers installer, quels réglages appliquer et quels services gérer. Kali sert de poste de contrôle personnel à Yanis pour ces opérations.

La présence de rôles Ansible dans un dépôt ne prouve pas qu’ils ont été testés ou appliqués. Les réserves historiques sur les rôles de migration restent valables ; des interventions distinctes déjà autorisées ne les lèvent pas automatiquement.

Pour une évolution, il faut identifier les sources actives, préserver les changements existants, disposer d’un retour arrière adapté et ne réaliser que les tests et opérations autorisés. Une simple correction documentaire ne nécessite pas de redémarrer les services.

## Les sauvegardes et les preuves de fonctionnement

Pour récupérer le fonctionnement du Pi, il ne suffit pas de reprendre le code sur GitHub. Une sauvegarde cohérente doit couvrir les données, les configurations, les éléments nécessaires au déchiffrement et l’état des services concernés. Les archives sensibles doivent être chiffrées et conservées hors du Pi.

Une copie présente uniquement sur le Pi ne protège pas contre la perte du Pi. La présence d’une archive ne prouve pas non plus qu’une restauration complète a été testée.

| Contrôle | Ce qu’il permet d’affirmer |
| --- | --- |
| Lecture d’un fichier ou d’un workflow | La configuration décrit ce comportement. |
| Test avec des données fictives | Le cas testé fonctionne dans les conditions de l’essai. |
| Vérification du programme installé | La version installée répond au contrôle effectué. |
| Envoi Gmail confirmé | Gmail a confirmé l’envoi ; la lecture par le destinataire reste une autre question. |
| Vérification du fichier servi | Le contenu comparé est bien accessible ; toutes les interactions du site ne sont pas nécessairement testées. |
| Restauration complète | Le système a réellement pu être récupéré dans les conditions vérifiées. |

Le [rapport 36](RAPPORT-36-test-reel-maquette-et-validation.md) atteste un parcours réel de maquette et livraison. Le [rapport 38](RAPPORT-38-jev-parcours-commercial-reel.md) donne les preuves et limites de l’intégration Jev. Ces résultats ne constituent pas une garantie générale sur tous les cas futurs, tous les accès extérieurs ou une restauration complète.

Pour poursuivre la lecture : [guide des workflows](WORKFLOWS-PIPELINE-PRINCIPAL.md), [continuité de service](PROCEDURE-CONTINUITE-RUN.md), [reprise après incident](PROCEDURE-REPRISE-ACTIVITE.md) et [passation publique](PASSATION.md). Les rapports sont des états datés : les plus anciens peuvent décrire un fonctionnement remplacé depuis.
