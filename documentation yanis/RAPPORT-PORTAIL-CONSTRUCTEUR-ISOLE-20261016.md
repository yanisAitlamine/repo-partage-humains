<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Portail — correction du constructeur isolé

16 octobre 2026.

## Demande et résultat

Yanis a demandé d'effectuer les actions du mail de son collaborateur, puis de
répondre. Le mail demandait un diagnostic du constructeur et une préparation
vérifiée ; il ne demandait pas d'activer une nouvelle version de l'application.

La reproduction a conservé le compte, l'environnement et les restrictions du
constructeur. Seules les destinations des sorties ont changé pour conserver une
trace privée. Dépendances : code 0. Contrôles : code 1, avec sept erreurs sur
213 tests. Les erreurs PermissionError apparaissaient dans les tests des outils
administratifs : leur temporaire était placé sous un parent traversable mais
non lisible, alors que la fonction testée ouvrait les ancêtres en lecture.

Le correctif utilise pour les seuls contrôles le temporaire privé déjà fourni
par l'isolation systemd. Les dépendances gardent leur emplacement précédent.
Les permissions, le compte, les caches, le réseau, les secrets inaccessibles et
les limites restent inchangés ; aucun test n'est supprimé. Un nouveau test
vérifie ces invariants. L'empreinte attendue par l'outil d'activation a aussi été
mise à jour, avec un contrôle empêchant sa dérive par rapport au source revu.

Les 51 tests Linux des outils passent. La recette de délégation a terminé
27 tâches sans erreur, avec un seul changement. La préparation normale de la
candidate demandée, sous le compte du collaborateur, a ensuite réussi : tests
Python, compilation et release scellée. Cette candidate reste non activée.
Le processus du portail, sa version, son unité, ses configurations et l'option
du lecteur public sont identiques au relevé initial ; santé HTTPS 200. Les
unités de construction sont arrêtées.

La réponse envoyée dans le même fil contient l'étape, le code retour, un exemple
de test et l'erreur assainie, le correctif et les vérifications. Les traces brutes
restent privées. Aucun workflow, site distant ou traitement client n'a été
exécuté. Cette réparation ne vaut pas autorisation d'une future mise en service.

## Orchestration et délégation

Trois agents internes ont préparé le correctif et son test, une revue indépendante
en lecture seule, et le rapport public. Ils ont terminé ; les résultats ont été
relus et intégrés. Codex a effectué directement la capture privée, l'intégration,
la mise à jour de l'empreinte, les tests Linux, l'installation opérateur, la
préparation réelle, les contrôles et la réponse autorisée.

La première revue statique ne suffisait pas à expliquer l'échec : la trace réelle
a révélé le droit de lecture exigé sur les parents. La correction a ensuite été
revue sans défaut bloquant concret repéré. Les modèles exacts n'ont pas fait
l'objet d'un relevé indépendant ; aucun coût ni gain n'est estimé. Aucun OpenCode
ni accès à la VM personnelle n'a été utilisé. La surveillance du journal avait
un seuil d'arrêt, pas une garantie de taille maximale stricte entre deux sondes.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche de reprise, les passations, le protocole et
les annonces pertinentes ont été consultés. L'intention et son extension ont
précédé les changements ; le verrou du constructeur a été respecté. Les travaux
concurrents de commerce en ligne et d'hébergement sont restés séparés. Les
contributions du collaborateur ont été récupérées sans les activer ni modifier
ses fichiers réservés.

Les modifications préexistantes des consignes et de la fiche de reprise sont
conservées hors des commits de ce lot. Les sources et la passation sont sur la
branche principale du dépôt canonique. Les preuves et échanges lisibles sont
conservés en copies d'audit privées, sans secret dans ce rapport. L'annonce finale
libère uniquement les réservations de cette mission pour permettre la suite
coordonnée des préparations du collaborateur.
