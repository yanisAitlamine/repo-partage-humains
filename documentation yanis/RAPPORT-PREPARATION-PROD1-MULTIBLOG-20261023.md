<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Promotion multiblog — préparation du 23 octobre 2026

## Demande et résultat

La demande est de déployer sur le serveur applicatif de production la solution multiblog qualifiée en laboratoire, puis d’annoncer la réussite par mail au collaborateur. La préparation porte sur le portail, les workflows de sources et de génération, le stockage des archives, le relais privé, le rendu et la livraison WordPress.

Le code permanent est intégré sur la branche principale du dépôt applicatif. Le paquet est construit depuis le commit exact, avec cinq composants, 40 fichiers et 770366 octets de sources. Les originaux et données de recette restent des données d’exploitation distinctes du paquet.

Le raccord conserve tous les groupes de sources d’un projet, vérifie leur admission native, archive les originaux et scanne les textes avant leur exposition au modèle. Les photographies sélectionnées conservent leurs octets ; le contexte de conception demeure borné. L’import final conserve les contenus complets indépendamment de cette limite de contexte. Les ressources manquantes ou corrompues gardent leurs diagnostics.

Les contrôles réalisés passent : 774 tests Python intégrés, 31 tests de paquet/bascule, 45 tests du collecteur, 73 tests Node des workflows, 95 tests Node d’interface et CMS synthétique, compilation du portail et validation native des six SDK n8n. Ces contrôles ne constituent pas une nouvelle recette connectée de production.

Les contre-revues ont corrigé le rejet des métadonnées de sélection photo, les tailles de rasters incohérentes entre maquette et installation, le retour arrière après activation partielle et l’oubli des tentatives WordPress incertaines dans la garde de bascule.

Le contrôleur installé du serveur applicatif a également préparé la révision, exécuté ses vérifications isolées et scellé les 46 fichiers du portail. Le paquet des composants a été transféré et revérifié. La préimage de l’installation existante a été relue avec ses empreintes et métadonnées, sans lui attribuer une provenance Git inventée.

La bascule complète reste conditionnée à l’accès normal aux cinq workflows concernés, au remapping du credential d’archivage et à la confirmation de la cible WordPress. Le registre de production désigne encore l’ancien hébergement externe ; la recette réussie utilisait un conteneur de laboratoire. Les droits de provisionnement externe et l’identité SSH du compte effectif ne sont pas attestés. Une clarification humaine a été demandée entre reprise du mode du laboratoire sur le serveur applicatif et conservation de l’hébergement externe.

## Orchestration et délégation

L’orchestrateur a lancé trois agents avec la configuration héritée du parent. Un agent a préparé collecte, archives et contexte n8n ; un autre le fournisseur WordPress et sa recette propriétaire ; le troisième le paquet, les sauvegardes cohérentes et le retour arrière. Ils ont rendu leurs périmètres après qualification, puis mené des contre-revues croisées.

Les sources correspondantes sont référencées par version :

- https://github.com/yanisAitlamine/atelier-portal/blob/2723db63757cb08c5b971adb6c24f799cafae793/integrations/site-archive/component.json
- https://github.com/yanisAitlamine/atelier-portal/blob/2723db63757cb08c5b971adb6c24f799cafae793/integrations/wordpress/component.json
- https://github.com/yanisAitlamine/atelier-portal/blob/2723db63757cb08c5b971adb6c24f799cafae793/Ansible/prod1-multiblog-20261023/components.json
- https://github.com/yanisAitlamine/atelier-portal/blob/2723db63757cb08c5b971adb6c24f799cafae793/tools/private-render/component.json

L’orchestrateur a assuré l’audit de l’installation réelle, le raccord applicatif, le relais concurrent, les délais, la fusion des historiques, les corrections de contrat, les vérifications intégrées et la préparation des artefacts. Les preuves détaillées et échanges d’agents sont archivés dans l’espace d’exploitation autorisé.

## Coopération et adaptation au contexte

Les consignes courantes du partage et les annonces des autres sessions ont été consultées. Le travail utilise des copies isolées et une fusion normale avec la branche distante ; les modifications concurrentes des checkouts existants ont été conservées. Les conflits de fusion ont conservé les contrôles récents de transport et les comptes rendus des deux historiques.

La préparation tient compte de trois faits observés : la version installée possède des octets vérifiables sans sceau Git de préparation correspondant ; n8n héberge des exécutions étrangères à la mission ; le rendu isolé utilisait une copie plus ancienne de son validateur. Le paquet distingue donc une préimage d’installation observée d’une nouvelle release Git, conserve une publication n8n limitée aux workflows concernés et relie le rendu aux validateurs de la même cohorte.

Les états et preuves de production sont conservés séparément des essais hors réseau. Le retour arrière porte sur le code et la configuration tout en conservant les nouvelles données. La recette connectée et le mail de fin restent attachés à une bascule réellement vérifiée.
