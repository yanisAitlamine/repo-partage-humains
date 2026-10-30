<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 06 — Domaine DuckDNS, HTTPS et préparation de Gmail

**Date : 9 octobre 2026 — Europe/Paris**

**Adresse habituelle : paramètre privé à consulter sur le Pi

## 1. Résultat de l'intervention

L'accès n8n par le domaine **paramètre privé à consulter sur le Pi** est réparé. Le DNS pointait
déjà vers la bonne IP ; il manquait la prise en charge du nom dans Caddy et
la mise à jour des URL publiques de n8n. Un certificat Let's Encrypt pour le
domaine a été obtenu, les URL ont été modifiées et les contrôles HTTPS et
de connexion ont réussi. Le modèle de l'assistant reste **GPT-6 Luna**.

Le retour OAuth indiqué par n8n est maintenant :

```text
# Détail d’exploitation retiré de la version publique.
```

Cette adresse est prête à être enregistrée dans un client OAuth Google.
**La boîte Gmail n'est pas encore connectée** : aucun identifiant Google ou
Gmail n'était enregistré dans n8n au début de l'intervention. Aucun client
Google Cloud, consentement Google ni workflow Gmail actif n'a été créé
pendant cette intervention. Les étapes restantes sont décrites plus bas.

Ce rapport complète le rapport 05 et ses annexes. Il reprend également la
gestion du dépôt GitHub, qui n'avait pas de rapport séparé.

## 2. Changements intervenus depuis l'installation de l'assistant

### GitHub et dépôt du Pi

Yanis a créé une clé SSH sur le Pi, ajouté sa partie publique à GitHub,
finalisé la connexion de GitHub CLI et cloné son dépôt. L'authentification
SSH utilisée pour Git et la connexion de `gh` sont deux mécanismes distincts.
La commande de connexion proposée pour éviter l'ouverture d'un navigateur
sur le Pi était :

```sh
GH_BROWSER=true gh auth login --hostname github.com --git-protocol ssh --web
```

La validation dans le navigateur a été réalisée par Yanis. Les jetons de
connexion et clés privées n'ont pas été affichés dans le rapport.

À sa demande, le dépôt GitHub **VMsetup** a été renommé **DevLinuxSetup** :

```sh
gh repo rename DevLinuxSetup --repo yanisAitlamine/VMsetup --yes
```

Le dossier local est désormais `paramètre privé à consulter sur le Pi`, et
l'origine Git pointe vers :

```text
[ADRESSE-MAIL]:yanisAitlamine/DevLinuxSetup.git
```

Les vérifications comprennent la consultation du dépôt avec `gh repo view`,
la lecture de l'origine avec `git remote get-url origin` et une lecture du
référencement distant avec `git ls-remote`. Les deux premiers contrôles ont
été répétés pendant cette intervention. Le dépôt est accessible à
yanisAitlamine/DevLinuxSetup (référence d’exploitation retirée).

Le script `devVMsetup.sh` a été examiné et sa syntaxe vérifiée, sans exécution
ni modification. Le problème principal relevé était l'installation de
`docker.io` : la simulation APT pouvait remplacer les paquets Docker déjà
utilisés par n8n. Autres points relevés : une ligne `echo` absorbant une
commande, les paramètres Git personnels écrits en dur, des dépendances de
polices manquantes et une version de Neovim insuffisante pour la configuration
LazyVim envisagée. Le script reste à corriger avant utilisation sur ce Pi.

### Modèles de l'assistant

L'assistant est passé de GPT-5.5 à GPT-6.1 Sol, puis à **GPT-6 Luna** après
la demande de réduction du coût. GPT-5.6 Luna avait été demandé avec la
possibilité de choisir un modèle encore moins cher ; GPT-6 Luna a été
retenu après comparaison des tarifs et test de compatibilité.

Ces deux changements sont détaillés dans les annexes du rapport 05.
Ils ont consisté à sauvegarder le Compose, changer le modèle, valider la
configuration et recréer uniquement le service n8n. Les tests ont confirmé
une réponse dans le chat et un appel d'outil de test avec le SDK installé.

