# Rapport de tests de l’Atelier — 28 octobre 2026

## Demande et résultat

Yanis demande un compte rendu Markdown du rapport JSON existant, accompagné de captures des sites créés et de résumés des conversations clients simulées.

**La campagne réelle a réussi ses 29 scénarios automatisés : 23 maquettes sans publication finale, cinq conversations clôturées et un site livré sur WordPress.** Elle s’est déroulée le 28 octobre 2026 de **11 h 16 min 38 s à 12 h 02 min 16 s, heure de Paris**, soit **45 min 38 s**. Les quatre scénarios de refonte retirés à la demande de Yanis ne font pas partie de ce résultat ; la numérotation conserve donc des trous.

Ce document est une restitution des preuves déjà enregistrées. Les clients et leurs activités sont fictifs ; les actions dans le navigateur, les réponses du modèle, les maquettes et la livraison WordPress ont réellement été exécutées pendant cette campagne. Les résumés sont des reformulations ; les conversations brutes ne sont pas reproduites.

**Le regroupement ultérieur en dépôt unique a passé une compilation neuve et des vérifications hors ligne. Les 29 conversations réelles n’ont pas été rejouées après ce regroupement**, conformément à la demande de Yanis de poursuivre sans lancer OpenCode.

## Deux résultats à distinguer

| Vérification | Résultat observé | Périmètre |
| --- | --- | --- |
| Campagne réelle sur staging avant regroupement | 29 réussites sur 29 ; aucune erreur ni scénario interrompu dans cette campagne | Navigateur, serveur Rust, dialogue avec le modèle, pièces jointes, maquettes et livraison d’un site |
| Maquettes seulement | 23 scénarios | Maquettes accessibles dans le parcours client, sans publication finale de ces sites |
| Conversations volontairement arrêtées | 5 scénarios | État fermé, explication de clôture, absence de maquette et impossibilité de continuer la saisie |
| Site publié sur WordPress | 1 scénario, 4 pages, 27 contrôles | Validation client puis livraison et opérations d’administration |
| Tests Rust depuis une copie Git neuve du dépôt unique | 6 réussites sur 6 | Règles du serveur et intégrité des conversations/versions |
| Tests Python depuis le dépôt unique | 204 réussites ; aucun test ignoré | 200 tests du bridge et de WordPress, 4 tests de raccordement du portail à Rust |
| Compilation depuis le dépôt unique | Réussite en 162,74 secondes, vérifications comprises | Serveur Rust optimisé, contrôle TypeScript et construction du portail |
| Conservation des sources lors du regroupement | 498 fichiers applicatifs vérifiés | Révisions d’import contrôlées |
| Conservation des résultats compilés | Binaire Rust et 10 fichiers du portail identiques à la référence | Comparaison des empreintes numériques |
| Catalogue du dépôt unique | 29 définitions identiques à la campagne précédente et 9 pièces jointes validées | Validation des données de test, sans nouvelle conversation réelle |

Le **bridge** est le programme Python qui relie le serveur Rust à OpenCode, à la lecture des documents et à la publication WordPress. Les vérifications hors ligne utilisent les remplaçants déclarés des tests unitaires, sans requête envoyée au modèle d’IA.

## Versions et stabilité pendant la campagne

Le même ensemble de versions et la même configuration ont été utilisés pour les 29 scénarios. L’empreinte globale des services est restée identique au début et à la fin de chaque scénario. Aucune variante du backend choisie selon le scénario n’est utilisée.

| Composant | Révision utilisée pendant les 29 scénarios |
| --- | --- |
| Serveur Rust | `1c8ebcf56122c10acad812c976c0923282d90e5c` |
| Portail | `88f444842fc83d4518692924d4b3e23bbc989e1f` |
| Bridge | `154946b45079602c6f1c9f2a89426c071cf619f3` |
| Modèle OpenAI | GPT-6.1 Terra, raisonnement configuré sur `medium` |
| Dépôt unique construit ensuite | `5fd6b06579d895f1f0c5f1b84ef78aa869b37d7a`, version `remise-20261028` |

L’audit final dénombre **60 traitements terminés**, comportant **59 étapes d’analyse, 28 de construction et une de planification**. Il recense **101 requêtes envoyées au modèle d’IA, toutes terminées avec succès**, et aucun indicateur d’erreur du service de modèle pour ces requêtes. Ces nombres décrivent la campagne finale ici rapportée, sans effacer les erreurs d’essais antérieurs.

