> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# 1 — Chronologie depuis le début du workflow

## 1. Point de départ : export de 25 nœuds

Le projet part de l'export JSON d'un workflow n8n existant : lecture Gmail, analyse OpenAI, mémoire de projet, anti-doublon et routage des demandes. L'objectif initial était de rendre cet export compréhensible par un autre assistant puis de stabiliser la gestion des demandes `A_VERIFIER`.

Une représentation intermédiaire composée d'enregistrements JSON plats a été produite pour contourner la limite du parseur de pièces jointes. L'export original a également été conservé séparément. Le fichier intact contient toujours **25 nœuds** ; son empreinte a été recalculée lors de cette rédaction et correspond à celle consignée depuis le début :

`paramètre privé à consulter sur le Pi`

L'audit initial dénombrait **31 connexions**. Cette sauvegarde est la référence d'origine, pas le workflow TEST actuel.

Sources : `workflow-n8n-original-intact.json`, `workflow-n8n-intermediaire-plat.json`, `README-stabilisation-A_VERIFIER.md`.

## 2. Stabilisation de la revue persistante

Une branche dédiée a été ajoutée pour conserver les demandes ambiguës dans une file de revue : ID réel du message Gmail, conversation, projets candidats, preuves de rattachement, raison et état de revue. La recherche d'une ligne existante évitait d'écraser une décision humaine. La branche ambiguë ne fusionnait plus immédiatement ses données dans la mémoire du projet.

La première copie comportait **28 nœuds et 36 connexions**. Les tables réelles avaient été remplacées par des marqueurs de tables TEST afin d'empêcher une utilisation accidentelle. Une autre copie préparait la reprise après décision : continuation d'un projet, nouveau projet ou absence de traitement commercial.

Cette première étape était une validation locale, avant l'accès API authentifié. Les règles de dédoublonnage et de mémoire ont ensuite évolué : la règle initiale de marquage après mise en revue ne résume donc pas tous les chemins actuels.

## 3. De l'analyse à la réponse commerciale contrôlée

Le projet s'est élargi à un assistant capable de compléter un brief et de répondre au client. Une copie sandbox ajoutait la réponse proposée et une barrière avant Gmail, avec les envois désactivés. Une copie de **46 nœuds** puis une version de conversation réelle de **51 nœuds et 57 connexions** ont été préparées.

Les protections prévoyaient un expéditeur TEST strict, un contrôle du Reply-To, le refus des newsletters et automatismes, l'absence de réponse vide et une réservation d'envoi. La réservation devait précéder Gmail ; un succès devenait `SENT`, un résultat incertain `UNKNOWN`, sans renvoi aveugle.

Le projet a alors été organisé en étapes : stabiliser Gmail et la mémoire, valider le brief, puis seulement intégrer la maquette et la construction du site.

## 4. Accès API et premiers essais réels — 10 octobre 2026

L'accès n8n a été configuré avec une clé conservée dans le gestionnaire d'informations Windows, utilisée en mémoire par les outils. La clé n'a pas été incluse dans les exports de workflow.

La copie importée pour les premiers essais manuels réels avait **34 nœuds**, quatre tables TEST et un déclencheur manuel. La version locale de 51 nœuds et la copie importée ne sont pas le même fichier : le développement n'a pas suivi une simple augmentation continue du nombre de nœuds.

Le premier problème de sélection était concret : un ancien message déjà traité masquait un nouvel email lorsque Gmail ne renvoyait qu'un résultat. La recherche a été étendue à plusieurs messages et l'anti-doublon a été contrôlé sur **l'ID du message**, distinct de l'ID de conversation. L'historique existant a été conservé.

Les chemins d'envoi ont d'abord été déconnectés pour observer Gmail et OpenAI sans réponse réelle. Après autorisation, les échanges réels ont été limités aux adresses TEST admises.

## 5. Spam, périmètre métier et séparation TEST/PRODUCTION