Le réglage conservé pendant la migration de domaine est :

```yaml
paramètre privé à consulter sur le Pi: openai/gpt-6-luna
```

La version de n8n et des runners reste **2.42.6**, avec les images figées par
empreinte. Les clés OpenAI et Daytona, les comptes Yanis et Ilyes et les
volumes persistants sont conservés.

## 3. Diagnostic du problème DuckDNS

### Ce qui fonctionnait déjà

Les résolutions DNS ont confirmé :

| Élément | Valeur constatée |
| --- | --- |
| Nom public | `paramètre privé à consulter sur le Pi` |
| Enregistrement A | `paramètre privé à consulter sur le Pi` |
| TTL de la réponse A du résolveur interrogé | 60 secondes |
| Requête AAAA auprès de `paramètre privé à consulter sur le Pi` | Aucune adresse IPv6 publiée dans la réponse |
| Adresse LAN du Pi | `paramètre privé à consulter sur le Pi` |
| Accès HTTPS existant | `paramètre privé à consulter sur le Pi |
| Point d'entrée public utilisé | TCP 443, redirigé vers le Pi |

Un nom DNS indique à quelle adresse IP se connecter. Il ne configure ni
le certificat du serveur ni l'application située derrière lui.

### Ce qui empêchait l'accès

L'ancien Caddyfile ne déclarait que le site `paramètre privé à consulter sur le Pi
Lors d'une connexion par domaine, le navigateur demande un certificat et
un site pour **paramètre privé à consulter sur le Pi**. Caddy ne connaissait pas ce nom.
Le test initial avec ce nom a échoué pendant la négociation TLS :
`tlsv1 alert internal error`, code curl **35**, sans réponse HTTP.

n8n annonçait aussi encore ces anciennes valeurs :

```yaml
N8N_HOST: paramètre privé à consulter sur le Pi
paramètre privé à consulter sur le Pi: paramètre privé à consulter sur le Pi
N8N_WEBHOOK_URL: paramètre privé à consulter sur le Pi
```

Même avec un certificat ajouté seul, certaines URL produites par n8n
auraient donc continué à utiliser l'IP. Les deux niveaux ont été corrigés.

## 4. Sauvegarde et méthode de déploiement

Avant les changements, la commande existante a réalisé une sauvegarde complète :

```sh
sudo n8n-sauvegarder
```

Elle a fermé momentanément Caddy, arrêté n8n proprement puis les runners,
vérifié SQLite, archivé les données, les secrets et les configurations,
contrôlé les archives et remis les services en marche. Le contrôle SQLite
a retourné **OK**. La sauvegarde vérifiée est :

```text
paramètre privé à consulter sur le Pi
```

Une copie supplémentaire des trois fichiers directement remplacés a été
créée dans le dossier privé :

```text
paramètre privé à consulter sur le Pi
```

Ce dossier contient le Caddyfile, le Compose, le programme d'entretien
précédents et leurs métadonnées de propriétaire et de permissions. Il
n'est pas une deuxième sauvegarde complète de la base de données.

Le programme `configurer-domaine-n8n.py` applique les fichiers préparés.
Il prend le même verrou que les scripts d'arrêt et de sauvegarde, vérifie
la syntaxe, refuse des changements supplémentaires inattendus dans le
Compose et conserve les propriétaires et les permissions des fichiers.
Les remplacements sont atomiques. En cas d'échec, il remet les trois
fichiers précédents puis recharge Caddy et relance n8n. Aucun retour arrière
n'a été nécessaire.

Les sorties susceptibles d'inclure des variables sensibles sont capturées
sans être affichées. Le rapport et le programme ne contiennent aucune clé
API, aucun mot de passe ni aucun jeton Google.

## 5. Configuration réalisée

### HTTPS et certificat du domaine

Un deuxième site a été ajouté au Caddyfile :

