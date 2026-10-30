<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Portail : dépôt PDF privé et reprise de plusieurs sites

Mission commencée le 17 octobre, état du 18 octobre 2026 : **parcours activé après accord humain, test réel en échec côté constructeur**.

## 1. Demande et résultat

Le demandeur souhaite reproduire depuis le portail un essai initialement envoyé
par mail : déposer son PDF et regrouper quatre sites existants. Il autorise les
adaptations nécessaires et choisit ensuite une cible TEST enregistrée. Les
données du cas réel restent privées et ne figurent pas dans ce rapport.

Le portail accepte désormais un PDF privé par projet, avec contrôle de session,
propriétaire, Origin, révision et consentement. Les octets restent dans le
stockage privé, sans URL publique. Le fichier actif peut remplacer une source
Drive, sans fusion implicite. Limites : 1 Mio, 50 pages, 50 000 caractères ;
aucun OCR ni extraction des images incorporées n’est promis. L’empreinte est
contrôlée avant lecture native page par page. Une lecture incomplète ou suspecte
bloque l’admission. La provenance du dépôt web reste distincte de Drive et du
mail ; les documents sont des données non fiables, jamais des instructions.

Quatre sites consentis peuvent être liés au brief et au job du constructeur.
La refonte exige une déclaration de réutilisation des contenus. Les liens de
l’assistant ou du PDF ne donnent aucun droit de collecte. Les sources restent
inchangées ; le constructeur conserve le registre opérateur, les budgets et
l’isolation du dossier de chaque job. L’entrée mail conserve son propre budget.

La release applicative approuvée a été déployée sur le Pi par le contrôleur
prévu. Service actif, accès HTTPS et sceaux vérifiés. Un cache Python ajouté
à l’ancienne release a d’abord été archivé avec son empreinte, par une recette
Ansible isolée propre à cette mission ; aucun ancien rôle réservé n’a été lancé.
Les workflows portail et le budget du constructeur ont été activés en préservant
leurs accès, paramètres et changements concurrents. Un push seul n’a pas servi
d’autorisation de déploiement.

Un compte et un projet ordinaires dédiés à l’essai ont reçu le PDF original et
les quatre adresses. L’automatisation du sélecteur de fichier était bloquée par
la permission locale de l’extension ; le dépôt a donc utilisé la même route
HTTPS authentifiée du portail. Aucune permission de navigateur n’a été élargie.

Le test réel a révélé deux défauts de transport, corrigés dans leurs sources :

- Le nœud natif de calcul d’empreinte consomme sa sortie binaire. Le workflow
  rattache maintenant l’item producteur exact après comparaison de l’empreinte.
  Une exécution native isolée puis le parcours réel ont lu les quatre pages
  complètes, avec zéro motif bloquant détecté.
- Une arobase dans les sources pouvait être interprétée par OpenCode comme une
  mention de fichier natif. Le suffixe JSON encode maintenant ce caractère,
  avec décodage strictement identique et empreinte du texte original conservée.
  Le plugin figé, ses permissions et ses refus restent inchangés. La tentative
  arrêtée avant création d’un enfant reste bloquée dans son historique ; aucun
  job n’a été réarmé ni état de validation forcé.

Le parcours a aussi révélé que les quatre sites redirigeaient vers leur variante
canonique avec « www ». Ces destinations ont été vérifiées en HTTPS ; les
adresses du brief ont été corrigées sans assouplir le garde d’origine. La mise
à jour structurée du brief a ensuite exposé une double lecture des URL depuis
une copie JSON des décisions. Cette projection serveur est désormais exclue
de la nomination des sites : les événements clients persistants restent la
source du consentement. Deux régressions vérifient les URL avec séparateurs
JSON et l’absence d’autorisation accordée par une projection seule. Les 79 tests
ciblés et la validation n8n du graphe corrigé passent.

L’assistant a demandé des précisions sur les pages, l’objectif et l’intention.
Elles ont été fournies à partir du document et de la demande initiale. Le moteur
a ensuite déclaré le brief READY ; le prompt a été vérifié avec ses quatre
sources, puis la construction a été demandée par le bouton normal du portail.
Les contrôles de devis et de livraison n’ont pas été acceptés à la place d’un humain.

La collecte réelle des quatre sources a produit du texte, des pixels et des
médias, avec des omissions annoncées. Le constructeur s’est arrêté sur une
interprétation trop stricte de cette couverture partielle et du dossier déjà
préprovisionné. Le contrat a été clarifié pour le prototype uniquement : quatre
avertissements attendus peuvent accompagner une capture principale réussie,
avec contenus exploitables et reçus vérifiés. Les requêtes refusées le restent,
les autres échecs sont bloquants et une migration exhaustive n’est pas annoncée.
Le plan MCP existant expose maintenant les métadonnées agrégées des fichiers
préprovisionnés du même job, avec contrôles de binding, chemins, empreintes et
budgets. Il exige explicitement une preuve fraîche ; il ne donne aucun droit
ou transfert supplémentaire. Le contrôle indépendant des fichiers déjà importés
par SSH/HTTPS a réussi. Quatorze tests Python sources, quinze de transport et
sept tests Node du collecteur/garde passent.