Les tests ont montré que des demandes valides pouvaient arriver dans Spam. La collecte a donc été adaptée pour les voir, tout en séparant le dossier Gmail du jugement métier : une présence dans Spam n'est pas, à elle seule, une preuve de phishing ou de non-pertinence.

Deux profils ont été distingués : TEST conserve une liste de destinataires autorisés ; PRODUCTION doit pouvoir accueillir de nouveaux prospects après les filtres métier, anti-boucle et anti-phishing. La production n'a pas été ouverte par ces changements.

Des contrôles explicites ont limité les réponses aux demandes commerciales web claires. Les emails personnels, scolaires, administratifs, fiscaux ou hors activité restent sans réponse commerciale automatique. Les ambiguïtés sont revues. Le modèle classe le sens du message ; les contrôles déterministes vérifient la cohérence de ses sorties. Ils ne rendent pas la classification infaillible.

Une date de mise en service a été prévue pour interdire les réponses rétroactives aux anciens messages, tout en conservant le contexte déjà mémorisé.

## 6. Amélioration ciblée des réponses commerciales

Plusieurs essais ont fait évoluer la qualité des échanges : accueil plus naturel, réponses courtes mais complètes, absence de tarifs ou dates inventés et interdiction de révéler les processus internes au client.

Une branche spéciale devis écrasait la réponse contextuelle de l'IA par un texte fixe. Elle pouvait ignorer le délai et la maquette demandés dans le même email. La correction a conservé la réponse produite en contexte tout en maintenant les protections commerciales.

Le nouveau texte du client a reçu la priorité sur les citations d'anciens emails : une ancienne demande de prix ne doit pas réapparaître à chaque échange. Les demandes vagues dans un projet identifié appellent une clarification utile. Les conseils généraux sur le site restent distincts des prestations réellement confirmées.

La présentation des emails a également été aérée : courts paragraphes, questions lisibles et absence de retours forcés qui coupent les phrases sur mobile.

## 7. Lots de messages, réponse vide et mémoire des échanges

La copie manuelle a évolué vers le traitement de tous les messages admissibles d'un lot, du plus ancien au plus récent, avec relecture de la mémoire avant chaque analyse. La boucle des pièces jointes a été réinitialisée entre messages.

Une réponse commerciale vide ne devait plus être considérée comme un traitement réussi. Elle devenait une anomalie visible, sans envoi et sans inscription injustifiée dans les IDs traités. La confirmation Gmail et l'outbox devenaient les preuves de l'état sortant.

Une coupure temporelle de session TEST a ensuite empêché la sélection d'anciens échanges. À ce stade, la recherche restait limitée à un lot de 25 résultats : ce n'était pas encore une file exhaustive de production.

## 8. Identité du client, entreprise et préparation de la livraison

L'assistant recueillait bien les fonctions du site mais pouvait oublier le nom de la marque. L'identité a donc été enrichie progressivement : personne de contact, entreprise, projet de site et informations à confirmer ont été séparés logiquement dans la mémoire.

La collecte a été organisée en **trois étapes** : comprendre le besoin ; préparer une maquette avec des éléments provisoires autorisés ; finaliser les informations avant publication. Coordonnées publiques, contenus, identité visuelle, domaine, hébergement et informations légales sont suivis sans être inventés ni demandés tous ensemble.

Les faits confirmés, propositions, inconnues et changements de décision restent distingués. Une suggestion de couleur ne devient pas automatiquement une décision client. Cette séparation est logique dans la mémoire du projet ; elle ne constitue pas un fichier client global nouvellement déployé.

## 9. Lecture des pièces jointes

Une première évolution a ajouté PDF textuels, PowerPoint, Word, Excel, OpenDocument et formats texte, avec contrôles de taille, signatures et structure. Les limites initiales étaient strictes : notamment 20 pages PDF et plafonds de texte. Les formats illisibles ou partiels restaient signalés.

Les essais ont révélé qu'un PDF d'une page pouvait malgré tout bloquer la conversation. Une extraction partielle ou impossible ne devait pas empêcher de répondre aux autres points compréhensibles de l'email. Une nouvelle décision explicite pouvait remplacer une ancienne décision sans créer une contradiction artificielle.