```caddyfile
paramètre privé à consulter sur le Pi {
    bind paramètre privé à consulter sur le Pi
    tls {
        issuer acme paramètre privé à consulter sur le Pi {
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

La validation ACME utilise **TLS-ALPN sur le port 443**. Le port 80 n'a
pas été ouvert et aucun jeton DuckDNS n'est nécessaire à cette méthode.
Caddy renouvelle automatiquement le certificat. Cette méthode est décrite
dans sa [documentation HTTPS](https://caddyserver.com/docs/automatic-https#tls-alpn-challenge).

Le certificat obtenu présente le domaine dans ses noms autorisés, est
émis par **Let's Encrypt / YE1** et expire le **7 janvier 2027 à
15:06:20 UTC**, selon le certificat observé. Sa validation par les clients
de test a réussi. Les clés privées TLS restent dans l'état privé de Caddy.

Le site de l'ancienne IP a été conservé avec sa configuration précédente.
Le domaine devient l'adresse habituelle. Utiliser explicitement **paramètre privé à consulter sur le Pi :
aucun accès public HTTP sur le port 80 ni redirection HTTP vers HTTPS n'a
été ajouté.

### URL publiques de n8n

Le Compose actif utilise maintenant :

```yaml
N8N_HOST: paramètre privé à consulter sur le Pi
N8N_PORT: "5678"
N8N_PROTOCOL: https
paramètre privé à consulter sur le Pi: paramètre privé à consulter sur le Pi
N8N_WEBHOOK_URL: paramètre privé à consulter sur le Pi
N8N_PROXY_HOPS: "1"
paramètre privé à consulter sur le Pi: "true"
```

n8n écoute toujours localement sur `paramètre privé à consulter sur le Pi:5678`. Caddy expose HTTPS
sur 443 et transmet les informations de la connexion d'origine. Les URL
de webhooks sont annoncées avec le domaine et sans le port interne 5678.
La variable utilisée est bien `N8N_WEBHOOK_URL`, adaptée à cette version ;
[la documentation n8n](https://docs.n8n.io/deploy/host-n8n/configure-n8n/basic-configuration/configuration-examples/configure-webhook-urls-with-reverse-proxy.md)
indique le remplacement de l'ancienne variable `WEBHOOK_URL` depuis 2.35.0.

### Scripts d'entretien et de vérification

Le programme installé `paramètre privé à consulter sur le Pi` utilise désormais
le domaine pour son contrôle HTTPS. Il se connecte directement à l'adresse
LAN du Pi tout en vérifiant le certificat pour le vrai nom DNS :

```sh
curl --resolve paramètre privé à consulter sur le Pi:443:paramètre privé à consulter sur le Pi \
  paramètre privé à consulter sur le Pi
```

Cela permet de contrôler localement le service sans dépendre du retour
du trafic par l'IP publique. Ce contrôle ne simule pas un accès depuis
un autre réseau ; le contrôle Windows utilise aussi le DNS normal.

Les sources du script de mise à jour, du vérificateur HTTPS, du
vérificateur de l'assistant et du programme de renouvellement du mot de
passe ont également été adaptées au domaine. Le programme de mot de passe
n'a pas été exécuté : aucun nouveau mot de passe n'a été généré.

Le lancement réel de `sudo n8n-demarrer` a réussi et affiche maintenant
`paramètre privé à consulter sur le Pi Docker, n8n, les runners et Caddy sont en service.

## 6. Commandes et utilité

Les fichiers et programmes ont été transmis depuis Windows avec SSH et
SCP, en utilisant l'original de la clé privée dans `.ssh` :

```powershell
ssh -o BatchMode=yes -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" [ADRESSE-MAIL]
scp -o BatchMode=yes -o StrictHostKeyChecking=yes -i "paramètre privé à consulter sur le Pi" .\Caddyfile .\compose.yaml .\pi-services.sh [ADRESSE-MAIL]:paramètre privé à consulter sur le Pi
```

