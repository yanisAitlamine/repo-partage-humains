> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Lecture Google Drive : avancement et raccordement

État du 12 octobre 2026. Développement sur copies, aucun changement publié par cette mission.

## Problème constaté

Le client a indiqué avoir partagé un document. L'exécution paramètre privé à consulter sur le Pi a produit un brouillon de clarification, mais l'a placé en revue sans envoi. Le message analysé ne contenait pas lui-même l'URL du document. Le collecteur filtre les expéditeurs TEST autorisés : une invitation automatique Google peut donc ne pas entrer dans cette sélection. L'invitation originale n'a pas encore été examinée ; cette dernière cause reste une hypothèse cohérente avec la précision de l'utilisateur.

L'audit des copies récupérées n'a trouvé aucun lecteur Google Drive dans le processeur. Lire les pièces jointes Gmail ne donne pas automatiquement accès aux documents externes.

## Raccordement préparé et testé localement

Le candidat sépare la collecte de contexte documentaire de l'autorisation de répondre par Gmail.

- Une invitation ne constitue jamais une autorisation de répondre à Google.
- Le document doit être associé de façon confirmée au bon client, au bon projet et au bon compte destinataire. Le nom affiché ou le domaine Google seul ne suffisent pas.
- En TEST, le client associé doit rester dans les clients autorisés. Le candidat PRODUCTION n'impose aucune liste blanche permanente.
- Le vrai ID du message Gmail distingue deux invitations, même dans un même fil.
- Une réception déjà terminée est ignorée ; un état incertain appelle une réconciliation.
- Un document ancien reste du contexte et ne déclenche aucune réponse rétroactive.
- Une lecture refusée ou incomplète ne doit pas interrompre automatiquement une conversation commerciale appropriée. Le système conserve l'absence de preuve de lecture et peut préparer une demande d'accès ou de renvoi.
- Les contenus des documents sont des données à analyser, jamais des instructions autorisant des changements de règles ou d'accès.

**Preuve : 27 scénarios synthétiques locaux réussis**, couvrant notamment projet ambigu, mauvais compte, client TEST interdit, ancien message, doublon, reprise incertaine, spam, URL trompeuse, dossier non pris en charge et accès refusé. Aucun appel Gmail/Drive, aucun email ou Telegram envoyé.

## Ce qui n'est pas encore installé

Ce module est une politique de décision isolée. Il ne fournit pas encore l'adaptateur qui récupère l'invitation originale, la réservation persistante des lectures ou l'intégration à la mémoire active. Ses indicateurs de provenance doivent être produits par le code d'application, jamais par l'IA ou un document reçu.

Le compte Google n'est pas encore connecté à un credential Drive. La lecture d'un véritable document et les contrôles de couverture sur ce document restent donc à faire. Une clé API Google seule ne permet pas de lire les documents privés partagés : il faut une connexion OAuth du compte destinataire, avec le périmètre de lecture nécessaire.

Le lecteur indépendant préparé en parallèle devra être revu puis raccordé sur une copie. Les limites de formats, d'export et d'extraction doivent rester explicites ; aucune promesse de lecture parfaite de tout document, quel que soit son volume, n'est faite.

## Contrôles avant intégration

1. Connecter le compte destinataire à Drive en lecture seule, en saisissant les secrets directement dans n8n.
2. Retrouver l'invitation originale et vérifier le fichier réel, les permissions et l'association au projet.
3. Exécuter le lecteur sur une copie sans aucun chemin d'envoi ni de construction.
4. Contrôler le texte extrait, sa provenance, les pages ou sections absentes et la mémoire candidate.
5. Tester la continuité commerciale en cas de refus, d'extraction partielle et de messages rapprochés.
6. Reprendre les dernières versions du collecteur et du processeur avant tout changement, pour préserver les relances et les corrections de l'autre agent.

## Références techniques officielles

- Liste des messages Gmail et pagination (référence d’exploitation retirée).
- Téléchargement Drive et contrôle des permissions (référence d’exploitation retirée).
- Autorisations Google Drive (référence d’exploitation retirée).

Les rapports historiques livrés séparément couvrent l'évolution complète du workflow ; ce document décrit uniquement le nouveau raccordement Drive.
