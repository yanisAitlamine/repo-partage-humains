# Reprise : déclenchement des emails, faisabilité Drive et dialogue commercial

État du 14 octobre 2026. Document public anonymisé. Les références d'exploitation, sauvegardes chiffrées, sorties privées et versions exactes restent dans l'espace autorisé, hors du dépôt public.

## Demande et résultat

La mission confiée par Ilyes consiste à suivre la dernière demande de Yanis : rechercher un déclenchement inattendu de la réception Gmail après un échec de construction, corriger sa cause et évaluer la récupération de documents, images et données depuis Google Drive. Ilyes a ajouté la vérification des annonces de préparation de maquette et des réponses répétitives après des remerciements ou validations.

La reprise tient compte de la levée du gel de coordination. La chaîne actuelle prépare un prototype après un brief suffisant et cohérent, puis demande la validation humaine finale avant livraison. Aucun ancien garde bloquant, ancien workflow manuel ou ancienne base de messages n'a été restauré.

### Déclenchement inattendu : cause et correction appliquée

Les traces montrent la succession suivante : un travail de construction échoue ; le circuit d'erreur produit un événement ; le journal transforme cet événement en demande de réveil du processeur Gmail ; le collecteur se lance sans nouveau message reçu. La même chaîne est observée sur deux incidents historiques.

Le journal utilisait la seule catégorie `ERROR` pour décider de réveiller le processeur. Le type d'incident ne suffisait pas à justifier une reprise d'email. Le lancement observé ne procédait pas à une nouvelle recherche Gmail : il consultait une file vide et les contrôles de relance. L'exécution verte de cette reprise ne prouvait donc pas la prise en charge d'un nouveau mail.

La correction publiée ajoute la provenance du workflow à l'événement technique, puis exclut les erreurs de construction du réveil Gmail. Deux paramètres de code ont changé dans les supports existants. Les autres nœuds, connexions, paramètres et données ont été comparés et préservés ; les trois pipelines principaux sont inchangés.

Une première proposition de déconnexion globale a été abandonnée pendant la revue : elle aurait supprimé également des reprises légitimes après incident Gmail. Le correctif final conserve ces reprises et les mécanismes de vidage des messages déjà en attente. « Pas de nouveau mail » ne signifie pas qu'un traitement commencé doit être abandonné lorsqu'il nécessite une reprise.

**Preuves :** 32 assertions locales portant sur la provenance des deux incidents historiques, le refus du réveil après erreur de construction, la conservation des autres erreurs et des cas historiques sans provenance, les confirmations d'insertion et le retour des données métier. Le responsable a relancé ces assertions. Les sauvegardes personnelles chiffrées ont été déchiffrées en mémoire et comparées avant publication ; les versions publiées ont ensuite été relues et le diff sémantique vérifié.

**Limites :** ces contrôles n'ont pas rejoué une erreur réelle sur le serveur. Aucun email, message Telegram, appel OpenAI ou site n'a été lancé par cette correction. Le circuit de réveil auquel l'API personnelle refuse l'accès n'a pas été inspecté ni contourné. La correction porte sur l'appel erroné émis par les composants accessibles.

### Réponses commerciales : défauts réellement observés

Une conversation historique montre une réponse longue répétant le projet après un simple accord et remerciement. Une nouvelle soumission du même projet a également été demandée. Le backend a retourné le même travail et la même révision : une soumission répétée est attestée, mais pas deux sites construits.

Deux instructions commerciales conservaient l'ancien fonctionnement, présentant la maquette comme une simple proposition sans lancement automatique. Le dialogue et la construction utilisent des branches indépendantes ; la rédaction ne reçoit pas de preuve d'acceptation ou de construction du travail. Une annonce telle que « votre maquette est prête » ou « sa création est en cours » reste donc injustifiée sans état fiable du bon projet et de la bonne révision.

Un correctif ciblé sur deux blocs existants est préparé. Il distingue l'intention du dernier apport : remerciement, accusé de réception, validation d'un choix, question nouvelle, changement ou document ajouté. Il ne repose pas sur une liste de mots et ne doit pas effacer une demande réelle contenue dans « merci, mais… ». Lorsque le brief est complet, il annonce clairement le passage à la préparation de la première maquette, sans prétendre à une action technique non prouvée.

**Contrôles structurels :** 94 vérifications de la copie, du remplacement des blocs et de la conservation des autres paramètres et connexions. Il ne s'agit pas de 94 réponses du modèle.