Le transfert incluait également les programmes de déploiement et de
vérification mis à jour. `BatchMode` évite les demandes de mot de passe
interactives ; `StrictHostKeyChecking` vérifie l'identité SSH du Pi.
Les programmes multi-lignes ont été transmis sur l'entrée standard, avec
suppression des retours chariot Windows avant interprétation par Python.
Les fins de ligne des sources transférés ont été normalisées avant déploiement.

| Commande ou contrôle utilisé | Utilité et résultat |
| --- | --- |
| `Resolve-DnsName -Name paramètre privé à consulter sur le Pi -Type A -Server paramètre privé à consulter sur le Pi` | Confirmer l'IP publique publiée. |
| `Resolve-DnsName -Name paramètre privé à consulter sur le Pi -Type AAAA -Server paramètre privé à consulter sur le Pi` | Vérifier qu'une adresse IPv6 inattendue ne détourne pas la connexion. |
| `getent ahostsv4 paramètre privé à consulter sur le Pi` | Confirmer la résolution IPv4 depuis le Pi. |
| `systemctl is-active docker n8n-stack caddy` | Contrôler l'état des services. |
| `docker compose -f paramètre privé à consulter sur le Pi ps --format json` | Identifier les conteneurs, leur disponibilité et leurs ports. |
| Lecture ciblée des variables avec `docker exec ... node -e ...` | Contrôler seulement les URL et le modèle ; aucune lecture globale des secrets Docker. |
| SQLite en lecture seule, types de credentials et nombres de workflows | Confirmer l'absence de connexion Gmail ; deux workflows, aucun actif avant migration. Aucun contenu de mail ni secret déchiffré. |
| `sudo n8n-sauvegarder` | Réaliser la sauvegarde complète avant modification. |
| `bash -n paramètre privé à consulter sur le Pi` | Vérifier la syntaxe du programme d'entretien. |
| `bash -n paramètre privé à consulter sur le Pi` | Vérifier la syntaxe de la source du programme de mise à jour ; il n'a pas été lancé. |
| `caddy validate --config paramètre privé à consulter sur le Pi --adapter caddyfile` | Valider les deux sites et les options TLS. Code 0. |
| `sudo python3 paramètre privé à consulter sur le Pi` | Installer les fichiers contrôlés, sauvegarder leurs anciennes versions et prévoir un retour arrière. |
| `docker compose -f paramètre privé à consulter sur le Pi config -q` | Valider le Compose sans afficher `.env`. Code 0. |
| `systemctl reload caddy` | Charger le domaine et lancer l'obtention du certificat sans redémarrage complet de Caddy. Code 0. |
| `docker compose ... up -d --no-deps --wait --wait-timeout 180 --pull never n8n` | Recréer n8n pour charger les URL, sans changer ses images ni ses données. Code 0. |
| `curl --resolve ... /healthz/readiness` | Attendre HTTPS et la disponibilité de n8n avec validation réelle du certificat. |
| `curl.exe ... paramètre privé à consulter sur le Pi depuis Windows | Tester l'accès par le DNS normal : HTTP 200. |
| `python3 .../verifier-domaine-n8n.py` | Vérifier la connexion, les cookies, les workflows et le retour OAuth avec un compte existant fourni sur stdin. |
| `sudo n8n-demarrer` | Confirmer que le programme de démarrage fonctionne avec le domaine. Code 0. |

Le programme Python de vérification TLS a également lu les informations
publiques du certificat : émetteur, domaine et dates. Il n'a pas lu sa clé
privée. Les vérifications du dépôt GitHub sont décrites dans la section 2.

## 7. Résultats des contrôles

| Contrôle | Résultat |
| --- | --- |
| Page principale par domaine, depuis le Pi | HTTP 200, certificat validé |
| Page principale par domaine, depuis Windows avec DNS normal | HTTP 200 |
| Disponibilité `/healthz/readiness` | HTTP 200 |
| Workflows sans authentification | HTTP 401 |
| Connexion du compte Yanis par domaine | Réussie, rôle propriétaire conservé |
| Cookie actif | Secure et HttpOnly |
| Accès authentifié aux workflows | Réussi |
| Constructeur de workflows de l'assistant | Disponible |
| Modèle actif dans le conteneur | `openai/gpt-6-luna` |
| Programme `n8n-demarrer` | Réussi avec l'URL du domaine |
| Autorisation Gmail et réception d'un vrai mail par workflow | Pas encore réalisées |

La connexion Yanis a utilisé son mot de passe existant, transmis uniquement
sur l'entrée standard et non enregistré dans un nouveau fichier. La session
de vérification a ensuite été fermée et la valeur retirée de la mémoire de
travail. Aucun email supplémentaire n'a été envoyé.

L'accès HTTP 200 à la route de callback seule ne signifie pas que Google
est connecté : un véritable retour OAuth contient des paramètres et un
état de connexion valides. L'URL attendue a donc aussi été contrôlée dans
les paramètres n8n après authentification.

Le contrôle HTTP externe via l'outil web n'était pas disponible. Les tests
réalisés depuis le Pi et Windows et l'émission ACME du certificat sont
confirmés ; un essai depuis le réseau d'Ilyes après migration reste utile.

## 8. Ce qu'il faut réellement pour le déclencheur Gmail

### Domaine DuckDNS et OAuth

`paramètre privé à consulter sur le Pi` est déjà un nom DNS public utilisable pour HTTPS.
Google exige un nom d'hôte HTTPS pour le retour OAuth d'une application
Web distante et refuse une IP brute, hors exceptions localhost.
Règles Google des URI de retour (référence d’exploitation retirée).

La liste officielle des suffixes publics contient `paramètre privé à consulter sur le Pi`.
Le domaine privé associé à cette adresse est donc `paramètre privé à consulter sur le Pi`.
Cela permet de préparer les champs de domaine avec ce nom, plutôt que
de prétendre posséder l'ensemble de `paramètre privé à consulter sur le Pi`.
Liste officielle des suffixes (référence d’exploitation retirée).

**L'achat d'un domaine n'est pas nécessaire pour réparer HTTPS ni obtenir
une URL de retour au format attendu.** L'acceptation complète du client,
du domaine déclaré et des permissions devra encore être validée dans
Google Cloud. Si Google demande de prouver la propriété, le faire pour le
sous-domaine réellement contrôlé, via Search Console et un enregistrement
TXT DuckDNS ou une autre méthode proposée. L'API DuckDNS prend en charge
les TXT ; aucun jeton DuckDNS n'a été demandé, copié ou utilisé ici.
API DuckDNS (référence d’exploitation retirée).

### Le déclencheur standard vérifie périodiquement Gmail

Le code installé de **Gmail Trigger**, versions 1 à 1.4, déclare `polling: true`.
Il consulte Gmail suivant la fréquence choisie. Le serveur n'a pas besoin
de recevoir un webhook Google pour ce mode. Le domaine sert à l'accès et
à la connexion OAuth ; ensuite, n8n interroge la Gmail API.
[Documentation Gmail Trigger](https://docs.n8n.io/integrations/builtin/trigger-nodes/n8n-nodes-base.gmailtrigger/).

Un système de notifications Gmail poussé via Google Pub/Sub est une autre
architecture, plus complexe, décrite dans
la documentation Google des notifications Gmail (référence d’exploitation retirée).
Il n'a pas été mis en place. Pour commencer, le déclencheur standard n8n
est la solution retenue dans les étapes ci-dessous.

## 9. Étapes restantes dans Google Cloud et n8n

Ces étapes constituent la suite à réaliser ; elles n'ont pas été exécutées
avec un compte Google pendant cette intervention.

### A. Préparer le projet et la connexion OAuth

1. Dans Google Cloud Console (référence d’exploitation retirée), choisir
   un projet existant ou créer un projet pour l'installation.
2. Activer **Gmail API** dans la bibliothèque d'API.
3. Configurer Google Auth Platform avec un nom d'application et l'adresse
   de contact. Pour un compte Gmail personnel, choisir une audience externe
   et commencer en mode de test.
4. Ajouter le compte Google qui autorisera sa boîte parmi les utilisateurs
   de test. Yanis peut utiliser `[ADRESSE-MAIL]`. Pour Ilyes,
   utiliser son compte Google donnant accès à Gmail ; son adresse Outlook
   connue ne suffit pas à identifier une boîte Gmail.

La démarche n8n self-hosted demande un client OAuth personnalisé ; elle
ne bénéficie pas de la connexion Google gérée par n8n Cloud.
audience Google (référence d’exploitation retirée).

### B. Enregistrer le domaine et le retour exact

Dans **Branding > Authorized domains**, utiliser :

```text
paramètre privé à consulter sur le Pi
```

Le champ domaine n'attend ni `paramètre privé à consulter sur le Pi ni chemin. Google peut demander une
preuve de propriété ; ne pas déclarer `paramètre privé à consulter sur le Pi` comme un domaine possédé.
Gestion des domaines autorisés (référence d’exploitation retirée).

