> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 07 — Neovim, affichage, dépôts et déploiement reproductible

**Date : 10 octobre 2026 — Europe/Paris**
**Période principale : après le rapport OpenCode du 9 octobre à 21:54, jusqu'à la livraison des dépôts puis à cet audit.**

## 1. Combien de lignes et combien de temps pour un senior ?

Pour le travail du 9 octobre, prolongé après minuit, les trois dépôts livrés contenaient **4 006 lignes ajoutées et conservées dans Git** au moment de ta question. La correction trouvée pendant cet audit porte ce total à **4 007**.

| Catégorie | Avant cet audit | Ce que compte le chiffre |
| --- | ---: | --- |
| Scripts et code | 2 071 | Bash, Python, Lua et lanceurs ; commentaires et lignes vides compris |
| Tests | 1 094 | Tests de configuration, sauvegarde/restauration et cycle des services, test Docker séparé |
| Documentation et configuration | 841 | README, consignes NOC, JSON, YAML, unités systemd, exemples et fichiers Git |
| **Total** | **4 006** | Changements conservés dans les trois dépôts |

**Cette mesure comprend du code repris, des fichiers importés et des réécritures.** La première création d'un dépôt compte aussi ses fichiers existants comme des additions. Par exemple, les consignes NOC existaient avant la publication. Le chiffre ne mesure donc ni 4 006 lignes entièrement inventées aujourd'hui ni le nombre de commandes ayant modifié le serveur. Il exclut les versions intermédiaires remplacées, les scripts temporaires, les autres fichiers non suivis et les rapports conservés hors des dépôts.

Pour les commandes, l'analyse du journal local de cette conversation et de ses agents auxiliaires, arrêtée **avant ta demande à 00:06:06**, relève :

- **505 emplacements d'appel littéraux à l'outil d'exécution shell**, soit un ordre de grandeur de **500 soumissions de commandes** ;
- **2 397 lignes non vides d'entrée de commande extractibles** ;
- 23 appels dont le texte de commande n'est pas extrait par le lecteur simple, notamment lorsque l'argument est construit autrement ;
- une conversation principale et 13 conversations auxiliaires existant avant cette demande, avec déduplication des appels hérités. Le relevé trouve également une conversation auxiliaire créée pour l'audit, dont aucune action n'entre dans ces compteurs.

Ces entrées comprennent des lectures, transferts de fichiers, recherches, commandes Git, tests et scripts multiligne. Une ligne `python3 ...` peut exécuter un programme entier ; une boucle peut lancer plusieurs commandes. Un script écrit dans une commande multiligne augmente aussi le compteur de texte. **Le nombre exact de commandes exécutées à l'intérieur des programmes et des boucles n'est pas reconstituable avec ce seul comptage.** Les 505 et les 2 397 sont des mesures du journal d'orchestration, avec les limites ci-dessus. Les commandes de rédaction de ce rapport et le correctif d'audit sont postérieurs au périmètre compté.

### Estimation pour un ingénieur senior

Mon estimation de jugement pour reproduire le travail de la journée avec une qualité comparable est **16 à 32 heures, soit environ 2 à 4 journées de travail** pour un senior Linux/DevOps. Ce n'est pas une mesure de productivité issue du nombre de lignes.

| Travail | Ordre de grandeur |
| --- | ---: |
| Diagnostic de la pile, réseau/HTTPS, assistant et paramètres | 3–6 h |
| Portabilité du script de développement et intégration OpenCode | 4–6 h |
| Neovim, serveurs de langage, complétion et terminal | 2–4 h |
| Déploiement réutilisable, sauvegarde/restauration, tests et publication | 6–10 h |
| Rapports et documentation | 1–3 h |

La connaissance préalable de n8n, Docker et du Pi peut réduire cette durée. Des difficultés de réseau, d'API ou d'authentification peuvent l'allonger. Un essai complet sur Debian fraîchement réinstallé, comprenant le premier démarrage et HTTPS public, peut ajouter environ une journée. Cet essai complet reste à faire.

## 2. Point de départ du rapport