**Essai réel du modèle :** un banc manuel isolé de neuf scénarios entièrement fictifs a été importé inactif puis exécuté une seule fois par le bouton officiel n8n. Il utilise les deux prompts candidats, le modèle configuré dans le dialogue (`gpt-5.6-luna`), ses options et le schéma existant. Le graphe ne contient aucun chemin Gmail, Telegram, Drive, table ou construction. Les neuf résultats structurés ont été obtenus et relus ; 18 générations principales sont observées. La copie reste inactive et non publiée. Ce test ne valide pas la persistance mémoire, les envois ou les jobs.

Les réponses de remerciement sont courtes, sans nouvelle question artificielle. Une confirmation de choix permet une annonce claire des pages à préparer. Les questions de délai et de suivi sont abordées sans inventer de date ; les trois prestations du document fictif sont conservées dans les faits ; la réponse en anglais reste en anglais.

**Mais le correctif commercial n'est pas appliqué au workflow actif**, car la revue trouve encore des défauts :

- Les demandes de délai et de suivi restent classées comme demandes de maquette, malgré une réponse pertinente.
- Les neuf cas conservent les indicateurs de brief suffisant et de préparation OpenCode. Sous les autres préconditions d'un client autorisé, ces indicateurs ne permettent pas au garde actuel de distinguer un remerciement d'une nouvelle demande. Aucun site n'a été lancé par le banc ; les identités fictives ne satisfont pas les protections d'envoi réelles.
- Le cas portant sur deux projets crée une contradiction injustifiée alors que la demande concernant l'atelier est explicite.
- La question anglaise sur la possibilité d'ajouter une photo au formulaire devient une décision trop affirmative dans le JSON. Une possibilité, une demande et un choix confirmé doivent rester distincts.

Le test lexical exigeant le mot « restauration » échoue dans le texte de réponse au document, mais les faits contiennent correctement les trois prestations : cet indicateur seul n'est pas un échec de compréhension. Le scénario de paiement possède une incohérence de type de site dans sa fixture ; il reste utile pour le remplacement de décision, mais ne valide pas la complétude du brief. Il n'y a pas de comparaison A/B avec les anciens prompts : les défauts observés ne sont pas attribués automatiquement à la modification candidate.

**Amélioration déterministe encore nécessaire :** croiser la décision sémantique sur le dernier message avec la révision et l'état réel du travail. Le seul statut « brief suffisant » ne permet pas de décider qu'un nouveau remerciement exige une nouvelle soumission. L'idempotence constatée protège la construction, mais ne rend pas pertinente une réponse répétée.

### Annonce de lancement demandée par Ilyes

La formulation retenue, conditionnée à une acceptation technique fiable, est : « Nous lançons la préparation de votre première maquette, avec les pages et fonctionnalités principales de votre projet. Nous reviendrons vers vous dès qu'elle sera prête à vous être présentée, afin de recueillir vos retours et vos ajustements. » Dans le mail réel, les pages et fonctions doivent être précisées à partir du brief confirmé, sans inventer de prestation ou de date.

L'audit du dernier parcours disponible trouve une réponse d'acceptation du travail contenant le projet, une révision et l'état de file. Le validateur de soumission actuel ne conserve pas la révision dans sa sortie. Surtout, l'appel de construction est asynchrone et parallèle à la réponse commerciale : ce récépissé n'est pas disponible au rédacteur avant l'envoi. Une simple modification de phrase risquerait donc d'annoncer un lancement qui a échoué.

Un complément sur copies prépare le contrat de transmission de ce récépissé et le rendu de l'annonce. La connexion effective au dialogue doit être coordonnée avec le propriétaire du bridge. Elle ne doit pas bloquer la première réponse jusqu'à la validation Telegram finale, ni introduire un second envoi répétitif ou relancer les travaux incertains. Aucun adaptateur de lancement n'est présenté ici comme déployé.

Le complément exécutable local comporte 81 assertions sur 22 scénarios, puis six scénarios du garde et quatre contrôles du validateur de récépissé en VM. Le responsable les a relancés. Il refuse l'annonce sans contexte serveur vérifié, concordance projet/révision/message, destinataire TEST autorisé et registre consulté. Une réservation existante, un état inconnu, une erreur ou une révision remplacée ne permettent pas d'annoncer un nouveau lancement. Le rendu ne crée aucun travail et n'envoie aucun mail ; il exige une réservation atomique avant un éventuel envoi.

Ces tests utilisent des adaptateurs fictifs : ils ne prouvent ni l'authentification du transport réel, ni une réservation concurrente en base, ni le raccordement au rédacteur. Une copie n8n inactive est livrée localement pour ce contrat, sans import supplémentaire. La copie partagée du backend est datée et ne correspond pas à toutes les capacités observées du service actif ; aucun endpoint de recherche par révision n'est présumé existant. Une demande technique a été publiée au partenaire pour déterminer le point d'intégration accessible, sans lui transmettre de données clients ou de secrets. Sa réponse et l'intégration réelle ne sont pas attestées dans ce bilan.