Créer ou modifier un client OAuth de type **Web application**. Dans ses
**Authorized redirect URIs**, enregistrer exactement :

```text
# Détail d’exploitation retiré de la version publique.
```

Cette URI n'a pas de slash final après `callback`, pas de port `5678` et
pas d'adresse IP. Pour le flux serveur n8n, l'URI de retour est le champ
essentiel. Si une origine JavaScript est utilisée par une autre partie
de l'application, son format serait `paramètre privé à consulter sur le Pi sans
chemin ; ce n'est pas le remplacement de l'URI de retour.
Gestion des clients OAuth (référence d’exploitation retirée).

Conserver le Client Secret lors de sa création dans un endroit privé.
Le saisir directement dans n8n par HTTPS, sans le publier dans Git, le
rapport, le chat ou un email.

### C. Autoriser la boîte depuis n8n

1. Se connecter à n8n **par le domaine**.
2. Créer une connexion **Gmail OAuth2 API** avec le Client ID et le Client Secret.
3. Pour un déclencheur qui lit seulement des messages, activer **Custom Scopes**
   et utiliser **Enabled Scopes** avec :

   ```text
   paramètre privé à consulter sur le Pi
   ```

4. Vérifier les permissions affichées puis cliquer sur la connexion Google,
   choisir le compte voulu, autoriser l'accès et enregistrer la connexion.

