<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 4 — Arrêt avec sauvegarde et remise en service du Raspberry Pi

**Date :** 9 octobre 2026, Europe/Paris. **Statut : installé sur le Pi et testé sans extinction réelle.**

Yanis a précisé que les scripts doivent s'exécuter directement sur le Raspberry Pi. Le Pi est un **Raspberry Pi 4 Model B Rev 1.5**. Il est rallumé en remettant son alimentation ; le script de démarrage intervient ensuite pour remettre n8n en service et vérifier son fonctionnement.

## 1. Utilisation

Dans un terminal sur le Pi, arrêter proprement et sauvegarder avant extinction :

```sh
sudo pi-eteindre
```

Après avoir rebranché le Pi, relancer ou vérifier n8n :

```sh
sudo n8n-demarrer
```

Le démarrage de la stack est également configuré automatiquement au démarrage de Linux. Le script permet de remettre en service des conteneurs arrêtés manuellement et confirme que le HTTPS fonctionne.

Sauvegarder sans éteindre :

```sh
sudo n8n-sauvegarder
```

Tester la séquence d'arrêt, la sauvegarde et le redémarrage des services sans éteindre le Pi :

```sh
sudo pi-eteindre --test
```

Afficher le plan sans agir sur les services ni créer de sauvegarde :

```sh
sudo pi-eteindre --dry-run
sudo n8n-demarrer --dry-run
```

Les commandes normales ne demandent pas une confirmation supplémentaire : `pi-eteindre` demande réellement l'extinction après sauvegarde. La session SSH se ferme alors. Enregistrer les modifications dans l'éditeur n8n avant l'arrêt et laisser la procédure finir avant de débrancher le Pi.

## 2. Fichiers et droits

| Fichier sur le Pi | Source dans le projet | Fonction |
|---|---|---|
| `paramètre privé à consulter sur le Pi` | `eteindre-pi.sh` | Lance l'action d'arrêt |
| `paramètre privé à consulter sur le Pi` | `demarrer-n8n.sh` | Lance la remise en service |
| `paramètre privé à consulter sur le Pi` | `sauvegarder-n8n-pi.sh` | Sauvegarde puis remet l'état précédent en service |
| `paramètre privé à consulter sur le Pi` | `pi-services.sh` | Logique commune, verrou, vérifications et sauvegardes |
| `paramètre privé à consulter sur le Pi` | `n8n-stack.service` | Démarrage automatique et arrêt ordonné des conteneurs |
| `paramètre privé à consulter sur le Pi` | Créé lors de l'installation | Place le démarrage Caddy après la stack n8n |

Les commandes sont détenues par root, de droits 755. Le fichier de logique commune est détenu par root, de droits 750. Les scripts exigent l'exécution avec sudo et ne contiennent aucun mot de passe ni clé privée.

La configuration n8n, son `.env` et son volume persistant sont ceux de l'installation existante. Les comptes et les clés de chiffrement ne sont pas remplacés lors d'un démarrage. Les images locales figées par empreinte sont utilisées ; le script ne met pas automatiquement les logiciels à jour.

## 3. Déroulement d'un arrêt normal

1. Vérifier les arguments, les fichiers de configuration et l'absence d'une opération concurrente.
2. Vérifier Docker, le volume SQLite attendu, l'état Caddy et l'espace disque disponible.
3. Fermer les accès HTTPS en arrêtant Caddy.
4. Envoyer l'arrêt normal à n8n et attendre sa fin. Les task runners restent disponibles pendant cette attente.
5. Vérifier que n8n n'a pas été tué pour manque de mémoire ou arrêté avec un code inattendu, puis arrêter les runners.
6. Vérifier l'intégrité SQLite, sauvegarder les données et les configurations, vérifier les archives et calculer leurs empreintes.
7. Synchroniser les écritures sur la carte SD, puis demander l'extinction à Linux.

Un verrou `flock` dans `paramètre privé à consulter sur le Pi` empêche les trois scripts de travailler simultanément. Un gestionnaire de sortie couvre les erreurs et les interruptions. Si une erreur survient après le début de l'arrêt, le script annule l'extinction et tente de rétablir l'état antérieur des services. Il indique si cette remise en service est incomplète.

