# Laboratoire Héphaïstos isolé — 20 octobre 2026

## Demande et résultat

La demande autorise un laboratoire dédié pour préparer une version passant une recette complète sans Telegram, en préservant les deux productions. Cette intervention porte sur le provisionnement et le runtime ; la correction applicative et la recette client restent une mission coordonnée distincte.

Une nouvelle VM Debian a été créée depuis le template propre. Les autres laboratoires et machines existantes sont préservés. Son amorçage utilise uniquement la clé publique personnelle autorisée, ses comptes de test et ses nouvelles identités locales. Aucun credential, workflow, consommateur ou historique de production n’est importé. L’accès SSH est épinglé, le mot de passe root verrouillé et les services applicatifs écoutent seulement en boucle locale, derrière un pare-feu dédié.

Le runtime comprend Node22, Python, PHP avec SQLite, Chromium, les dépendances Playwright verrouillées et un CLI OpenCode natif de version compatible. Une cible d’hébergement locale distincte respecte le contrat de rangement du CMS. Le frontal HTTPS possède sa propre autorité de test. Les erreurs initiales de permissions du certificat, d’extensions X509 strictes, d’imports MCP et de résolution DNS ont été corrigées uniquement dans le lab.

Vérifications réelles : connexion SSH, interrogation SQLite par PHP, égalité de l’index SSH et HTTPS, validation TLS stricte, lancement de Chromium avec sandbox et capture d’écran. Le serveur MCP démarre et annonce ses neuf outils sans appel de modèle ni invocation de job ou de cible. Les recettes Ansible dédiées ont été appliquées sans échec ; leur orchestration finale est validée syntaxiquement. Aucun ancien rôle réservé n’a été exécuté.

Ces preuves valident le runtime. Elles ne constituent ni une livraison de site client, ni un test fournisseur IA authentifié. Le CLI est installé sans import de connexion fournisseur ; les profils et une éventuelle nouvelle authentification restent à la recette. Aucun prompt payant n’a été lancé par cette intervention.

## Orchestration et délégation

Codex réalise directement le provisionnement, les recettes, les contrôles et la documentation. Aucun sous-agent ni session OpenCode n’est lancé. Une autre conversation, autorisée par l’utilisateur, conduit les corrections applicatives et la recette. Elle transmet les contrats attendus du frontend HTTPS, du stockage CMS et des dépendances ; les périmètres sont coordonnés avant chaque adaptation.

Les imports manquants proviennent d’une révision Git exacte, avec comparaison des blobs et empreintes avant installation. Les fichiers existants différents sont refusés. L’installation native utilise la distribution documentée par [OpenCode](https://opencode.ai/docs/fr/), sans exécuter ses scripts d’installation, puis vérifie uniquement sa version.

## Coopération et adaptation au contexte

La nouvelle séparation entre production et laboratoire remplace l’ancien usage du Pi comme lab. Les consignes, les annonces et les réservations pertinentes ont été consultées. La machine de contrôle personnelle et les sources applicatives concurrentes sont préservées. L’environnement déjà nommé « stage » n’est pas réutilisé faute d’état suffisamment attesté ; une nouvelle cible est réservée avant création.

Les sources des recettes sont préparées et vérifiées dans le lab, puis intégrées normalement dans Git. Les copies lisibles des échanges de délégation sont archivées en privé comme copies d’audit, sans prétention de déchiffrement natif. La documentation privée conserve les accès, l’ordre des opérations et l’inventaire des nouvelles clés sans leurs valeurs. Le lab reste remplaçable : cette opération ne crée pas une sauvegarde chiffrée indépendante de ses identités.
