# Migration de production vers Debian amd64 — 19 octobre 2026

## 1. Demande et résultat

La demande autorisait une nouvelle VM issue d'un template existant, une sauvegarde récente avant restauration des données, le redéploiement des services clients et une procédure retraçant l'ordre réel des opérations.

La production applicative fonctionne sur la nouvelle VM. Le lot de sauvegarde chiffré comprend le socle, les compléments applicatifs et une base de service auparavant omise du parcours de reprise. Des copies hors de la machine source ont été contrôlées. Les configurations après bascule ont aussi été chiffrées et vérifiées.

Les images et outils ont été adaptés à amd64 ; les binaires ARM n'ont pas été réinstallés. Les versions de workflows restaurées correspondent à la source arrêtée. Les exécutions interrompues ont été conservées comme interrompues, sans rejeu ; les attentes et états incertains n'ont pas été réarmés. L'ancienne copie applicative ne redémarre plus en parallèle.

Disponibilité HTTPS privée, refus des API anonymes, connexion propriétaire, collecte et lecture MCP ont été vérifiés. Les moteurs répondent depuis leurs appelants autorisés. Chromium a réellement produit deux captures d'une page fictive, sans projet client, modèle de revue ou publication. La dernière validation après redémarrage donne un système sans unité en échec. Un snapshot final a été conservé après retrait des extractions claires temporaires.

La reprise du point d'entrée réseau reste une opération distincte : cette migration ne constitue pas une preuve d'autonomie complète après disparition de toute l'infrastructure source. Aucun nouveau parcours métier avec envoi réel ou livraison externe n'a été déclenché pour valider la migration.

## 2. Orchestration et délégation

Codex a effectué directement la préparation, la sauvegarde, les adaptations Ansible, la restauration, les contrôles et la documentation. Aucun sous-agent ni session d'agent applicatif n'a été lancé pour cette mission. Aucun coût ou gain de délégation n'est déduit.

Le contrôleur personnel autorisé a exécuté les recettes, avec des limites explicites de cible. Les contrôles de volume vide, de propriété, de cohérence et d'identité ont été conservés. Le bootstrap Python précède désormais les modules qui en dépendent ; le template possédait déjà Python, donc la branche d'installation des paquets manquants a été relue sans prétendre avoir été éprouvée sur un autre système minimal.

Les contrôles synthétiques existants du collecteur ont recensé 35 tests : 34 réussis, un ignoré. Les contrôles de restauration et de fonctionnement ont été réalisés dans l'environnement cible. Les sondes techniques et la capture fictive ne sont pas présentées comme une validation de tous les parcours commerciaux.

## 3. Coopération et adaptation au contexte

Les consignes, états Git, protocole de coopération, annonces et passations pertinentes ont été consultés. La migration a été annoncée et réservée. Les sources modifiées préexistantes et les autres VM ont été préservées.

Les difficultés observées ont modifié le parcours : scalaire YAML invalide, filtrage de transit ajouté par Docker, résolution DNS différente entre hôte et conteneurs, cache exclu mais exigé par la sandbox, manque de marge de reconnexion VPN et attente réseau héritée d'un gestionnaire inutilisé. Les reprises ont été ciblées, puis les redémarrages et accès ont été revérifiés.

Une candidate préparée après la capture a été conservée sans activation implicite. Les guides distants ajoutés pendant l'historique ont été intégrés avant publication de la procédure, sans écraser leurs changements. La documentation privée contient les commandes, leur ordre réel, les garde-fous, les sauvegardes, les limites et les précautions pour refaire l'exercice sur un lab isolé. Ce rapport public omet les accès, inventaires privés, identifiants internes, secrets et données clients.
