# Jev ou OpenAI Decisions pour le dialogue commercial

16 octobre 2026 — diagnostic et comparaison isolée.

## Demande et résultat

La demande était de corriger les blocages de Jev ou de recommander un fine-tuning
ou son remplacement. La recommandation est de remplacer Jev **pour cette étape
de décision du brief** par OpenAI Decisions, après intégration et validation
complètes. Aucun fine-tuning n’est justifié par cette évaluation.

La version publiée correspondait bien aux sources : le problème ne provenait
pas d’une ancienne installation. Deux échanges fictifs complets provoquaient
encore des demandes de précisions déjà fournies. Les consignes mélangeaient
confirmation et modification, et les citations exigeaient plusieurs références
indirectes. La vérification locale d’une citation et la décision globale
cumulaient aussi plusieurs jugements.

Les corrections candidates séparent ces jugements, distinguent les intentions,
définissent explicitement la navigation comme une fonctionnalité et précisent
ce qui constitue une ambiguïté de projet. Les paragraphes restent des citations
littérales ; les contrôles finaux conservent tout l’historique. Les seuils
d’acceptation, les preuves de provenance et les validations humaines sont
conservés.

| Configuration réellement appelée | Premier scénario complet | Second scénario complet |
| --- | --- | --- |
| Jev 1.13 publié, état initial | Poursuite des questions | Poursuite des questions |
| Jev 1.14, questions candidates finales | Blocage pour incertitude | Poursuite pour preuves incertaines |
| OpenAI Decisions, mêmes questions candidates finales | Brief complet | Brief complet |

OpenAI Decisions a aussi respecté les huit attentes de non-préparation :
arrêt, simple merci, suivi de statut, contradiction, ambiguïté de projet,
tentative d’instruction accompagnant un arrêt, retrait des fonctionnalités,
brief incomplet. Ces huit variations synthétiques testent la décision finale,
pas une nouvelle réception physique de mails ni toute l’extraction documentaire.
Dans tous ces cas, la préparation d’un nouveau prompt est restée interdite.

**État livré : diagnostic et candidat évalué, pas migration de production.**
Le service publié reste inchangé. Les deux workflows temporaires de diagnostic
ont été archivés. Aucun mail, construction, livraison ou publication de site
n’a été déclenché pendant cette comparaison.

Deux cas positifs et huit variations ne donnent pas une mesure générale de
fiabilité. Avant bascule, il reste à versionner l’adaptateur fournisseur et les
questions retenues, vérifier les refus et réponses mal formées, puis les
parcours documents, arbitrage humain, portail et reprise. L’échec d’un fournisseur
doit rester bloquant ; aucun abaissement des seuils n’est proposé.

Le fine-tuning est une étape d’optimisation après les évaluations et les
corrections de consignes. Cette comparaison ne constitue pas un jeu
d’entraînement suffisant et montre déjà une alternative sans entraînement.
La disponibilité d’une offre de fine-tuning Jev spécifique n’a pas été établie.

Références consultées :
[limites documentées de Jev 1.13](https://docs.typesafe.ai/model-jaggedness/jev-1.13),
[Jev 1.14](https://typesafe.ai/blog/jev-1-14),
[OpenAI Decisions](https://developers.openai.com/api/docs/guides/decisions),
[cycle d’optimisation](https://developers.openai.com/api/docs/guides/model-optimization).
L’API Decisions est actuellement en bêta publique avec le modèle gpt-6-luna ;
les essais ont utilisé cette API dédiée, pas une réponse JSON générée par chat.

## Orchestration et délégation

Codex a effectué directement la lecture des sources et versions publiées, la
préparation des variantes, les appels réels et la revue des résultats.
Aucun sous-agent, aucune session PIAgentControl et aucun accès Kali n’ont été
lancés. Les fournisseurs réellement observés étaient Jev 1.13, Jev 1.14 et
OpenAI gpt-6-luna. Les identités des fournisseurs ont été conservées dans les
réponses ; aucune réponse OpenAI n’a été présentée comme une réponse Jev.
Les preuves détaillées et candidats restent dans l’espace privé de mission
sur le serveur, hors Git public. Aucun coût ou gain n’est estimé.

## Coopération et adaptation au contexte

Le parcours de reprise, les consignes du projet et du dépôt, le protocole et les
annonces pertinentes ont été consultés. Une intention puis son extension
documentaire ont réservé le diagnostic et son rapport. Les changements
concurrents du portail et les arbres Git déjà modifiés ont été préservés ;
la publication du rapport utilise une copie Git séparée.

L’observation des cas réels a conduit à vérifier d’abord l’intégration, puis à
comparer les fournisseurs avec les mêmes règles finales. Le premier essai
OpenAI ne suffisait pas non plus sans ces corrections. Le rapport distingue
donc les appels de diagnostic, le candidat et le service actif.
La fin de mission libère les réservations ; les références exactes et la
passation technique demeurent privées.
