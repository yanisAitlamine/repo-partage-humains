> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 3 — Mise en ligne HTTPS, comptes et remise des accès

**Date :** 9 octobre 2026, Europe/Paris. **Statut : mise en ligne réalisée et vérifiée.**

Les scripts d'arrêt avec sauvegarde, de remise en service et le démarrage
automatique ajoutés ensuite sont décrits dans le
[rapport 4](RAPPORT-04-arret-et-demarrage.md).

Ce document complète le rapport d'installation et le rapport de conception. Il décrit les opérations effectuées après la confirmation de la redirection Freebox et les résultats observés. Les vérifications répétées sont regroupées. Aucun mot de passe, contenu de clé privée, cookie de session ou secret n8n n'est reproduit.

## 1. Résultat final

L'adresse à utiliser est **paramètre privé à consulter sur le Pi Le navigateur doit utiliser HTTPS. Le certificat est un certificat public Let's Encrypt pour cette adresse IP ; sa vérification a réussi sans désactiver les contrôles TLS.

| Compte | Identifiant de connexion | Rôle | Remise des accès |
|---|---|---|---|
| yanis | `[ADRESSE-MAIL]` | Propriétaire de l'instance | Email envoyé uniquement à Yanis |
| ilyes | `[ADRESSE-MAIL]` | Membre | Email envoyé uniquement à Ilyes |

Chaque email contient l'adresse HTTPS, l'identifiant et le mot de passe du destinataire. Les mots de passe sont distincts, générés aléatoirement, et longs de 36 caractères. L'adresse email sert d'identifiant de connexion ; `yanis` et `ilyes` sont les noms affichés des comptes.

La connexion des deux comptes a été testée par l'API HTTPS, puis l'accès authentifié à la liste des workflows a répondu HTTP 200 pour chacun. Une requête sans connexion à cette même liste a répondu HTTP 401. La page de création initiale du propriétaire est désactivée.

La double authentification reste à activer personnellement par chaque utilisateur. Le SMTP de n8n n'est pas configuré : la récupération de mot de passe par email n'est pas encore disponible. Les emails d'accès ont été envoyés par le connecteur Gmail, pas par n8n.

## 2. Architecture déployée

```text
Navigateur de Yanis ou d'Ilyes
        |
        | HTTPS : paramètre privé à consulter sur le Pi
        v
Freebox : redirection TCP WAN 443 vers le Pi, LAN 443
        |
        v
Caddy 2.11.7 : écoute paramètre privé à consulter sur le Pi:443
        |
        | HTTP sur la boucle locale du Pi
        v
n8n 2.42.5 : paramètre privé à consulter sur le Pi:5678
        |
        +-- volume persistant n8n_n8n_data
        +-- réseau Docker privé vers les task runners

Administration Caddy : paramètre privé à consulter sur le Pi:2019
Validation et renouvellement du certificat : TLS-ALPN sur TCP 443
```

Le port 80 n'a pas été ajouté. Caddy écoute uniquement sur l'adresse IPv4 LAN indiquée ; il ne publie pas l'application sur l'IPv6 globale du Pi. Le port un essai ou état interne reste lié à la boucle locale. Le service de code conserve son réseau privé et n'a pas de port publié sur Internet.

La capture fournie par Yanis montre une redirection active TCP WAN 443 / LAN 443 vers `yanis-pi`, avec toutes les adresses sources autorisées et la case DMZ décochée. Aucun réglage Freebox n'a été modifié par l'assistant. La réservation DHCP et les autres règles existantes ne sont pas confirmées par cette capture.

Les serveurs de validation Let's Encrypt ont effectivement atteint le Pi par Internet, d'abord en environnement de test puis en production. L'adresse publique a aussi répondu depuis Windows et depuis le Pi, via l'IP publique. Le test dans un navigateur sur un réseau mobile ou chez Ilyes reste à effectuer par les utilisateurs ; ces dernières vérifications locales passent par la même Freebox.

## 3. Pourquoi Caddy a remplacé la proposition Nginx/Certbot

