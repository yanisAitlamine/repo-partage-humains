<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 2 — Rendre n8n accessible à deux personnes par l'IP publique

**Projet :** Raspberry Pi de Yanis — **date :** 9 octobre 2026, Europe/Paris.

**Statut : proposition initiale, conservée comme document de conception.** La
mise en ligne a ensuite été réalisée avec Caddy sur le seul port TCP 443, à la
place de Nginx/Certbot et du challenge HTTP sur le port 80. L'état final, les
commandes exécutées, les comptes et les contrôles sont dans le
[rapport 3](RAPPORT-03-mise-en-ligne-realisee.md). Les commandes Nginx/Certbot
ci-dessous n'ont pas été exécutées. Les éléments indiqués « non relevés »
correspondent aux informations disponibles au moment de cette proposition.

## 1. Objectif et décision proposée

L'objectif est que Yanis et son ami accèdent à n8n depuis leurs réseaux respectifs, en utilisant la connexion publique de la Freebox. Le Raspberry Pi continue d'héberger l'application et les données.

Pour respecter la demande d'une **adresse IP directement dans le navigateur**, la solution proposée est :

```text
Navigateur de Yanis / de son ami
          |
          | HTTPS vers paramètre privé à consulter sur le Pi
          v
Freebox — redirection TCP 443
          |
          v
Raspberry Pi paramètre privé à consulter sur le Pi
          |
          +-- Nginx : terminaison TLS et relais HTTP
          |       |
          |       +-- paramètre privé à consulter sur le Pi:5678 -> n8n
          |
          +-- n8n <-> réseau Docker privé <-> service de code
          |
          +-- volume persistant et clé de chiffrement n8n

Let’s Encrypt -> TCP 80 -> chemin ACME uniquement
```

Nginx est installé sur le système du Pi, devant le port local n8n déjà existant. Cela permet de conserver le Compose, les volumes et la séparation des tâches de code. Les connexions publiques utilisent TLS ; le trajet local Nginx–n8n reste HTTP sur la boucle locale.

Cette architecture n'exige pas de transmettre la clé SSH de Yanis à son ami. L'ami reçoit un accès applicatif n8n, pas un compte administrateur Linux.

Deux variantes sont étudiées plus loin : un nom DNS pointant vers la même IP publique, et un VPN pour réserver l'interface aux deux personnes. Un nom DNS ne change pas l'hébergement : le trafic peut toujours aller directement à la Freebox.

## 2. Ce que nous savons et ce qu'il reste à relever

| Élément | État |
|---|---|
| n8n | 2.42.5, en fonctionnement |
| Pi | Debian 13 ARM64, environ 8 Go de RAM |
| Adresse LAN du Pi | `paramètre privé à consulter sur le Pi`, attribuée par DHCP |
| Passerelle | `paramètre privé à consulter sur le Pi` |
| Interface | `wlan0`, MAC `[ADRESSE-MAC-ANONYMISEE]` |
| n8n côté Pi | uniquement `paramètre privé à consulter sur le Pi:5678` |
| Données | volume `n8n_n8n_data` |
| IPv6 | le Pi possède aussi une IPv6 globale ; à traiter dans le filtrage |
| IPv4 publique | **non relevée** |
| Plage de ports Free | **non confirmée** |
| Réservation DHCP | **non confirmée** |
| Redirections existantes / DMZ / UPnP | **non lus** |
| Compte propriétaire et 2FA | création/configuration par l'utilisateur à vérifier |
| Licence n8n | aucune licence payante installée par l'assistant ; vérifier l'état dans l'interface |

La fenêtre `Freebox OS – Brave` a été trouvée. Son contenu n'a pas pu être lu : le module de contrôle a arrêté la lecture, faute de pouvoir identifier l'URL courante avec assez de confiance. Les chemins de menus ci-dessous sont donc une procédure générale, pas une description de réglages vus dans cette Freebox.

Avant mise en œuvre, relever dans Freebox OS ou l'Espace Abonné : l'IPv4 publique, les ports attribués, l'état du bail DHCP et l'éventuel usage de 80/443 par l'administration distante. Il faut aussi préciser si vous voulez travailler sur **les mêmes workflows** ou simplement utiliser **la même instance** avec des workflows distincts.

## 3. Le point décisif : collaboration dans n8n

