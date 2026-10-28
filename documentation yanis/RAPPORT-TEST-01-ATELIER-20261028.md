# Test 01 de l’Atelier — exécution, dialogue, prompts et coût

## Demande et résultat

Yanis demande l’exécution du premier scénario depuis le lanceur Kali, puis un rapport Markdown complet avec l’échange, la fabrication du prompt, la délégation OpenCode et le suivi des jetons/coûts.

**Le scénario « brief complet dès le premier message » a réussi le 28 octobre 2026 en 84,055 secondes.** Une seule demande client a conduit à quatre pages de maquette. Le client Terre Claire, son activité et son adresse en domaine réservé constituent un jeu de test fictif. Les textes ci-dessous sont ceux de cette simulation ; les appels au modèle et les actions du navigateur ont été réels.

Version applicative : `bd6438dcfc0d13d72396364963a3f3c89773f9ed`. Modèle observé : **OpenAI GPT‑6.1 Terra**, raisonnement **medium**. Résultat automatique : `AUTOMATED_PASS`. Les huit captures ont ensuite été examinées par Codex ; cette revue d’agent est distincte du statut de revue humaine du rapport automatique.

Le scénario s’arrête à la maquette privée. Il ne comprend ni accord client final ni publication WordPress.

## Chronologie observée

Toutes les heures sont celles de Paris, le 28 octobre 2026.

| Heure | Événement |
| --- | --- |
| 15:35:25,935 | Début du scénario |
| 15:35:27,053 | Message client enregistré |
| 15:35:27,178 à 15:35:37,806 | Analyse et construction du brief ; 10,62 s pour l’invocation OpenCode |
| 15:35:37,834 à 15:36:46,775 | Génération HTML/CSS ; 68,93 s pour l’invocation OpenCode |
| 15:36:46,782 | Message de disponibilité ajouté par le serveur Rust |
| 15:36:49,990 | Fin du scénario : contrôles réussis |
| 15:36:50,005 | Rapport de campagne finalisé |

Les deux invocations représentent 79,55 secondes ; le reste couvre les autres opérations de la chaîne, notamment le navigateur et les validations. Le rapport automatique a conservé les mêmes versions et la même empreinte du backend avant et après le scénario.

## Échange exact du client simulé avec l’Atelier

### Message client

> Projet : Terre Claire
> 
> Je veux le site suivant : Terre Claire propose des ateliers de poterie pour adultes debutants a Tours. L action principale est Demander une place. Accueil, Ateliers, A propos, Contact. Palette ivoire, terre cuite et bleu cobalt. Mercredi et samedi de 10 h a 18 h. Initiation : 90 minutes, 55 EUR, 8 places ; Tournage : 120 minutes, 85 EUR, 4 places ; Email sauvage : 150 minutes, 110 EUR, complet. Contact bonjour@terre-claire.example.test. Ton direct et chaleureux. Textes courts redigeables a partir de ces seules informations, sans inventer de temoignages, de chiffres ni de biographies. Liberte sur la composition dans la palette indiquee. Aucun compte client, paiement ou inscription. Les visuels generes sont autorises ; aucun portrait reel invente. Contact en texte lisible.

### Réponse affichée

> Votre maquette est prête. Décrivez vos modifications ou écrivez « Je valide la maquette » pour construire et publier le site.

Aucune question complémentaire n’a été posée. La réponse affichée est une phrase fixe du serveur Rust, ajoutée lorsque la maquette a été enregistrée. Ce n’est pas un troisième appel au modèle.

## Création du prompt de construction

Le premier appel porte le rôle fonctionnel `chat-decision`. Ses instructions applicatives nomment l’analyste « JEV ». Le modèle a reçu la conversation entière, sans pièce jointe, sans maquette précédente et sans contenu de site source. Il devait déterminer si les données permettaient une première maquette et retourner une décision structurée.

Décision enregistrée : `sufficient=true`, `question=""`, `stop=false`. Son champ `prompt` contient exactement :

> Créer une première maquette du site Terre Claire, qui propose des ateliers de poterie pour adultes débutants à Tours. L’objectif est de présenter les ateliers et de faciliter la prise de contact ; l’action principale est « Demander une place ».
> 
> Prévoir quatre pages ou sections clairement accessibles : Accueil, Ateliers, À propos et Contact. Présenter les informations suivantes sans en ajouter : ateliers le mercredi et le samedi de 10 h à 18 h ; Initiation, 90 minutes, 55 €, 8 places ; Tournage, 120 minutes, 85 €, 4 places ; Émail sauvage, 150 minutes, 110 €, complet. Afficher clairement le statut complet de ce dernier atelier. Indiquer Tours et l’adresse bonjour@terre-claire.example.test en texte lisible ; ne pas inventer d’adresse précise.
> 
> Employer des textes courts, directs et chaleureux, rédigés uniquement à partir des faits fournis. Ne pas inventer de témoignages, de chiffres, de biographie ou de détails sur le contenu des ateliers. Utiliser une palette ivoire, terre cuite et bleu cobalt, avec une composition libre. Les visuels générés sont autorisés, mais aucun portrait réel ne doit être inventé.
> 
> Rendre la navigation et l’action principale faciles à repérer. « Demander une place » peut orienter vers le contact par e-mail, sans promettre de réservation ni créer de formulaire d’inscription. Ne prévoir aucun compte client, paiement ou inscription. Concevoir une maquette lisible et adaptée aux mobiles.

