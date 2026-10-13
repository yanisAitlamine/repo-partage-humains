# Faisabilité : documents, images et données Google Drive

État du 14 octobre 2026. Audit documentaire et lecture des copies disponibles uniquement. Aucun accès Google, test n8n, envoi, changement de workflow ou implémentation réalisé pendant cet audit. Version publique relue par le responsable.

## Demande et résultat

La mission consiste à déterminer comment récupérer un cahier des charges partagé, ses images et ses données, sans confondre un fichier accessible avec un contenu réellement analysé ou conservé. L'implémentation future reste soumise à la validation humaine demandée dans la mission.

**Conclusion : réalisable avec l'accès OAuth personnel existant, mais pas encore intégré au dialogue commercial dans la copie actuelle inspectée.** Il faut compléter l'association fiable entre fichier et projet, le téléchargement des images et données, et leur conservation contrôlée. Une invitation automatique ne doit jamais devenir une autorisation de répondre au service Google.

### Ce qui est attesté

| Élément | Preuve disponible | Limite |
|---|---|---|
| Lecture d'un Google Doc privé | Ancien résultat d'exécution : export texte HTTP 200, 5 420 caractères, un lot complet | Pas de preuve de couverture de tout le document, aucune mise à jour mémoire |
| Politique d'association invitation/client/projet | 27 scénarios synthétiques historiques enregistrés | Adaptateur de collecte et réservation persistante absents de ce candidat |
| Premier lecteur Drive isolé | 83 assertions synthétiques enregistrées | Aucun Google ni PDF réel appelé dans ces tests |
| Lecteur structuré Docs/PDF | 313 assertions synthétiques enregistrées, import inactif vérifié de 19 nœuds sans références de credentials | Non exécuté nativement ; le scénario de 250 pages simulait une sortie, sans lire un binaire PDF |
| Pièces jointes Gmail dans le processeur actuel inspecté | Nœuds PDF, Excel, Office et analyse de photos présents | Présence de nœuds ne prouve pas toutes leurs capacités ni la réussite d'un fichier particulier |
| Drive dans le processeur actuel inspecté | Aucun HTTP Drive/Docs ni appel au lecteur Drive trouvé dans l'export récemment récupéré | Cette observation porte sur ce graphe ; elle ne constitue pas un audit de tous les services privés |

Les comptes ci-dessus sont ceux des résultats historiques relus, **pas des tests relancés aujourd'hui**. Les anciens rapports indiquant « compte Google non connecté » sont datés : la lecture réelle ultérieure les a dépassés. Le nouveau lecteur structuré reste cependant une copie séparée, sans raccordement commercial attesté.

## Chemin technique recommandé

1. **Identifier la source** : lien reçu dans un email commercial ou invitation récupérée dans un circuit documentaire séparé. Garder le véritable ID Gmail, l'heure de réception, le fichier attendu et l'association au projet. Si plusieurs projets sont possibles, demander une précision ; ne pas les fusionner d'après le seul nom du fichier.
2. **Résoudre les métadonnées via l'API** : ID, type MIME, taille, modification, état supprimé et capacité de téléchargement. Une erreur 403/404 est un accès non obtenu, pas une absence de besoin client. Conserver les clés de ressource nécessaires dans le traitement protégé, sans les publier. [Clés de ressource Google](https://developers.google.com/workspace/drive/api/guides/resource-keys).
3. **Lire selon le format** : fichiers binaires par téléchargement, documents Workspace par export ou API structurée adaptée. Contrôler `capabilities.canDownload`. Un PDF stocké sur Drive est téléchargé comme binaire ; l'export Workspace a une limite officielle de 10 Mo. [Téléchargements et exports](https://developers.google.com/workspace/drive/api/guides/manage-downloads).
4. **Conserver un résultat traçable** : manifeste et contenu autorisé dans le stockage du projet, lots ordonnés pour les textes longs, empreintes, couverture et erreurs explicites. La mémoire commerciale contient les faits et leurs références ; les images et originaux restent dans un stockage dédié.
5. **Continuer la conversation** : un fichier inaccessible ou partiellement lisible ne bloque pas une réponse possible à partir de l'email. Expliquer simplement l'accès ou le format manquant, sans prétendre avoir lu le contenu.

### Formats et périmètre

| Type | Solution proposée | Complément nécessaire |
|---|---|---|
| Google Docs | API Docs avec tous les onglets retournés ; extraction structurée | Vérifier API activée et parcours réel multi-onglets ; traiter les images séparément |
| PDF | Télécharger puis extraire texte et couverture | OCR pour pages scannées/mélangées, inventaire page par page et budget mémoire/temps |
| Photos JPEG/PNG/WebP | Télécharger le fichier original, vérifier contenu/type puis analyser si utile | Stockage durable associé au projet, réutilisation ultérieure par le constructeur ; lien temporaire seul insuffisant |
| SVG | Conserver comme ressource puis produire un aperçu sécurisé si nécessaire | Ne pas exécuter scripts, liens externes ou XML dangereux ; ne pas l'injecter brut dans le site |
| DOCX/PPTX/XLSX | Télécharger, décoder structure puis extraire textes, tableaux, médias | Couverture des diapositives/feuilles et extraction des images à implémenter/vérifier |
| Google Sheets | API Sheets ou export approprié | Ne pas assimiler un CSV unique à tout un classeur ; garder feuilles, types et limites explicites |
| Google Slides | API Slides ou export PPTX/PDF | Texte, notes, images et mise en page ne sont pas une seule preuve d'analyse exhaustive |
| CSV/JSON | Télécharger et parser avec schéma et limites | Aucun code exécuté, formules de tableur neutralisées lors des exports |
| Dossier Drive | Inventaire borné et paginé des enfants | Nouveau chemin : le lecteur existant rejette les dossiers ; profondeur, quotas, doublons et raccourcis à gérer |