Le délai n8n est maintenant configuré avec `paramètre privé à consulter sur le Pi=300`, variable confirmée dans la configuration de la version installée. Docker dispose de 330 secondes avant sa limite d'arrêt ; les runners disposent de 30 secondes. Caddy dispose de 15 secondes pour fermer ses connexions. Une exécution dépassant le délai de cinq minutes peut être interrompue ; la sauvegarde conserve les données enregistrées, sans garantir la fin d'un workflow arbitrairement long. [Délai d'arrêt Docker Compose](https://docs.docker.com/reference/compose-file/services/#stop_grace_period).

## 4. Contenu d'une sauvegarde

Chaque opération crée un dossier privé unique :

```text
paramètre privé à consulter sur le Pi
    data.tar.gz
    config.tar.gz
    caddy-state.tar.gz
    SHA256SUMS
    COMPLETE
```

| Archive | Contenu |
|---|---|
| `data.tar.gz` | Tout le dossier persistant `.n8n` : SQLite, comptes, workflows, identifiants chiffrés et fichiers enregistrés dans ce volume |
| `config.tar.gz` | Compose, `.env` et clé de chiffrement n8n, Caddyfile, unités systemd, scripts de contrôle et binaire Caddy |
| `caddy-state.tar.gz` | État privé Caddy : comptes ACME, certificats et leurs clés privées |

Les données sont copiées avec n8n et Caddy arrêtés. Le contrôle SQLite utilise `PRAGMA quick_check` sur la base en lecture seule. Le conteneur de copie utilise le volume en lecture seule, sans réseau, et ne modifie pas la base.

Les fichiers ont d'abord le suffixe `.partial`. Après contrôle `gzip -t`, ils prennent leur nom définitif. `COMPLETE` est créé uniquement après la réussite de toutes les archives et de la génération des empreintes. Un dossier incomplet doit être examiné avant toute restauration.

Les dossiers ont des droits privés et les archives sont de droits 600, détenues par root. Elles contiennent des secrets : conserver une copie chiffrée hors de la carte SD. Cette sauvegarde couvre le projet n8n et Caddy ; elle n'est pas une image complète de tous les fichiers du système. Les anciennes sauvegardes sont conservées, sans suppression automatique.

## 5. Déroulement du démarrage

Le script démarre Docker, active la stack n8n existante, puis attend que son contrôle de santé soit positif. Il vérifie également la réponse `/healthz/readiness`. Il démarre Caddy et contrôle le HTTPS avec l'identité du certificat de l'IP publique. Il affiche l'adresse d'accès uniquement après réussite : **paramètre privé à consulter sur le Pi

L'unité `n8n-stack.service` est activée au démarrage. C'est utile après un arrêt volontaire : avec la politique Docker `unless-stopped`, les conteneurs arrêtés manuellement peuvent rester arrêtés après une remise sous tension. L'unité exécute explicitement leur remise en service et attend leur état de santé. [Politiques de redémarrage Compose](https://docs.docker.com/reference/compose-file/services/#restart).

Lors d'un arrêt système, l'ordre des unités ferme Caddy avant n8n, puis n8n avant Docker. Les deux commandes `ExecStop` de la stack arrêtent n8n avant les runners, pour garder le service de code disponible pendant la fin des exécutions.

La récupération de l'adresse LAN par DHCP et la disponibilité du réseau restent nécessaires. La réservation de `paramètre privé à consulter sur le Pi` dans la Freebox doit être confirmée. Si l'adresse IP publique ou LAN change, les paramètres des scripts doivent être adaptés avec ceux de Caddy et n8n.

## 6. Commandes d'installation exécutées et utilité

Les sources ont été transférées par `scp` depuis Windows, avec la clé originale et le contrôle strict de l'identité du Pi. Sur le Pi, les fins de ligne des sources ont été normalisées avec `sed -i 's/\r$//'`.

```sh
bash -n paramètre privé à consulter sur le Pi
bash -n paramètre privé à consulter sur le Pi
bash -n paramètre privé à consulter sur le Pi
bash -n paramètre privé à consulter sur le Pi
sudo systemd-analyze verify paramètre privé à consulter sur le Pi
```

Ces commandes ont vérifié la syntaxe shell et la définition du service. `install -d` a créé les dossiers système ; `install -m` a posé la logique, les trois commandes et l'unité avec leurs droits respectifs. Un fichier additionnel Caddy contient :

```ini
[Unit]
Wants=n8n-stack.service
After=n8n-stack.service
```

Le Caddyfile a été formaté, validé et rechargé après l'ajout du délai de fermeture de connexions. Le Compose précédent a été conservé dans `compose.before-power-scripts.yaml`, puis le nouveau Compose a été posé et validé.

```sh
sudo systemctl daemon-reload
sudo systemctl reload caddy
cd paramètre privé à consulter sur le Pi
sudo docker compose config --quiet
sudo docker compose up -d --wait --wait-timeout 180 --pull never
sudo systemctl enable --now n8n-stack
```

`daemon-reload` charge les unités ; `reload` recharge Caddy ; `up` applique les délais d'arrêt et attend le service ; `enable --now` démarre l'unité n8n et l'active pour les prochains démarrages.

Les commandes internes importantes des scripts sont :

| Commande | Utilité |
|---|---|
| `flock -n` | Refuser une opération concurrente |
| `docker compose config --quiet` | Vérifier la configuration sans afficher les secrets |
| `docker inspect`, `du`, `stat`, `df` | Identifier le volume et vérifier les états et l'espace disponible |
| `systemctl stop caddy` | Fermer les accès avant l'arrêt de l'application |
| `docker compose stop --timeout 330 n8n` | Laisser n8n terminer son arrêt normal |
| `docker compose stop --timeout 30 task-runners` | Arrêter le service de code ensuite |
| Python `sqlite3`, `PRAGMA quick_check` | Vérifier la cohérence de la base arrêtée |
| `mktemp -d` | Créer un dossier privé unique sans écraser une ancienne sauvegarde |
| `docker run ... tar`, `tar -czf` | Sauvegarder le volume, les configurations et l'état Caddy |
| `gzip -t`, `sha256sum` | Vérifier la compression et produire les empreintes d'intégrité |
| `sync` | Envoyer les écritures en attente vers le stockage |
| `systemctl poweroff` | Demander l'arrêt normal de Linux après réussite |
| `docker compose up ... --wait` | Remettre les conteneurs existants en service et attendre leur santé |
| `curl` local et HTTPS | Vérifier n8n et le certificat sans désactiver TLS |

## 7. Résultats des vérifications

`sudo pi-eteindre --dry-run` a affiché le plan sans arrêter les services. `sudo pi-eteindre --test` a ensuite effectué réellement l'arrêt de Caddy, n8n et des runners, le contrôle SQLite, la sauvegarde et le démarrage via la même fonction que `n8n-demarrer`.

Résultats :

- Base SQLite : contrôle réussi.
- Sauvegarde créée et archives vérifiées : `paramètre privé à consulter sur le Pi`.
- n8n et runners : remis en service ; n8n `healthy`.
- HTTPS : vérification réussie par le script, puis HTTP 200 et TLS vérifié depuis Windows.
- Docker, Caddy et `n8n-stack` : activés au démarrage ; les unités applicatives sont actives.
- Délai Docker n8n : 330 secondes confirmé dans le conteneur.
- Opération concurrente simulée avec `flock` : la seconde commande a été refusée avant toute action sur les services.
- Propriété et permissions des fichiers installés : vérifiées.

L'extinction électrique réelle, un démarrage complet après rebranchement, une restauration et le comportement d'un workflow long en cours n'ont pas été testés. Le test a volontairement remis les services en marche et laissé le Pi allumé pour continuer à utiliser n8n.

## Complément après l'activation de l'assistant

contenant les clés OpenAI et Daytona. La base inclut aussi les paramètres et
conversations de l'assistant. Les commandes d'arrêt et de démarrage sont
inchangées. Les environnements Daytona sont hébergés à distance et suivent
leur propre arrêt automatique ; leur disque n'est pas exporté dans une
sauvegarde locale du Pi. Voir le
[rapport de mise à jour et d'activation](RAPPORT-05-mise-a-jour-et-assistant.md).
