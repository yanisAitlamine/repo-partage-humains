<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 1 — Installation de n8n et journal des commandes

**Projet :** Raspberry Pi de Yanis — **date du rapport :** 9 octobre 2026, Europe/Paris.

**Périmètre : première installation, avant publication Internet.** La mise en ligne
ultérieure, les comptes et la remise des accès sont documentés dans le
[rapport 3](RAPPORT-03-mise-en-ligne-realisee.md).

Ce rapport reconstitue les opérations de cette conversation : installation, corrections, vérifications et préparation documentaire. Les commandes sont présentées avec leur lieu d'exécution, leur utilité et leur résultat. Les contrôles répétés sont regroupés, mais les variantes utiles et les échecs sont conservés. Les secrets ne sont pas reproduits. Ce document contient des informations sur le réseau local : le garder avec la documentation du projet.

## 1. Résultat obtenu et limites des vérifications

n8n **2.42.5** fonctionne sur Debian 13, architecture ARM64. Docker Engine **29.9.0** et Docker Compose **5.6.0** sont installés. Deux conteneurs tournent : `n8n-n8n-1` et `n8n-task-runners-1`.

Le service n8n utilise le volume Docker `n8n_n8n_data`, monté sur `paramètre privé à consulter sur le Pi`. Le service de code séparé annonce les lanceurs JavaScript et Python et s'est enregistré auprès de n8n. Le Pi héberge la configuration dans `paramètre privé à consulter sur le Pi`.

Le contrôle `/healthz/readiness` a répondu `{"status":"ok"}` ; l'interface a répondu HTTP 200 depuis Windows. Le conteneur n8n est déclaré `healthy`. Le redémarrage automatique est configuré et Docker est activé au démarrage. **Un redémarrage complet du Pi, une restauration de sauvegarde et l'exécution d'un workflow métier n'ont pas été testés.** Les lanceurs se sont enregistrés, mais un bloc de code JavaScript/Python n'a pas été exécuté pour validation fonctionnelle.

À ce stade, n8n écoute sur **paramètre privé à consulter sur le Pi:5678 du Pi**, et l'accès Windows passe par un tunnel SSH. L'installation ne constitue pas une publication Internet. Aucune règle Freebox n'a été créée par l'assistant. L'état réel des anciennes règles de la Freebox n'a pas pu être lu.

## 2. État initial découvert

| Élément | Observation |
|---|---|
| Dossier Windows | `paramètre privé à consulter sur le Pi` |
| Fichiers initiaux du projet | `.env` et `.keys/id_rsa` |
| Hôte déclaré | `[HOTE-LOCAL]` |
| Compte SSH | `yanis` |
| Clé initialement référencée | copie `.keys/id_rsa` du projet |
| Original de la clé | `paramètre privé à consulter sur le Pi` |
| Comparaison des deux clés | empreintes de fichier identiques |
| Système du Pi | Debian GNU/Linux 13, trixie, ARM64/aarch64 |
| Mémoire | environ 7,6 Gio |
| Stockage avant installation | partition d'environ 117 Gio, 108 Gio disponibles |
| Docker avant installation | absent |
| Accès sudo de `yanis` | fonctionne sans demande de mot de passe |
| Adresse LAN observée | `paramètre privé à consulter sur le Pi` |
| Passerelle | `paramètre privé à consulter sur le Pi` |
| Connexion active | Wi-Fi, interface `wlan0` |
| MAC Wi-Fi | `[ADRESSE-MAC-ANONYMISEE]` |

L'ancien alias `raspberrypi` dans la configuration SSH Windows désigne `paramètre privé à consulter sur le Pi`. Il n'a pas été utilisé pour le déploiement et n'a pas été modifié. L'accès repose sur `[HOTE-LOCAL]`, qui évite cette adresse ancienne.

## 3. Convention des commandes SSH

La plupart des commandes distantes ont été lancées depuis PowerShell avec cette forme :

```powershell
ssh -o BatchMode=yes -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" [ADRESSE-MAIL] 'commande distante'
```

| Élément | Utilité |
|---|---|
| `ssh` | Exécuter une commande sur le Pi à travers une connexion chiffrée. |
| `BatchMode=yes` | Échouer au lieu d'attendre un mot de passe ou une interaction. |
| `StrictHostKeyChecking=yes` | Vérifier le serveur à partir des clés déjà connues, sans accepter silencieusement une nouvelle identité. |
| `ConnectTimeout=10` lorsqu'il est présent | Limiter à dix secondes l'attente de connexion. |
| `-i ...id_rsa` | Désigner le fichier de clé ; son contenu n'est pas affiché. |
| `[ADRESSE-MAIL]` | Utilisateur et nom du Pi. |

Les commandes distantes montrées ci-dessous sont celles qui se trouvaient entre les apostrophes, ou dans le script envoyé à SSH. `;` sépare plusieurs contrôles dans une même connexion. `&&` n'exécute la suite que si la première commande réussit. `2>paramètre privé à consulter sur le Pi` masque des erreurs attendues sur des fichiers ou paquets absents.

## 4. Découverte des fichiers et instructions locales

### 4.1 Repérer le dossier et les fichiers pertinents — Windows