Le rapport 2 proposait Nginx avec Certbot et une validation HTTP sur le port 80. Après la confirmation du port 443, Caddy a permis d'utiliser la validation TLS-ALPN sur ce seul port. Il assure le proxy HTTPS, l'obtention et le renouvellement du certificat dans un service unique. Nginx et Certbot n'ont pas été installés.

Let's Encrypt fournit les certificats d'IP avec le profil `shortlived`. Le certificat obtenu est valable environ 160 heures. Son renouvellement doit donc rester automatique et le port 443 accessible. Annonce officielle Let's Encrypt (référence d’exploitation retirée).

L'issuer ACME a été configuré explicitement pour l'IP, avec `profile shortlived` et `disable_http_challenge`. Une première configuration répondait uniquement par une page de préparation HTTP 503 : le formulaire initial n8n n'a donc pas été publié avant la création du propriétaire.

## 4. Déblocage de sudo

Une nouvelle session SSH demandait un mot de passe pour sudo, malgré une ligne personnelle `NOPASSWD` dans le fichier montré par Yanis. La liste des autorisations faisait apparaître une règle `NOPASSWD` puis une autre règle autorisant sudo avec mot de passe. L'ordre des règles explique le comportement : la dernière règle correspondante peut définir l'authentification applicable.

Yanis a effectué lui-même la modification avec `visudo`, en plaçant sa règle après celle du groupe sudo. L'assistant n'a pas modifié le fichier sudoers et n'a pas reçu le mot de passe système.

```sh
sudo -n true
sudo -n visudo -c
```

La première commande vérifie que sudo peut fonctionner sans interaction. La seconde vérifie la syntaxe du fichier principal et de ses fichiers inclus. Les contrôles ont réussi. La règle personnelle reste un accès administrateur complet sans mot de passe : la protection de la clé SSH est donc essentielle. Le succès observé lors de l'installation initiale ne suffisait pas, à lui seul, à établir le comportement d'une nouvelle session sans cache sudo.

## 5. Préparation du logiciel et des fichiers

La version officielle Caddy ARM64 **2.11.7** a été obtenue depuis les releases du dépôt `caddyserver/caddy`. Les fichiers de travail se trouvent dans `paramètre privé à consulter sur le Pi`, dossier privé avec droits 700 : archive `caddy.tar.gz`, liste `checksums.txt`, binaire `caddy`, configurations et scripts.

La liste des empreintes utilise SHA-512. Une première tentative avec SHA-256 ne pouvait pas la vérifier ; le contrôle a été corrigé avec SHA-512 et a réussi avant l'installation du binaire. La validation de configuration Caddy et le contrôle de syntaxe du script shell ont également réussi. [Releases officielles Caddy](https://github.com/caddyserver/caddy/releases/tag/v2.11.7).

Depuis Windows, les transferts de fichiers ont utilisé `scp` et la clé originale, par exemple :

```powershell
scp -q -o BatchMode=yes -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" .\Caddyfile .\compose.yaml [ADRESSE-MAIL]:paramètre privé à consulter sur le Pi
```

`BatchMode=yes` empêche une attente de saisie de mot de passe. `StrictHostKeyChecking=yes` impose l'utilisation de l'identité SSH déjà connue du Pi. `-i` désigne l'original de la clé, sans copier son contenu. Les transferts suivants ont ajouté les configurations de préparation et les scripts.

| Fichier du projet | Utilité |
|---|---|
| `Caddyfile.preparation` | Certificat de test et page de préparation 503 |
| `Caddyfile.production-preparation` | Certificat de production, toujours derrière la page 503 |
| `Caddyfile` | Configuration finale du proxy vers n8n |
| `preparer-https-pi.sh` | Sauvegarde initiale, installation du binaire et du service Caddy |
| `creer-comptes-n8n.py` | Initialisation des comptes via les routes n8n |
| `verifier-acces-https.py` | Contrôles du certificat, de l'authentification et des cookies |
| `sauvegarder-n8n-pi.sh` | Sauvegarde cohérente des données et des configurations finales |
| `compose.yaml` | Paramètres n8n adaptés à l'URL publique |

