<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Portail : parcours complet et images IA préparés — 16 octobre 2026

## Demande et résultat

La demande porte sur deux essais réels depuis le portail client : demande initiale, prototype, approbation du prototype exact, construction du site complet, revue puis livraison au client. Une illustration générée doit pouvoir accompagner chaque site.

Le code a été intégré, poussé dans le dépôt canonique et préparé comme release scellée sur le serveur. Cette release n'est pas activée : l'accord humain pour sa révision exacte et la connexion au compte de test sont encore attendus. Aucun nouvel essai réel, appel de génération d'image, chantier de site ou livraison portail n'a été lancé pendant cette préparation.

Les changements préparés comprennent :

- Le même moteur OpenAI Decisions dans l'entrée et le sous-workflow de décision, avec validation stricte des réponses. Les questions sur les informations manquantes restent formulées concrètement.
- La cible explicitement fournie dans la demande. Le serveur la résout dans le registre opérateur autorisé ; une cible absente, ambiguë ou non autorisée bloque la construction.
- Une action distincte pour construire le site complet, après livraison et approbation du prototype exact. Le nouveau chantier conserve l'historique du prototype.
- Une génération d'illustration avec le modèle gpt-image-2, déclenchée par une demande et un consentement explicites. Le fichier PNG doit être reçu, vérifié et lié au manifeste du chantier avant construction. Le site complet réutilise cette illustration.
- Un outil opérateur pour les essais expressément autorisés : autorisation privée liée à l'artefact exact, à usage unique, revue indépendante et recette navigateur préalables. Sa trace indique explicitement une livraison de test, sans prétendre à un clic humain dans la messagerie.

Les contrôles réalisés passent : 222 tests Python, 241 tests JavaScript finaux, compilation TypeScript/Vite et validation des deux graphes n8n sans avertissement. La préparation officielle de la release réussit. Ces preuves valident les sources et leur préparation ; elles ne démontrent pas encore le parcours installé, la qualité d'une image réelle ou sa réception dans le portail.

La suite reste à exercer sur chacun des deux projets fictifs : analyse réelle, génération de l'image, prototype reçu, approbation de sa version, site complet distinct, recette des pages et de l'image sur ordinateur et mobile, puis lien effectivement accessible au client. Les essais mail précédents ne servent pas de preuve pour ce nouveau parcours.

## Orchestration et délégation

Codex a réalisé directement le développement, les adaptations n8n, les tests, l'intégration Git et la préparation de release. Aucun nouvel agent Codex ni session OpenCode via la base personnelle de contrôle n'a été lancé pour cette mission.

Le moteur de décision préparé utilise gpt-6-luna ; la branche image prépare un appel natif de génération. La disponibilité du modèle a été vérifiée avec l'intégration existante, sans exposer ses identifiants. Aucun résultat d'image ni résultat de construction n'est inventé à partir des fixtures de test.

## Coopération et adaptation au contexte

Les consignes, la fiche de reprise, la passation, les règles de déploiement et les annonces pertinentes ont été consultées. Les intentions et extensions de périmètre ont précédé les écritures. Les modifications concurrentes des consignes et les travaux d'un autre contributeur ont été préservés.

La version publiée du dialogue a servi de référence pour conserver ses corrections récentes. L'avertissement sur une migration du seul sous-workflow a conduit à préparer ensemble l'entrée et la décision, avec le même moteur et des tests de compatibilité. Les autres workflows et les projets de l'autre contributeur n'ont pas été modifiés.

La passation privée conserve la release exacte, les preuves, les questions humaines en attente et les étapes restantes. La clôture de préparation libère les réservations ; une reprise doit relire les changements intervenus avant toute activation. Le service actif reste sur son ancienne release.