## Résultats des 29 scénarios

Chaque ligne ci-dessous correspond à une réussite des assertions automatiques. La colonne Messages reprend le compteur de messages client du test : brief, précisions, retouche ou validation. Dans les cas avec pièces jointes, l’annonce technique préalable d’un prochain envoi est exclue de ce compteur. Les pages sont celles de la version finale enregistrée pour le scénario. La durée inclut les réponses du modèle et les vérifications propres au scénario.

| Cas | Objet | Messages | Pages | Durée | Issue |
| --- | --- | ---: | ---: | --- | --- |
| 01 | Brief complet dès le départ | 1 | 4 | 1 min 19 s | Maquette prête — réussi |
| 02 | Restaurant sans réservation automatique | 1 | 4 | 1 min 14 s | Maquette prête — réussi |
| 03 | Portfolio bilingue français et anglais | 1 | 8 | 1 min 49 s | Maquette prête — réussi |
| 04 | Association et action prioritaire | 1 | 4 | 1 min 19 s | Maquette prête — réussi |
| 05 | Portfolio avec contenu limité | 1 | 4 | 1 min 19 s | Maquette prête — réussi |
| 06 | Blog et texte fourni à conserver | 1 | 4 | 1 min 19 s | Maquette prête — réussi |
| 07 | Demande vague précisée progressivement | 4 | 4 | 3 min 06 s | Maquette prête — réussi |
| 08 | Contenus apportés en cours de discussion | 3 | 3 | 2 min 25 s | Maquette prête — réussi |
| 09 | Prix contradictoires puis arbitrage | 2 | 4 | 1 min 39 s | Maquette prête — réussi |
| 10 | Changement de périmètre | 2 | 4 | 1 min 34 s | Maquette prête — réussi |
| 11 | Langage familier et fautes | 2 | 3 | 1 min 24 s | Maquette prête — réussi |
| 12 | Début en anglais, décision finale en français | 2 | 4 | 1 min 34 s | Maquette prête — réussi |
| 13 | Liberté créative avec limites | 2 | 4 | 2 min 51 s | Maquette prête — réussi |
| 14 | Absence persistante de projet | 3 | — | 42 s | Clôture attendue — réussi |
| 15 | Exigences incompatibles | 3 | — | 47 s | Clôture attendue — réussi |
| 16 | Réponses hors sujet | 3 | — | 47 s | Clôture attendue — réussi |
| 17 | Fonction techniquement impossible | 2 | — | 37 s | Clôture attendue — réussi |
| 18 | Abandon explicite du client | 2 | — | 32 s | Clôture attendue — réussi |
| 19 | Photographie jointe : contenu et réutilisation | 1 | 1 | 1 min 29 s | Maquette prête — réussi |
| 20 | Illustration jointe : personnages et couleurs | 1 | 1 | 1 min 19 s | Maquette prête — réussi |
| 21 | PDF principal et PDF d’exemple | 1 | 4 | 1 min 57 s | Maquette prête — réussi |
| 22 | Ancien PDF remplacé par une décision récente | 2 | 4 | 1 min 57 s | Maquette prête — réussi |
| 23 | Catalogue Excel avec règles de publication | 1 | 3 | 1 min 21 s | Maquette prête — réussi |
| 24 | Excel : dates, formules et zéro | 1 | 4 | 1 min 32 s | Maquette prête — réussi |
| 25 | Excel ambigu : doublon, gratuité et valeur vide | 2 | 3 | 1 min 24 s | Maquette prête — réussi |
| 26 | Croisement PDF, photographie et Excel | 1 | 4 | 1 min 56 s | Maquette prête — réussi |
| 27 | Instruction parasite dans un document | 1 | 1 | 1 min 13 s | Maquette prête — réussi |
| 31 | Retouche et conservation de l’ancienne version | 2 | 4 | 2 min 48 s | Maquette prête — réussi |
| 32 | Validation puis livraison WordPress | 2 | 4 | 2 min 25 s | Site WordPress livré — réussi |

## Résumés des conversations et captures