### Google Drive : faisabilité et décision attendue

La récupération d'un cahier des charges, de photos et de fichiers de données est réalisable. Une lecture réelle historique d'un document Google a déjà produit 5 420 caractères. Un lecteur structuré séparé a également été préparé et importé inactif ; ses 313 assertions sont synthétiques et ne constituent pas une lecture réelle d'un PDF de plusieurs centaines de pages.

L'export du dialogue actuel inspecté ne montre pas de lecteur Drive raccordé au parcours commercial. La présence de lecteurs de pièces jointes Gmail ne prouve pas le téléchargement d'un document partagé ou la conservation de ses images. L'audit ne prétend pas couvrir tous les services privés du propriétaire.

Le complément recommandé est progressif :

1. Associer le lien ou l'invitation au bon client et au bon projet, sans répondre au service automatique de partage.
2. Vérifier les métadonnées et les droits du compte personnel, puis exporter les documents Workspace ou télécharger les fichiers binaires selon leur type.
3. Conserver les originaux et les ressources utiles dans un stockage privé du projet, avec empreintes et provenance ; la mémoire conserve les faits confirmés et leurs références.
4. Traiter les textes longs par lots avec couverture explicite. Un fichier inaccessible ou partiellement lu ne doit pas bloquer une réponse possible à partir du mail.
5. Tester les documents multi-onglets, dossiers paginés, images, fichiers Office et données, erreurs de permission et modifications concurrentes.

L'accès en lecture seule est suffisant en principe ; aucun droit d'écriture Drive n'est nécessaire. Un accès restreint à des fichiers sélectionnés n'est pas automatiquement équivalent aux droits permettant de lire les invitations reçues. Les secrets OAuth restent dans les credentials existants.

L'export Workspace est limité à 10 Mo selon la documentation Google. La taille d'un fichier, l'OCR, les quotas et la couverture doivent être traités explicitement ; promettre une lecture universelle ou illimitée serait incorrect. Pour les gros PDF, les tests devront vérifier réellement les pages et les sections comprises, pas seulement simuler un résultat d'extraction.

L'implémentation Drive reste volontairement différée jusqu'à la décision d'Ilyes demandée dans cette mission. Aucun nouveau droit Google, téléchargement Drive ou changement de credential n'a été effectué.

Voir l'[étude détaillée Drive](ETUDE-2026-10-14-Drive-documents-images-donnees.md), avec les références officielles et la liste des vérifications à réaliser.

## Orchestration et délégation

### Délégation

Le responsable a confié quatre tâches indépendantes : une étude de faisabilité Drive, un audit du dialogue commercial avec préparation et revue du banc, une revue du correctif de réveil, puis une étude du récépissé de lancement dans la chaîne. Les sous-agents ont utilisé la configuration héritée ; leur modèle précis n'a pas été attesté par un outil et aucun coût ou gain n'est estimé. Le modèle commercial configuré dans le banc est, lui, observable dans les paramètres n8n.

Les agents ont rendu des rapports et candidats locaux. Le responsable a lu les résultats, retiré la proposition trop large, relancé les tests de provenance, préparé les sauvegardes et réalisé seul la publication contrôlée du correctif ciblé. Il a importé et lancé le banc commercial par l'interface officielle, récupéré les résultats et demandé une revue indépendante. Les candidats Drive et commerciaux ne doivent pas être présentés comme des fonctions déjà intégrées.

## Coopération et adaptation au contexte

### Collaboration

Le responsable a lu l'état, le protocole, les consignes du dépôt et les dernières annonces par son accès personnel avant le diagnostic. La levée du gel et la nouvelle architecture ont été prises en compte ; les déclarations de réussite du partenaire restent distinguées des vérifications propres du responsable.

L'intention initiale portait sur l'audit, les copies locales et le rapport public. Une extension a réservé les éléments du journal concernés. La revue a entraîné une correction annoncée du périmètre avant toute écriture : la déconnexion globale proposée n'a pas été appliquée. Seuls les deux paramètres de provenance et de décision de réveil ont finalement changé. La fin du correctif a été publiée et les réservations libérées.

Le brouillon de construction différait de sa version publiée ; cette divergence existante a été préservée. Les droits personnels ont été respectés, y compris le refus d'accès à un support. Aucun compte du partenaire, source privée, service, réseau, donnée réelle ou ancienne base n'a été modifié.

La visibilité publique du dépôt documentaire et le droit de contribution ont été vérifiés. Les versions publiques excluent les identifiants internes, coordonnées, messages clients, prompts privés et chemins d'accès sensibles. Les références techniques exactes restent dans les preuves autorisées et les messages de coordination.