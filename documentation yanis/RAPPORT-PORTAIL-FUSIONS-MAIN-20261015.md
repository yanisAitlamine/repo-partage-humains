# Portail : vérification des PR et travail direct sur main — 15 octobre 2026

## Demande et résultat

L’utilisateur demande de vérifier les demandes de fusion existantes, de les
intégrer dans leur ordre de dépendance et de modifier les consignes du projet
pour que les futurs changements testés soient poussés directement sur main,
sans ouverture systématique de PR.

Une première PR était déjà fusionnée. Les trois autres ont été vérifiées puis
intégrées dans l’ordre : dialogue et maquettes, correctifs de parcours, support.
Leur destination a été ajustée vers main après intégration de leur dépendance.
Les corrections des parents ont été transmises aux branches suivantes par des
fusions ordinaires, sans réécrire leur historique. Les états de fusion ont été
relus côté GitHub ; aucune PR ouverte ne reste dans le dépôt concerné.

Les commentaires de revue n’ont pas été ignorés. Les sources corrigent la limite
de taille du contexte transmis, l’acceptation d’un résultat devenu obsolète,
la conservation inutile des copies de conversation dans les jobs terminés et
la duplication des prix dans le prompt. Les exports candidats limitent également
les voies d’exécution des workflows. La proposition de relance automatique n’est
pas appliquée : le contrat existant prévoit explicitement une nouvelle demande
volontaire, sans rejeu aveugle d’une opération potentiellement déjà partie.

Le contrôle d’accès aux workflows tient compte de la distinction expliquée dans
la [documentation officielle n8n sur MCP](https://github.com/n8n-io/n8n-docs/blob/main/docs/connect/connect-to-n8n-mcp-server.md).
Les modifications de sources ne prétendent pas modifier un workflow publié.
Une mise à jour coordonnée du workflow et du serveur est documentée pour le
nouveau champ de prix ; l’ancien validateur strict ne doit pas recevoir ce champ.

L’historique des anciens sites est de nouveau consultable depuis leur conversation,
y compris les événements enregistrés seulement dans l’activité et dépourvus de
nouveaux messages de cycle de vie. Un navigateur sur base fictive a vérifié
l’affichage d’une ancienne approbation et d’une ancienne demande acceptée.

Les consignes du dépôt, le guide de reprise, le backlog et le README prévoient
désormais les commits et pushes normaux sur main après revue et contrôles.
Aucune nouvelle PR n’est nécessaire sauf demande humaine explicite. La règle
préserve les modifications concurrentes, interdit les pushes forcés et le
contournement des protections. L’autorisation de déploiement d’une version
précise reste distincte. La mise à jour des consignes a été poussée directement
sur main, puis les références distante et locales ont été vérifiées.

Les 46 tests Python passent sur Windows et sur le serveur, ainsi que dix groupes
HTTP isolés, les deux contrôles hors ligne des workflows, TypeScript et la
compilation. Il n’existe pas de contrôle CI configuré sur les commits examinés :
ces preuves sont des exécutions locales, pas un statut CI inventé. Les corrections
de revue ne sont pas déployées par cette mission ; les services, workflows actifs
et données de production restent sur les versions précédemment approuvées.
Aucun mail ou appel modèle réel supplémentaire n’est effectué.

## Orchestration et délégation

Codex effectue directement l’inventaire des PR, la lecture des avis et des
différences, les corrections, les contrôles, les fusions, la mise à jour des
consignes et la synchronisation des sources. Aucun sous-agent, agent OpenCode ou
session PIAgentControl n’est lancé. Les avis automatiques GitHub sont des données
à examiner et ne remplacent pas les vérifications. Aucun coût ou gain n’est déduit.

## Coopération et adaptation au contexte

Les consignes et passations du portail ainsi que les annonces machine récentes
ont été consultées. Une intention et des extensions ont réservé le dépôt, les
corrections de revue et les documents propres à cette mission. Les travaux
concurrents sur le pipeline commercial, ses documents et les sites de test sont
préservés. Le fichier global protégé, les anciens rôles d’administration et la
machine de contrôle ne sont pas modifiés ni utilisés.

Une réponse de fusion a expiré après l’opération : le résultat a été vérifié par
l’état GitHub et le commit réellement présent sur main avant de poursuivre,
sans répéter aveuglément la mutation. Les copies de source propres ont été
avancées normalement ; les releases exécutées ne sont pas confondues avec ces
copies. Le navigateur et le serveur de test temporaires ont été fermés.
