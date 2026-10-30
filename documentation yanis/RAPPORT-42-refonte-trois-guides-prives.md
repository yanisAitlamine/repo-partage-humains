<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Rapport 42 — Guides privés, continuité et reprise

## Demande et résultat

La demande humaine porte sur la compréhension de la documentation : expliquer les mécanismes dans un français courant, conserver les détails utiles et corriger les descriptions devenues anciennes. Après la refonte de l’architecture et des workflows, trois autres guides privés doivent recevoir la même réécriture complète. La demande est ensuite étendue aux deux procédures de continuité et de reprise ajoutées par l’utilisateur dans son clone local. La publication des documents terminés est explicitement demandée.

Le périmètre comprend la documentation des recettes d’administration, de la configuration des agents, des secrets sans leurs valeurs, de l’exploitation quotidienne et de la reconstruction après perte de machine. Il comprend aussi les liens entre ces références et leur synchronisation. Il ne comprend pas la réalisation d’une sauvegarde, d’une restauration ou d’un déploiement.

Les procédures doivent pouvoir répondre à des questions concrètes : quel service fait quoi, quels fichiers lui sont nécessaires, quelles données doivent être conservées ensemble, ce que les scripts existants prennent en charge et ce qui nécessite encore une préparation. Elles distinguent une copie sur la machine, une sauvegarde indépendante chiffrée, un contrôle d’intégrité et une restauration effectivement démontrée.

La revue relève plusieurs descriptions à corriger : anciennes règles de délégation, différence entre fichiers sources et copies installées, étapes de validation humaine, conservation des états d’envoi et couverture des composants ajoutés récemment. Une reprise doit rapprocher les données restaurées des effets déjà produits à l’extérieur ; un état ancien ne donne pas la permission de renvoyer un message ou de reconstruire un résultat.

Les cinq textes sont réorganisés intégralement, avec explications, exemples, tableaux et parcours de décision. Les trois guides ne se limitent plus à un ajout en tête de leur ancien contenu. Le catalogue des recettes conserve la couverture de ses 93 fichiers antérieurs et explicite les dépendances récentes. L’architecture reçoit les liens vers les deux procédures : le dépôt privé comporte désormais six références cohérentes.

Les principales corrections de fond concernent :

- La différence entre installer les dépendances d’Ansible et exécuter un rôle.
- Les profils sources, profils installés et paramètres réellement chargés, qui ne constituent pas une preuve interchangeable.
- Les composants récents du service de revue et les configurations privées à sauvegarder avec leur état durable.
- La portée limitée des collecteurs et restaurateurs historiques, même lorsque leurs contrôles réussissent.
- La nécessité de stabiliser plusieurs programmes pour obtenir une collecte cohérente de toute la chaîne.
- Les exécutions persistées : dépublier un workflow ne suffit pas à garantir qu’une attente restaurée ne produira aucun effet.
- La réconciliation des envois, décisions humaines, révocations et fichiers distants avant réactivation.

Les opérations de sauvegarde et de reprise restent à intégrer et à essayer dans une mission distincte. La documentation ne présente ni nouvelle copie indépendante ni reconstruction complète comme réalisées. Les écarts de couverture sont des travaux explicitement décrits, avec leur raison et leurs critères de contrôle.

Les deux procédures de l’utilisateur ont été conservées dans l’historique avant leur réécriture. Son clone local et la branche distante avaient évolué séparément : les historiques ont été réunis par fusion, sans abandonner son commit ni remplacer les guides plus récents par leurs anciennes copies.

## Orchestration et délégation — Délégation

L’orchestrateur Codex répartit la préparation des trois guides entre trois enfants Codex, avec un fichier distinct par enfant. Le premier traite l’inventaire explicatif des secrets sans valeurs. Le deuxième traite les configurations d’agents, les profils et les permissions. Le troisième traite les recettes Ansible et leur catalogue de fichiers. Cette répartition permet de relire intégralement les anciens textes et les sources utiles sans partager les mêmes fichiers d’écriture.

Les modèles effectivement exécutés et les coûts consolidés ne sont pas mesurés. Aucune économie n’est chiffrée. Aucune session OpenCode n’est lancée depuis la base réservée à l’usage personnel de Yanis.

L’orchestrateur assure la lecture des outils de récupération, le rapprochement avec les composants installés, la conservation de l’historique utilisateur, la revue des textes, l’intégration et les publications autorisées. La délégation d’un brouillon ne vaut ni installation ni contrôle d’un service : les résultats et les vérifications finales sont distingués dans la restitution.

Après la rédaction des trois guides, l’enfant chargé de l’inventaire prépare la procédure de reprise ; l’orchestrateur rédige la procédure d’exploitation quotidienne. Deux enfants participent ensuite aux relectures indépendantes : cohérence du guide d’administration, lecture de la procédure quotidienne et contrôle croisé des besoins de récupération. Les corrections de revue sont intégrées avant publication, notamment une ambiguïté sur le stockage des jetons, les copies d’exemples qui pouvaient écraser un fichier existant et la distinction entre données archivées, données vérifiées et données réellement remises en place par les restaurateurs.

## Coopération et adaptation au contexte — Collaboration

Les consignes du projet, l’architecture, la passation, les anciens guides et les annonces de coordination sont consultés. Une intention réserve les trois guides ; une extension réserve ensuite les deux procédures et les références croisées. Les périmètres d’autres interventions sont conservés. Les changements applicatifs simultanés sont traités comme des faits datés et non comme des validations réalisées par la mission documentaire.

La règle actuelle d’usage personnel de la base d’agents est respectée. Le contrôleur personnel n’est ni contacté ni sondé. Les réserves sur les essais des recettes Ansible demeurent applicables. Le changement concurrent d’un fichier de consignes dans le clone public est conservé hors des commits documentaires de cette mission.

Les contrôles de cette mission sont documentaires et statiques : lecture des sources, métadonnées et empreintes ciblées, revue des différences, couverture des anciens sujets, cohérence des liens et vérification de la publication. Ils ne constituent pas un essai de restauration. Aucun service n’est redémarré, aucun workflow n’est exécuté et aucun message métier ni site n’est produit pour écrire les procédures.

Les valeurs de secrets, les archives et les données clients ne sont pas lues pour la rédaction. Le présent rapport public ne reprend pas l’inventaire privé des accès, les chemins de récupération ou les identifiants internes. Les références détaillées restent dans le dépôt privé prévu pour elles.
