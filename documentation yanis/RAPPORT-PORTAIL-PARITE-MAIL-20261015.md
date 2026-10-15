# Adaptation des fonctions du pipeline mail au portail web — 15 octobre 2026

## Demande et résultat

L'extension demandée ensuite ajoute un chat unique de 20 000 caractères, la
classification des demandes par Jev, le contrôle des fichiers Drive et des logs
de diagnostic pour les développeurs. Elle est également préparée, testée et
poussée sur la branche principale privée ; elle n'est pas encore installée.
La demande de mise en service vise désormais cette nouvelle version exacte.

Le chat ne présente plus de boutons de catégories. La décision distingue contenu,
design, page et fonctionnalité ; une incertitude demande une précision. Elle peut
produire un brouillon de devis lié au message, avec les seuls tarifs du serveur.
Aucun accord, paiement ou travail n'est lancé automatiquement.

Le contrôle des sources intervient avant les modèles et le dépôt d'images. Il
signale les instructions suspectes, délimiteurs forgés et caractères cachés,
préserve les données d'origine et bloque leur admission au contexte. Ce contrôle
heuristique ne garantit pas l'absence d'injection ; ni antivirus ni OCR ne sont
annoncés. Les documents restent des données citées sans autorité d'instruction.

Les logs bornés recensent connexions, refus, demandes, classifications, générations,
revues et support avec des références de corrélation. Ils excluent textes, URLs,
documents, mots de passe, cookies, jetons et IP brutes. Une lecture limitée aux
métadonnées est préparée pour les développeurs, sans droit direct sur la base
clients ; son installation attend l'accord de mise en service.

La dernière suite sur le serveur comporte 79 tests Python, 100 cas Node, deux
scripts des workflows existants, 56 cas du moteur et dix groupes du parcours
HTTP existant. Tout passe, ainsi que TypeScript et la compilation. Les graphes
sont validés et relus. Le navigateur a aussi accepté un message dépassant l'ancien
plafond, vérifié l'absence des catégories manuelles, le devis dans la conversation
et le blocage d'une source fictive. Aucun appel externe réel n'est attesté par ces
tests ; la recette d'accès aux diagnostics a été relue sans exécution.