Les travaux suivants ont testé des PDF synthétiques de **50, 100 et 250 pages**, ainsi que des images. Cela démontre ces fixtures, pas une lecture universelle de tous les documents, scans, tableaux ou mises en page. Les fichiers sont enregistrés dans un registre d'actifs ; leur archivage binaire durable reste à finaliser. Aucun antivirus n'a été installé par ces évolutions.

## 10. Gmail automatique et Telegram — 11 octobre 2026

Des copies automatiques ont ajouté Gmail Trigger, une relève complémentaire, une file persistante, le traitement en série, un verrou et un journal de notifications. Sept tables TEST isolent les états du parcours.


Les copies de préparation inutiles ont été sauvegardées avant nettoyage. La chaîne a été ramenée à un collecteur, un moteur commercial, un journal de notifications et un composant d'erreurs, avec des contrôles temporaires séparés.

L'activation TEST est documentée à **17 h 37 min 32 s, heure de Paris, le 11 octobre 2026**. Elle conserve une coupure empêchant le rattrapage automatique des anciens emails. Les essais de l'utilisateur se sont ensuite déroulés sans bouton manuel, avec réponses Gmail et notifications Telegram.

## 11. Fiabilité : raisonnement, reprises et régressions

Les défauts rencontrés ont conduit à séparer raisonnement commercial et mise en forme JSON, borner les réparations et reprises, distinguer questions prévues et réellement envoyées, et vérifier un nouvel ID Gmail avant de considérer une réponse comme envoyée.

Des tests de verrou concurrents ont confirmé un seul propriétaire dans le lot observé. Les tests conversationnels ont montré que la mémoire et les questions pouvaient encore dériver : des lots ont échoué malgré une exécution n8n verte. Les corrections récentes ont donc été développées sur copies et rejouées avec de vrais appels OpenAI dans un banc isolé, sans Gmail ni Telegram.

Les résultats ciblés **4293** corrigent des défauts observés dans **4232** ; ils ne prouvent pas que toutes les corrections sont déjà intégrées dans le workflow actif.

## 12. Liaison avec OpenCode développée par le collègue

Le collègue a ajouté le workflow de préparation, validation et lancement OpenCode. Le parent commercial lui transmet le projet et le contexte. L'utilisateur rapporte un site créé lors de leurs essais ; une page de démonstration accessible a aussi été observée.

Les audits ont relevé un contrat parent/enfant initial incomplet, des approbations répétées et une panne de formulaire OAuth2. Des corrections et une approbation simplifiée ont été préparées sur copies. Le collègue a ensuite fait évoluer son enfant de 17 à **25 nœuds**, avec contexte Gmail conservé et confirmation humaine avant notification de livraison. Les anciens patches ne doivent pas écraser sa version.

Une approbation Telegram a été préparée/importée en copie inactive, sans lancement OpenCode. Aucun parcours réel de clic Telegram jusqu'à construction n'est démontré. La réservation concurrente d'une décision a été testée sur une ligne fictive isolée ; elle n'est pas une preuve d'idempotence du backend entier.

## 13. Coordination sécurisée et nouveau chantier Google Drive — 12 octobre 2026

Un accès SSH personnel a été mis en place, distinct des accès du collègue. Les règles imposent lecture de l'état partagé, annonces de périmètre et préservation des modifications concurrentes. Les copies publiques ne se synchronisent pas seules avec les services exécutés.

Le dernier diagnostic porte sur un document partagé par invitation automatique Google Drive. La collecte TEST peut exclure l'expéditeur automatique ; le moteur examiné ne comporte pas de lecteur Drive. Un email de suivi commercial a produit un brouillon mais a été bloqué en revue. Cela ne prouve pas une lecture du document ni un envoi.

Les agents préparent maintenant une ingestion de contexte et un lecteur séparé sur copies, sans retirer les protections TEST ni modifier les prompts commerciaux réservés au collègue. **La lecture réelle du document Drive n'est pas encore opérationnelle.**