Le dernier rapport formel conservé localement est `DevLinuxSetup/RAPPORT-OPENCODE.md`, daté du 9 octobre, copie modifiée à **21:54:17**. Il couvrait déjà l'installation d'OpenCode 1.18.35, le profil GPT-6 Luna, les rôles d'agents et les contrôles de configuration. Le rapport 06, modifié à **18:13:54**, couvrait DuckDNS, HTTPS et la préparation de Gmail.

Ce rapport couvre principalement la configuration Neovim demandée ensuite, les corrections d'affichage, la publication de NOCAgent et n8n-services et le parcours d'installation sur une nouvelle machine. Il rappelle brièvement les changements antérieurs du script de développement pour rendre le résultat compréhensible.

Le rapport OpenCode a été supprimé du dépôt Git par ton commit `8685ee9`. Sa copie Windows sert ici de référence. Ce nouveau rapport est conservé **hors des trois dépôts Git**, dans le dossier de travail Windows.

## 3. État du service n8n actuel

La création du dépôt de déploiement n'a pas remplacé l'installation actuelle du Pi. Pendant les contrôles, les conteneurs de production `n8n-n8n-1` et `n8n-task-runners-1` sont restés en marche ; n8n est signalé **healthy**, avec environ six heures d'activité au contrôle de fin de livraison.


Depuis le rapport OpenCode, les principales modifications sur le Pi concernent les outils utilisateur, Neovim, tmux et les dossiers de projet. Le test Docker de déploiement a utilisé une instance temporaire avec son propre volume, son propre réseau et un port localhost aléatoire. Ce projet temporaire a été supprimé à la fin du test.

La connexion Gmail réelle n'est pas établie par ces travaux. Les rapports précédents fournissaient la préparation OAuth et un modèle de workflow ; la livraison de dépôts ne prouve ni un consentement Google ni une réception Gmail testée.

## 4. DevLinuxSetup : installation et configuration livrées

Le dépôt existant est DevLinuxSetup (référence d’exploitation retirée), privé, sur la branche `master`. Son dossier sur le Pi est `paramètre privé à consulter sur le Pi`.

La refonte antérieure au dernier rapport avait déjà remplacé l'ancien script par `DevLinuxSetup.sh`, séparé les choix de plateforme Debian/Kali/Ubuntu, amélioré la gestion des erreurs et évité le remplacement automatique de Docker. Elle avait aussi corrigé la dépendance `software-properties-common` qui bloquait ton Debian 13 et documenté les paramètres Git facultatifs.

Pour rappel, les variables Git précèdent directement la commande, sans barre de pipeline :

```bash
GIT_USER_NAME="Yanis Aitlamine" GIT_USER_EMAIL="[ADRESSE-MAIL]" bash DevLinuxSetup.sh
```

Une configuration Git déjà présente peut être conservée. Les informations personnelles ne sont pas exigées pour installer les outils.

La livraison finale ajoute le prérequis `openssh-client` et le guide reliant les trois dépôts. Le commit poussé pour cette partie est **`paramètre privé à consulter sur le Pi`**. Le contrôle local/distant a confirmé le même commit et un arbre propre.

OpenCode **1.18.35** est présent dans `paramètre privé à consulter sur le Pi`. Le profil est configuré avec GPT-6 Luna pour planifier, implémenter et relire. Aucun plafond fixe de trois agents n'a été remis après ton annulation de cette idée. Les permissions des rôles et la limitation de récursion sont décrites dans le rapport OpenCode.

La clé OpenAI d'OpenCode est à renseigner avec `/connect` au premier usage sur une nouvelle machine. L'installation du binaire et la validation du profil ne constituent pas un test de génération payante ni une mission NOC exécutée.

## 5. Neovim et complétion légère

Le binaire du Pi a été vérifié explicitement : **Neovim 0.12.5**, installé dans `paramètre privé à consulter sur le Pi` avec un lien `paramètre privé à consulter sur le Pi`. La configuration est sous `paramètre privé à consulter sur le Pi` et utilise LazyVim.

Une session SSH non interactive peut ne pas inclure `paramètre privé à consulter sur le Pi` dans son PATH. Le chemin explicite permet de vérifier l'installation sans conclure à tort que le programme est absent :