Les scripts présents dans le dossier documentent leurs commandes internes. Ils ne contiennent aucun secret. Le script de création des comptes est une opération d'initialisation ; il refuse désormais de recommencer lorsque la remise des accès est enregistrée.

## 6. Sauvegarde initiale et installation Caddy

La préparation a été lancée sur le Pi avec :

```sh
sudo -n bash paramètre privé à consulter sur le Pi
```

Les commandes internes et leur fonction sont :

| Commande ou opération | Fonction et résultat |
|---|---|
| `test`, `id -u` | Vérifier l'exécution administrateur, la présence des fichiers et l'absence d'une configuration Caddy à écraser |
| `umask 077`, `mkdir -p backups` | Créer des archives privées |
| `docker compose config --quiet` | Vérifier le Compose avec les secrets déjà présents sur le Pi, sans les afficher |
| `docker compose ps -q n8n` | Identifier le conteneur et son volume existant |
| `docker compose stop n8n` | Arrêter brièvement n8n pour une copie cohérente de SQLite |
| `trap ... EXIT` | Prévoir la relance de n8n si la sauvegarde échoue |
| `docker inspect --format ...` | Retrouver l'image exacte du conteneur |
| `docker run --rm --volumes-from ... --entrypoint tar ...` | Archiver `.n8n` en utilisant l'image existante et le volume persistant |
| `tar -czf ... compose.yaml .env` | Sauvegarder également la clé de chiffrement et les autres paramètres |
| `gzip -t` | Vérifier l'intégrité de compression des deux archives |
| `docker compose start n8n` | Relancer le service après la sauvegarde |
| `useradd --system ... caddy` | Créer un compte dédié, sans shell interactif |
| `install -m 0755 ... paramètre privé à consulter sur le Pi` | Installer le binaire vérifié |
| `install -d`, `install -m 0644` | Installer la configuration de préparation |
| Écriture de `caddy.service` | Définir le service systemd et ses restrictions |
| `caddy validate --config ... --adapter caddyfile` | Valider la configuration avant démarrage |
| `systemctl daemon-reload` | Charger la définition du service |
| `systemctl enable --now caddy` | Démarrer Caddy et l'activer au démarrage du Pi |

Le service utilise le compte `caddy`, un dossier d'état `paramètre privé à consulter sur le Pi` de droits 700, `NoNewPrivileges`, `PrivateTmp`, `ProtectSystem=strict` et `ProtectHome=true`. Il reçoit seulement la capacité nécessaire à l'ouverture du port 443. La définition complète figure dans `preparer-https-pi.sh`.

La sauvegarde initiale a créé `data-paramètre privé à consulter sur le Pi-020051.tar.gz` et `config-paramètre privé à consulter sur le Pi-020051.tar.gz`. Les fichiers sont détenus par root avec droits 600. Leur compression a été vérifiée ; une restauration complète n'a pas été effectuée.

## 7. Création et vérification des deux comptes

L'adresse d'Ilyes a été retrouvée dans les emails de la boîte Gmail de Yanis : `[ADRESSE-MAIL]`. Yanis a confirmé sa propre adresse puis demandé explicitement que chacun reçoive uniquement ses accès.

```sh
python3 paramètre privé à consulter sur le Pi
```

Le script attendait d'abord la disponibilité de `/healthz/readiness`, puis lisait `/rest/settings` pour connaître l'état de l'initialisation. La création s'est déroulée via les routes de la version n8n installée, sans modifier directement la base de données :

| Requête | Fonction |
|---|---|
| `POST /rest/owner/setup` | Créer Yanis comme propriétaire avec son email et son mot de passe |
| `POST /rest/invitations` | Créer l'invitation d'Ilyes avec le rôle membre |
| `POST /rest/invitations/accept` | Accepter l'invitation et définir son profil et son mot de passe |
| `POST /rest/logout` | Fermer les sessions de vérification |