L'ouverture du réseau donne accès à la page n8n. Elle n'ajoute pas les permissions de partage de workflows.


| Besoin réel | Conséquence |
|---|---|
| Chacun crée ses propres workflows | Deux comptes peuvent utiliser l'instance ; vérifier les permissions effectives. |
| Les deux modifient les mêmes workflows avec comptes distincts | Choisir une offre donnant le partage/projet nécessaire, puis tester les deux accès. |
| Rester gratuit et échanger les modifications | Export/import JSON et organisation du travail, avec gestion manuelle des versions. |
| Éditer simultanément comme dans Google Docs | Ne pas le promettre ; tester les capacités réelles, éviter les modifications concurrentes qui s'écrasent. |

Le partage d'un même compte propriétaire est une mauvaise base de sécurité : pas d'attribution fiable, révocation individuelle difficile, double authentification partagée et accès très large. La procédure proposée repose sur **deux comptes distincts**, avec le minimum de droits nécessaire. Une licence réseau, un proxy ou un VPN ne contourne pas les limites applicatives de l'édition.

## 4. HTTPS sur une adresse IP : faisable, avec renouvellement fréquent

Let’s Encrypt délivre maintenant des certificats pour IPv4/IPv6. Ils ont une durée de **160 heures**, soit un peu plus de six jours ; le profil utilisé est `shortlived`. Un renouvellement automatique fiable est donc un prérequis. Annonce officielle (référence d’exploitation retirée).

Pour la méthode `webroot` présentée ici, Certbot doit être **5.4 ou supérieur**. Il obtient le certificat ; la configuration du serveur web pour le charger est faite séparément. La validation d'une IP ne passe pas par un challenge DNS. Procédure officielle IP avec Certbot (référence d’exploitation retirée), validation des certificats IP (référence d’exploitation retirée).

Un certificat pour un nom de domaine ne valide pas automatiquement une URL contenant une IP. Le certificat doit inclure l'IP réellement utilisée. Un certificat autosigné et une consigne de cliquer sur une alerte du navigateur ne constituent pas la solution proposée.

Si l'IP publique change, il faut réémettre le certificat pour la nouvelle IP et corriger l'URL n8n. Les invitations, webhooks et redirections OAuth déjà enregistrés peuvent également devoir être mis à jour. Certains fournisseurs OAuth exigent une URL ou un nom DNS particulier : une URL IP n'est pas compatible avec toutes les intégrations.

## 5. Paramètres Freebox à préparer

### 5.1 Stabiliser l'adresse locale du Pi

Dans le serveur DHCP de Freebox OS, créer ou vérifier un bail statique pour le Pi :

| Champ | Valeur proposée |
|---|---|
| Appareil | `yanis-pi` / Raspberry Pi correspondant |
| MAC de l'interface utilisée | `[ADRESSE-MAC-ANONYMISEE]` |
| Adresse réservée | `paramètre privé à consulter sur le Pi` si disponible et compatible avec la plage DHCP |

Le Pi utilise le Wi-Fi. Une réservation pour la MAC Ethernet ne stabiliserait pas son adresse Wi-Fi. Un passage ultérieur à Ethernet est intéressant pour la disponibilité, mais il faudra alors ajuster la réservation et les règles NAT.

Ne pas attribuer cette IP à un second appareil. Vérifier le bail après reconnexion ; ne pas provoquer un redémarrage réseau pendant la préparation d'une opération distante.

### 5.2 Vérifier les ports accessibles sur l'IPv4 publique

Certaines connexions Free utilisent une IPv4 partagée avec une plage de ports limitée. Si 80 et 443 sont disponibles, les règles proposées peuvent être utilisées directement. Sinon, une IPv4 fixe **full-stack** permet l'ensemble des ports. La demande se fait dans l'Espace Abonné, rubrique Ma Freebox ; elle peut changer l'IP et demande un redémarrage selon les consignes Free. Ce changement doit être planifié car il affecte aussi d'autres services. Assistance Free : full-stack (référence d’exploitation retirée).

Un simple remplacement de 443 par un port élevé peut permettre l'accès au navigateur, mais **ne remplace pas** les ports standards exigés par les challenges ACME HTTP-01/TLS-ALPN-01. Sans ces ports, choisir une autre architecture, par exemple le VPN, ou un domaine avec validation DNS compatible.

