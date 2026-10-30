<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 09 — OpenVPN et accès privé à n8n

**11 octobre 2026 — Yanis et Ilyes.** Ce rapport couvre la mise en place demandée après le rapport 08. L’architecture complète est dans `ARCHITECTURE.md` et son PDF ; les sources VPN publiques sont dans `OpenVPNDeploy/`, copiées depuis le Pi.

## 1. Objectif et résultat

Tu voulais passer directement à un accès VPN utilisable, avec délégation éventuelle à PIAgentControl, puis recevoir chacun vos propres accès par email. Le chat **« Tester Ansible pas à pas sur le Pi »** a été lu : il contient le début de ton parcours d’apprentissage, sans déploiement Ansible réalisé. Ta nouvelle demande autorisait l’installation directe d’OpenVPN. Aucun rôle Ansible des trois dépôts n’a été testé ni appliqué.

**OpenVPN est maintenant actif sur le Pi.** Yanis et Ilyes disposent de profils personnels, remis séparément par Gmail. Le tunnel donne accès à n8n en HTTPS et à son DNS, sans ouvrir SSH, le réseau local, les autres clients ou le port interne5678. Le domaine habituel reste `paramètre privé à consulter sur le Pi

Le tunnel, le DNS, HTTPS et la révocation ont été testés avec un véritable client isolé sur le Pi. Le refus de l’accès HTTP public a aussi été contrôlé depuis N0C, donc depuis Internet. **La connexion VPN UDP d’un client réellement extérieur reste à confirmer lors de votre premier essai**, par exemple en partage 4G/5G. Ce test ne doit pas être confondu avec le test du tunnel effectué sur le serveur.

## 2. Choix d’architecture

Le serveur utilise les paquets Debian 13 déjà présents : OpenVPN 2.6.14, dnsmasq et nftables. `miniupnpc` a été ajouté pour configurer la redirection de la Freebox sans nouveau jeton d’administration. La machine reste dédiée à sa production n8n ; ses deux conteneurs sont restés en fonctionnement pendant la mise en place.

Le point d’entrée est `paramètre privé à consulter sur le Pi:1194`, en UDP. Ce nom résolvait déjà vers l’IP publique actuelle `paramètre privé à consulter sur le Pi`. La Freebox redirige uniquement ce port UDP vers `paramètre privé à consulter sur le Pi:1194`. Un timer rétablit cette redirection toutes les cinq minutes et après démarrage si UPnP reste disponible ; la redirection TCP 443 existante est conservée.

Dans le tunnel, le serveur est `paramètre privé à consulter sur le Pi`, Yanis reçoit `paramètre privé à consulter sur le Pi` et Ilyes `paramètre privé à consulter sur le Pi`. Ce sous-réseau ne chevauchait ni le LAN ni les réseaux Docker constatés. Aucun routage général vers le LAN ou tunnel Internet complet n’a été ajouté.


Le DNS du VPN remplace **exactement** `paramètre privé à consulter sur le Pi` par `paramètre privé à consulter sur le Pi`, tout en laissant le nom `paramètre privé à consulter sur le Pi` public. Ce détail évite que le client cherche à rejoindre le VPN via une adresse privée qu’il ne peut atteindre avant connexion. Le comportement d’enregistrement local est documenté par dnsmasq (référence d’exploitation retirée).


## 3. Découpage et responsabilités

| Intervenant | Travail réellement effectué |
| --- | --- |
| Planificateur OpenCode, depuis PIAgentControl | Organisation de la création des fichiers publics, revue, corrections et relecture. Aucun shell ni accès aux secrets autorisé pendant cette mission. |
| Implémenteurs OpenCode | Trois appels : création des dix fichiers initiaux, correction des constats, clarification d’un fichier ajouté par l’opérateur. |
| Revue OpenCode | Deux appels : revue initiale, puis relecture des corrections. |
| Sous-agent Codex de sécurité | Relecture indépendante de la conception, de la PKI et des fichiers serveur ; identification de corrections avant validation. Aucune mutation. |
| Sous-agent Codex de documentation | Actualisation du générateur PDF, schémas VPN et contrôle visuel du document d’architecture. |

La session OpenCode a duré environ quatre minutes et vingt-quatre secondes. Ce temps couvre la préparation publique, pas le déploiement complet. La délégation a permis de préparer les fichiers en parallèle de la partie réseau ; elle ne garantit pas une économie de tokens. Les opérations privilégiées et la remise des secrets sont restées sous la responsabilité de Codex.

## 4. Étapes réalisées et blocages corrigés

**Inventaire et réseau.** Vérification de sudo, de TUN, de l’espace disque, des services, des ports et des réseaux existants. OpenVPN et les outils cryptographiques étaient déjà installés, mais aucun serveur VPN ne tournait. UPnP était disponible sur la Freebox : ajout et lecture de confirmation de la redirection UDP 1194. Aucune DMZ ni redirection SSH/5678 ajoutée.



**Préflight et permissions.** Le contrôle initial de signature ECDSA utilisait un mauvais nombre d’arguments et bloquait le démarrage. Il a été corrigé avec la validation de signature de CRL, celle du certificat serveur et les usages/dates de la CA. Les dossiers et fichiers ont reçu les permissions nécessaires au compte technique `openvpn-n8n` après abandon des privilèges. La comparaison des modes de l’installateur a également été corrigée pour éviter des sauvegardes inutiles à chaque relance.

**Serveur, pare-feu et DNS.** OpenVPN démarre après une table nftables dédiée. Celle-ci filtre seulement l’interface du tunnel et refuse tout transfert ; les règles Docker n’ont pas été vidées. Les adresses clients sont fixes et seuls les CN déclarés sont admis. Le DNS a été limité à son écoute IPv4 privée, après détection d’une écoute IPv6 implicite de dnsmasq. La syntaxe du paramètre DNS poussé a été corrigée. Ces corrections ont été appliquées avant les contrôles finaux.

**HTTPS et démarrage.** Sauvegarde de Caddy, validation de la nouvelle configuration, puis rechargement avec retour arrière prévu en cas d’échec. Ajout du bind VPN et du filtre sur les deux sites pour éviter un contournement par l’IP publique. DNS et Caddy attendent OpenVPN au démarrage. Les timers de redirection et de contrôle d’expiration sont activés.


## 5. Vérifications et commandes majeures

| Contrôle réalisé | Résultat |
| --- | --- |
| Connexion OpenVPN avec clé cliente chiffrée | Tunnel établi, adresse temporaire fixe reçue. |
| DNS n8n A/AAAA et nom du serveur VPN | n8n vers paramètre privé à consulter sur le Pi, aucune réponse AAAA pour ce nom privé, endpoint VPN restant public. |
| HTTPS à travers le tunnel | Réponse 200, certificat public valide vérifié. |
| SSH, port 5678, LAN et autre client | Connexions de test refusées ; politique VPN limitée. |
| Révocation du certificat temporaire | Nouvelle connexion rejetée, motif « certificate revoked » confirmé. |
| HTTP public depuis N0C | Réponse 403 sur domaine et IP, même avec un faux en-tête d’IP interne. |
| Syntaxe, unités et état final | Scripts et unités valides ; VPN/DNS/pare-feu/Caddy/Docker/n8n actifs ; redirection NAT confirmée. |
| Coffre et CRL hors Pi | Déchiffrement vérifié, signature de CRL réalisée depuis Windows, préflight réussi après installation. |

Les commandes ci-dessous expliquent les actions principales ; **ne pas rejouer le bootstrap sur la production**.

```sh
sudo bash paramètre privé à consulter sur le Pi --install-only
# Installe les fichiers publics, sans démarrer et sans générer de clé.