**Résultat terminal : aucun prototype construit ni livré.** Quatre jobs distincts
ont été soumis normalement au fil des corrections, sans réarmement. Le dernier
s’arrête avant d’achever la coordination et les contrôles de fichiers ; son
index est absent. Les budgets de 64 étapes d’implémentation/revue ont été
confirmés par diagnostic de configuration, avec et sans l’overlay du runner,
sans prompt payant. Les sessions observées se terminent normalement après
13 à 25 tours, sans erreur de budget signalée. Ce n’est donc pas une limite de
64 étapes effectivement atteinte. La cause de cette sortie prématurée reste
à corriger dans l’exécution NOC. Aucun contrôle n’a été supprimé pour afficher
un succès. Les fichiers importés restent dans leurs dossiers isolés ; leur
lecture SSH/HTTPS a été revérifiée, l’index racine est inchangé et aucune revue
ni approbation opérateur n’a été produite. Le portail est sain et répond en HTTPS.

Le travail restant est de faire terminer les contrôles et la réalisation par le
constructeur, puis d’obtenir les captures, la revue indépendante et l’accord
humain lié aux octets finaux avant livraison. Les corrections d’entrée et les
captures sources ne constituent pas cette livraison.

Contrôles : 226 tests Python et 270 JavaScript du portail, 77 tests ciblés de
l’adaptateur, 11 tests des sites sources, compilation frontend et validation
n8n des SDK. Le correctif binaire a repassé les 77 tests et la validation du
graphe à 43 nœuds sans avertissement. Le transport du texte a passé 15 tests
Python et 86 Node. La suite historique de 38 tests du runner présente toujours
les mêmes deux échecs de sous-cas et une erreur que la version de départ,
confirmés par comparaison ; elle n’est donc pas annoncée entièrement verte.
Ces tests isolés restent distincts des appels réels au modèle et au constructeur.

Un prototype ne prouve ni une migration exhaustive des quatre sites, ni une
administration de blog réellement connectée. La revue du site et la validation
humaine exacte de livraison restent des étapes séparées.

## 2. Orchestration et délégation

Codex réalise directement l’analyse, les modifications, la revue de diff, les
tests, le versionnement, l’activation autorisée et les interactions du portail.
Aucun sous-agent Codex n’a été lancé. Le modèle de décision du portail reste
celui configuré, sans changement de seuil ni de règles d’arrêt.

Le parcours réel a lancé quatre sessions du planificateur NOC. La première a
été refusée avant création d’un enfant. Les trois suivantes ont chacune eu
trois Tasks d’implémentation terminées ; leurs rapports sont des arrêts sans
site construit. Aucun réviseur indépendant n’a été lancé. Le modèle observé
pour les sessions d’implémentation diagnostiquées est gpt-6-luna ; il n’a pas
été remplacé. Les refus de Task avant enfant sont distingués de ces neuf Tasks
réellement démarrées et terminées. Aucun résultat de site n’a été intégré ni
validé ; les rapports lisibles et leurs limites ont été conservés en privé.

Aucune session PIAgentControl, connexion Kali ou ancien rôle Ansible réservé
n’a été utilisé. Aucun coût ou gain de tokens n’est inventé. Les copies lisibles
des prompts et retours effectivement consultés restent dans l’archive privée,
étiquetées comme copies d’audit, sans revendication de déchiffrement natif.

## 3. Coopération et adaptation au contexte

Les consignes, la fiche de reprise, le protocole, l’état partagé, la passation et
les références utiles au portail, aux sources et au constructeur ont été lus.
Les intentions et extensions ont annoncé les fichiers, graphes et essais avant
modification. Les versions actives ont été sauvegardées et comparées avant
publication ; les sources sont committées et poussées dans leurs dépôts canoniques.
Le service reste sur la release applicative approuvée ; les correctifs suivants
portent sur le workflow et le helper exécuté pour chaque job.

Les changements préexistants des checkouts canoniques, la reconnexion Gmail et
la mission parallèle de couleurs sur copie ont été préservés. Leurs annonces
ont été relues ; aucune de leurs réservations n’a été considérée expirée.
L’ancienne tentative bloquée reste conservée et le nouvel essai possède sa
propre identité et son dossier isolé. Aucun mail client n’a été envoyé.

Les réservations propres à cette mission sont clôturées par une annonce de fin
après publication de ce bilan. Les réservations des autres sessions sans fin
ne sont pas considérées expirées. Aucun chantier de construction ne reste actif
au contrôle terminal ; les jobs bloqués et leurs traces restent conservés.

Les identités opérationnelles, données client et preuves détaillées restent
hors du dépôt public. Ce bilan décrit nos contrôles, sans certifier les
opérations historiques d’autres sessions.