### 5.3 Redirections proposées

| Protocole | Port WAN | Destination LAN | Port LAN | Usage |
|---|---:|---|---:|---|
| TCP | 80 | `paramètre privé à consulter sur le Pi` | 80 | Validation et renouvellement ACME uniquement dans le modèle de ce rapport. |
| TCP | 443 | `paramètre privé à consulter sur le Pi` | 443 | Interface/API/webhooks n8n en HTTPS. |

La configuration Freebox propose des paramètres DHCP, redirections et VPN dans ses réglages réseau avancés. Les libellés précis peuvent varier selon l'interface. Assistance Free (référence d’exploitation retirée).

Ne pas créer de DMZ vers le Pi. Ne pas ouvrir directement 5678, 5679, 5680 ou 22 vers Internet. Ne pas publier l'administration Freebox pour donner accès à n8n. Vérifier les redirections manuelles et automatiques existantes avant ajout. Si 443 sert déjà à un autre service, résoudre le conflit ; ne pas écraser sa règle sans examiner l'impact.

La source de la règle 80 doit permettre les serveurs de validation ACME. Restreindre 80 uniquement à l'IP de l'ami empêcherait le renouvellement. Le proxy ne relaiera pas n8n sur 80.

## 6. Préparation du Pi avant ouverture

### 6.1 Sauvegarder et valider les comptes



### 6.2 Installer Nginx et Certbot — commandes proposées sur le Pi

Ces commandes modifient le système ; elles sont écrites ici pour le futur déploiement.

```sh
sudo apt-get update
sudo apt-get install -y nginx python3 python3-venv
sudo python3 -m venv paramètre privé à consulter sur le Pi
sudo paramètre privé à consulter sur le Pi install --upgrade pip
sudo paramètre privé à consulter sur le Pi install --upgrade 'certbot>=5.4'
paramètre privé à consulter sur le Pi --version
sudo install -d -m 0755 paramètre privé à consulter sur le Pi
```

| Commande | Utilité |
|---|---|
| `apt-get update` | Actualiser les index des paquets. |
| Installation Nginx | Ajouter le serveur proxy HTTP/TLS sur le Pi. |
| Installation Python/venv | Permettre un environnement isolé pour Certbot. |
| `python3 -m venv paramètre privé à consulter sur le Pi` | Isoler Certbot des bibliothèques Python du système. |
| Mise à jour `pip` | Préparer l'installation du client. |
| `certbot>=5.4` | Obtenir une version compatible avec les certificats IP en webroot. Vérifier la version réellement obtenue et la consigner. |
| `certbot --version` | Valider la version avant d'aller plus loin. |
| `install -d` | Créer le dossier des challenges publics ACME. |

Au déploiement, vérifier qu'un environnement `paramètre privé à consulter sur le Pi` ou un autre Certbot n'existe pas déjà, et adapter la méthode si nécessaire. Le script ne doit pas écraser une installation existante à l'aveugle. La méthode en environnement Python suit la documentation Certbot (référence d’exploitation retirée) ; ici on n'utilise pas le plugin Nginx pour l'installation automatique des certificats IP.

### 6.3 Variables des exemples

Dans les extraits de configuration, remplacer **`IP_PUBLIQUE`** par l'IPv4 réelle de la Freebox. Dans les commandes interactives, définir :

```sh
PUBLIC_IP='paramètre privé à consulter sur le Pi'
ACME_EMAIL='ADRESSE_EMAIL_REELLE_DE_CONTACT'
```

Ce sont des paramètres à renseigner, pas les valeurs découvertes sur le réseau. Les exemples sont à utiliser dans une session Bash sur le Pi, pas directement dans PowerShell. La clé privée SSH et `paramètre privé à consulter sur le Pi` ne doivent pas être copiées dans ces variables.

## 7. Phase initiale : validation ACME sans publier n8n en HTTP

Créer un fichier `paramètre privé à consulter sur le Pi` avec ce contenu **en remplaçant le marqueur IP** :

```nginx
server {
    listen 80;
    server_name IP_PUBLIQUE;
    server_tokens off;

    location ^~ /.well-known/acme-challenge/ {
        root paramètre privé à consulter sur le Pi;
        default_type text/plain;
        try_files $uri =404;
    }

    location / {
        return 404;
    }
}
```