Après audit du code et de l'historique puis accord explicite de l'utilisateur,
une [copie publique assainie](https://github.com/yanisAitlamine/atelier-portal-public)
a été créée sans reprendre l'historique privé. Son dépôt canonique est sur le
serveur ; son code est accessible anonymement. Une invitation d'écriture au
collaborateur est en attente d'acceptation. Les paramètres d'exploitation et
l'ancien dépôt restent privés ; les exemples publics ne donnent aucun accès aux
workflows, services ou logs réels.

La copie publique inclut maintenant le chat et les nouveaux modules. Son
[guide pour les agents](https://github.com/yanisAitlamine/atelier-portal-public/blob/main/docs/RESSOURCES-AGENTS.md)
localise interface, API, décision, contrôle Drive, diagnostics et tests. Elle
passe 78 tests Python, 100 cas Node, 56 cas du moteur, deux scripts historiques,
dix groupes HTTP, le générateur et la compilation. Le seul test privé exclu
contrôle un wrapper d'exploitation volontairement absent de cette copie ; les
autres tests des diagnostics sont conservés. Les exemples restent fictifs.

La demande est de retrouver dans le portail les fonctions du parcours mail,
notamment un dossier Google Drive contenant images, cahier des charges et données
du projet. La précision humaine conserve l'hébergement de test existant et
demande d'éviter des essais de construction concurrents.

Une version candidate est préparée, vérifiée, commise et poussée directement sur
la branche principale du dépôt privé du portail, sans nouvelle pull request.
Quatre workflows distincts sont enregistrés comme brouillons inactifs. Le portail
en service et le pipeline mail publié restent inchangés dans l'attente de l'accord
humain pour la version exacte à installer.

Le client peut fournir un dossier avec son consentement, consulter les fichiers
lus et un brief avec citations, puis autoriser explicitement un prototype. Le
lecteur, les règles de décision et le constructeur existants sont réutilisés.
La réalisation et la revue indépendante doivent être prouvées ; une validation
opérateur distincte précède la livraison du lien dans l'espace client. Les retours
réouvrent l'analyse ; ils ne lancent pas automatiquement une autre construction.
Les conversations et preuves restent liées au compte et au site concernés.

Les erreurs sont explicites : une source incomplète bloque, une réponse perdue
ne vaut pas succès, et une construction incertaine reste bloquante même après
un nouveau message. Le support reçoit la conversation conservée et le lien de la
bonne maquette, sans joindre un ancien fichier comme s'il s'agissait de la nouvelle
version. Les sources privées ne deviennent pas des pièces jointes de support.

Contrôles initiaux réussis sur le serveur : 61 tests Python, 26 cas de l'adaptateur web,
56 régressions du moteur, deux scripts des workflows antérieurs et dix groupes
du parcours HTTP existant. La compilation a réussi sur le poste et le serveur.
Les quatre graphes passent la validation de configuration ; leurs définitions
correspondent aux sources. Les versions publiées de référence sont préservées.
Le navigateur a vérifié le vrai frontend/backend avec des réponses externes
fictives : compte, dossier autorisé, document de trente pages, brief sourcé,
demande de construction, attente de validation, livraison opérateur simulée,
retour client et affichage sur petit écran.

Ces tests n'attestent encore ni lecture d'un Drive réel ni construction distante
pour cette nouvelle version. Aucun mail de test n'a été envoyé pour cette mission.
L'installation et le parcours réel restent à effectuer après accord. La maquette
de test sera accessible à toute personne ayant son lien, ce qui est expliqué
avant le clic de construction. Les documents et identifiants restent privés.

Les fonctions métier sont adaptées au web ; les déclencheurs et relances de mails
ne sont pas recopiés. La validation opérateur web utilise actuellement une
commande dédiée, plutôt qu'un bouton de messagerie. Le paiement et la publication
commerciale automatique restent séparés. Les formats non pris en charge, les
scans sans texte et les limites de lecture/contexte nécessitent une vérification.

## Orchestration et délégation

Codex a effectué directement la préparation initiale et l'intégration. Lors de
l'extension, trois sous-agents Codex ont reçu des périmètres distincts : module
de diagnostics/tests/guide puis recette d'accès borné ; module pur de contrôle
Drive/tests/limites ; audit d'exposition du code, préparation puis publication
de la copie assainie après accord humain. Leur configuration était héritée du
parent, sans modèle nominal supplémentaire relevé.

Les trois travaux sont revenus terminés. Le parent a relu et intégré les modules,
raccordé le scan et la classification aux graphes, synchronisé le dépôt canonique,
exécuté les contrôles globaux et vérifié le parcours navigateur. Une seconde revue
statique ciblée a examiné déduplication, séparation des accords, barrière avant
modèle et absence de contenu dans les logs. Aucun blocage concret n'a été signalé.
Aucune session de l'outil de délégation réservé à l'utilisateur n'a été lancée.
Aucun coût ou gain de consommation n'est estimé.

Le travail porte sur le frontend, le contrat du serveur, sa file durable, les
preuves privées, la validation opérateur, l'adaptateur de support et les quatre
nouveaux graphes. Les mécanismes réutilisés du mail sont figés dans les sources
du portail pour rendre la candidate reproductible sans modifier le parcours mail.
Les validations de graphes, les doubles externes et les opérations réelles sont
distingués dans la documentation de reprise.

## Coopération et adaptation au contexte

Les consignes du projet, l'architecture, la passation et le rapport récent du
parcours Drive/mail ont été consultés, ainsi que les instructions du portail et
les annonces partagées. Une intention puis une extension ont réservé les sources
et les nouveaux workflows. Les annonces des missions voisines ont été lues ;
leurs modifications et les brouillons existants ont été préservés.

Les nouvelles annonces d'une mission distincte sur la livraison de sites complets
ont été lues et son périmètre préservé. Elle ne justifie aucun changement de ses
sources par cette mission ; le contrat réellement publié du constructeur devra
être vérifié avant un futur essai web. Les tests réels restent séquentiels sur
l'hébergement partagé. Les extensions de réservation ont décrit les modules,
la copie publique et la préparation de lecture des diagnostics avant les écritures.

La clarification sur l'hébergement a conduit à conserver la cible et son verrou,
avec un futur essai réel séquentiel. Le serveur conserve le dépôt canonique ; le
poste sert de miroir de développement et de client navigateur. Les anciennes
réserves d'administration, la machine personnelle de contrôle et les accès privés
n'ont pas été élargis. Les détails opérationnels et preuves exactes restent dans
la passation privée ; ce rapport public ne contient ni données client ni accès.

Cette étape se clôt au stade de la préparation et de la publication du code.
Le message de fin libère les réservations propres et signale l'attente d'accord
de mise en service. Les réservations de la mission voisine sont préservées.
La réussite des tests et le push des sources ne constituent pas un déploiement.