Le backend a vérifié que le prompt envoyé ensuite à la génération correspondait à cette décision enregistrée. Le contexte du générateur comprenait la conversation originale et ce prompt ; les critères de réussite du scénario n’y figuraient pas.

## Construction de la maquette

Le deuxième appel porte le rôle `generate_private`. Les instructions de construction imposent une maquette HTML/CSS adaptée au mobile, un objet structuré avec pages et fichiers, des liens locaux valides, des contacts en texte lisible et le respect des faits fournis. Les scripts, formulaires, accès réseau et appels d’outils sont refusés pour cette génération statique.

Le modèle a produit **quatre documents HTML et une feuille de style, 17 596 octets de contenu** : Accueil, Ateliers, À propos et Contact. Les illustrations sont des formes CSS. Aucun générateur d’images distinct n’apparaît dans cette exécution.

Chaque invocation a terminé sans erreur. Les traces ne contiennent aucune demande de réparation après validation, aucune normalisation de réponse et aucune seconde tentative de génération pour ce scénario.

## Orchestration et délégation

| Étape | Responsable réel | Agent OpenCode observé | Sessions | Sous-agents | Appels d’outils |
| --- | --- | --- | ---: | ---: | ---: |
| Comprendre la demande et écrire le prompt | Modèle appelé par le backend Python ; rôle JEV/analyse | `hephaistos-bounded`, principal | 1 | 0 | 0 |
| Produire le HTML/CSS | Modèle appelé par le backend Python ; rôle génération | `hephaistos-bounded`, principal | 1 | 0 | 0 |
| Enregistrer la maquette et afficher la disponibilité | Serveur Rust | Sans appel OpenCode | 0 | 0 | 0 |
| Vérifier les pages et prendre les captures | Scripts de tests et Chromium | Sans appel OpenCode | 0 | 0 | 0 |
| Examiner les captures | Codex | Revue d’agent après exécution | — | — | — |

Les deux sessions OpenCode sont indépendantes, sans session parente. La base des messages confirme une demande et une réponse de modèle dans chacune. L’agent est configuré comme agent principal, avec les permissions d’outils refusées.

**Il n’y a donc pas eu de délégation multiagent.** Le programme Python a enchaîné deux invocations du même type d’agent. OpenCode n’a pas distribué le travail à des agents de développement, recherche ou test. Ce scénario ne valide pas une navigation autonome des agents dans des sources client : il ne contient aucun site source à explorer.

## Jetons et coût des appels API

Les compteurs viennent des messages assistants enregistrés par OpenCode, et non d’une estimation de longueur du prompt. Dans ce format, les sorties visibles et le raisonnement sont séparés ; les sorties facturables réunissent les deux une seule fois. Les entrées non mises en cache, les lectures de cache et les écritures de cache sont trois catégories distinctes.

| Appel | Entrée non mise en cache | Cache écrit | Cache lu | Entrée totale | Sortie visible | Raisonnement | Sortie facturable | Coût estimé USD |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| JEV / analyse | 3 | 1 729 | 0 | 1 732 | 345 | 57 | 402 | 0,00417425 |
| Génération de la maquette | 3 | 1 869 | 0 | 1 872 | 5 433 | 370 | 5 803 | 0,03135425 |
| **Total OpenAI** | **6** | **3 598** | **0** | **3 604** | **5 778** | **427** | **6 205** | **0,03552850** |

**JEV est ici un rôle consommant OpenAI. Son coût est inclus dans le total OpenAI : il ne faut pas additionner une deuxième facture JEV à ce total.** L’authentification observée est de type API. Le suivi ne dispose pas d’une facture confirmant le débit ; les montants sont des estimations aux tarifs publics. Ils correspondent également aux coûts enregistrés par OpenCode pour ces deux appels ; ce champ enregistré est un calcul, pas une confirmation de facture.

Tarifs vérifiés le 28 octobre 2026 pour GPT‑6.1 Terra, par million de jetons : entrée 1 USD ; lecture de cache 0,05 USD ; écriture de cache 30 minutes 1,25 USD ; sortie, raisonnement compris, 5 USD. Hypothèses : traitement Standard, contexte court, traitement global sans supplément régional. Les deux appels restent sous le seuil de contexte long.

Calcul de JEV : `(3 × 1 + 1 729 × 1,25 + 402 × 5) / 1 000 000 = 0,00417425 USD`.

Calcul de génération : `(3 × 1 + 1 869 × 1,25 + 5 803 × 5) / 1 000 000 = 0,03135425 USD`.