Le port 80 sert seulement un dossier de validation. Il ne contient pas de `proxy_pass` vers n8n, donc n'expose ni formulaire de connexion ni API n8n sans chiffrement.

Si ce Pi est dédié et si le site Nginx par défaut vient seulement d'être installé, désactiver son lien après vérification :

```sh
sudo unlink paramètre privé à consulter sur le Pi
sudo ln -s paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi
sudo nginx -t
sudo systemctl enable --now nginx
sudo systemctl reload nginx
```

`unlink` retire uniquement le lien d'activation, pas les données. `ln -s` active le nouveau site. `nginx -t` vérifie la syntaxe avant le rechargement. Si un lien existe déjà ou si un autre site est utilisé, ajuster cette séquence au lieu de la rejouer telle quelle.

Une fois le port 80 redirigé sur la Freebox, contrôler depuis une connexion extérieure que le chemin ACME atteint bien ce Nginx. Un test uniquement depuis le LAN ne vérifie pas la traversée Internet.

### Obtenir et tester le certificat

Utiliser d'abord un nom de certificat distinct pour le test de staging :

```sh
sudo paramètre privé à consulter sur le Pi certonly \
  --staging \
  --preferred-profile shortlived \
  --webroot --webroot-path paramètre privé à consulter sur le Pi \
  --ip-address "$PUBLIC_IP" \
  --cert-name n8n-ip-staging \
  --email "$ACME_EMAIL" --agree-tos --non-interactive
```

Puis, après réussite, créer le certificat de production :

```sh
sudo paramètre privé à consulter sur le Pi certonly \
  --preferred-profile shortlived \
  --webroot --webroot-path paramètre privé à consulter sur le Pi \
  --ip-address "$PUBLIC_IP" \
  --cert-name n8n-ip \
  --email "$ACME_EMAIL" --agree-tos --non-interactive
```

| Option | Utilité |
|---|---|
| `certonly` | Obtenir les fichiers sans modifier automatiquement Nginx. |
| `--staging` | Tester la validation avec un certificat de test non reconnu par les navigateurs. |
| `--preferred-profile shortlived` | Demander le profil de courte durée adapté à l'IP. |
| `--webroot` | Écrire les challenges dans le dossier servi par Nginx. |
| `--ip-address` | Désigner l'IP à certifier. |
| `--cert-name` | Garder des chemins stables et séparer test et production. |
| `--email` | Contact pour le compte ACME. |
| `--agree-tos` | Accepter les conditions de l'autorité ; à faire en connaissance de cause au déploiement. |
| `--non-interactive` | Éviter les questions dans un script, une fois les paramètres définis. |

Ne pas utiliser le certificat staging pour l'accès de l'ami. Ne pas modifier les droits de la clé TLS pour la rendre lisible à tous. Le chemin de production sera `paramètre privé à consulter sur le Pi`.

## 8. Configuration HTTPS Nginx proposée

Après obtention du certificat de production, remplacer le fichier de site par cette configuration, avec la vraie IP :

```nginx
map $http_upgrade $paramètre privé à consulter sur le Pi {
    default upgrade;
    ''      close;
}

# Seules les tentatives POST de connexion alimentent cette limite.
# Confirmer l'endpoint /rest/login sur la version déployée.
map "$request_method:$uri" $n8n_login_key {
    default "";
    "POST:/rest/login" $binary_remote_addr;
}
limit_req_zone $n8n_login_key zone=n8n_login:10m rate=5r/m;

server {
    listen 80;
    server_name IP_PUBLIQUE;
    server_tokens off;

    location ^~ /.well-known/acme-challenge/ {
        root paramètre privé à consulter sur le Pi;
        default_type text/plain;
        try_files $uri =404;
    }
    location / { return 404; }
}

server {
    listen 443 ssl;
    server_name IP_PUBLIQUE;
    server_tokens off;

    ssl_certificate paramètre privé à consulter sur le Pi;
    ssl_certificate_key paramètre privé à consulter sur le Pi;
    ssl_protocols TLSv1.2 TLSv1.3;

    # Valeur de départ à adapter aux fichiers utilisés dans les workflows.
    client_max_body_size 16m;
    add_header X-Content-Type-Options nosniff always;
    add_header Referrer-Policy no-referrer always;

    access_log paramètre privé à consulter sur le Pi;
    error_log paramètre privé à consulter sur le Pi;

    location / {
        limit_req zone=n8n_login burst=5 nodelay;
        limit_req_status 429;

        proxy_pass paramètre privé à consulter sur le Pi
        proxy_http_version 1.1;

        proxy_set_header Host IP_PUBLIQUE;
        proxy_set_header X-Forwarded-Host IP_PUBLIQUE;
        proxy_set_header X-Forwarded-Proto https;
        proxy_set_header X-Forwarded-Port 443;
        # Remplacer l'en-tête reçu du client plutôt que lui faire confiance.
        proxy_set_header X-Forwarded-For $remote_addr;
        proxy_set_header X-Real-IP $remote_addr;

        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection $paramètre privé à consulter sur le Pi;
        proxy_read_timeout 300s;
        proxy_send_timeout 300s;
        proxy_buffering off;
    }
}
```