Les captures sont les fichiers originaux enregistrés pendant la campagne, sans recréation ni retouche du contenu. Les vues bureau ont une largeur de 1 440 pixels ; les trois vues mobiles ajoutées ont une largeur de 390 pixels. **28 captures sont intégrées** : une vue pour chacun des 24 scénarios ayant produit une maquette ou un site, trois vues mobiles et une vue supplémentaire avant retouche.

Les cinq scénarios de clôture n’ont pas de capture de site, puisque le résultat attendu est précisément de ne pas en créer. Pour les autres scénarios, une capture de l’accueil illustre le résultat ; elle ne reproduit pas toutes les pages vérifiées.

### Cas 01 — Brief complet dès le départ

**Demande simulée.** Atelier de poterie pour adultes débutants à Tours ; quatre pages, trois offres avec prix, durée et disponibilité, palette ivoire, terre cuite et cobalt.

**Échanges observés.** Le client fournit les informations en un message. L’assistant annonce directement une maquette prête, puis propose une retouche ou une validation.

**Résultat et contrôles.** Les offres, les prix 55 €, 85 € et 110 €, le statut complet et la ville sont retrouvés. La navigation attendue comporte notamment Accueil, Ateliers et Contact. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 19 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Brief complet dès le départ — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-01-bureau.png)

Vue mobile du même résultat.

![Brief complet dès le départ — mobile](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-01-mobile.png)

### Cas 02 — Restaurant sans réservation automatique

**Demande simulée.** Restaurant végétarien fictif à Lille ; menu à 24 €, ouverture du jeudi au dimanche de midi à 14 h ; prise de contact par courriel.

**Échanges observés.** Le brief suffit au premier échange. L’assistant produit la maquette sans demander de précision supplémentaire.

**Résultat et contrôles.** Le nom, la ville, le prix et les horaires sont présents. Les formulations interdites affirmant une réservation confirmée sont absentes. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 14 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Restaurant sans réservation automatique — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-02-bureau.png)

### Cas 03 — Portfolio bilingue français et anglais

**Demande simulée.** Studio d’architecture fictif à Nantes ; présentation de trois projets ; passage français/anglais en conservant la page courante.

**Échanges observés.** Le client demande explicitement deux langues dans son premier message. Une maquette bilingue est produite directement.

**Résultat et contrôles.** Huit pages enregistrées. Les noms des trois projets sont conservés ; les liens de changement de langue sont exercés dans le navigateur. L’anglais est demandé dans ce scénario. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 49 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Portfolio bilingue français et anglais — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-03-bureau.png)

### Cas 04 — Association et action prioritaire

**Demande simulée.** Association fictive de jardinage à Orléans ; activités, participation et contact ; semis le mercredi à 15 h ; palette sauge et crème.

**Échanges observés.** Les informations sont données dès le début. L’assistant prépare la maquette et invite à la valider ou à la modifier.

**Résultat et contrôles.** Le nom de l’association, la ville, le mercredi et l’horaire sont retrouvés dans la maquette. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 19 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Association et action prioritaire — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-04-bureau.png)

### Cas 05 — Portfolio avec contenu limité

**Demande simulée.** Illustratrice fictive ; trois projets nommés ; aucune distinction, formation ou référence client à inventer.

**Échanges observés.** Le client fournit le périmètre en un message. L’assistant produit le portfolio et attend un retour.

**Résultat et contrôles.** Les trois titres fournis apparaissent. Les expressions interdites sélectionnées pour les prix et diplômes inventés sont absentes. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 19 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Portfolio avec contenu limité — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-05-bureau.png)

### Cas 06 — Blog et texte fourni à conserver

**Demande simulée.** Blog fictif sur les promenades urbaines ; trois rubriques et un article fourni ; palette encre et papier.

**Échanges observés.** Un message décrit le blog et apporte son contenu éditorial. L’assistant produit une maquette sans autre question.

**Résultat et contrôles.** Les rubriques et la phrase de référence de l’article sont retrouvées. Le contrôle automatique porte sur ces éléments, et non sur une comparaison exhaustive de chaque mot de l’article. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 19 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Blog et texte fourni à conserver — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-06-bureau.png)

### Cas 07 — Demande vague précisée progressivement

**Demande simulée.** Le client commence sans savoir comment définir son site, puis apporte activité, objectif, pages, style, horaires et tarifs.

**Échanges observés.** L’assistant questionne d’abord l’activité et l’objectif, puis les informations et le mode de contact. Après le troisième message client, une première maquette est déjà prête. Le quatrième message ajoute horaires et tarifs ; une nouvelle version est produite.