Ces opérations d'initialisation utilisaient la boucle locale du Pi pendant que Caddy présentait encore la page 503. Le script vérifiait que le SMTP était absent afin que n8n n'envoie pas une invitation avant la remise demandée par Yanis. Les emails d'accès ont ensuite été envoyés séparément.


## 8. Certificat de production et correction pour l'accès par IP

La configuration de test a obtenu un certificat staging. Les journaux ont confirmé la réussite du challenge externe `tls-alpn-01`. La configuration a ensuite été remplacée par l'environnement de production :

```sh
sudo -n paramètre privé à consulter sur le Pi fmt --overwrite paramètre privé à consulter sur le Pi
sudo -n paramètre privé à consulter sur le Pi validate --config paramètre privé à consulter sur le Pi --adapter caddyfile
sudo -n install -m 0644 paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi
sudo -n systemctl restart caddy
sudo -n systemctl is-active caddy
```

Le formatage normalise le fichier, la validation vérifie sa syntaxe et ses modules, `install` copie le fichier avec les droits adaptés, puis le redémarrage charge la configuration de production. Le certificat de production a été obtenu.

Un premier contrôle client retournait une erreur de connexion TLS. Les clients accédant directement à une IP peuvent omettre SNI ; l'adresse locale du serveur étant différente de l'IP publique, Caddy devait recevoir une identité de certificat par défaut. L'ajout de `default_sni paramètre privé à consulter sur le Pi` a corrigé le problème. [Option officielle `default_sni`](https://caddyserver.com/docs/caddyfile/options#default-sni).

Après formatage, validation, installation et `systemctl reload caddy`, ce contrôle a réussi :

```sh
curl --connect-timeout 5 --max-time 15 --resolve paramètre privé à consulter sur le Pi:443:paramètre privé à consulter sur le Pi -sS -o paramètre privé à consulter sur le Pi -w 'HTTP: %{http_code}, TLS: %{ssl_verify_result}\n' paramètre privé à consulter sur le Pi
```

`--resolve` fait joindre l'adresse LAN tout en vérifiant l'identité TLS de l'IP publique. Le résultat était HTTP 503, volontaire en mode préparation, avec vérification TLS 0, donc réussie. Aucun `-k` ni contournement du certificat n'a été utilisé.

Le certificat final, lu avec `openssl x509`, indique :

| Champ | Valeur observée |
|---|---|
| Émetteur | Let's Encrypt, YE1 |
| Identité SAN | `IP Address:paramètre privé à consulter sur le Pi` |
| Début | 8 octobre 2026, 23:06:49 UTC |
| Fin du certificat initial | 15 octobre 2026, 15:06:48 UTC |

Cette date de fin concerne le premier certificat. Caddy est configuré pour le renouveler ; un renouvellement réel n'a pas encore eu lieu pendant cette intervention.

## 9. Adaptation du Compose et ouverture de l'application

Les paramètres publics ont été définis dans le Compose :

```yaml
N8N_HOST: paramètre privé à consulter sur le Pi
N8N_PORT: "5678"
N8N_PROTOCOL: https
paramètre privé à consulter sur le Pi: paramètre privé à consulter sur le Pi
N8N_WEBHOOK_URL: paramètre privé à consulter sur le Pi
N8N_PROXY_HOPS: "1"
paramètre privé à consulter sur le Pi: "true"
```

Le nombre de proxies correspond au seul Caddy devant n8n. Le mappage `paramètre privé à consulter sur le Pi:5678:5678` et le volume persistant ont été conservés. Les valeurs de chiffrement et d'authentification des runners n'ont pas été régénérées.

```sh
cd paramètre privé à consulter sur le Pi
sudo -n cp -p compose.yaml compose.before-https.yaml
sudo -n install -o yanis -g yanis -m 0600 paramètre privé à consulter sur le Pi compose.yaml
sudo -n docker compose config --quiet
sudo -n docker compose up -d
sudo -n docker compose ps
```


La configuration finale Caddy est :