Sources : [tarifs officiels GPT‑6.1 Terra](https://developers.openai.com/api/docs/models/gpt-6.1-terra), [facturation du cache](https://developers.openai.com/api/docs/guides/prompt-caching), [jetons de raisonnement facturés en sortie](https://developers.openai.com/api/docs/guides/reasoning).

## Contrôles et limites du résultat

- Une décision native de construction contient les informations requises du brief.
- Les pages contiennent Terre Claire, Tours, les ateliers, les prix et le statut complet.
- Les pages demandées sont présentes et accessibles depuis la navigation.
- Les liens internes et les ressources locales répondent correctement.
- Aucun défilement horizontal n’a été détecté à 390 ou 1 440 pixels.
- Huit captures ont été prises ; leur examen par Codex constate une mise en page lisible, une palette conforme, les durées/prix/places, les horaires et le contact attendus.
- L’exécution automatique est réussie ; elle ne prouve pas une délégation multiagent ou une livraison WordPress.

Le suivi avait initialement signalé un arrêt parce que le programme de tests s’était terminé entre la lecture d’un rapport encore en cours et celle de l’état du programme. Le rapport final indiquait pourtant une réussite et le code de sortie était zéro. La correction du suivi, publiée dans `9d8d62c`, relit le rapport terminal avant de conclure à un arrêt anormal. Le backend et les critères du test sont restés identiques.

## Suivi réutilisable ajouté aux tests

Le lanceur relève les messages assistants des sessions OpenCode associées aux travaux de chaque projet de test, ainsi que les éventuelles sessions enfants. Il conserve le fournisseur, le modèle, le rôle, les jetons d’entrée/sortie/cache/raisonnement, l’état de l’appel et le coût calculé avec une grille tarifaire datée.

Un registre déduplique les appels par session et message. Relire les résultats met à jour le même relevé et ne refacture pas virtuellement l’exécution. Les appels repris et les sous-agents qui possèdent des messages distincts sont comptés distinctement. Un tarif ou un compteur manquant donne un état incomplet, jamais un coût nul fabriqué. Les appels encore en cours et les appels dont les compteurs n’ont pas été enregistrés restent explicitement incomplets.

Les résultats comportent des données structurées, un tableau CSV et un rapport Markdown avec coûts, dialogue et prompts disponibles. Le rapport automatique d’origine est conservé séparément du rapport enrichi. La grille actuelle chiffre les jetons de GPT‑6.1 Terra ; un autre modèle exige un tarif explicite et les outils payants éventuels exigent leur propre grille. Ce suivi a été appliqué au test 1 existant sans relancer les appels au modèle. Le code a été publié dans le commit `dec5472`. Les **249 vérifications hors ligne** passent, dont les tests de ventilation du cache et du raisonnement, de déduplication, de collecte des sessions enfants, de données manquantes et de conservation de la grille tarifaire. Le post-traitement a aussi été exécuté sur le rapport réel du staging ; son empreinte avant et après est identique. Le navigateur connecté depuis Kali confirme que le coût apparaît dans le tableau de suivi.

## Collaboration et adaptation au contexte

Codex a exécuté ce travail directement. La coordination du dépôt unique et du lanceur a été annoncée dans l’espace partagé ; cette mission réserve le suivi des coûts et le présent rapport. Les changements applicatifs concurrents sont préservés. Le rapport distingue les appels observés, le rôle JEV, les validations automatiques, l’examen des captures et la facturation estimée. Les sessions, coordonnées de machines et chemins d’exploitation restent dans les preuves opérationnelles.

## Captures de la maquette réellement produite

### Accueil — 1440 pixels

![Accueil — 1440 pixels](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-test-01-20261028/documentation%20yanis/assets/test-01-20261028/accueil-1440.png)

### Accueil — 390 pixels

![Accueil — 390 pixels](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-test-01-20261028/documentation%20yanis/assets/test-01-20261028/accueil-390.png)

### Ateliers — 1440 pixels

![Ateliers — 1440 pixels](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-test-01-20261028/documentation%20yanis/assets/test-01-20261028/ateliers-1440.png)

### Ateliers — 390 pixels

![Ateliers — 390 pixels](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-test-01-20261028/documentation%20yanis/assets/test-01-20261028/ateliers-390.png)

### A-propos — 1440 pixels

![A-propos — 1440 pixels](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-test-01-20261028/documentation%20yanis/assets/test-01-20261028/a-propos-1440.png)

### A-propos — 390 pixels

![A-propos — 390 pixels](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-test-01-20261028/documentation%20yanis/assets/test-01-20261028/a-propos-390.png)

### Contact — 1440 pixels

![Contact — 1440 pixels](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-test-01-20261028/documentation%20yanis/assets/test-01-20261028/contact-1440.png)

### Contact — 390 pixels

![Contact — 390 pixels](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-test-01-20261028/documentation%20yanis/assets/test-01-20261028/contact-390.png)