```bash
paramètre privé à consulter sur le Pi --version
paramètre privé à consulter sur le Pi --version
```

Trois profils sont livrés dans le dépôt et présents sur le Pi :

- `devlinuxsetup-completion.lua` : complétion discrète ;
- `devlinuxsetup-lsp.lua` : serveurs et diagnostics adaptés ;
- `devlinuxsetup-appearance.lua` : couleurs et éléments visuels lisibles.

### Comportement de la complétion

Les suggestions viennent principalement des serveurs de langage et des chemins de fichiers. Les propositions fondées sur tous les mots du buffer et les snippets automatiques sont désactivées. Le texte fantôme, la présélection et l'insertion automatique sont désactivés.

Le menu est limité à six lignes visibles, attend environ 180 ms et utilise généralement au moins deux caractères pour une suggestion automatique. Les caractères de déclenchement d'un langage, par exemple un point, gardent leur comportement utile.

En Markdown, texte et messages de commit, le menu ne s'ouvre pas automatiquement. On peut demander les suggestions avec **Ctrl+Espace**. **Entrée** conserve son rôle normal ; **Tab** ou **Ctrl+Y** accepte explicitement une proposition ; **Ctrl+E** ferme le menu. Les diagnostics ne sont pas ajoutés en permanence à la fin des lignes et ne se recalculent pas pendant la saisie. Les annotations intégrées et les code lenses sont désactivés.

### Serveurs présents

L'inventaire Mason du Pi confirme les paquets de serveurs Lua, Bash, Markdown/Marksman, Python/Pyright, JavaScript/TypeScript/vtsls, JSON, YAML, HTML et CSS. `stylua` et `shfmt` sont également présents pour le formatage. C/C++ utilise le `clangd` de la distribution lorsque disponible, pour éviter une archive Mason incompatible ARM64.

Les serveurs démarrent pour les types de fichiers concernés. Cela garde le lancement et la consommation plus légers. Le README consigne les contrôles précédents avec dix serveurs, les suggestions Python/TypeScript/Markdown et le démarrage sans erreur ; cet audit a vérifié à nouveau les fichiers et paquets présents, sans rejouer toute cette série interactive.

Avant les modifications, la configuration a été sauvegardée. Deux dossiers de sauvegarde existent sous `paramètre privé à consulter sur le Pi`, datés du 9 octobre à 22:39 et 23:00. L'option suivante permet de réappliquer le profil à LazyVim sans relancer toute l'installation des outils :

```bash
bash DevLinuxSetup.sh --neovim-config-only
```

## 6. Affichage : Neovim, tmux et PuTTY

Le problème de texte bleu sombre était lié à la chaîne terminal/tmux et au rendu des couleurs. Debian Lite dispose des capacités nécessaires pour afficher une palette lisible ; la légèreté de l'OS n'impose pas ce rendu.

Le thème Tokyo Night personnalisé emploie désormais un fond charbon opaque, un texte presque blanc, des commentaires plus lumineux, une ligne active visible et des sélections contrastées. Les numéros de ligne sont absolus et les marques d'espaces sont masquées. Le bloc géré dans `paramètre privé à consulter sur le Pi` configure les capacités RGB et une barre d'état sombre.

Sur Windows, le profil PuTTY enregistré `pi` utilise **JetBrainsMono NFM, taille 14**, UTF-8, `xterm-256color`, et les indicateurs de couleurs vraies/256 couleurs. Les fontes Regular/Bold sont présentes et enregistrées. Les anciens réglages ont été sauvegardés dans `.work/putty-pi-display-backup-paramètre privé à consulter sur le Pi-225953.json`.

Précision de l'audit : les indicateurs TrueColour et Xterm256Colour étaient déjà activés dans cette sauvegarde. Les changements portaient notamment sur la police, sa taille, l'annonce du terminal et la palette ; ce rapport ne prétend pas qu'un indicateur RGB auparavant désactivé a été découvert.