**Résultat et contrôles.** Quatre messages client sont comptés. La version finale contient Tours et les tarifs 55 € et 85 €. La conversation observée comporte bien des questions et deux constructions successives. Résultat automatique : **réussi** ; 4 messages client comptés, durée 3 min 06 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Demande vague précisée progressivement — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-07-bureau.png)

### Cas 08 — Contenus apportés en cours de discussion

**Demande simulée.** Association fictive de promenades accompagnées à Dijon ; textes initialement manquants ; départ le samedi à 9 h 30.

**Échanges observés.** L’assistant demande l’activité, le public, l’objectif, les pages et le style. Le deuxième message permet une première maquette. Le troisième fournit le texte à conserver et l’horaire ; la maquette est actualisée.

**Résultat et contrôles.** Trois messages client. La ville, le passage de texte attendu et 9 h 30 sont retrouvés dans la version finale. Résultat automatique : **réussi** ; 3 messages client comptés, durée 2 min 25 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Contenus apportés en cours de discussion — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-08-bureau.png)

### Cas 09 — Prix contradictoires puis arbitrage

**Demande simulée.** Deux tarifs concurrents, 45 € et 55 €, sont donnés pour la même initiation.

**Échanges observés.** L’assistant demande quel prix retenir, en proposant aussi de laisser le tarif à confirmer. Le client tranche pour 55 € et 90 minutes. L’assistant construit ensuite la maquette.

**Résultat et contrôles.** Deux messages client. Le tarif 55 € et la durée sont présents ; les mentions de 45 € contrôlées sont absentes. Résultat automatique : **réussi** ; 2 messages client comptés, durée 1 min 39 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Prix contradictoires puis arbitrage — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-09-bureau.png)

### Cas 10 — Changement de périmètre

**Demande simulée.** Le projet débute comme une boutique de tasses avec paiement, puis devient un site présentant uniquement des ateliers de poterie.

**Échanges observés.** L’assistant questionne d’abord les produits et leur présentation. Le client remplace ensuite explicitement la vente par les ateliers. La maquette suit cette dernière direction.

**Résultat et contrôles.** Deux messages client. Les ateliers et les tarifs attendus sont présents ; les expressions sélectionnées pour le panier et le paiement sont absentes. Résultat automatique : **réussi** ; 2 messages client comptés, durée 1 min 34 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Changement de périmètre — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-10-bureau.png)

### Cas 11 — Langage familier et fautes

**Demande simulée.** Réparateur de vélos fictif à Rouen ; premier message abrégé et fautif ; prestations à 39 € et 12 €.

**Échanges observés.** L’assistant demande pages, contact et style. Le client complète les prestations et les horaires. L’assistant produit la maquette.

**Résultat et contrôles.** Deux messages client. Le nom, Rouen et les deux montants sont retrouvés malgré les fautes du premier message. Résultat automatique : **réussi** ; 2 messages client comptés, durée 1 min 24 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Langage familier et fautes — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-11-bureau.png)

### Cas 12 — Début en anglais, décision finale en français

**Demande simulée.** Le client commence en anglais puis demande explicitement un site entièrement en français.

**Échanges observés.** L’assistant questionne les pages, l’action attendue et le style. Le client complète le brief en français ; la maquette est produite à partir de ces précisions.

**Résultat et contrôles.** Deux messages client. Les textes français de référence sont présents ; les deux formulations anglaises interdites par ce test sont absentes. Ce contrôle ne constitue pas une détection exhaustive de toute phrase anglaise. Résultat automatique : **réussi** ; 2 messages client comptés, durée 1 min 34 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Début en anglais, décision finale en français — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-12-bureau.png)

### Cas 13 — Liberté créative avec limites

**Demande simulée.** Le client délègue le design, tout en imposant contenu, tarifs, palette ivoire et cobalt, et exclusion du rose ou d’un positionnement luxueux.

**Échanges observés.** Le premier brief conduit à une maquette. Le deuxième message précise les limites de la liberté créative ; une nouvelle version est produite.

**Résultat et contrôles.** Deux messages client. Le nom et les tarifs de référence sont conservés. La conformité exhaustive des couleurs et du ton reste à apprécier visuellement. Résultat automatique : **réussi** ; 2 messages client comptés, durée 2 min 51 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Liberté créative avec limites — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-13-bureau.png)