Les deux champs de scopes personnalisés ont été confirmés dans le code des
credentials installé sur le Pi. La connexion standard demande autrement
des permissions plus larges, dont modification et composition. Le scope
en lecture seule ne convient pas à une étape ultérieure qui envoie un mail
ou le marque comme lu : adapter alors les permissions au besoin réel et
refaire le consentement. Le scope lui-même est défini dans
les permissions de la Gmail API (référence d’exploitation retirée).

Chaque personne autorise sa propre boîte. Le Client Secret identifie
l'application, pas le mot de passe Gmail d'un utilisateur. n8n conserve
les credentials dans sa base chiffrée avec la clé d'instance existante.
Les sauvegardes qui contiennent la base et cette clé restent sensibles.

### D. Tester un workflow de réception

Le fichier **workflow-gmail-reception-test.json** a été préparé comme modèle
inactif, sans identifiant ni secret et sans installation dans l'instance.
Il contient :

```text
Gmail Trigger → Réception vérifiée
```

Le déclencheur est configuré pour une vérification chaque minute, une
réponse simplifiée, au plus dix emails par interrogation et un filtre
sur les messages non lus contenant **N8N-TEST-GMAIL** dans l'objet. Le
deuxième nœud est un point de contrôle sans action sur la boîte.

Importer ce fichier dans n8n, sélectionner la connexion Gmail autorisée,
lancer le test et faire parvenir un message de test correspondant au
filtre. Examiner la sortie du nœud. Ne publier le workflow qu'après ce
contrôle et la définition du traitement souhaité. **Aucun message de
test n'a été envoyé par l'assistant.**

