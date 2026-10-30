<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Préparation de la recette Héphaïstos après migration — 19 octobre 2026

## Demande et résultat

Demande : vérifier le redéploiement sur le nouvel hébergement de production,
exercer le parcours client complet dans un projet TEST isolé et remettre la
maquette. État de cette étape : préparation vérifiée ; aucune nouvelle maquette
produite et aucun parcours métier annoncé réussi.

La nouvelle machine répond par SSH avec la clé hôte épinglée dans l’alias
opérateur existant. Le lien de release réellement exécutée a été lu, le portail
est actif et quatre services du parcours sont actifs. L’accès HTTPS de santé
répond 200 avec vérification TLS normale. Le navigateur affiche la vraie page
d’accueil puis demande une connexion au compte de recette.

La version déployée ne contient pas encore la politique qui supprime les mails
de progression technique. Lancer les échanges immédiatement reproduirait les
notifications refusées par le demandeur. La candidate conserve le correctif
concurrent d’affichage des maquettes et la correction DNS du builder. Une
incohérence de pin de sécurité a été détectée par la suite complète : le helper
d’activation référençait l’ancienne empreinte du contrôleur. Une seule constante
a été mise à jour vers les octets du contrôleur relu ; aucune protection supprimée
et aucun lecteur activé. Ce correctif a été committé et poussé normalement.

Validation : 438 tests Python passent après correction ; 94 tests frontend
passent et la compilation TypeScript/Vite réussit. Les 21 tests ciblés
d’activation et les 33 tests du contrôleur passent aussi. Le premier lancement
frontend dans le worktree sans dépendances a échoué avant les tests ; la suite
a ensuite été exécutée dans la copie ayant les dépendances installées, avec les
mêmes sources frontend. Des avertissements existants de ressources SQLite
subsistent. L’installation npm signale une vulnérabilité de sévérité élevée ;
aucune mise à jour forcée des dépendances n’a été effectuée dans cette mission.
Ces validations utilisent des fixtures, pas les données de production.

La connexion au compte client et l’accord humain pour la release exacte restent
nécessaires avant reprise. Le compte personnel SSH actuel ne dispose pas du sudo
nécessaire au déploiement. Le passage par une autre tâche nécessite une
instruction explicite d’envoi ; une question groupée a été présentée au demandeur.
Aucun mot de passe demandé ou lu, aucun mail client envoyé, aucun ancien job
réarmé. Aucun redéploiement effectué pendant cette préparation.

## Orchestration et délégation

Travail direct par Codex : lectures ciblées, vérification des versions et des
services, contrôle du navigateur, comparaison des sources, correction du pin,
tests et publication Git. Aucun nouvel agent lancé, aucune session
PIAgentControl utilisée, aucune consigne envoyée à une autre tâche. Les
services actifs ne constituent pas une preuve de génération ou de revue de
maquette : ce parcours reste à exercer après levée des prérequis.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche de reprise, le protocole et l’état partagé,
la fin de migration, la fin du déploiement concurrent, les passations du portail
et la politique mail ont été consultés. La production migrée a été distinguée
du lab conservé sur l’ancien serveur ; aucun effet métier n’a été déclenché
sur ce lab et aucun accès au contrôleur personnel réservé n’a été tenté.

Une intention et une extension ont réservé le dossier de preuves privé, le
rapport et la seule constante corrigée. Les nouvelles annonces ont été
consultées avant les mutations. Les changements existants du checkout, les
projets concurrents et la candidate de profil ont été préservés. La préparation
a utilisé une copie source et un worktree isolés ; aucun service n’exécute ces
copies. Les réservations de code ont été libérées après le push. Les preuves
techniques exactes restent privées, hors du présent rapport public.
