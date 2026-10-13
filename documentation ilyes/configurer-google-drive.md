> Version publique anonymisée ; détails d’exploitation réservés au Pi.

Copie n8n créée : DEV - Drive lecture seule - copie Ilyes paramètre privé à consulter sur le Pi. ID : paramètre privé à consulter sur le Pi. Importation vérifiée, inactive et non publiée ; 15 nœuds fonctionnels et 3 annotations. Aucun document Google réellement lu. Le texte ci-dessous décrit le candidat de départ avant importation.

# Candidat lecteur Drive — copie locale du 12 octobre 2026

Le JSON comporte 15 nœuds, un déclencheur manuel et uniquement des requêtes GET vers l’API officielle Drive. Aucun nœud Gmail, Telegram, OpenCode ou écriture de table. Aucun credential n’est renseigné. Il n’a pas été importé ni exécuté sur l’instance.

## Configuration requise avant essai réel


La configuration est volontairement bloquante par défaut : dans « Saisir lien », l’URL est vide et `authenticated_invitation_context` faux. Cette valeur ne doit devenir vraie qu’après une liaison vérifiée entre invitation, message Gmail, client et projet. Ce lecteur seul ne réalise pas cette liaison et n’installe pas une collecte automatique d’invitations.

### Parcours minimal dans n8n

1. Dans Credentials, créer **OAuth2 API**, nom « Google Drive personnel lecture seule ». Grant Type : **Authorization Code**. Ne pas choisir un credential d’un autre compte et ne pas modifier le credential Gmail actuellement utilisé.
4. Cliquer **Connect my account**, se connecter au compte Gmail destinataire du partage et vérifier le droit de lecture demandé. Ne jamais fournir de token dans le chat ni via le presse-papier à un script d’import de workflow.
5. Affecter ce credential aux trois HTTP Request du candidat. Essayer d’abord un document synthétique partagé avec ce compte dans la copie inactive. Une connexion OAuth réussie seule ne prouve pas l’accès au document : vérifier ensuite l’ID et les métadonnées retournées puis le texte réellement extrait.

Une clé API Google ne remplace pas cet OAuth pour un document privé. Le credential ne doit pas contenir de portée d’écriture. Ce guide prépare la configuration ; il ne prétend pas qu’elle est déjà réalisée.

## Capacités et limites

- Google Docs : export texte ; les réponses HTTP d’échec ne deviennent jamais du contenu lu. Limite officielle de l’export Google Workspace : 10 Mo. Couverture de tous les onglets, images et commentaires non vérifiée.
- PDF : téléchargement uniquement lorsque `canDownload === true`, taille connue positive jusqu’à 25 Mio (budget mémoire provisoire, pas une limite de pages), extraction avec le nœud officiel sans `maxPages`. Documents scannés sans texte demandent une voie OCR. Aucun vrai PDF de 100 ou 250 pages n’a été extrait par ce candidat.
- Texte découpé en lots ordonnés de 12 000 caractères, reconstruction identique vérifiée localement sur plus de 650 000 caractères. Aucun résumé IA n’est réalisé par ce lecteur.
- Autres formats, dossiers : statut explicite non pris en charge, sans prétendre les avoir lus.
- Aucun téléchargement par URL fournie par un document ; seules les URL API construites à partir d’un ID validé sont utilisées. Redirections désactivées, TLS conservé.
- Le texte documentaire est une donnée non fiable ; les instructions contenues dans un document ne donnent aucune permission et ne doivent pas être suivies par l’assistant aval.
- Compatibilité des paramètres HTTP/extraction avec la version exacte de l’instance, autorisation OAuth2 et comportement réseau restent à vérifier dans une copie inactive. Les tests locaux ne prouvent pas ces points.

## Sources officielles

- https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/
- https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.extractfromfile/
- paramètre privé à consulter sur le Pi
- paramètre privé à consulter sur le Pi
- paramètre privé à consulter sur le Pi

Pour régénérer et contrôler le candidat : exécuter `node build.mjs`, puis `node test.mjs` depuis ce dossier (les chemins sont relatifs au module). Ces commandes ne font aucun appel réseau.