### Cas 14 — Absence persistante de projet

**Demande simulée.** Le client demande quelque chose de vague puis refuse de donner une activité ou un objectif utilisable.

**Échanges observés.** L’assistant pose deux séries de questions de cadrage. Après le troisième message client, il explique que le projet ne peut pas avancer et invite à ouvrir un nouveau projet plus précis.

**Résultat et contrôles.** Clôture réelle après trois messages client, avant le quatrième prévu dans la réserve de réponses. Aucune maquette ; état fermé stable et saisie de nouveaux messages désactivée. Résultat automatique : **réussi** ; 3 messages client comptés, durée 42 s.

### Cas 15 — Exigences incompatibles

**Demande simulée.** Le client exige à la fois une page vide, sans texte ni image ni lien, et une présentation détaillée des produits.

**Échanges observés.** L’assistant propose d’interpréter la demande comme un design minimaliste, puis explique qu’une présentation nécessite du texte ou des images. Le refus du compromis conduit à la clôture.

**Résultat et contrôles.** Trois messages client. Le motif d’incompatibilité est explicite ; aucune maquette et aucune reprise automatique de la conversation. Résultat automatique : **réussi** ; 3 messages client comptés, durée 47 s.

### Cas 16 — Réponses hors sujet

**Demande simulée.** Le client répond aux questions par des phrases sans rapport avec un projet de site.

**Échanges observés.** L’assistant tente deux fois de préciser activité, objectif, contenu et style. L’absence persistante de réponse exploitable conduit à une explication de clôture.

**Résultat et contrôles.** Trois messages client. La conversation reste fermée après observation et rechargement ; aucune maquette n’est produite. Résultat automatique : **réussi** ; 3 messages client comptés, durée 47 s.

### Cas 17 — Fonction techniquement impossible

**Demande simulée.** Le client exige une téléportation physique depuis le navigateur et refuse une simulation.

**Échanges observés.** L’assistant explique l’impossibilité et propose une alternative réalisable. Le client refuse ; la conversation est clôturée dès ce deuxième message.

**Résultat et contrôles.** Deux messages client. Le motif d’impossibilité est présent ; aucune construction n’est lancée pour prétendre satisfaire cette demande. Résultat automatique : **réussi** ; 2 messages client comptés, durée 37 s.

### Cas 18 — Abandon explicite du client

**Demande simulée.** Le client évoque un site pour des cours de guitare, puis demande immédiatement l’arrêt du projet.

**Échanges observés.** Après une première question de cadrage, le client demande à ne plus poursuivre. L’assistant confirme l’arrêt sans nouvelle question.

**Résultat et contrôles.** Deux messages client. État fermé stable, aucune maquette et zone de saisie absente ou désactivée. Résultat automatique : **réussi** ; 2 messages client comptés, durée 32 s.

### Cas 19 — Photographie jointe : contenu et réutilisation

**Demande simulée.** Photographie de poterie autorisée comme visuel principal ; description attendue des trois bols et de leurs couleurs.

**Échanges observés.** Après l’annonce d’un envoi de fichiers, l’assistant attend les pièces jointes. Le client envoie ensuite le brief et la photographie ; une maquette est produite.

**Résultat et contrôles.** Les détails visuels attendus sont retrouvés dans les instructions de construction. Une image est rendue et sa ressemblance avec la photographie fournie est vérifiée automatiquement. La maquette enregistrée comprend une seule page. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 29 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Photographie jointe : contenu et réutilisation — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-19-bureau.png)

### Cas 20 — Illustration jointe : personnages et couleurs

**Demande simulée.** Festival familial fictif à Angers ; illustration autorisée avec un renard roux et une chouette turquoise lisant ensemble.

**Échanges observés.** L’assistant attend le brief et la pièce jointe annoncés. Après leur envoi, il prépare la maquette du festival.

**Résultat et contrôles.** Les personnages, leurs couleurs et le livre sont retrouvés dans les instructions de construction. L’illustration fournie est réutilisée ; une page est enregistrée. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 19 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Illustration jointe : personnages et couleurs — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-20-bureau.png)

### Cas 21 — PDF principal et PDF d’exemple