```powershell
Get-Location
rg --files -g AGENTS.md -g '*ssh*' -g '*rasp*' -g '*n8n*' -g '*.md' -g '*.txt' -g '*.yml' -g '*.yaml' -g '*.env*' -g '*key*' -g 'id_*'
```

`Get-Location` confirme le dossier de travail. `rg --files` cherche les noms de fichiers correspondant aux indices du projet, notamment les instructions `AGENTS.md`, configurations et clés. Il a trouvé `.env` et `.keys/id_rsa`. Aucun `AGENTS.md` n'a été trouvé dans le projet par cette recherche.

### 4.2 Lire les paramètres sans afficher de secret évident — Windows

```powershell
Get-ChildItem -Force | Select-Object Mode,Length,Name
Get-Content .env | ForEach-Object {
# Détail d’exploitation retiré de la version publique.
    ($_ -split '=',2)[0] + '=<masqué>'
  } else { $_ }
}
if (Test-Path .git) { git status --short; git ls-files }
Get-Command ssh,scp -ErrorAction SilentlyContinue | Select-Object Name,Source
Get-ChildItem paramètre privé à consulter sur le Pi -Force -ErrorAction SilentlyContinue | Select-Object Name,Length
```

| Commande | Utilité et résultat |
|---|---|
| `Get-ChildItem -Force` | Liste aussi les éléments cachés. |
| `Test-Path .git` | Vérifie si le projet est un dépôt Git. Le bloc Git n'a pas produit de liste de fichiers suivis. |
| `git status --short` / `git ls-files` | Auraient inspecté les modifications et fichiers suivis si `.git` était présent. |
| `Get-Command ssh,scp` | Confirme la disponibilité des outils de connexion et transfert. |
| Liste de `.ssh` | Confirme la présence de l'original `id_rsa`, sans lire son contenu. |

### 4.3 Chercher les consignes parentes, lire la configuration SSH et comparer les clés

```powershell
$paths = @(
  'paramètre privé à consulter sur le Pi
  'paramètre privé à consulter sur le Pi
  'paramètre privé à consulter sur le Pi
  'paramètre privé à consulter sur le Pi
  'paramètre privé à consulter sur le Pi
  'paramètre privé à consulter sur le Pi
)
foreach ($p in $paths) {
  if (Test-Path -LiteralPath $p) {
    Write-Output $p
    Get-Content -LiteralPath $p
  }
}
Get-Content paramètre privé à consulter sur le Pi
$same = (Get-FileHash .keys\id_rsa).Hash -eq (Get-FileHash paramètre privé à consulter sur le Pi).Hash
Write-Output "Clés identiques: $same"
```

`Test-Path` évite de lire un fichier absent. `Get-FileHash` calcule localement des empreintes ; la sortie a seulement montré **True** pour la comparaison, pas le contenu ni les empreintes. La lecture de `config` a révélé l'ancien alias SSH mentionné plus haut.

## 5. Diagnostic initial du Raspberry Pi

Première connexion avec l'original de la clé :

```powershell
ssh -o BatchMode=yes -o StrictHostKeyChecking=yes -o ConnectTimeout=10 -i "paramètre privé à consulter sur le Pi" [ADRESSE-MAIL] 'uname -m; cat paramètre privé à consulter sur le Pi; free -h; df -h /; command -v docker; sudo -n true; ss -ltn; ls -d paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi 2>paramètre privé à consulter sur le Pi'
```

| Commande sur le Pi | Utilité | Résultat |
|---|---|---|
| `uname -m` | Identifier l'architecture | `aarch64`, compatible ARM64. |
| `cat paramètre privé à consulter sur le Pi` | Identifier distribution et version | Debian 13 trixie. |
| `free -h` | Vérifier la mémoire disponible | Ressources suffisantes pour ce démarrage. |
| `df -h /` | Vérifier la place disque | Plus de 100 Gio libres au départ. |
| `command -v docker` | Rechercher Docker | Absent. |
| `sudo -n true` | Tester sudo sans interaction | Fonctionne. |
| `ss -ltn` | Lister les ports TCP en écoute | SSH sur 22 ; n8n absent. |
| `ls -d paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi` | Chercher une installation existante | Dossiers non trouvés. |

La connexion a fonctionné. Le code global de cette commande était 1, car le dernier `ls` ne trouvait pas les dossiers ; ce n'était pas un échec d'authentification SSH.

Deuxième diagnostic :

```sh
sudo -n true && echo SUDO_OK
dpkg-query -W docker.io docker-ce containerd runc 2>paramètre privé à consulter sur le Pi
ls paramètre privé à consulter sur le Pi
hostname -I
systemctl is-active ssh
command -v curl
command -v openssl
```

`dpkg-query` recherche les paquets susceptibles d'entrer en conflit avec Docker. `ls` inspecte les dépôts de paquets. `hostname -I` relève les adresses. `systemctl` confirme SSH actif. `curl` et `openssl` sont déjà présents. Aucun paquet conflictuel n'a été désinstallé par l'assistant.

## 6. Installation de Docker

Le script suivant a été construit dans une variable PowerShell `$installScript`, puis envoyé au Pi :