Le client tmux actuellement attaché annonce encore `xterm`, mais inclut RGB et UTF-8 dans ses capacités. Le profil PuTTY enregistré annonce `xterm-256color` pour une nouvelle connexion. Modifier le profil enregistré ne change pas automatiquement la police d'une fenêtre déjà ouverte : rouvrir cette connexion puis rattacher tmux applique le nouvel affichage.

## 7. NOCAgent : publication privée

Le dépôt NOCAgent (référence d’exploitation retirée) a été créé **privé**, avec une branche `main` et le commit **`paramètre privé à consulter sur le Pi`**.

Sur le Pi, le dossier existant reste `paramètre privé à consulter sur le Pi`. Un nouveau clone de GitHub est normalement nommé `NOCAgent`.

Le dépôt contient les consignes `AGENTS.md`, un README, un exemple `.env.example` sans valeurs sensibles et les exclusions Git. Le `.env` local est exclu et protégé ; les clés, sauvegardes d'agents et sorties locales ne sont pas publiées.

C'est l'espace de consignes à ouvrir dans OpenCode. La publication n'a pas exécuté une nouvelle mission NOC ni effectué de changements PlanetHoster/WordPress. Les accès externes et la session de navigateur restent à établir sur une nouvelle machine selon le README.

## 8. n8n-services : déploiement complet préparé

Le dépôt n8n-services (référence d’exploitation retirée) a été créé **privé**. Son premier commit est **`paramètre privé à consulter sur le Pi`**. Le correctif d'audit décrit plus bas porte la branche `main` à **`paramètre privé à consulter sur le Pi`**.

Le dossier du Pi est `paramètre privé à consulter sur le Pi`. L'installation neuve vise **Debian 13 trixie, ARM64/AMD64**, avec un utilisateur sudo, Git et un accès au dépôt privé. Les autres distributions sont refusées explicitement pour l'instant.

### Architecture des fichiers

| Fichier ou dossier | Utilité |
| --- | --- |
| `deploy.sh` | Coordonne les contrôles, paquets, Docker, Caddy, secrets, configuration et démarrage |
| `lib/platforms/debian13.sh` | Actions propres à Debian 13 ; emplacement prévu pour de futurs adaptateurs |
| `lib/render.py` | Génère les paramètres de la machine et protège la clé de chiffrement existante |
| `config/versions.sh` | Versions, digests d'images et checksums Caddy |
| `compose.yaml` | n8n, runners, volume persistant, disponibilité, arrêt propre et logs bornés |
| `templates/` | Unités systemd et dépendances de démarrage |
| `runtime/` | Démarrage, sauvegarde, extinction, restauration et vérification des archives |
| `tests/` | Tests reproductibles et intégration Docker optionnelle |


Le script refuse aussi une installation n8n existante non gérée, des unités Caddy/n8n étrangères ou un projet Docker n8n non géré. Ce refus a été vérifié sur le Pi avant toute installation de paquets.

Caddy dessert le domaine en HTTPS, avec une option d'accès par IP publique. n8n reste publié seulement sur `paramètre privé à consulter sur le Pi:5678`. Les secrets OpenAI et Daytona sont demandés de façon masquée ou lus depuis des fichiers privés ; ils ne sont pas envoyés dans les arguments de commande. La clé OpenAI de secours peut être conservée, mais aucun basculement automatique n'est configuré.

L'assistant reproduit le profil actuel : module `instance-ai`, modèle `openai/gpt-6-luna` et sandbox Daytona configuré. Son fonctionnement sur une nouvelle machine dépend de clés valides, d'un compte Daytona utilisable et des droits/crédits API du fournisseur.

### Démarrage et sauvegarde

Les unités n8n et Caddy sont activées au démarrage. Un contrôle préalable bloque le lancement de l'assistant si ses clés sont absentes ou vides.

Les quatre raccourcis existants sont conservés : démarrer, sauvegarder, redémarrer et éteindre. La sauvegarde ferme HTTPS, arrête proprement n8n puis les runners, vérifie SQLite, archive les données et la configuration privée, vérifie gzip et SHA256, puis marque le snapshot complet. L'extinction est annulée en cas d'échec et les services précédents sont rétablis autant que possible.