Le fichier est inclus dans le contexte `http` standard de Nginx Debian : `map` et `limit_req_zone` doivent rester à ce niveau, en dehors d'un bloc `server`. Les extraits sont une configuration de départ à valider avec la version Nginx réellement installée, pas une validation syntaxique déjà exécutée.

Le proxy transmet les requêtes à la boucle locale, préserve les connexions WebSocket et remplace les en-têtes indiquant l'origine. La limitation vise les tentatives de connexion ; elle ne doit pas limiter arbitrairement tous les webhooks. Les paramètres de taille et délai doivent être adaptés aux workflows, et les journaux soumis à rotation. Proxy HTTP Nginx (référence d’exploitation retirée), WebSocket (référence d’exploitation retirée), limitation de requêtes (référence d’exploitation retirée).

Il ne s'agit pas d'une protection contre toute attaque ni d'un système de détection d'intrusion. Une limite à cinq tentatives par minute est une valeur de départ, à tester sans bloquer les utilisateurs légitimes. Vérifier que l'IP journalisée est bien celle du client Internet.

Après modification :

```sh
sudo nginx -t
sudo systemctl reload nginx
```

Le port 443 pourra être redirigé une fois le certificat et les comptes prêts. Aucun accès utilisateur n8n ne doit être distribué en HTTP.

## 9. Adapter n8n à son URL publique

Modifier seulement ces variables dans `paramètre privé à consulter sur le Pi`, en gardant les autres réglages, les images figées et le volume :

```yaml
environment:
  N8N_HOST: "IP_PUBLIQUE"
  N8N_PORT: "5678"
  N8N_PROTOCOL: "https"
  paramètre privé à consulter sur le Pi: "paramètre privé à consulter sur le Pi
  N8N_WEBHOOK_URL: "paramètre privé à consulter sur le Pi
  N8N_PROXY_HOPS: "1"
  paramètre privé à consulter sur le Pi: "true"
```

Le mapping reste :

```yaml
ports:
  - "paramètre privé à consulter sur le Pi:5678:5678"
```