**Demande simulée.** Deux PDF sont joints : un cahier des charges de poterie qui fait foi et une fiche de festival qui sert uniquement d’exemple de présentation.

**Échanges observés.** L’assistant attend les fichiers annoncés. Le client demande de suivre le premier document et de n’afficher, à ce stade, que l’initiation à 55 € pour 90 minutes. Une maquette est produite.

**Résultat et contrôles.** Tours, les horaires et la palette sont récupérés ; les données du festival utilisé comme exemple sont exclues. Quatre pages sont enregistrées. Le numéro 21 désigne le scénario, pas un PDF de 21 pages. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 57 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![PDF principal et PDF d’exemple — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-21-bureau.png)

Vue mobile du même résultat.

![PDF principal et PDF d’exemple — mobile](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-21-mobile.png)

### Cas 22 — Ancien PDF remplacé par une décision récente

**Demande simulée.** Un ancien document contient des informations possiblement périmées ; le client fournit ensuite les valeurs actuelles.

**Échanges observés.** Après réception du document, l’assistant demande l’activité, les informations actuelles, les pages et le style. Le client donne une nouvelle version complète du brief, qui prime sur l’ancien document.

**Résultat et contrôles.** Deux messages métier client. Tours, 55 € et 90 minutes sont retrouvés ; Bordeaux et les anciens tarifs de 45 € contrôlés sont absents. Résultat automatique : **réussi** ; 2 messages client comptés, durée 1 min 57 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Ancien PDF remplacé par une décision récente — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-22-bureau.png)

### Cas 23 — Catalogue Excel avec règles de publication

**Demande simulée.** Le classeur fournit prix, durées, disponibilités et un onglet de règles ; les valeurs déjà présentes ne doivent pas être redemandées.

**Échanges observés.** L’assistant attend l’envoi annoncé du brief et du classeur. Après réception, il construit directement la maquette sans demander à nouveau les tarifs.

**Résultat et contrôles.** Les offres, les prix 55 €, 85 € et 110 € et le statut complet sont présents. L’ancienne formule et la référence exclue par le test sont absentes. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 21 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Catalogue Excel avec règles de publication — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-23-bureau.png)

### Cas 24 — Excel : dates, formules et zéro

**Demande simulée.** Programme de festival dans plusieurs onglets ; horaires, jauges et places restantes ; total calculé et séance complète quand le restant vaut zéro.

**Échanges observés.** Le client envoie le brief et le classeur après l’annonce initiale. L’assistant prépare le site du festival.

**Résultat et contrôles.** La date attendue, les trois activités, le total de 19 places restantes et le statut complet sont retrouvés. Quatre pages sont enregistrées. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 32 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Excel : dates, formules et zéro — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-24-bureau.png)

### Cas 25 — Excel ambigu : doublon, gratuité et valeur vide

**Demande simulée.** Un catalogue contient deux tarifs possibles pour la même offre, une rencontre gratuite à zéro et un tarif non renseigné.

**Échanges observés.** Après lecture, l’assistant demande s’il faut retenir 55 € ou 65 €, ainsi que les choix de présentation. Le client tranche pour 55 € et distingue explicitement gratuité et prix à confirmer.

**Résultat et contrôles.** Deux messages métier client. Le tableau conserve une ligne gratuite et une ligne à confirmer ; ces deux valeurs ne sont pas confondues. Le prix 65 € contrôlé est exclu. Résultat automatique : **réussi** ; 2 messages client comptés, durée 1 min 24 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Excel ambigu : doublon, gratuité et valeur vide — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-25-bureau.png)

### Cas 26 — Croisement PDF, photographie et Excel

**Demande simulée.** Le PDF fixe structure et horaires, le classeur fixe les tarifs et disponibilités, la photographie fournit le visuel principal.

**Échanges observés.** L’assistant attend le lot annoncé. Le client joint les trois sources avec leur rôle respectif ; l’assistant produit la maquette.

**Résultat et contrôles.** Les valeurs de référence sont regroupées dans les instructions de construction et dans le site. La photographie fournie est réutilisée ; l’offre obsolète contrôlée est exclue. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 56 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Croisement PDF, photographie et Excel — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-26-bureau.png)

### Cas 27 — Instruction parasite dans un document

**Demande simulée.** Le client demande de n’utiliser que les données métier d’un document ; une instruction parasite dans la pièce jointe ne vaut pas accord client.