La restauration sur une machine neuve exige un volume vide et des services arrêtés. Elle vérifie les archives et refuse les chemins dangereux, les liens ou les données incohérentes. Elle conserve la clé de chiffrement originale et le domaine de la nouvelle machine. Elle vérifie que les images originales sont disponibles avant l'import et prévoit un retour arrière en cas d'erreur d'écriture ou d'interruption.

## 9. Correctif découvert pendant cet audit

Une incohérence a été trouvée entre le rapport 06 et le nouveau fichier Compose. Le rapport 06 indiquait `N8N_WEBHOOK_URL`, alors que le dépôt neuf utilisait encore `WEBHOOK_URL`.


Le fichier Compose a été corrigé et son test de rendu renforcé pour contrôler le nom exact et refuser l'ancien. **Les 32 tests ont été relancés avec succès**, la configuration Compose a été revalidée et le correctif a été commité puis poussé : **`fae35a5`**.

Le Pi actif utilisait déjà le bon nom. Ce correctif porte sur la recette pour les nouvelles machines. La validation initiale de syntaxe Compose ne suffisait pas à détecter un nom de variable ignoré par l'application ; c'est une limite concrète du premier contrôle, corrigée à partir du contrat réel de la version installée.

## 10. Contrôles réalisés et limites

| Contrôle | Résultat et portée |
| --- | --- |
| DevLinuxSetup | 35 tests documentés comme réussis lors des travaux, syntaxe vérifiée, dernière modification et test associés poussés |
| n8n-services | 32 tests réussis sur Debian 13 ARM64 ; nouvelle exécution réussie après le correctif d'audit |
| Syntaxe Bash | Scripts du dépôt vérifiés |
| Compose | Rendu base + assistant validé sans afficher les secrets |
| Caddy | Configuration générée domaine/IP acceptée par le validateur |
| systemd | Syntaxe des unités vérifiée avec le script préalable pointant vers le fichier du dépôt pour ce contrôle |
| Installation existante | Refus contrôlé avant changement des paquets |
| Docker isolé | n8n/runners ont démarré, disponibilité vérifiée, arrêt propre, schéma et intégrité SQLite vérifiés ; projet temporaire supprimé |
| Publication Git | Trois dépôts privés ; commits locaux/distants identiques et arbres propres à la livraison ; correctif n8n confirmé poussé ensuite |
| Production | n8n toujours healthy lors de l'audit |

**Ce qui n'a pas été validé par cette livraison :** une réinstallation complète de Debian, l'installation initiale de tous les paquets sur un hôte vide, le premier boot de cet hôte, l'émission publique de ses certificats, une restauration des données personnelles sur une autre machine, une requête payante du nouvel assistant, un nouveau login des deux utilisateurs sur une instance reconstruite ou une réception Gmail réelle.

Les tests de restauration utilisent des archives et clés artificielles. Le test Docker vérifie une instance neuve ; il ne constitue pas une répétition de toute l'installation système. Les clés et la base personnelles sont conservées sur le serveur et ne sont pas publiées dans GitHub.

## 11. Commandes principales et leur utilité

Ce tableau donne les commandes de contrôle et d'exploitation utiles. Les paramètres de dossiers temporaires varient entre les exécutions. Les commandes marquées « nouvelle machine » sont le parcours livré ; elles n'ont pas été toutes exécutées sur un système fraîchement réinstallé.