`N8N_PROTOCOL=https` décrit l'URL externe. Le proxy termine TLS ; n8n écoute encore en HTTP interne. `N8N_PROXY_HOPS=1` correspond au proxy HTTP Nginx unique. La Freebox fait du NAT, donc elle n'est pas un second proxy HTTP. Si une autre couche HTTP est ajoutée, il faudra réexaminer ce nombre et la confiance dans les en-têtes. [Configuration officielle des URL derrière un proxy](https://docs.n8n.io/hosting/configuration/configuration-examples/webhook-url/).

Appliquer et vérifier :

```sh
cd paramètre privé à consulter sur le Pi
sudo docker compose config --quiet
sudo docker compose up -d
sudo docker compose ps
curl -fsS paramètre privé à consulter sur le Pi
```

Ne pas utiliser `docker compose down -v`, ne pas régénérer la clé de chiffrement et ne pas remplacer le volume par un nouveau. Après le passage à l'URL publique, utiliser celle-ci dans le navigateur ; l'ancien tunnel HTTP reste utile pour le diagnostic, mais les liens de l'application pointeront vers HTTPS public.

## 10. Renouvellement automatique du certificat

Le certificat IP expire vite. Prévoir un contrôle de renouvellement au moins deux fois par jour, un rechargement de Nginx après changement et une alerte en cas d'échec prolongé.

Le certificat staging est réservé aux tests. Pour éviter que le timer ne le renouvelle aussi, limiter les commandes au nom de production `n8n-ip`.

Fichier proposé `paramètre privé à consulter sur le Pi` :

```ini
[Unit]
Description=Renouvellement du certificat HTTPS n8n
Wants=network-online.target
After=network-online.target nginx.service

[Service]
Type=oneshot
ExecStart=paramètre privé à consulter sur le Pi renew --cert-name n8n-ip --quiet --deploy-hook "paramètre privé à consulter sur le Pi -t && paramètre privé à consulter sur le Pi reload nginx"
```

Fichier `paramètre privé à consulter sur le Pi` :

```ini
[Unit]
Description=Verification deux fois par jour du certificat n8n

[Timer]
OnCalendar=*-*-* 00,12:00:00
RandomizedDelaySec=30m
Persistent=true
Unit=n8n-cert-renew.service

[Install]
WantedBy=timers.target
```

Activer et tester, après vérification des chemins des exécutables :

```sh
sudo systemctl daemon-reload
sudo systemctl enable --now n8n-cert-renew.timer
sudo paramètre privé à consulter sur le Pi renew --cert-name n8n-ip --dry-run
sudo systemctl start n8n-cert-renew.service
sudo systemctl list-timers n8n-cert-renew.timer
sudo journalctl -u n8n-cert-renew.service --since today
```

| Commande | Utilité |
|---|---|
| `daemon-reload` | Relire les nouveaux fichiers d'unités. |
| `enable --now ...timer` | Activer le calendrier et le démarrer. |
| `--dry-run` | Tester le mécanisme de renouvellement sans remplacer le certificat de production. |
| Démarrage du service | Tester le chemin réel de la tâche. |
| `list-timers` | Vérifier la prochaine exécution prévue. |
| `journalctl` | Lire les succès/échecs. |

Le `deploy-hook` recharge Nginx uniquement après un renouvellement réussi ; sinon Nginx pourrait continuer à servir l'ancien certificat en mémoire. Un timer actif ne prouve pas la réussite des renouvellements. Ajouter une surveillance de l'expiration et des erreurs ; l'email ACME ne remplace pas cette surveillance. Une panne de box, une règle 80 supprimée ou un Pi arrêté plusieurs jours peut laisser expirer le certificat.

## 11. Filtrage réseau et réduction des accès

### IPv4, IPv6 et Docker

Le Pi possède une IPv6 globale. En IPv6, une absence de redirection IPv4 ne prouve pas l'absence d'accès Internet : contrôler le pare-feu IPv6 Freebox et celui du Pi. Le modèle Nginx ci-dessus écoute en IPv4 ; aucun `listen [paramètre privé à consulter sur le Pi]:443` n'est ajouté. SSH écoute actuellement sur IPv4 et IPv6 : le garder limité au LAN/VPN par les règles de filtrage.

Examiner le pare-feu existant avant de le modifier. Autoriser d'abord SSH depuis `paramètre privé à consulter sur le Pi/24`, puis seulement les services publics voulus. Garder une session de secours et tester une seconde connexion avant de fermer la première. Ne pas désactiver la protection réseau pour résoudre un problème de certificat.

Docker peut publier des ports d'une façon qui contourne certaines règles UFW. Le choix de conserver `paramètre privé à consulter sur le Pi:5678` est donc essentiel ; le proxy public tourne ici directement sur l'hôte. Après toute modification, vérifier les bindings Docker et le filtrage réellement observé depuis Internet. [Précautions Docker et pare-feu](https://docs.docker.com/engine/install/debian/).

### Réserver l'éditeur à deux personnes si possible

Si l'IP publique de l'ami est stable et si aucun service tiers n'a besoin de webhooks, une liste d'IP autorisées sur le port 443 ou dans Nginx réduit fortement l'exposition. Il faut autoriser aussi l'accès de Yanis et vérifier le comportement depuis son LAN. La règle 80 reste disponible pour ACME.

Si des services tiers doivent appeler les webhooks, séparer les chemins publics et l'interface privée. Autoriser seulement les endpoints webhook nécessaires, avec authentification ou signature côté workflow. Prévoir aussi les callbacks OAuth requis. Ne pas copier une règle globale qui bloque les webhooks ou, inversement, qui expose toute l'API en pensant protéger seulement l'éditeur.

L'IP n'est pas une identité parfaite : elle peut changer ou être partagée. La liste d'IP complète les comptes/MFA, elle ne les remplace pas. Un VPN est souvent plus pratique si l'IP de l'ami change régulièrement.

## 12. Sécurité applicative et secrets

| Sujet | Mesure proposée |
|---|---|
| Comptes | Un compte par personne, mot de passe unique, 2FA, codes de récupération conservés séparément. |
| Permissions | Rôle minimal ; tester ce que l'ami peut voir et modifier. |
| SSH | Pas de copie de la clé de Yanis ; pas de partage du compte `yanis` ni du sudo. |
| Clé de chiffrement n8n | Conserver la valeur actuelle ; sauvegarder avec les données, droits limités. |
| Clé TLS | Garder sous `paramètre privé à consulter sur le Pi` avec les droits gérés par Certbot. |
| Extensions | Garder les paquets non vérifiés désactivés ; examiner les permissions des extensions nécessaires. |
| Nœuds puissants | Réexaminer l'usage de commandes système, fichiers, requêtes internes et code importé. |
| Journalisation | Rotation, droits restreints ; les journaux peuvent contenir IP, chemins et informations métier. |
| Maintenance | Surveiller les correctifs n8n, runners, Docker, Debian, Nginx et Certbot. |

Un utilisateur autorisé à modifier un workflow peut souvent utiliser les identifiants attachés à ce workflow. Chiffrer les identifiants sur disque ne supprime pas les possibilités offertes par les fonctions applicatives. Il faut considérer l'ami comme un collaborateur de confiance et limiter les comptes des services externes eux-mêmes.

Un audit complémentaire peut être lancé sur le Pi et ses résultats conservés localement :

```sh
cd paramètre privé à consulter sur le Pi
sudo docker compose exec -T n8n n8n audit
```

Cet audit signale certaines mauvaises configurations et certains nœuds/accès ; ce n'est pas un test d'intrusion complet. Il n'a pas été exécuté pendant la rédaction de ce rapport. [Audit n8n](https://docs.n8n.io/hosting/securing/security-audit/), [blocage de nœuds](https://docs.n8n.io/hosting/securing/blocking-nodes/).

## 13. Vérifications avant remise de l'accès à l'ami

Les tests externes doivent se faire depuis le réseau de l'ami ou une connexion mobile avec Wi-Fi désactivé. Un test depuis le LAN peut dépendre du NAT loopback et ne prouve pas l'accès extérieur.

| Test | Résultat attendu |
|---|---|
| HTTPS par IP | Certificat reconnu, couvrant exactement l'IP, aucune alerte à contourner. |
| HTTP sur 80 hors ACME | 404 selon le modèle, aucun formulaire n8n. |
| Connexion sans compte | Pas d'accès aux workflows ou identifiants ; page de connexion éventuellement visible. |
| Compte de l'ami | 2FA opérationnelle et permissions adaptées. |
| Workflow commun | Les deux comptes ont réellement les droits nécessaires, si la licence le permet. |
| Ports 22, 5678, 5679, 5680 depuis Internet | Inaccessibles. |
| IPv6 | Pas d'exposition inattendue de SSH/n8n/ports de code. |
| Sessions actives / WebSocket | Exécutions et retour d'état fonctionnels dans le navigateur. |
| Webhook de test puis actif | URL HTTPS correcte et authentification testée. |
| Intégration OAuth utilisée | Callback conforme et accepté par le fournisseur. |
| Redémarrage Pi | n8n, runners et proxy repartent ; données présentes. |
| Renouvellement | Dry-run réussi, timer planifié, Nginx recharge les certificats. |

Commandes locales de diagnostic, sur le Pi :

```sh
sudo nginx -t
sudo systemctl status nginx --no-pager
cd paramètre privé à consulter sur le Pi
sudo docker compose ps
ss -ltn
curl -fsS paramètre privé à consulter sur le Pi
sudo openssl x509 -in paramètre privé à consulter sur le Pi -noout -dates -ext subjectAltName
```

Depuis une machine extérieure, après définition de l'IP :

```sh
curl -I "paramètre privé à consulter sur le Pi
curl -i "paramètre privé à consulter sur le Pi
openssl s_client -connect "$PUBLIC_IP:443" -verify_ip "$PUBLIC_IP" -verify_return_error <paramètre privé à consulter sur le Pi
```

Ne pas employer `curl -k` pour déclarer que TLS est validé : cette option désactive la vérification du certificat. Une erreur de certificat doit être corrigée, pas masquée.

## 14. Ordre de déploiement et retour arrière

1. Confirmer besoin de collaboration, édition n8n, comptes et 2FA.
2. Relever IPv4 publique, ports attribués, règles existantes et bail DHCP.
3. Sauvegarder configuration/données et vérifier une restauration isolée.
4. Stabiliser l'IP locale du Pi et préparer le filtrage IPv4/IPv6.
5. Installer Nginx et Certbot, configurer le site ACME sans relais HTTP vers n8n.
6. Ouvrir seulement le TCP 80 nécessaire à ACME ; valider staging puis production.
7. Configurer HTTPS, adapter les URL n8n, valider les configurations et démarrer le timer de renouvellement.
8. Ouvrir TCP 443, éventuellement filtré aux IP autorisées ; vérifier depuis un réseau extérieur.
9. Tester les comptes, le workflow commun et les intégrations, puis transmettre seulement URL et invitation par un canal convenu.

La dernière étape implique de donner effectivement accès à quelqu'un : elle doit correspondre aux personnes et permissions choisies. Aucune invitation n'a été envoyée dans cette conversation.

En cas de problème, retirer d'abord les redirections publiques de la Freebox pour couper l'exposition. Garder SSH local. Désactiver le site Nginx public si nécessaire, puis restaurer les anciennes URL dans le Compose et lancer `docker compose up -d`. Le volume et la clé de chiffrement doivent rester identiques. Ne pas restaurer une base plus ancienne sans évaluer les nouvelles données créées depuis la sauvegarde.

Il ne faut jamais supprimer les volumes pour résoudre un problème NAT/TLS. La coupure d'accès public n'exige pas de détruire n8n : les workflows planifiés peuvent continuer sur le Pi.

## 15. Autres architectures possibles

| Option | Adresse de l'ami | Points forts | Contraintes |
|---|---|---|---|
| IP directe + Nginx/Certbot | `paramètre privé à consulter sur le Pi | Respect exact de la demande ; hébergement local direct. | Certificat court, renouvellement impératif, intégrations parfois incompatibles avec une IP. |
| Domaine + proxy HTTPS | `paramètre privé à consulter sur le Pi | URL stable et souvent plus adaptée à OAuth ; pointe toujours vers l'IP Freebox. | Domaine/DNS à gérer ; renouvellement TLS reste nécessaire. |
| VPN | Adresse privée après connexion | Interface accessible aux deux personnes sans la publier largement. | Client VPN et accès individuel ; webhooks publics à traiter séparément. |

Avec un domaine, un enregistrement DNS `A` peut pointer vers l'IPv4 publique. Ne pas ajouter un `AAAA` tant que l'accès IPv6 n'est pas maîtrisé. Caddy peut gérer automatiquement HTTPS et relayer vers `paramètre privé à consulter sur le Pi:5678` avec une configuration courte ; le DNS doit pointer correctement et les challenges doivent être possibles. [Guide officiel Caddy](https://caddyserver.com/docs/quick-starts/reverse-proxy).

Pour deux personnes qui n'ont pas besoin de webhooks entrants, je privilégierais un VPN avec un accès individuel. Pour l'adresse IP publique directement saisie dans le navigateur, la procédure Nginx/Certbot de ce rapport est la réponse proposée. Le choix final peut conserver une interface privée tout en publiant seulement les webhooks nécessaires.

## 16. Informations nécessaires pour passer du rapport au déploiement

Les points non établis sont : IPv4 publique réelle et ports 80/443 disponibles ; éventuels conflits Freebox ; besoin de mêmes workflows ; édition/licence ; comptes et 2FA déjà configurés ; besoin de webhooks/OAuth ; email de contact ACME ; possibilité de tester depuis l'extérieur.

**État en fin de rédaction :** n8n reste en accès local via SSH. Aucun certificat public, proxy Internet, timer de renouvellement, changement DHCP ou redirection Freebox de ce rapport n'a été appliqué. L'ouverture sera une opération distincte à partir de paramètres confirmés et des résultats des tests.
