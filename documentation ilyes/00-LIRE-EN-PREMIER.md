> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapports du projet depuis sa création

**Bilan documentaire du 12 octobre 2026.** Ce dossier reprend le développement depuis l'export initial de 25 nœuds, et non seulement les derniers travaux.

## Les trois rapports

1. [Chronologie complète](01-chronologie-complete.md) : point de départ, corrections, évolution commerciale, automatisation et liaison OpenCode.
2. [Preuves et tests](02-preuves-et-tests.md) : ce qui a réellement été vérifié, à quel niveau et avec quelles limites.
3. [État, risques et prochaines étapes](03-etat-risques-et-suite.md) : fonctionnalités établies, copies encore à intégrer et priorités.

## Lecture rapide

La base a évolué d'un workflow d'analyse Gmail vers un assistant commercial en mode TEST, avec mémoire, revue, réponses protégées, file persistante et notifications Telegram. Les essais réels ont révélé des défauts utiles : sélection d'anciens messages, réponses trop génériques, mémoire de questions inexacte, blocages documentaires et erreurs de format JSON. Des corrections ont été appliquées à certaines versions ; les corrections récentes sur copies sont signalées séparément.

Le collègue a ajouté la chaîne OpenCode. Un site de démonstration a été observé et sa création réussie a été rapportée par l'utilisateur. Cela ne prouve pas encore toute la chaîne automatique jusqu'à la livraison. L'approbation Telegram n'est pas opérationnelle de bout en bout, et la lecture effective des documents Google Drive reste à mettre en place.

Ces rapports ne reproduisent ni emails, ni données permettant d'identifier les clients, ni prompts privés, ni secrets. Les exemples cités dans les anciens dossiers restent hors de ce livrable.

## Comment interpréter l'historique

Les dates exactes ne sont données que lorsqu'un document les établit. Les phases sans date sont présentées dans leur ordre de développement. Un ancien README décrit son état de l'époque : son intitulé « inactif » ou « reste à tester » ne doit pas être pris pour l'état présent.

Les nombres de tests ne s'additionnent pas en un taux de fiabilité : plusieurs lots rejouent les mêmes cas sur des versions différentes. Une exécution n8n verte ne constitue pas une preuve d'email envoyé, de mémoire correcte ou de site construit.

## Périmètre de cette rédaction

Lecture des documents et preuves déjà présents, contrôle de l'export original et consultation du protocole de coordination. Aucun workflow, compte Gmail, table métier ou site modifié pour produire ces rapports. Aucun nouveau test fonctionnel ni email envoyé.