| Commande | Utilité / statut |
| --- | --- |
| `paramètre privé à consulter sur le Pi` | Vérifie explicitement le binaire Neovim installé, indépendamment du PATH |
| `paramètre privé à consulter sur le Pi` | Vérifie OpenCode ; version 1.18.35 confirmée |
| `bash DevLinuxSetup.sh --neovim-config-only` | Installe le profil léger dans un LazyVim existant avec sauvegarde préalable |
| `python3 -m unittest discover -s tests -v` | Exécute les 32 tests n8n-services, relancés après correction |
| `bash -n FICHIER` | Contrôle la syntaxe d'un script sans exécuter ses actions |
| `bash deploy.sh --render-only NOUVEAU_DOSSIER --assistant` | Génère une configuration de validation et des secrets factices sans installation |
| `docker compose ... config --quiet` | Valide les fichiers Compose générés ; ne publie pas leur contenu |
| `caddy validate --config FICHIER --adapter caddyfile` | Valide la configuration HTTPS sans lancer une émission publique de certificat |
| `systemd-analyze verify UNITES` | Contrôle les unités générées sans les installer dans le service actif |
| `sudo bash tests/integration-docker.sh` | Lance et nettoie l'instance Docker temporaire distincte de la production |
| `git diff --cached --check` | Contrôle le diff préparé avant commit |
| `git commit ...` puis `git push ...` | Enregistre et publie les sources autorisées |
| `gh repo create ... --private` | Crée chacun des deux nouveaux dépôts privés |
| `gh repo view ... --json name,isPrivate,url` | Vérifie l'identité, l'URL et la confidentialité du dépôt |
| `git ls-remote origin refs/heads/BRANCHE` | Compare le commit distant au commit local après push |
| `git status --porcelain` | Vérifie l'absence de modifications non enregistrées |
| `docker ps --format ...` | Vérifie l'activité et la santé des conteneurs de production |
| `bash deploy.sh --domain paramètre privé à consulter sur le Pi --assistant` | Nouvelle machine : installation complète avec saisie locale des clés |
| `bash deploy.sh --assistant --no-start` | Nouvelle machine : prépare une installation arrêtée pour restauration |
| `sudo bash runtime/restore.sh SNAPSHOT --dry-run` | Contrôle le snapshot sans importer les données |
| `sudo bash runtime/restore.sh SNAPSHOT` | Restaure sur un volume vide, services arrêtés |
| `./demarrer-n8n.sh` | Lance ou remet en service n8n, runners et HTTPS |
| `./sauvegarder-n8n.sh` | Sauvegarde puis rétablit l'état précédent des services |
| `./redemarrer-n8n.sh` | Sauvegarde et relance sans éteindre |
| `./eteindre-pi.sh` | Sauvegarde vérifiée puis extinction ; interruption de la connexion SSH |


## 12. Parcours prévu sur une nouvelle machine

1. Installer Debian 13 en 64 bits, Git/sudo, et donner à cette machine un accès GitHub au dépôt privé.
2. Mettre DuckDNS et la redirection Freebox TCP 443 vers cette machine. Une redirection encore dirigée vers l'ancien Pi ne suffit pas.
3. Cloner n8n-services et lancer `bash deploy.sh --domain paramètre privé à consulter sur le Pi --assistant`.
4. Créer les comptes dans le navigateur pour une instance vide ; ou choisir `--no-start`, restaurer un snapshot privé puis démarrer pour retrouver les comptes, workflows et identifiants existants.
5. Si nécessaire, cloner DevLinuxSetup et lancer son script complet, ou `--opencode-only` pour OpenCode seul.
6. Cloner NOCAgent, ouvrir son dossier puis lancer `paramètre privé à consulter sur le Pi` ; fournir les accès nécessaires localement.

Le README n8n-services contient les étapes détaillées, les options, l'organisation des fichiers privés et les adaptations futures des distributions.

## 13. Sources de cet audit

- Rapports locaux 06 et OpenCode, avec leurs dates de fichiers.
- Diffs et historiques Git du Pi, états locaux/distants et visibilité GitHub.
- Sources finales des trois dépôts ; le commit utilisateur `8685ee9` reste identifié comme tel.
- Versions explicites de Neovim/OpenCode, inventaire Mason, profils PuTTY/tmux et sauvegardes de configuration.
- Sorties des 32 tests, validations Compose/Caddy/systemd et test Docker temporaire.
- Code de configuration de n8n 2.42.6 installé sur le Pi, plus test artificiel du nom de variable webhook.
- Journal local de cette conversation et de ses agents, analysé pour les compteurs sans publier les valeurs sensibles. Les compteurs techniques sont enregistrés dans `.work/audit-command-counts.json`.

**Aucune valeur de secret n'est incluse dans ce rapport.** Le document est enregistré dans le dossier de travail Windows et n'est pas ajouté aux dépôts Git.