```sh
set -eu
sudo apt-get update -qq
sudo apt-get install -y -qq ca-certificates curl
sudo install -m 0755 -d paramètre privé à consulter sur le Pi
sudo curl -fsSL paramètre privé à consulter sur le Pi -o paramètre privé à consulter sur le Pi
sudo chmod a+r paramètre privé à consulter sur le Pi
sudo tee paramètre privé à consulter sur le Pi >paramètre privé à consulter sur le Pi <<'EOF'
Types: deb
URIs: paramètre privé à consulter sur le Pi
Suites: trixie
Components: stable
Architectures: arm64
Signed-By: paramètre privé à consulter sur le Pi
EOF
sudo apt-get update -qq
sudo apt-get install -y -qq docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl enable --now docker
sudo docker version --format '{{.Server.Version}}'
sudo docker compose version
```

Enveloppe Windows utilisée :

```powershell
$installScript.Replace("`r", '') | ssh -o BatchMode=yes -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" [ADRESSE-MAIL] 'bash -s'
```

| Ligne ou option | Utilité |
|---|---|
| `set -e` | Arrêter le script si une commande échoue. |
| `set -u` | Arrêter le script lorsqu'une variable non définie est utilisée. |
| `apt-get update` | Mettre à jour l'index des paquets, sans mise à niveau générale du Pi. |
| `-qq` | Réduire la sortie. |
| `install -y` | Accepter l'installation des paquets listés sans interaction. |
| `ca-certificates curl` | Fournir les certificats système et l'outil de téléchargement HTTPS. |
| `install -m 0755 -d` | Créer le dossier des clés de dépôt, avec droits adaptés. |
| `curl -fsSL ...docker.asc` | Télécharger la clé de signature du dépôt Docker officiel. |
| `chmod a+r` | Permettre aux outils de paquets de lire cette clé publique. |
| `tee ...docker.sources` | Écrire la définition du dépôt Debian officiel, limitée à ARM64/trixie. |
| `Signed-By` | Associer ce dépôt à sa clé de signature. |
| `docker-ce` | Installer le moteur Docker. |
| `docker-ce-cli` | Installer le client. |
| `containerd.io` | Installer le moteur de gestion des conteneurs. |
| `docker-buildx-plugin` | Installer le composant de construction d'images fourni avec Docker. |
| `docker-compose-plugin` | Installer le composant de déploiement Compose. |
| `systemctl enable --now docker` | Démarrer Docker et l'activer aux prochains démarrages. |
| `docker version --format ...` | Afficher la version du moteur, sans toutes les métadonnées. |

**Incident corrigé :** PowerShell a ajouté un retour chariot à la fin du flux transmis. La dernière ligne est arrivée comme `docker compose version\r` et a échoué. Docker était néanmoins installé et actif. Les scripts suivants ont utilisé `tr -d "\r" | bash -s` côté Pi pour supprimer les retours chariot Windows. La commande de version a ensuite réussi.

Référence de la méthode : [installation Docker sur Debian](https://docs.docker.com/engine/install/debian/).

## 7. Vérification de la clé Windows et suppression du doublon

### 7.1 Vérifier le port local, l'agent et les permissions

```powershell
Get-NetTCPConnection -LocalPort 5678 -ErrorAction SilentlyContinue | Select-Object LocalAddress,State,OwningProcess
Get-Service ssh-agent | Select-Object Name,Status,StartType
(Get-Acl "paramètre privé à consulter sur le Pi").Access | Select-Object IdentityReference,FileSystemRights,IsInherited
Get-ChildItem .keys -Force | Select-Object Name,Length
```

Le port 5678 local était disponible. L'agent SSH Windows était arrêté et désactivé. `Get-Acl` consulte les permissions NTFS. Une lecture détaillée ultérieure a confirmé des droits explicites pour `yanis`, le système et les administrateurs. Aucun changement de ces permissions n'a été fait.

### 7.2 Modifier le chemin de la clé dans `.env`

```powershell
$envPath = Join-Path (Get-Location) '.env'
$envText = [IO.File]::ReadAllText($envPath)
$envText = [regex]::Replace($envText, '(?m)^KEYFILE=.*$', 'KEYFILE=paramètre privé à consulter sur le Pi
[IO.File]::WriteAllText($envPath, $envText, [Text.UTF8Encoding]::new($false))
```

Cette modification a réussi. `Join-Path` construit le chemin du `.env`. La substitution remplace uniquement la ligne `KEYFILE`. `WriteAllText` réécrit le texte en UTF-8 sans BOM. Le contenu de la clé reste à l'extérieur du projet.

### 7.3 Première tentative de supprimer la copie

```powershell
$copiedKey = (Resolve-Path -LiteralPath '.keys\id_rsa').Path
$originalKey = (Resolve-Path -LiteralPath "paramètre privé à consulter sur le Pi").Path
$projectRoot = (Get-Location).Path
if ($copiedKey -ne (Join-Path $projectRoot '.keys\id_rsa')) { throw 'Chemin de la copie inattendu' }
if ((Get-FileHash -LiteralPath $copiedKey).Hash -ne (Get-FileHash -LiteralPath $originalKey).Hash) { throw 'Les cles different' }
Remove-Item -LiteralPath $copiedKey
Write-Output 'Copie du projet supprimee, original conserve.'
(Get-Acl -LiteralPath $originalKey).Access | Format-List IdentityReference,FileSystemRights,IsInherited
```

`Resolve-Path` vérifie le chemin réel. Les deux conditions empêchent de viser un autre fichier ou de supprimer une clé différente. **La suppression a échoué** : le fichier est caché et la suppression standard a été refusée. Le message `Copie ... supprimee` affiché ensuite était erroné : PowerShell a poursuivi après une erreur non bloquante. Il ne constitue pas une preuve de suppression.

### 7.4 Deuxième tentative rejetée avant exécution

Une commande contenant `$ErrorActionPreference = 'Stop'`, les mêmes contrôles et :

```powershell
Remove-Item -Force -LiteralPath $copiedKey
if (Test-Path -LiteralPath $copiedKey) { throw 'Suppression non effectuee' }
```

a été **rejetée par le contrôle automatique d'approbation avant exécution**. Le refus indiquait `blocked by policy`, sans explication plus détaillée. La création du dossier distant et le transfert qui figuraient aussi dans cette commande n'ont pas été exécutés par cet appel ; ils ont été effectués séparément ensuite.

La copie `.keys/id_rsa` existe encore lors de la rédaction du rapport, avec les attributs `Hidden, Archive`. La clé originale n'a jamais été supprimée, remplacée, transférée au Pi ou affichée. Sa phrase de passe et l'activation de l'agent n'ont pas été modifiées par l'assistant.

## 8. Fichiers créés par édition locale

Les fichiers ont été écrits avec l'outil d'édition du workspace, pas par une commande shell qui manipulerait des secrets.

| Fichier | Rôle |
|---|---|
| `compose.yaml` | Décrit n8n, ses données, son contrôle de santé et le service de code. |
| `.gitignore` | Exclut `.keys/`, `.env`, `.env.*` sauf `.env.example`, les clés courantes, `.pem`, `.ppk` et `backups/`. |
| `ouvrir-n8n.ps1` | Ouvre le tunnel SSH depuis Windows. |
| `README-n8n.md` | Explique l'accès, l'entretien, un exemple de sauvegarde et les pratiques SSH. |
| Les deux rapports | Documentent les travaux et la future publication. |

Un `.gitignore` protège des futurs ajouts à Git ; il ne chiffre pas les fichiers et ne retire pas une clé d'un ancien historique.

## 9. Création du dossier distant et transfert

```powershell
ssh -o BatchMode=yes -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" [ADRESSE-MAIL] 'mkdir -p paramètre privé à consulter sur le Pi; chmod 700 paramètre privé à consulter sur le Pi'
scp -o BatchMode=yes -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" compose.yaml [ADRESSE-MAIL]:n8n/compose.yaml
```


Le même `scp` a été exécuté une deuxième fois après l'ajout du service de code au Compose.

## 10. Première mise en service de n8n

Script envoyé au Pi dans `$deployScript` :

```sh
set -eu
cd "paramètre privé à consulter sur le Pi"
sudo docker compose version
sudo docker pull docker.n8n.io/n8nio/n8n:stable >pull.log 2>&1 || { tail -20 pull.log; exit 1; }
image=$(sudo docker image inspect docker.n8n.io/n8nio/n8n:stable --format '{{index .RepoDigests 0}}')
umask 077
if [ ! -f .env ]; then
  printf 'N8N_IMAGE=%s\paramètre privé à consulter sur le Pi=%s\n' "$image" "$(openssl rand -hex 32)" > .env
fi
chmod 600 .env
sudo docker compose config --quiet
sudo docker compose up -d
sudo docker compose ps
```

Enveloppe corrigée :

```powershell
$deployScript | ssh -o BatchMode=yes -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" [ADRESSE-MAIL] 'tr -d "\r" | bash -s'
```

| Commande | Utilité |
|---|---|
| `cd "paramètre privé à consulter sur le Pi"` | Travailler dans le dossier distant, indépendamment du dossier de connexion. |
| `docker pull ...:stable` | Télécharger la version stable officielle compatible avec le Pi. |
| `>pull.log 2>&1` | Enregistrer la progression et les erreurs dans un fichier local au Pi. |
| `|| { tail ...; exit 1; }` | Montrer l'erreur et arrêter en cas d'échec du téléchargement. |
| `docker image inspect ...RepoDigests` | Récupérer l'empreinte immuable de l'image téléchargée. |
| `umask 077` | Restreindre par défaut les droits des nouveaux fichiers au propriétaire. |
| `if [ ! -f .env ]` | Ne pas remplacer une clé n8n déjà créée. |
| `openssl rand -hex 32` | Générer sur le Pi une clé aléatoire de 256 bits pour le chiffrement n8n. |
| `printf ... > .env` | Enregistrer l'image et la clé sur le Pi sans les afficher. |
| `chmod 600 .env` | Lecture/écriture pour le propriétaire seulement, hors root. |
| `docker compose config --quiet` | Valider la configuration sans imprimer les variables secrètes. |
| `docker compose up -d` | Créer réseau/volume/conteneur et démarrer en arrière-plan. |
| `docker compose ps` | Afficher l'état des services. |
| `tr -d "\r"` | Retirer les retours chariot du flux PowerShell avant Bash. |

L'image stable obtenue est n8n 2.42.5, figée à :

```text
docker.n8n.io/n8nio/n8n@paramètre privé à consulter sur le Pi
```

L'empreinte d'image n'est pas un secret. La valeur de `paramètre privé à consulter sur le Pi`, elle, n'est pas reproduite dans ce rapport.

## 11. Configuration appliquée et utilité de chaque réglage

### Service n8n

| Réglage | Effet |
|---|---|
| `image: ${N8N_IMAGE:?...}` | Utiliser l'image figée ; échouer si la variable manque. |
| `restart: unless-stopped` | Relancer après interruption ou démarrage du moteur, sauf arrêt volontaire. Ce réglage ne relance pas à lui seul un conteneur simplement marqué `unhealthy`. |
| `paramètre privé à consulter sur le Pi:5678:5678` | Publier l'interface uniquement sur la boucle locale du Pi. |
| `TZ`, `GENERIC_TIMEZONE: Europe/Paris` | Régler fuseau système et planification n8n. |
| `N8N_HOST: localhost` | Utiliser le nom correspondant à l'accès par tunnel. |
| `N8N_PORT: 5678` | Port d'écoute dans le conteneur. |
| `N8N_PROTOCOL: http` | HTTP dans l'installation locale actuelle. SSH chiffre le transport PC–Pi. |
| `paramètre privé à consulter sur le Pi` | URL de l'interface annoncée par n8n. |
| `N8N_WEBHOOK_URL` | Base des URL de webhooks ; actuellement locale. |
| `paramètre privé à consulter sur le Pi: true` | Faire respecter les droits du fichier de réglages n8n. |
| `paramètre privé à consulter sur le Pi: true` | Conserver la protection des cookies ; l'accès actuel utilise `localhost`. |
| `paramètre privé à consulter sur le Pi: false` | Désactiver les diagnostics optionnels n8n. |
| `EXECUTIONS_DATA_PRUNE: true` | Purger les anciens historiques. |
| `EXECUTIONS_DATA_MAX_AGE: 168` | Âge maximal configuré de sept jours, en heures, pour la purge applicable. |
| `n8n_data:paramètre privé à consulter sur le Pi` | Conserver base SQLite et autres données au-delà du remplacement du conteneur. |
| `paramètre privé à consulter sur le Pi: external` | Exécuter les tâches de code via le service séparé. |
| `paramètre privé à consulter sur le Pi: paramètre privé à consulter sur le Pi` | Accepter la connexion du service de code dans le réseau Docker ; le port 5679 n'est pas publié sur le Pi. |
| `paramètre privé à consulter sur le Pi` | Authentifier ce service auprès de n8n. |
| `paramètre privé à consulter sur le Pi: false` | Désactiver l'installation de paquets communautaires non vérifiés. |
| `healthcheck` | Tester périodiquement la disponibilité avec Node et `fetch`. |
| `interval: 30s`, `timeout: 10s` | Fréquence du contrôle et durée maximale de chaque test. |
| `start_period: 120s`, `retries: 5` | Tolérer la phase initiale puis compter les échecs. |
| Journaux `json-file`, `10m`, `3` | Limiter les fichiers de journaux Docker à trois fichiers d'environ 10 Mo par service. |

La configuration initiale contenait `WEBHOOK_URL`. Les journaux de cette version ont indiqué sa dépréciation ; elle a été remplacée par `N8N_WEBHOOK_URL`.

### Service de code

| Réglage | Effet |
|---|---|
| `paramètre privé à consulter sur le Pi` | Image officielle des lanceurs correspondant à n8n 2.42.5, figée par empreinte. |
| `paramètre privé à consulter sur le Pi: paramètre privé à consulter sur le Pi | Contacter n8n par le réseau interne Compose. |
| Même jeton d'authentification | Prouver au broker que le service est autorisé. |
| Dépendance `service_healthy` | Attendre que n8n soit disponible avant de démarrer les lanceurs. |
| `no-new-privileges:true` | Empêcher l'obtention de nouveaux privilèges par certains mécanismes Unix. |
| `cap_drop: ALL` | Retirer les capacités Linux supplémentaires. |
| Aucun volume des données n8n | Éviter l'accès direct à la base et à la clé de chiffrement par montage. |
| Aucun `ports` publié | Garder les ports du service de code dans Docker. |

Ces mesures améliorent l'isolation ; elles ne rendent pas un workflow dangereux inoffensif ni le Pi invulnérable.

## 12. Ajout des lanceurs JavaScript/Python : incident et correction

Les journaux du premier démarrage ont révélé l'absence de Python dans le conteneur principal et la dépréciation du mode interne. Le Compose a été modifié pour utiliser un service officiel séparé, selon la [documentation des task runners](https://docs.n8n.io/deploy/host-n8n/configure-n8n/set-up-task-runners.md).

Première tentative, échouée :

```sh
sudo docker pull docker.n8n.io/n8nio/runners:2.42.5 >runners-pull.log 2>&1 || { tail -20 runners-pull.log; exit 1; }
```

Le registre miroir utilisé pour n8n ne proposait pas cette référence : `not found`. Le script s'est arrêté avant la création du jeton.

Deuxième tentative, réussie, via Docker Hub :

```sh
set -eu
cd "paramètre privé à consulter sur le Pi"
sudo docker pull n8nio/runners:2.42.5 >runners-pull.log 2>&1 || { tail -20 runners-pull.log; exit 1; }
runner_image=$(sudo docker image inspect n8nio/runners:2.42.5 --format '{{index .RepoDigests 0}}')
umask 077
if ! grep -q '^paramètre privé à consulter sur le Pi=' .env; then
  printf 'paramètre privé à consulter sur le Pi=%s\n' "$(openssl rand -hex 32)" >> .env
fi
if ! grep -q '^paramètre privé à consulter sur le Pi=' .env; then
  printf 'paramètre privé à consulter sur le Pi=%s\n' "$runner_image" >> .env
fi
sudo docker compose config --quiet
sudo docker compose up -d
sudo docker compose ps
```

`grep -q` vérifie seulement l'existence des noms de variables ; il n'affiche pas leur valeur. `>>` complète le `.env` existant. La clé de chiffrement n8n n'a pas changé. L'image obtenue est :

```text
n8nio/runners@paramètre privé à consulter sur le Pi
```

Le remplacement du conteneur n8n et le démarrage du service de code ont réussi. Les journaux n8n montrent l'enregistrement de `launcher-javascript` et `launcher-python`.

## 13. Tunnel SSH depuis Windows

Un processus SSH a été lancé en arrière-plan avec ce script PowerShell :

```powershell
$ErrorActionPreference = 'Stop'
$sshArgs = @(
  '-N','-o','BatchMode=yes','-o','ExitOnForwardFailure=yes',
  '-o','ServerAliveInterval=30','-o','ServerAliveCountMax=3',
  '-o','StrictHostKeyChecking=yes','-i',"paramètre privé à consulter sur le Pi",
  '-L','paramètre privé à consulter sur le Pi:5678:paramètre privé à consulter sur le Pi:5678','[ADRESSE-MAIL]'
)
$tunnel = Start-Process -FilePath (Get-Command ssh).Source -ArgumentList $sshArgs -WindowStyle Hidden -PassThru -RedirectStandardError "$env:TEMP\n8n-ssh-tunnel.log"
Write-Output "Tunnel SSH lance, processus $($tunnel.Id)."
```

Le processus lancé avait le PID `17816` à cet instant ; ce numéro est temporaire et ne doit pas être réutilisé aveuglément pour arrêter un processus plus tard.

| Option | Utilité |
|---|---|
| `-N` | Ouvrir le tunnel sans exécuter de commande sur le Pi. |
| `-L paramètre privé à consulter sur le Pi:5678:paramètre privé à consulter sur le Pi:5678` | Transférer le port local Windows vers la boucle locale du Pi. |
| `ExitOnForwardFailure=yes` | Échouer si le port local ne peut pas être ouvert. |
| `ServerAliveInterval=30` | Vérifier périodiquement la connexion. |
| `ServerAliveCountMax=3` | Fermer après trois vérifications sans réponse. |
| `WindowStyle Hidden` | Éviter d'ouvrir une fenêtre de terminal supplémentaire pendant l'installation. |
| `RedirectStandardError` | Conserver les erreurs du tunnel dans le dossier temporaire Windows. |
| `PassThru` | Récupérer les métadonnées du processus. |

Le fichier `ouvrir-n8n.ps1` utilise la même redirection, en premier plan, pour les prochaines connexions :

```powershell
$ErrorActionPreference = 'Stop'
Write-Host 'Acces n8n : paramètre privé à consulter sur le Pi
Write-Host 'Garde cette fenetre ouverte. Ctrl+C ferme le tunnel.'
& ssh -N -o ExitOnForwardFailure=yes -o ServerAliveInterval=30 -o ServerAliveCountMax=3 -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" -L 'paramètre privé à consulter sur le Pi:5678:paramètre privé à consulter sur le Pi:5678' '[ADRESSE-MAIL]'
if ($LASTEXITCODE -ne 0) { throw "Le tunnel SSH a echoue (code $LASTEXITCODE)." }
```

Cette commande est documentée pour le lancer, mais le lanceur lui-même n'a pas été exécuté pendant l'installation : le tunnel caché a été lancé avec `Start-Process`.

```powershell
powershell -ExecutionPolicy Bypass -File .\ouvrir-n8n.ps1
```

`ExecutionPolicy Bypass` s'applique à ce processus PowerShell, pas à un changement permanent de politique Windows.

## 14. Commandes de progression et diagnostics répétés

Les commandes suivantes ont été exécutées pendant les téléchargements et le démarrage :

```sh
tail -5 paramètre privé à consulter sur le Pi
sudo systemctl is-enabled docker
sudo systemctl is-active docker
tail -8 paramètre privé à consulter sur le Pi
sudo docker ps --format "{{.Names}} {{.Status}} {{.Ports}}"
df -h /
ps -eo pid,etime,comm | rg "docker|containerd"
tail -4 paramètre privé à consulter sur le Pi
ps -eo pid,etime,comm | grep -E "docker|containerd"
sudo du -sh paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi
free -h
tail -4 paramètre privé à consulter sur le Pi
```

| Commande | Utilité/résultat |
|---|---|
| `tail -5`, `-8`, `-4` | Voir les dernières étapes sans tout le journal. |
| `systemctl is-enabled` | Confirmer le démarrage automatique : `enabled`. |
| `systemctl is-active` | Confirmer l'exécution : paramètre privé à consulter sur le Pi. |
| `docker ps --format` | Voir les conteneurs et leurs ports. |
| `ps ...etime` | Voir les processus et leur durée d'exécution. |
| `rg` sur le Pi | A échoué : l'outil n'était pas installé sur le Pi. |
| `grep -E` | Remplacement disponible pour le même filtre de processus. |
| `du -sh` | Vérifier que l'espace occupé par les images progresse. |
| `free -h`, `df -h /` | Vérifier les ressources pendant l'installation. |

Les sessions de téléchargement ont également été suivies par l'outil de collecte des sorties du processus (`write_stdin` avec une entrée vide). Cela ne lance pas de nouvelle commande sur le Pi et ne modifie pas sa configuration.

## 15. Vérifications de disponibilité

### Contrôle sur le Pi

```sh
cd paramètre privé à consulter sur le Pi
sudo docker compose ps
curl -fsS paramètre privé à consulter sur le Pi
sudo docker compose logs --tail=25 n8n
```

`curl -f` renvoie une erreur sur un statut HTTP d'échec ; `-sS` réduit la sortie tout en conservant les erreurs. Lors du tout premier démarrage, une réinitialisation de connexion et un statut 503 ont été observés avant la fin des migrations. Ce n'était pas encore le résultat final.

Une boucle d'attente a ensuite été envoyée au Pi :

```sh
set -eu
cd "paramètre privé à consulter sur le Pi"
for i in $(seq 1 30); do
  if curl -fsS paramètre privé à consulter sur le Pi 2>paramètre privé à consulter sur le Pi; then
    printf '\nREADY\n'
    sudo docker compose exec -T n8n n8n --version
    sudo docker compose ps
    exit 0
  fi
  sleep 2
done
sudo docker compose logs --tail=60 n8n
exit 1
```

`seq 1 30` permet jusqu'à trente contrôles ; `sleep 2` les espace. `exec -T` exécute la commande de version dans le conteneur sans pseudo-terminal. Résultat : `READY`, **2.42.5**, puis `healthy`.

Autres lectures ciblées des journaux :

```sh
cd paramètre privé à consulter sur le Pi
sudo docker compose logs --tail=20 n8n
sudo docker compose logs --tail=8 n8n
sudo docker compose logs --tail=12 task-runners
stat -c "%a %n" .env
sudo systemctl is-enabled docker
sudo docker compose logs --tail=20 task-runners
sudo docker compose logs --tail=6 n8n
ss -ltn | grep -E "5678|5679"
```

`stat` a confirmé `600 .env`. `ss` a confirmé `paramètre privé à consulter sur le Pi:5678`. Le port 5679 est dans le réseau des conteneurs, pas publié sur l'hôte. Les journaux ont confirmé l'inscription des deux lanceurs.

### Contrôles Windows

Première lecture de santé et des erreurs de tunnel :

```powershell
Get-Content "$env:TEMP\n8n-ssh-tunnel.log" -ErrorAction SilentlyContinue
try {
  $r = Invoke-WebRequest -Uri 'paramètre privé à consulter sur le Pi -TimeoutSec 10
  Write-Output "HTTP $($r.StatusCode) $($r.Content)"
} catch { Write-Output $_.Exception.Message }
```

Des contrôles suivants ont inclus la page d'accueil et les cinq dernières lignes du journal :

```powershell
try {
  $r = Invoke-WebRequest -Uri 'paramètre privé à consulter sur le Pi -TimeoutSec 10
  Write-Output "HTTP $($r.StatusCode) $($r.Content)"
  $homePage = Invoke-WebRequest -Uri 'paramètre privé à consulter sur le Pi -TimeoutSec 10
  Write-Output "Page n8n HTTP $($homePage.StatusCode)"
} catch { Write-Output $_.Exception.Message }
Get-Content "$env:TEMP\n8n-ssh-tunnel.log" -Tail 5 -ErrorAction SilentlyContinue
```

Enfin, les vérifications ont réussi :

```powershell
$r = Invoke-WebRequest -Uri 'paramètre privé à consulter sur le Pi -TimeoutSec 10
Write-Output "Depuis Windows : HTTP $($r.StatusCode) $($r.Content)"
$page = Invoke-WebRequest -Uri 'paramètre privé à consulter sur le Pi -TimeoutSec 10
Write-Output "Interface : HTTP $($page.StatusCode)"
if ($page.Content -match '<title>([^<]+)</title>') {
  Write-Output "Titre : $($Matches[1])"
}
```

Résultats : HTTP 200 pour la disponibilité et l'interface ; titre `n8n.io - Workflow Automation`. Un dernier contrôle de disponibilité identique a réussi après l'ajout des lanceurs.

## 16. Opérations réalisées via les outils de l'application

- Recherche et lecture de documentations officielles : Docker Debian, n8n Docker/Compose/task runners, gestion des clés OpenSSH Windows. Ces recherches ne changent pas le Pi.
- Édition des fichiers locaux avec `apply_patch`, puis transfert du seul Compose.
- Demande d'ouverture de `paramètre privé à consulter sur le Pi dans le panneau navigateur par `open_in_codex`. L'outil a répondu `queued` ; cela ne prouve pas à lui seul l'affichage final de l'onglet. Les contrôles HTTP, eux, ont réussi.
- Aucun compte n8n, mot de passe, inscription commerciale ou invitation à un tiers n'a été créé par l'assistant.

## 17. Vérifications supplémentaires pour préparer les rapports

### État du Pi

```sh
cd paramètre privé à consulter sur le Pi
sudo docker compose ps
curl -fsS paramètre privé à consulter sur le Pi
printf "\n"
stat -c "%a %n" .env
hostname -I
ip -4 route
ip -4 -o link
ss -ltn
sudo -n true && echo SUDO_OK
sudo systemctl is-enabled docker
sudo docker volume ls --format "{{.Name}}"
sudo docker compose exec -T n8n n8n --version
```

Les premières commandes reconfirment l'état. `ip -4 route` identifie passerelle et interface ; `ip -4 -o link` relève les interfaces et adresses MAC pour une future réservation DHCP. La liste des volumes confirme `n8n_n8n_data`.

### Dernier état local et métadonnées Docker

```powershell
$ErrorActionPreference = 'Stop'
Get-ChildItem .keys -Force | Select-Object Name,Length,Attributes
Get-Service ssh-agent | Select-Object Name,Status,StartType
try {
  $r = Invoke-WebRequest -Uri 'paramètre privé à consulter sur le Pi -TimeoutSec 10
  Write-Output "WINDOWS_HTTP=$($r.StatusCode)"
} catch { Write-Output "WINDOWS_HTTP_ECHEC=$($_.Exception.Message)" }
```

Puis sur le Pi :

```sh
sudo docker version --format "{{.Server.Version}}"
sudo docker compose version
sudo docker inspect n8n-n8n-1 --format "Restart={{.HostConfig.RestartPolicy.Name}} Mount={{range .Mounts}}{{.Name}}:{{.Destination}}{{end}}"
cd paramètre privé à consulter sur le Pi
sudo docker compose logs --tail=8 task-runners
sudo test -f paramètre privé à consulter sur le Pi && echo NGINX_PRESENT || true
sudo test -f paramètre privé à consulter sur le Pi && echo CADDY_PRESENT || true
```

`docker inspect` a confirmé `unless-stopped` et le volume persistant. Les deux `test -f` recherchent les fichiers usuels de Nginx et Caddy : ils n'ont pas été trouvés. Cela n'est pas un inventaire exhaustif de tous les logiciels du Pi. Aucune installation de proxy public n'a été faite.

### Lecture des fichiers du projet pour les rapports

```powershell
Get-ChildItem -Force | Select-Object Name,Length
Get-Content compose.yaml
Get-Content README-n8n.md
```

Ces lectures assurent que le rapport décrit les fichiers réellement produits. Les fichiers d'instructions du module de contrôle Windows ont également été lus avec `Get-Content -LiteralPath` sous `paramètre privé à consulter sur le Pi` : `skills/computer-use/SKILL.md`, `docs/guidance.md`, `docs/confirmations.md`, `docs/api.md`. Il s'agit des consignes des outils, pas de la configuration n8n.

### Tentative d'inspection de Brave — aucune modification

Le module a été initialisé, les fenêtres ont été listées, et une fenêtre intitulée `Freebox OS – Brave` a été trouvée. Une demande de lecture de son état a été bloquée, car l'outil ne pouvait pas déterminer l'URL courante avec assez de confiance pour appliquer ses règles. La lecture du navigateur s'est arrêtée. Aucun clic dans Freebox OS, formulaire de redirection, réglage VPN, mot de passe ou permission réseau n'a été effectué.

## 18. Mesures documentées mais non exécutées

Les commandes suivantes figurent dans le guide pour l'utilisateur ; elles ne font pas partie des changements effectués :

```powershell
ssh-keygen -p -f "paramètre privé à consulter sur le Pi"
Set-Service ssh-agent -StartupType Automatic
Start-Service ssh-agent
ssh-add "paramètre privé à consulter sur le Pi"
ssh-add -l
ssh-add -D
```


Un exemple de sauvegarde avec arrêt temporaire, archivage du volume et reprise automatique figure dans `README-n8n.md`. Il n'a pas été exécuté. Aucune sauvegarde automatique, copie sur un autre appareil ni restauration n'a encore été validée.

## 19. Points à conserver pour la suite

1. Sauvegarder les données et `paramètre privé à consulter sur le Pi` avant changement public ; conserver la même clé de chiffrement.
2. Finaliser les comptes n8n et leur double authentification avant publication.
3. Vérifier la collaboration réellement disponible selon l'édition : réseau accessible et partage des workflows sont deux sujets distincts.
4. Supprimer manuellement le doublon de clé du projet, en conservant l'original `.ssh`.
5. Ne pas exposer le compte SSH `yanis` à l'ami : il possède sudo sans mot de passe.
6. Ne pas confondre la déclaration de redémarrage avec un test de redémarrage effectué.
7. Maintenir les versions : l'empreinte fixe améliore la reproductibilité, mais ne remplace pas les mises à jour de sécurité.

Références complémentaires : [OpenSSH Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement), [installation n8n](https://docs.n8n.io/hosting/installation/docker/), [éditions n8n](https://docs.n8n.io/hosting/community-edition-features/).