La documentation n8n prévoit le téléchargement et la conversion de Docs, Slides, Sheets et Drawings. Cela fournit le transport, pas une garantie de compréhension de chaque contenu. [Opérations fichier n8n Drive](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.googledrive/file-operations).

Pour Google Docs, `includeTabsContent=true` permet de récupérer les onglets ; parcourir également leurs enfants. Le candidat existe déjà, mais images et commentaires ne sont pas couverts par son texte. Le scope Drive en lecture seule est accepté par `documents.get`. [Onglets Docs](https://developers.google.com/workspace/docs/api/how-tos/tabs), [documents.get](https://developers.google.com/workspace/docs/api/reference/rest/v1/documents/get).

Pour un dossier, poursuivre les `nextPageToken` jusqu'à leur absence et signaler `incompleteSearch`. Ne pas considérer une première page de résultats comme un inventaire complet ; les changements pendant la pagination peuvent nécessiter une nouvelle vérification. [files.list](https://developers.google.com/workspace/drive/api/reference/rest/v3/files/list).

## Permissions et protections

Conserver OAuth dans les credentials n8n, sans extraire ses secrets. `drive.readonly` autorise la consultation et le téléchargement des fichiers accessibles au compte, mais son étendue est large. Utiliser un compte dédié aux partages clients et limiter les fichiers traités par les associations métier. `drive.metadata.readonly` ne suffit pas pour le contenu. `drive.file` est plus restreint mais suppose que le fichier soit accordé à l'application, notamment via un sélecteur : ce n'est pas un remplacement automatique pour les invitations reçues par email. Aucun scope d'écriture n'est nécessaire. [Scopes Google Drive](https://developers.google.com/workspace/drive/api/guides/api-specific-auth).

Recommandations de conception propres à cet audit :

- Construire les URLs API à partir d'identifiants validés, sur domaines fixes ; ne pas suivre arbitrairement les liens du document ni transmettre OAuth à une URL externe.
- Les contenus et noms de fichiers sont des données non fiables. Ils ne peuvent définir les destinataires, modifier les protections ou approuver une construction.
- Réserver une lecture de façon persistante par projet, fichier et version observée. Une invitation répétée ne doit pas dupliquer les ressources ; une modification réelle du document doit produire un nouveau manifeste.
- Conserver SHA-256, taille, type détecté, version ou date de modification, source métier et couverture. Relire les métadonnées après téléchargement si une modification concurrente est possible. Une empreinte prouve l'intégrité des octets conservés, pas l'identité commerciale ni leur innocuité.
- Stocker les originaux dans un espace privé dédié au projet, avec durée de conservation et contrôle d'accès ; les fichiers d'exécution n8n ne sont pas à présumer comme archive durable.
- Limiter ressources et tentatives, pas arbitrairement le nombre de pages. « Plus de 100 pages » reste possible selon taille, OCR et contexte ; traiter par lots et signaler les parties non comprises.
- Préserver la liste TEST, la séparation des clients/projets, les envois incertains et le nouveau parcours maquette puis validation finale. Ce module ne donne aucun droit d'envoi ou de publication.

## Vérifications à réaliser après validation humaine

Un vrai Doc avec plusieurs onglets et dernière cellule identifiable ; des PDF textuels et scannés de 1, 50, 100 et plus de 100 pages ; images réutilisables dans un projet de test ; Office multi-feuilles/diapositives ; dossier paginé ; 403/404, clés de ressource, accès révoqué, modification concurrente ; invitations répétées et projets ambigus ; document contenant des instructions malveillantes ; preuve que le dialogue continue sans fausse affirmation lorsque la lecture échoue. Aucun de ces nouveaux essais n'a été effectué dans cette mission.

## Orchestration et délégation

### Délégation

Le responsable a confié un audit indépendant à l'agent `drive_feasibility_20261014`. L'agent a lu les preuves et candidats existants, inspecté le graphe commercial transmis par le responsable et consulté uniquement les documentations officielles Google et n8n. Aucun sous-agent supplémentaire lancé. Le modèle n'a pas été établi dans cet audit. Rapport local remis au responsable pour revue et intégration ; aucune publication GitHub par cet agent.

## Coopération et adaptation au contexte

### Collaboration

STATE, PROTOCOL et AGENTS du dépôt ont été lus par SSH personnel. La levée du gel et sa fin ont été lues avant l'intention propre d'audit ; la nouvelle architecture après correction est préservée. Intention publiée sous session déclarative locale ; nouvelle liste de messages consultée avant rédaction. Aucun fichier ou workflow distant réservé pour modification. Les seuls livrables appartiennent au dossier local attribué à cet agent ; aucune source d'un autre agent modifiée. La fin de mission libère cette réservation documentaire et cite l'intention correspondante. Les références précises privées de preuves et de coordination sont communiquées séparément au responsable, sans données clients dans le rapport public.