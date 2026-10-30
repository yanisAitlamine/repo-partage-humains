<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Procédures de redéploiement et de restauration par commandes

## Demande et résultat

Yanis demande d'intégrer le site web, son workflow et le dashboard à la documentation d'implémentation, de continuité et de reprise. Il veut les fichiers à récupérer, les commandes, leur raison et ce qu'elles redéploient, avec moins de texte général.

Un guide pratique d'implémentation est ajouté. Les deux procédures privées sont réécrites avec des étapes exécutables et des tableaux de résultat. Le sommaire privé dirige vers ces trois parcours. L'architecture et le guide Ansible donnent accès à ces commandes et distinguent les installations actuelles des catalogues historiques. Les versions publiques présentent les mêmes choix sans divulguer les accès réels.

Le redéploiement du portail conserve sa base et ne publie aucun workflow. Le dashboard conserve son stockage et sa connexion propriétaire. La reprise distingue l'archive historique du socle et un complément contenant les services récents, leur code exécuté et leurs données. Elle prévoit aussi l'état TLS, les propriétaires, les ACL et la copie indépendante de l'hébergement. La préparation peut récupérer les sources directement depuis le complément sauvegardé, sans installer une nouvelle identité GitHub sur le serveur neuf.

La relecture de l'installation trouve une incompatibilité entre les prérequis des anciens playbooks opérationnels et les helpers réellement présents. Les commandes courantes documentées utilisent les services et helpers actuels ; aucun faux marqueur d'adoption n'est proposé. Les versions exécutées et les sources plus récentes sont distinguées. Le consommateur Telegram volontairement suspendu reste exclu d'une relance générale.

Les commandes de collecte complémentaire et de restauration sont des instructions préparées, pas une automatisation globale déjà éprouvée. Aucun nouveau lot de sauvegarde, déploiement, restauration, reboot, envoi ou traitement de workflow n'est exécuté. La vérification porte sur les sources des commandes, les métadonnées des services, les liens et les différences documentaires. Un exercice complet sur une cible isolée reste à réaliser par l'opérateur.

## Orchestration et délégation

Codex réalise directement le repérage, la lecture des sources, la rédaction et la revue documentaire. Aucun sous-agent, session OpenCode ou outil réservé de délégation n'est lancé. Aucun modèle payant, test Ansible, contrôle de syntaxe des anciens rôles ou accès à la VM personnelle n'est utilisé. Aucun coût ou gain n'est estimé.

Les vérifications ne démarrent pas les applications : elles relèvent leurs états, versions et chemins d'exécution, puis confrontent les arguments aux scripts et recettes. Les exemples de commande restent du texte. Le code applicatif et les bases ne sont pas modifiés.

## Coopération et adaptation au contexte

Les consignes, la fiche courte, le protocole machine, les passations du portail et de l'Observatoire ainsi que les annonces de fin pertinentes sont lus. Après le repérage initial, une intention documentaire réserve les procédures et guides avant leur écriture. Les nouvelles annonces sont relues pendant la mission.

Une contribution parallèle à l'interface du portail publie une source plus récente sans déployer le service. La documentation conserve cette distinction et ne remet pas la copie source à une version ancienne. Une nouvelle mission parallèle de refonte du portail reste hors périmètre. Les modifications préexistantes des consignes et de la fiche de reprise sont conservées hors des commits de cette mission.

Les documents publics sont relus pour exclure chemins d'accès, identifiants internes, valeurs secrètes et données clients. Les commandes et inventaires opérationnels restent privés. La clôture libère seulement les réservations documentaires de cette mission ; elle n'autorise aucune remise en route métier.
