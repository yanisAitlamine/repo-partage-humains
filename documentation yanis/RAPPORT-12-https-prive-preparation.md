<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 12 — Préparation de la fermeture HTTPS publique

**11 octobre 2026. Intervention en attente du jeton DuckDNS.** Yanis autorise
le passage à DNS-01 et la fermeture du port HTTPS public, en conservant
l'accès LAN/VPN. OpenVPN utilise UDP1194, indépendant de TCP443.

## Observations actuelles

Caddy 2.11.7 écoute uniquement sur `paramètre privé à consulter sur le Pi:443` et `paramètre privé à consulter sur le Pi:443`.
Il sert encore le domaine et l'IP publique, avec filtre HTTP 403 hors LAN/VPN,
et dépend de TLS-ALPN pour ses certificats. Aucun module DuckDNS installé.
IPv6 globale présente sur wlan0, sans listener Caddy IPv6. La liste UPnP
Freebox ne montre que UDP1194 vers le Pi ; la redirection 443 signalée
précédemment doit être contrôlée dans la configuration statique Freebox.

Les services Caddy, VPN, n8n et bridge sont actifs. OpenVPN garde le un essai ou état interne,
actif depuis le 11 octobre à 02:33:33 CEST. Aucun service redémarré, aucune
modification de configuration active, aucun port fermé pour cette préparation.

## Sources préparées

`OpenVPNDeploy/caddy-dns/` contient le programme Caddy avec modules standard
et DuckDNS, dépendances épinglées, script de compilation, candidat Caddyfile
DNS-01 sans site IP public, filtre nftables IPv4/IPv6 dédié et unités systemd.
Le drop-in retire `--environ` du service Caddy avant d'injecter un token : ce
paramètre existant pourrait sinon journaliser le secret.

Go 1.26.9 ARM64 téléchargé depuis go.dev et vérifié SHA256, dans un dossier
de construction séparé. Caddy conserve la version2.11.7 ; DuckDNS est épinglé
au paramètre privé à consulter sur le Pi.

Compilation réussie : version2.11.7 et module `dns.providers.duckdns`
confirmés. SHA256 du candidat :
`paramètre privé à consulter sur le Pi`.
Le candidat Caddyfile a passé `caddy validate` avec un token factice, sans
émission réelle ni changement actif. Le test staging est préparé dans
`test-dns01.py` mais attend le token réel.

Le filtre a passé `nft --check` sur le Pi, **sans application**. Il remplace
uniquement sa propre table ; il préserve Docker et UDP1194. Aucun test des
rôles Ansible existants lancé. AGENTS global intact et empreinte vérifiée.

## Délégation

Cette étape était une préparation directe et ciblée : compilation déterministe, configuration et contrôle statique ; aucun agent payé lancé. La mission de réalisation ultérieure est détaillée au rapport13, avec sessions Luna, tentatives bloquées, implémentation, revue et interventions Codex.

## Blocage et suite

Aucun token DuckDNS connu trouvé par recherche de noms de fichiers. Le
Ne pas lire sa valeur dans un prompt ou une sortie d'outil.

Avant fermeture : tester une émission DNS-01 réelle avec ACME staging,
sauvegarder les fichiers actifs, installer le candidat et l'injection privée,
vérifier le certificat de production puis appliquer le filtre et vérifier
LAN/VPN/public depuis l'extérieur. Supprimer la redirection statique443 si
accès Freebox disponible, conserver UDP1194. Ne pas redémarrer OpenVPN.

Après réalisation : inclure le token et les nouvelles unités dans la collecte
privée/restauration, produire une nouvelle sauvegarde chiffrée hors Pi,
actualiser l'architecture/PDF, le plan et REPRISE, puis publier les sources
et preuves Git. La sauvegarde actuelle reste celle du rapport11 ; aucune
migration effective ni fermeture publique ne doit être annoncée à ce stade.
