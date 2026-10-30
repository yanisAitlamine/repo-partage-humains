<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Délégation du déploiement du portail — 15 octobre 2026

## Demande et résultat

Yanis a demandé de consulter la demande d'accès de son collaborateur et de lui
permettre de déployer les nouvelles versions du portail. Le service concerné
fonctionne sous systemd ; l'accès à Docker n'était pas nécessaire.

Une commande de déploiement limitée est maintenant installée sur le Pi pour le
compte personnel du collaborateur. Elle permet de consulter l'état, préparer une
révision Git exacte, l'activer et revenir à une version connue. La préparation
exécute les dépendances, les tests Python et la compilation sous une identité
isolée, puis scelle les fichiers du service. Une activation exige toujours
l'approbation humaine de la révision exacte ; le paramètre correspondant est
une attestation du compte, pas une preuve technique de présence humaine.

Le mécanisme prévoit un verrou, le refus des traitements actifs, une sauvegarde
cohérente avant bascule, le contrôle de santé et le retour au code précédent en
cas d'échec. Le compte n'obtient pas de commande administrateur libre, de droit
Docker ou de lecture directe de la base et des secrets. Les workflows et les
autres services conservent leurs permissions.

Vérifications réalisées : 29 tests du contrôleur réussis sur Linux, recette
d'installation appliquée sans erreur, règle sudo validée et essais réels sous
l'identité du collaborateur. Une candidate a terminé ses tests et sa compilation
et a été préparée sans activation. Une commande sur la version déjà active a
réussi sans changement. Le processus, les configurations et l'unité du portail
sont restés identiques ; la santé HTTPS répond 200. Les arguments interdits et
les tentatives d'accès hors périmètre testées sont refusés.

Aucune nouvelle version cliente n'a été activée. La sauvegarde et le retour
arrière lors d'une vraie bascule restent à exercer dans une mission autorisée ;
leurs scénarios ont été testés avec des données fictives. La compatibilité des
futures migrations de données et l'entretien de l'historique des sauvegardes et
releases restent des responsabilités d'exploitation.

## Orchestration et délégation

Codex a lancé trois agents internes : un pour le contrôleur et ses tests, un
pour la nouvelle recette et le guide, et un pour une revue indépendante en
lecture seule. Les fichiers attribués étaient distincts. Les agents ont terminé
et leurs résultats ont été relus puis intégrés. Ils ont hérité de la
configuration de la session ; aucun relevé indépendant du modèle exact n'a été
effectué. Aucun coût ni économie n'a été estimé.

Codex a effectué directement la lecture du besoin, l'intégration au dépôt
canonique, les tests Linux, l'installation et les essais avec le compte délégué.
La première préparation a révélé une incompatibilité d'isolation systemd. Des
essais avec une commande fictive ont isolé la cause ; le correctif conserve un
espace d'exécution protégé et la préparation complète a ensuite réussi. Les
échanges lisibles des agents ont été archivés en copies d'audit privées. Aucune
session OpenCode n'a été lancée.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche de reprise, les passations pertinentes, le
protocole partagé et les annonces récentes ont été consultés. Une intention et
des extensions de périmètre ont précédé les écritures. Les contributions du
collaborateur ont été récupérées sans écraser son travail ; les modifications
locales étrangères à la mission ont été préservées.

L'examen du service réel a conduit à déléguer une opération limitée plutôt
qu'un accès Docker. Les anciennes interdictions ont été conservées avec une
exception ciblée pour le portail. Les ACL des consignes partagées ont été
préservées et vérifiées. Les commandes et leurs limites sont documentées dans
le dépôt opérationnel privé ; les détails d'accès restent hors de ce rapport.

Le suivi partagé signale la livraison, distingue la candidate préparée du
service actif et libère les réservations propres à cette mission. Aucun mail
n'a été envoyé, aucun autre déploiement ni pipeline n'a été exécuté.