```caddyfile
{
    auto_https disable_redirects
    default_sni paramètre privé à consulter sur le Pi
    servers {
        protocols h1 h2
    }
}

paramètre privé à consulter sur le Pi {
    bind paramètre privé à consulter sur le Pi
    tls {
        issuer acme paramètre privé à consulter sur le Pi {
            profile shortlived
            disable_http_challenge
        }
    }
    header {
        X-Content-Type-Options nosniff
        Referrer-Policy no-referrer
        -Server
    }
    reverse_proxy paramètre privé à consulter sur le Pi:5678
}
```

Les en-têtes ajoutés limitent l'interprétation MIME et la transmission de l'adresse de provenance ; l'en-tête `Server` est retiré. Caddy transmet les requêtes et les connexions de l'éditeur au service local. Ses options TLS par défaut sont conservées. [Configuration TLS officielle Caddy](https://caddyserver.com/docs/caddyfile/directives/tls).

L'ouverture finale a utilisé :

```sh
curl -fsS paramètre privé à consulter sur le Pi
sudo -n paramètre privé à consulter sur le Pi fmt --overwrite paramètre privé à consulter sur le Pi
sudo -n paramètre privé à consulter sur le Pi validate --config paramètre privé à consulter sur le Pi --adapter caddyfile
sudo -n install -m 0644 paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi
sudo -n systemctl reload caddy
```

La réponse 503 de préparation a alors été remplacée par le proxy vers n8n, après création des comptes et vérification du certificat.

## 10. Contrôles fonctionnels et limites

```sh
python3 paramètre privé à consulter sur le Pi
```

Le script a vérifié le certificat avec le magasin de confiance système, sans désactiver les contrôles, puis les deux comptes via l'adresse publique. Sa première version supposait un champ `urlBaseEditor` absent de `/rest/settings` ; le contrôle a été corrigé. Les URL effectives ont été vérifiées séparément dans l'environnement du conteneur.

| Contrôle | Résultat |
|---|---|
| Certificat public, identité IP et chaîne de confiance | Vérifiés |
| `/healthz/readiness` par HTTPS | HTTP 200 |
| Interface n8n par HTTPS | HTTP 200 |
| En-tête `X-Content-Type-Options` | `nosniff` |
| Création initiale du propriétaire | Désactivée |
| `/rest/workflows` sans session | HTTP 401 |
| Connexion Yanis et accès aux workflows | Réussis |
| Connexion Ilyes et accès aux workflows | Réussis |
| Cookies d'authentification | `Secure` et `HttpOnly` vérifiés |

Depuis Windows :

```powershell
curl.exe --connect-timeout 5 --max-time 15 -sS -o NUL -w "HTTP: %{http_code}, TLS: %{ssl_verify_result}\n" paramètre privé à consulter sur le Pi
```

Résultat : HTTP 200, vérification TLS 0. L'ouverture avec le lecteur web distant de l'assistant a échoué parce que cet outil ne pouvait pas ouvrir cette référence IP ; ce résultat n'est pas présenté comme une panne du service. Les validations ACME externes et les contrôles clients précédents ont réussi.

Les commandes d'état ont aussi été utilisées :

```sh
sudo -n ss -ltnp '( sport = :443 or sport = :80 or sport = :5678 or sport = :2019 )'
sudo -n systemctl is-enabled caddy docker
sudo -n journalctl -u caddy -n 40 --no-pager
sudo -n stat -c '%a %U %n' paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi
```

Elles ont confirmé les écoutes prévues, l'absence d'écoute Caddy sur 80, l'activation de Docker et Caddy au démarrage, l'émission du certificat, et les droits 600 du `.env` / 700 des dossiers privés. Une première lecture de `docker compose ps` sans sudo a échoué sur la socket Docker ; les commandes suivantes ont utilisé sudo.

Un redémarrage complet du Pi, une restauration, un workflow métier, les webhooks entrants, une intégration OAuth et le travail des deux personnes sur un même workflow n'ont pas été testés. Le partage standard de workflows en auto-hébergement est une fonction des offres Business et Enterprise ; deux comptes sur Community ne l'activent pas. Le propriétaire possède une visibilité plus large que le membre. [Documentation officielle du partage](https://docs.n8n.io/workflows/sharing/).

## 11. Envoi des emails et retrait des secrets temporaires

Le connecteur Gmail a envoyé deux messages distincts après les tests HTTPS. Aucun destinataire en copie n'a été ajouté.

| Destinataire | Objet | Identifiant du message envoyé |
|---|---|---|
| `[ADRESSE-MAIL]` | Tes accès n8n — Yanis | `paramètre privé à consulter sur le Pi` |
| `[ADRESSE-MAIL]` | Tes accès n8n — Ilyes | `paramètre privé à consulter sur le Pi` |

Le service Gmail a confirmé les deux envois. La réception dans la boîte d'Ilyes n'a pas été vérifiée ; il peut consulter aussi ses courriers indésirables.

Après enregistrement des références d'envoi sans mots de passe, le fichier temporaire a été supprimé :

```sh
rm -- paramètre privé à consulter sur le Pi
test ! -e paramètre privé à consulter sur le Pi
stat -c '%a %U %n' paramètre privé à consulter sur le Pi
```

Le contrôle a confirmé l'absence du fichier de mots de passe et les droits 600 du fichier de suivi. Les mots de passe n'ont pas été enregistrés dans les rapports ni dans les scripts. Les emails constituent les copies de remise demandées par Yanis ; chacun peut remplacer son mot de passe après connexion et le conserver dans son gestionnaire.

## 12. Sauvegarde de l'état final

Cette section décrit la première version du script de sauvegarde. La version
installée ensuite sauvegarde aussi l'état Caddy et les scripts de contrôle ;
voir le rapport 4 pour son format actuel.

Le script de sauvegarde a été transféré sur le Pi, ses fins de ligne Windows normalisées, sa syntaxe vérifiée, puis il a été lancé :

```sh
sed -i 's/\r$//' paramètre privé à consulter sur le Pi
bash -n paramètre privé à consulter sur le Pi
sudo -n bash paramètre privé à consulter sur le Pi
```

Il applique la même copie cohérente que la première sauvegarde, avec arrêt bref de n8n et relance garantie en cas d'échec. L'archive de configuration ajoute `paramètre privé à consulter sur le Pi` et `paramètre privé à consulter sur le Pi`. Il vérifie les deux archives avec `gzip -t`, redémarre n8n et attend sa disponibilité.

La sauvegarde finale a créé :

- `paramètre privé à consulter sur le Pi` : données après création des comptes.

Le service est redevenu prêt. Ces archives contiennent des données sensibles et restent privées. Elles doivent être copiées de manière chiffrée sur un autre appareil pour couvrir une panne de carte SD. Aucune sauvegarde automatique régulière ni copie extérieure n'a été configurée pendant cette intervention.

## 13. Entretien et points restant à mettre en place

Les commandes courantes sont :

```sh
cd paramètre privé à consulter sur le Pi
sudo docker compose ps
sudo docker compose logs --tail=100 n8n
sudo systemctl status caddy --no-pager
sudo journalctl -u caddy -n 50 --no-pager
sudo bash paramètre privé à consulter sur le Pi
```

La réservation DHCP de `paramètre privé à consulter sur le Pi` doit être confirmée dans la Freebox. Si l'adresse LAN change, l'écoute Caddy doit être adaptée ; si l'adresse publique change, il faut modifier les URL n8n et l'identité du certificat. Caddy doit rester démarré et le port 443 disponible pour renouveler les certificats courts.


La clé SSH originale reste dans `paramètre privé à consulter sur le Pi`. La copie du projet n'est pas utilisée et sa suppression manuelle reste documentée dans le README et le rapport 1. Une phrase de passe et l'agent SSH permettent l'usage local sans remettre le contenu de la clé dans le projet ; ils ne retirent pas à un assistant exécutant des outils avec les droits de Yanis les permissions de ce compte. Pour une séparation stricte, utiliser un compte d'intervention distinct et limiter ses autorisations sur le Pi.

Ces points d'entretien et d'identité complètent l'accès HTTPS maintenant opérationnel. Ils ne sont pas présentés comme déjà configurés.
