# Rapport 28 — Quatre références privées et guide Ansible

13 octobre 2026. Compte rendu public sans cartographie d'accès, valeurs de
secrets, identifiants métier ou fichiers de conversation.

## Demande et résultat

Yanis demande d'abord un guide Ansible très détaillé pour comprendre les
scripts, leurs appels et leur utilisation depuis son contrôleur personnel.
Il interrompt ensuite la rédaction faute de budget, puis la reprend en
ajoutant un quatrième document sur les fichiers de configuration des agents.
Il demande d'alléger l'architecture, de répartir les détails par sujet et
d'indiquer le versionnement et la sauvegarde pour chaque fichier décrit.

Le dépôt personnel privé conserve désormais quatre documents :
ARCHITECTURE.md, secrets.md, GUIDE-ANSIBLE.md et CONFIGURATION-AGENTS.md.
L'architecture devient une vue d'ensemble et un catalogue d'exploitation ;
les secrets, playbooks et configurations d'agents ont leurs références
spécialisées. Des liens permettent de passer de l'une à l'autre.

Le guide décrit les points d'entrée, groupes d'inventaire, rôles, imports,
templates, handlers, helpers, options et effets des commandes. Il donne des
parcours futurs pour préparer une cible jetable, modifier le code, administrer
les services installés ou préparer une restauration. Son catalogue couvre
93 fichiers Ansible lus dans les trois dépôts et migrations complémentaires,
avec les noms de tâches/modules permettant de les retrouver dans les sources.

Il distingue le provisionnement neuf de l'exploitation et précise que la
recette historique ne sait pas adopter la production existante ni reconstruire
seule tous ses composants récents. Les migrations initiales à empreintes
fixes ne deviennent pas des commandes de maintenance récurrente.

Le document agents couvre Codex, règles du projet, profils et bases OpenCode,
wrapper et références de coopération. Les chats, conversations, exports de
sessions et journaux individuels sont exclus. Les authentifications sont
renvoyées à l'inventaire des secrets, sans leurs valeurs.

Chaque catalogue distingue fichier suivi, modification locale, copie installée
hors Git, source récupérable, sauvegarde datée et copie indépendante non
attestée. Des ajouts récents présents dans les dossiers de sources ne sont
pas suivis au contrôle ; ils ne sont donc pas présentés comme publiés sur GitHub.
Une ancienne sauvegarde ne garantit pas l'état courant d'une configuration.

## Orchestration et délégation

Codex effectue directement la collecte autorisée de sources publiques, les
lectures de configuration sélectionnées, l'analyse des appels, la rédaction
et la revue documentaire. Aucun agent OpenCode ou sous-agent n'est lancé :
le travail porte sur les documents et leurs preuves, sans implémentation
applicative, et conserve les opérations privées sous contrôle de l'opérateur.
Aucun coût ou gain n'est inventé.

Un outil local construit les annexes à partir des textes publics examinés :
noms des tâches, modules, imports et métadonnées Git. Ce relevé textuel n'est
pas une validation YAML et ne remplace pas les conditions héritées des parents.
Les sections explicatives françaises et les chaînes principales sont rédigées
et relues par Codex. Des corrections de description et d'appels de rôle sont
intégrées avant publication.

La compétence OpenAI Docs est utilisée pour le rôle des consignes Codex et
de la configuration MCP, avec pages officielles consultées. La documentation
officielle Ansible et OpenCode complète les explications générales ; les faits
propres au projet viennent des sources courantes et de la documentation datée.

## Coopération et adaptation au contexte

Les consignes globales, architecture, passation, dernier rapport utile, README
des dépôts et guides Ansible ont été lus dans cette mission et sa première
phase. La reprise réutilise le snapshot préparé au lieu de recommencer sa
collecte ; une comparaison des empreintes confirme que les fichiers Ansible
examinés n'ont pas changé entre les phases.

Le protocole et les annonces récentes sont relus. Ils indiquent des travaux
concurrents sur des copies candidates et essais isolés ; ces activités ne
prouvent pas une nouvelle capacité de production. Leurs fichiers applicatifs
ne sont pas modifiés. Les contraintes de contrôleur personnel et de tests
réservés à Yanis restent intactes.

Une mission parallèle a publié les sources VPN dans un dépôt privé dédié.
Ses métadonnées Git sont confirmées et la documentation distingue cette
récupération des recettes d'une sauvegarde des configurations installées.
Son rapport public et une autre mission de préparation de déclenchement mail
sont préservés ; aucun candidat en cours n'est présenté comme déjà déployé.

La session déclarative codex_guide_ansible_20261013 reprend explicitement son
intention restée ouverte après l'arrêt humain, puis annonce les quatre documents
et leurs réservations. La nouvelle demande autorise quatre références et
remplace l'ancienne limite de deux sans réouvrir la publication de secrets.
Le global Windows protégé et les configurations actives d'agents ne sont pas
modifiés ; la passation et les consignes du dépôt documentaire public indiquent
la nouvelle organisation. Les fichiers locaux antérieurs sont conservés avant
restructuration afin de préserver leur contenu historique.

Les annonces sont vérifiées avant publication. La fin de session libère les
réservations et distingue les documents publiés des modifications locales
préexistantes qui ne sont pas poussées en bloc.

## Contrôles et limites

Visibilité privée contrôlée avant publication, lecture ciblée de git ls-files
et status, comparaison des empreintes Ansible, présence des 93 entrées,
cohérence des liens entre les quatre fichiers, délimiteurs Markdown et formats
connus de secrets vérifiés. Le diff est relu et contrôlé avant commit/push.
Un scan lexical ne constitue pas une preuve universelle d'absence de secret.

Aucune connexion au contrôleur personnel, aucun playbook, syntax-check, lint,
mode check, parseur YAML, suite applicative, service, workflow ou site n'est
lancé pour rédiger cette documentation. Les commandes proposées sont des
exemples futurs pour Yanis, pas des essais déjà réussis. Les fichiers de
credentials et valeurs de secrets ne sont pas ouverts ; les portions fournisseur
des JSON publics de configuration ne sont pas reproduites.

Le contrôle des sources ne prouve ni sauvegarde indépendante actuelle de
tous les fichiers, ni validité des identités, ni restauration complète.
Les statuts non attestés sont indiqués, sans créer une sauvegarde ni publier
les fichiers applicatifs non suivis. Les documents privés sont publiés dans
le dépôt privé et ce rapport seulement dans le dépôt public partagé.