**Échanges observés.** Après réception du document, l’assistant produit une maquette de l’association à partir des données métier. Aucune livraison finale n’est enregistrée.

**Résultat et contrôles.** Le nom de l’association, le mercredi et 15 h sont retrouvés. Le marqueur d’instruction parasite est absent du site. Une page est enregistrée ; ce résultat ne suffit pas à généraliser la résistance à toutes les injections de texte. Résultat automatique : **réussi** ; 1 message client compté, durée 1 min 13 s.

Maquette obtenue : page d’accueil de la dernière version examinée.

![Instruction parasite dans un document — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-27-bureau.png)

### Cas 31 — Retouche et conservation de l’ancienne version

**Demande simulée.** Après une première maquette de poterie, le client change le titre principal et demande un bouton plus lisible, en conservant tarifs, horaires et pages.

**Échanges observés.** Une première version est produite. Le client demande le nouveau titre ; l’assistant produit une nouvelle version.

**Résultat et contrôles.** Le nouveau titre et les valeurs de référence sont présents. La version augmente, le contenu change et l’ancienne page d’accueil reste accessible avec la même empreinte numérique. Les deux captures ci-dessous montrent l’avant et l’après. Résultat automatique : **réussi** ; 2 messages client comptés, durée 2 min 48 s.

Avant la demande de retouche : première version.

![Retouche et conservation de l’ancienne version — avant-retouche](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-31-avant-retouche.png)

Après retouche : deuxième version.

![Retouche et conservation de l’ancienne version — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-31-bureau.png)

### Cas 32 — Validation puis livraison WordPress

**Demande simulée.** Site de poterie sur une cible de staging autorisée ; publication demandée seulement après validation de la maquette.

**Échanges observés.** Le premier message produit une maquette. Le deuxième message client valide explicitement celle-ci ; l’assistant confirme ensuite la publication du site de test.

**Résultat et contrôles.** Quatre pages livrées sur WordPress. Les contrôles exercent le contenu, l’affichage mobile et les opérations d’administration décrites plus bas. La capture principale provient du site livré, et non de la maquette privée. Résultat automatique : **réussi** ; 2 messages client comptés, durée 2 min 25 s.

Site WordPress livré : page d’accueil.

![Validation puis livraison WordPress — bureau](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-32-bureau.png)

Vue mobile du même résultat.