# Détail d’exploitation retiré de la version publique.
# Initialisation neuve uniquement : crée la PKI et les profils privés.

sudo paramètre privé à consulter sur le Pi paramètre privé à consulter sur le Pi
sudo systemctl enable --now n8n-vpn-firewall.service
sudo systemctl enable --now [ADRESSE-MAIL]
sudo systemctl enable --now n8n-vpn-dns.service
# Contrôle puis activation effective du pare-feu, du VPN et du DNS.
# L'option install.sh --start regroupe ce parcours pour une installation future.

upnpc -e n8n-OpenVPN -a paramètre privé à consulter sur le Pi 1194 1194 UDP 0
# Redirection dédiée sur la Freebox ; vérifiée ensuite avec upnpc -l.

sudo python3 paramètre privé à consulter sur le Pi
# Caddy, ordre de démarrage et timer de redirection.

sudo systemctl status openvpn-server@n8n n8n-vpn-dns n8n-vpn-firewall
# Contrôle des services ; journalctl permet le diagnostic.
```

Les signatures et mots de passe ont été manipulés par les outils dans des emplacements privés, sans être affichés ni inclus dans les prompts ou ce rapport. L’envoi Gmail a confirmé un message séparé à `[ADRESSE-MAIL]` et à `[ADRESSE-MAIL]`, chacun avec uniquement son propre profil et sa propre passphrase. L’import par fichier est décrit dans la [documentation OpenVPN Connect](https://openvpn.net/connect-docs/import-profile.html).

## 6. Fichiers et suites

`OpenVPNDeploy/README.md` détaille les fichiers et l’exploitation. Les configurations actives sont sous `paramètre privé à consulter sur le Pi`, les unités sous `paramètre privé à consulter sur le Pi`, les contrôles sous `paramètre privé à consulter sur le Pi`. Les sources publiques sont disponibles sur le Pi et dans ce projet Windows ; **aucun nouveau dépôt GitHub n’a été créé ou poussé pour cette mission**. L’architecture Markdown/PDF et les lectures de reprise des agents ont été actualisées.


La CRL expire le **9 avril 2027** : renouveler avec marge grâce à `manage-crl.py`, en récupérant toujours la CRL courante pour préserver les révocations. Les certificats serveur/clients expirent le **11 octobre 2027** ; leur renouvellement est distinct d’un bootstrap neuf. Le contrôle quotidien signale une échéance proche dans systemd, sans envoyer d’email ni renouveler automatiquement.

Les prochaines vérifications utiles sont votre connexion depuis un réseau extérieur, la réservation DHCP du Pi dans la Freebox, puis un essai de démarrage complet lors d’une maintenance. La réservation et le redémarrage complet n’ont pas été vérifiés ici. Aucun workflow n8n n’était actif au relevé ; les futurs webhooks publics demanderont des règles limitées explicites. Les sauvegardes n8n hors serveur, MFA, filtrage général IPv6 et réduction du sudo des agents restent les priorités du plan de sécurité. Les permissions OpenCode de cette mission limitent ses outils, mais ne constituent pas une isolation système du compte Yanis.
