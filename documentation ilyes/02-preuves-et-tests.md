> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# 2 — Preuves, tests et portée réelle

## Quatre niveaux de preuve

| Niveau | Ce qu'il permet de conclure | Ce qu'il ne prouve pas |
| --- | --- | --- |
| Contrôle local | JSON, graphe, logique déterministe et sorties simulées conformes aux cas fournis | Qualité de la vraie IA ou fonctionnement des services |
| OpenAI réel isolé | Réponses et analyses réellement produites pour des messages fictifs | Réception Gmail, envoi, webhook et concurrence de production |
| n8n/API réel isolé | Comportement natif observé, avec états relus dans les tables de test | Réussite de tous les emails ou absence de toute panne |
| Échange utilisateur réel | Conversation et notification constatées lors d'un essai | Couverture exhaustive et garantie de disponibilité |

Les fichiers cités ci-dessous sont dans `outputs/`, sauf indication `ameliorations-agence/`. Les comptes de tests sont ceux des preuves historiques, pas de nouveaux tests lancés pour ce rapport.

## Base et première sécurisation

| Vérification | Résultat consigné | Preuve principale |
| --- | --- | --- |
| Export intact | 25 nœuds ; empreinte recalculée conforme à l'empreinte historique | `workflow-n8n-original-intact.json`, `README-stabilisation-A_VERIFIER.md` |
| Première copie de revue | 28 nœuds, 36 connexions, références d'origine conservées, tables TEST par marqueurs | `workflow-n8n-A_VERIFIER-file-revue.json` |
| Réponse sandbox | 13 cas synthétiques de garde ; aucun envoi réel | `README-stabilisation-A_VERIFIER.md` |
| Conversation de 51 nœuds | 11 cas synthétiques de garde ; une seule action Gmail Reply ; copie inactive | `workflow-n8n-test-conversation-reelle.json` |
| Lecture et réponse contrôlées | Copie distante manuelle de 34 nœuds, tables TEST, outbox et ID message vérifiés | `README-stabilisation-A_VERIFIER.md` |

L'existence d'une action Gmail dans un export ne prouve pas qu'elle a envoyé une réponse. La version sandbox, la copie de 51 nœuds et la copie importée de 34 nœuds doivent rester distinguées.

## Évolution commerciale et mémoire

| Lot | Résultat local documenté | Limite |
| --- | --- | --- |
| Réponse devis/délai/maquette | 76 assertions ; conservation de la réponse contextuelle et gardes | Sorties IA simulées |
| Suivi vague et lot | 116 assertions ; réponse vide, ordre et mémoire entre messages | Nouvelle boucle complète encore à valider réellement à cette étape |
| Coupure de session | 22 vérifications supplémentaires ; ancien email et IDs incohérents bloqués | Ne démontre pas la pagination exhaustive |
| Identité progressive | 100 assertions ; entreprise, contact et projet séparés | Aucun nouvel appel OpenAI pour ce lot |
| Collecte en trois étapes | 95 assertions ; faits, propositions, contenus provisoires et livraison | Informations légales déclarées, pas audit juridique |

Sources : `resultats-test-reponses-contextuelles-devis.json`, `README-reponses-contextuelles-devis.md`, `README-suivi-commercial-et-lot.md`, `README-identite-progressive.md`, `README-collecte-trois-etapes.md`. Les confirmations d'application et relecture distantes sont séparées des résultats locaux.

## Automatisation et Telegram

| Vérification | Preuve et résultat | Portée |
| --- | --- | --- |
| Préparation automatique | 101 assertions locales | Date de bascule, filtres, file, propriétaires et notifications |
| Telegram natif | Exécution paramètre privé à consulter sur le Pi arrêtée sur format inattendu, puis 108 avec notification confirmée | Un vrai essai de notification personnelle ; 106 n'est pas une réussite |
| Verrou concurrent | 12 tentatives API ; 1 propriétaire ; résultat relu | Lot réellement observé, pas une garantie générale |
| Activation TEST | Coupure `2026-10-11T15:37:32.674Z` | Nouveau service TEST autorisé, pas ouverture production |
| Améliorations appliquées | 744 assertions de composants et 6 scénarios avec OpenAI réel fictif | Ni nouveaux emails ni preuve de toute la chaîne Gmail après cette mise à jour |

Sources : `README-automatique-gmail-telegram.md`, `README-workflows-ranges.md`, `resultats-test-verrou-concurrent.json`, `activation-automatique-test.json`, `etat-automatique-test-actif.json`, `ameliorations-agence/README-avancees-agence.md`.

La préparation initiale avait rencontré un refus HTTP 405 pour une méthode de mise à jour ; ce refus n'était pas un test de verrou réussi. Les essais concurrents ultérieurs constituent une preuve distincte. Une notification préparée ou un polling Telegram sans résultat conservé ne vaut pas confirmation récente de réception.

## Pièces jointes et continuité : les succès et les échecs