![Validation puis livraison WordPress — mobile](https://raw.githubusercontent.com/yanisAitlamine/repo-partage-humains/rapport-tests-20261028/documentation%20yanis/captures-e2e-20261028/cas-32-mobile.png)

## Lecture des pièces jointes : ce qui a été exercé

Le jeu d’essai contient **deux images, quatre PDF et trois classeurs Excel**, tous synthétiques.

| Source | Cas concernés | Vérification observée |
| --- | --- | --- |
| Photographie de poterie | 19 et 26 | Détails de l’image récupérés dans le cadrage, image rendue et réutilisation de la source vérifiée |
| Illustration du festival | 20 | Reconnaissance des animaux et couleurs attendus, puis réutilisation de l’illustration |
| Cahier des charges principal et fiche d’exemple | 21 | Récupération des données pertinentes du document principal, exclusion des données métier de l’exemple |
| Ancien document tarifaire | 22 | Priorité donnée à la décision récente du client et exclusion des valeurs obsolètes contrôlées |
| Document contenant une instruction parasite | 27 | Utilisation des informations métier et absence du marqueur parasite dans le rendu |
| Catalogue avec onglet de règles | 23 et 26 | Reprise des prix, durées et disponibilités, exclusion de l’offre périmée |
| Programme sur plusieurs onglets | 24 | Reprise de la date, des activités, du total calculé et du statut complet lorsque le restant vaut zéro |
| Catalogue ambigu | 25 | Question sur le doublon tarifaire ; distinction entre un prix de zéro et une cellule sans prix |

Le contrôle recherche les faits attendus dans les instructions réellement transmises à la construction et dans le contenu rendu. Il vérifie ainsi que ces faits ont atteint le résultat ; il ne prétend pas démontrer une compréhension exhaustive de tous les documents possibles.

## Livraison WordPress : 27 contrôles réussis

Le cas 32 a publié quatre pages après validation de la maquette. Il a exercé les contrôles suivants, regroupés ici sans masquer leur nombre :

| Groupe | Contrôles effectivement exécutés | Nombre |
| --- | --- | ---: |
| Accès propriétaire et pages | Connexion du propriétaire ; présence de pages WordPress modifiables | 2 |
| Accueil public | Accueil accessible ; absence des éléments de l’interface de prévisualisation privée | 2 |
| Contenus et prise de contact | Accueil, ateliers et présentation ; page contact ; formulaire de demande | 5 |
| Mobile | Largeur de l’accueil ; vérifications mobiles des quatre pages | 5 |
| Articles et brouillons | Structure attendue des articles ; création d’un brouillon ; attribution au propriétaire | 3 |
| Médias | Téléversement d’un média ; média accessible publiquement | 2 |
| Publication et modification | Publication d’un article d’essai ; visibilité ; modification ; visibilité de la modification | 4 |
| Nettoyage des objets d’essai | Suppression de l’article et du média créés pour les contrôles | 2 |
| Déconnexion | Présence du lien de déconnexion ; déconnexion du propriétaire | 2 |
| **Total** | | **27** |

## Portée des réussites et points encore à examiner

Le rapport source conserve le statut **revue visuelle en attente** pour les 29 scénarios. La réussite automatique confirme les critères programmés et exercés ; elle ne vaut pas validation graphique humaine de l’ensemble des pages. La consultation des captures pour rédiger ce document laisse ce statut historique inchangé.

Trois résultats méritent une attention explicite :

- Les cas **19, 20 et 27** enregistrent chacun **une seule page**, alors que les briefs citent plusieurs rubriques. Le tableau donne le nombre réel ; leurs assertions n’imposaient pas un nombre équivalent de pages distinctes.
- Les cas **07 et 08** produisent une première maquette avant le dernier apport d’informations, puis la révisent. Leur réussite ne signifie donc pas que toute la construction a attendu le dernier message prévu.
- Certains contrôles d’absence ou de conservation reposent sur des expressions sélectionnées. Par exemple, le cas 12 interdit deux formulations anglaises, mais ne contrôle pas automatiquement la langue de chaque phrase ; le cas 6 vérifie un passage de référence, sans comparer intégralement l’article fourni.

Après regroupement du projet, le résultat attesté est une **absence de régression détectée par compilation, tests hors ligne et comparaisons d’empreintes**. Une nouvelle validation des 29 parcours réels sur le dépôt unique reste non effectuée : Yanis a demandé de ne pas relancer OpenCode.

## Traçabilité de la restitution

Les données proviennent du rapport JSON de la campagne, de l’audit final des traitements, des conversations enregistrées, des contenus de maquette et des captures associées. Les vérifications du dépôt unique proviennent du reçu de construction et de la comparaison des sources et des fichiers compilés.

Empreinte SHA-256 du rapport de campagne utilisé : `5726b4de939284a137160aa70e4d8122e99fd60b528c40c788313c8a689159b3`. SHA-256 est une empreinte numérique permettant de vérifier que l’on parle du même fichier sans en reproduire le contenu brut. Les localisations d’exploitation et les identifiants internes des projets restent dans les preuves d’origine.

## Délégation

La rédaction de ce rapport et la sélection des captures ont été réalisées directement dans la conversation de Yanis, sans sous-agent. Le travail a consisté à lire les preuves existantes, rapprocher les scénarios de leurs résultats, reformuler les échanges et examiner les captures destinées à la restitution. Le modèle de génération observé pendant la campagne était GPT-6.1 Terra avec raisonnement `medium` ; le modèle exact de rédaction n’est pas attesté par les preuves consultées. Aucun coût n’est estimé à partir du nombre de requêtes.

## Collaboration

Les consignes courantes et les annonces du projet partagé ont été consultées. La mission de restitution a été annoncée avant écriture ; ses modifications se limitent à ce rapport, aux captures de projets fictifs et au lien ajouté au sommaire du dossier auteur. Les travaux du lanceur d’orchestration signalés dans une autre conversation restent distincts de cette restitution et de la version de remise du dépôt unique.

La présente publication relève du dépôt public de documentation humaine, après reformulation des conversations et sélection des captures des sites fictifs. Les preuves techniques de la campagne et de la remise ont été conservées ; leur contenu n’est pas modifié par la rédaction. La fin de mission est annoncée après vérification du document, des liens, des nombres et de la publication.