Ce modèle n'envoie ni ne supprime de messages, ne les marque pas comme
lus et n'appelle pas OpenAI. Pour un véritable traitement créant des
tâches ou des lignes, prévoir une gestion des doublons avec l'identifiant
Gmail du message ou un marquage effectué après succès. Le seul filtre
« non lu » ne marque pas les messages comme traités.

### E. Éviter une déconnexion après sept jours

Avec une application externe en **Testing**, Google fait expirer les
autorisations et les refresh tokens après sept jours pour ces permissions.
Le workflow peut alors cesser de consulter Gmail et demander une nouvelle
connexion. Passer en production demande de respecter les conditions
Google, et certains scopes peuvent nécessiter une vérification. Le
changement de domaine ne lève pas ces exigences.
Statuts d'audience et durée des autorisations (référence d’exploitation retirée).

## 10. Maintien en service et dépannage

| Symptôme | Contrôle à effectuer |
| --- | --- |
| Impossible d'ouvrir le site | Utiliser l'URL complète en HTTPS ; vérifier DNS, Pi, Caddy et redirection TCP 443. |
| Domaine résolu vers une autre IP | Mettre à jour l'enregistrement A DuckDNS. |
| Connexion différente entre navigateurs | Vérifier les cookies du domaine et leur propre connexion ; les sessions de l'IP ne migrent pas. |
| `redirect_uri_mismatch` | Copier le retour OAuth affiché dans n8n et comparer exactement au client Google. |
| Accès Google refusé en test | Vérifier le compte choisi et la liste des testeurs, ainsi que les éventuelles restrictions du compte. |
| `invalid_client` | Vérifier Client ID, Client Secret et client sélectionné. |
| Gmail fonctionne puis se déconnecte une semaine après | Vérifier le statut Testing et renouveler le consentement, ou préparer le passage en production. |
| Aucun email reçu dans le test | Vérifier que le mail est non lu, que l'objet correspond au filtre et que la connexion Gmail est autorisée. |

La réservation DHCP du Pi à `paramètre privé à consulter sur le Pi` dans la Freebox reste à vérifier :
Caddy se lie à cette adresse LAN. Si l'IP publique change, mettre à jour
DuckDNS ; les URL n8n du domaine peuvent rester identiques. L'ancien site
Caddy de l'IP devra être adapté ou supprimé à ce moment-là.

Aucun nouveau client de mise à jour DuckDNS n'a été installé. Aucun
service portant un nom DuckDNS n'a été trouvé dans les emplacements
systemd/cron inspectés ; cela ne prouve pas qu'aucune autre méthode de mise
à jour existe. Avant d'automatiser cette mise à jour, vérifier la méthode
déjà utilisée, puis conserver le jeton DuckDNS dans un fichier privé si
nécessaire. Ne pas l'écrire directement dans une commande ou un rapport.

## 11. Fichiers livrés et limites

- `RAPPORT-06-domaine-duckdns-et-gmail.md` : ce rapport.
- `README-n8n.md` : guide courant avec la nouvelle adresse et le retour OAuth.
- `Caddyfile` et `compose.yaml` : copies de la configuration actuelle.
- `configurer-domaine-n8n.py` : programme de migration contrôlée ; il refuse
  de rejouer une migration sur un Compose qui n'est plus à l'état initial attendu.
- `verifier-domaine-n8n.py` : vérification HTTPS authentifiée sans sauvegarde d'accès.
- `workflow-gmail-reception-test.json` : modèle inactif à importer après connexion Google.
- Sources des scripts d'entretien et de vérification mises à jour.

Ces fichiers sont également conservés dans `paramètre privé à consulter sur le Pi`,
un dossier privé du compte Yanis. Les sauvegardes sont dans le dossier
privé `paramètre privé à consulter sur le Pi`.

La migration n'a pas publié de workflow, modifié les mails ni connecté
Google sans consentement. L'accès au domaine et la préparation des URL
sont terminés. La création ou modification du client Google, le
consentement Gmail et le premier test de réception restent à effectuer.