| Lot/exécution | Résultat observé | Conclusion correcte |
| --- | --- | --- |
| Première lecture Office/texte | Extraction locale et gardes ; PDF natif encore à confirmer alors | Prise en charge initiale partielle |
| 1534 | 13/13 contrôles, véritables appels OpenAI sur données fictives | Ces cas indépendants passent, y compris fixtures PDF longues |
| 1613 | 12 messages analysés ; défauts de continuité et de répétition relevés | Ce lot n'était pas entièrement réussi |
| 3868 | 12 passages séquentiels persistés, 10/12 contrôles passent | Deux blocages documentaires demeuraient |
| 4232 | 6 cas : 4 contrôles automatiques passent ; revue du texte détecte une formulation trompeuse et deux blocages | Un statut vert n'a pas suffi ; lot incomplet |
| 4293 | Replay ciblé de 3 cas, 3/3 contrôles et revue indépendante acceptés | Correction démontrée sur ces trois cas, pas sur tout le corpus |
| Mémoire des sorties 4293 | 167 assertions locales sur les rapports réellement capturés | Mapping corrigé dans une copie ; pas un nouvel appel IA ni une nouvelle exécution native |

Sources : `ameliorations-agence/point-reprise-2026-10-12.md`, `pieces-jointes-resultats-reels.json`, `rafales-resultats-reels.json`, `historiques-cible-resultats-reels.json`, `continuite-ack-resultats-reels.json`, `continuite-ack-cible-resultats-reels.json`, `ack-cible-4293-bilan.md`, `memoire-shadow-4293-bilan.md` dans le même dossier.

Deux précisions sont essentielles :

- Les cas 4293 sont indépendants sur un historique commun : ils ne prouvent pas trois tours consécutifs sans répétition.
- Dans l'un de ces cas, des nouvelles informations ont été conservées dans le journal de revue, sans devenir des faits confirmés. « Mémoire conservée » ne signifie donc pas « chaque nouvelle information validée ».

L'exécution paramètre privé à consulter sur le Pi n'est pas utilisable comme preuve de réponse correcte, car les sorties n'ont pas été conservées. Les résultats 4232 et 4293 sont les références exploitables.

## Corpus de tests adversariaux

Sept séquences de six emails, soit **42 messages fictifs**, ont été préparées : changements de décisions, plusieurs marques, clients entrelacés, anglais, documents illisibles et PDF longs. Préparer ce corpus ne revient pas à l'avoir entièrement exécuté.

Les lots prioritaires réellement exécutés doivent être reliés à leurs résultats ci-dessus. Les autres scénarios restent des tests à dérouler. Une arrivée simulée à trois secondes d'intervalle, traitée séquentiellement par l'IA, ne démontre pas à elle seule la concurrence du collecteur Gmail.

Sources : `ameliorations-agence/tests-rafales.md`, `scenarios-rafales.json`, `tests-adversariaux.md`.

## OpenCode, approbations et site

| Vérification | Résultat | Limite |
| --- | --- | --- |
| Site de démonstration | Création rapportée par l'utilisateur ; page HTTP 200 observée | Chaîne exacte de construction pas établie par cette seule lecture |
| Exécution paramètre privé à consulter sur le Pi | Arrêt/annulation avant la soumission de construction | Aucune construction démontrée par cette exécution |
| Simulation OpenCode | 30/32 sur source, 32/32 après correction locale du mode | Aucun job réel lancé par ce test |
| Approbation simplifiée | 23 tests locaux | Copie avec POST désactivé/déconnecté |
| Contrat parent/enfant | 24 tests locaux | Ancien patch devenu à reconsidérer après évolution du collègue |
| Décision par révision de projet | 32 assertions locales | Journal durable pas intégré dans le workflow fonctionnel |
| Réservation conditionnelle | Deux processus concurrents sur une ligne fictive : 1 gagnant, 0 pour le second et le replay | Preuve sur cette ligne ; pas unicité universelle ou idempotence du backend |
| Approbation Telegram | Copie inactive importée ; tests locaux | Pas de clic réel ni de construction via Telegram démontrés |

Sources : `ameliorations-agence/opencode-preuve-1625-lecture-seule.json`, `opencode-simulation-rapport.md`, `opencode-approbation-simple-bilan.md`, `opencode-contrat-parent-enfant-bilan.md`, `approbation-reservation-concurrente-resultats-reels.json`, `telegram-approbation-bilan.md`.

## Google Drive : état des preuves

Le diagnostic réel a trouvé un suivi commercial bloqué en revue et aucun lecteur Google Drive dans le moteur examiné. L'invitation automatique peut être exclue par la recherche des expéditeurs TEST. Le document lui-même n'a pas été lu.


## Conclusion

Le projet dispose de nombreuses preuves utiles, dont de vrais essais IA et n8n. Ces preuves sont bornées par leur version, leur corpus et leur parcours. Elles ne justifient pas une garantie de 99,99 %, une affirmation d'absence de défaut ou une déclaration générale « prêt à la production ».
