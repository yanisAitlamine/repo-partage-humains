# Recette de migration de plusieurs blogs dans le lab

État du 22 octobre 2026 après reprise autorisée : le transport Gmail fonctionne
de nouveau et le cas client a été reçu réellement dans l’atelier. La génération
et la livraison restent suspendues avant leur premier appel modèle, après un
nouveau quota HTTP 429 d’Internet Archive lors de la recherche d’un document
source corrompu. La décision humaine demandée porte sur la poursuite avec cette
limite explicitement signalée. Aucun site n’a encore été livré par cette recette.

## Demande et résultat

La demande consiste à reprendre un cas comportant un PDF et quatre blogs,
à les regrouper dans un site administrable, et à vérifier la conservation des
articles, pages, photographies, audios, vidéos et fichiers accessibles. Le dialogue
doit se dérouler principalement par mail, avec un compte de recette distinct et
une cible explicitement choisie. Les corrections et essais sont limités au lab.

Le premier refus Gmail concernait un quota de requêtes par minute du projet
Google. Après autorisation humaine de reprendre et vérification de l’absence
d’envoi précédent réussi, deux réponses du connecteur client ont effectivement
été envoyées et reçues par le récepteur n 8 n isolé. La première a provoqué une
clarification ; la seconde a admis le PDF original et les quatre sites dans le
même événement natif. L’adresse du compte a été vérifiée depuis le jeton lu
dans sa boîte entrante authentifiée, avec destinataire et identité du mail liés.

Un défaut réel de consentement a été corrigé : demander de ne pas inventer une
biographie ou remplacer les articles par des résumés était interprété à tort
comme une interdiction de réutiliser les contenus. Le correctif conserve
l’autorisation positive obligatoire et le refus des vraies restrictions.
Le mail refusé n’a pas été réadmis ; une nouvelle réponse à la clarification
a emprunté normalement le parcours natif.

Le prompt seul ne pouvait pas assurer la migration : le modèle privé ne possède
pas d’outils de navigation et l’ancien lecteur ne conservait pas tout le corpus.
Les candidats ajoutent une collecte publique bornée en amont, la conservation
privée des originaux, leurs empreintes et leur provenance, puis un import complet
déterministe dans le CMS. Les prompts n 8 n demandent cette fidélité explicitement.
L’extrait de conception reste nommé et borné ; il ne remplace pas les articles.
Le stockage temporaire par projet est nettoyé après conservation durable vérifiée.

La première archive liée au vrai événement client contient 190 pages HTML,
dont 14 articles, quatre flux RSS et 687 références de ressources. Elle comprend
634 entrées téléchargées, correspondant à 604 fichiers distincts et environ 838 Mo.
Les empreintes, modes privés et liens de provenance réciproques ont été vérifiés.
Les inventaires opérateur antérieurs restent conservés séparément et ne sont
jamais présentés comme des sources client.

Une révision distincte, conservée sans écraser cette archive, comporte 194 HTML,
636 entrées téléchargées et 606 fichiers médias distincts, soit environ 839 Mo.
Elle ajoute quatre URL de pages d’accueil réellement interrogées, aux octets
identiques aux racines, récupère un logo après qualification de sa redirection
exacte, et conserve une image historique retrouvée avec date et preuve de
capture. Le contrôle indépendant retrouve les 14 articles des RSS ; les quatre
écarts initiaux des sitemaps sont désormais attestés par leurs propres réponses.
Les références externes sont qualifiées plus précisément :43 vidéos individuelles,
une playlist, une chaîne, un album et une dépendance de lecteur inerte.
Aucun album ou script n’est présenté comme une vidéo individuelle.

Cette révision est gelée avec qualification en échec : un fichier annoncé comme
document Word ne contient qu’un octet nul. Une nouvelle requête exacte a confirmé
HTTP 200, un contenu binaire d’un octet et l’absence de structure ZIP/DOCX valide.
Les quatre autres documents Word sont valides. Le fichier corrompu reste conservé
comme preuve ; il n’est ni importé comme document valide ni remplacé par un autre.

La recherche publique exacte de ce document a rencontré HTTP 429 sur le service
d’archives ; les requêtes d’index exactes n’ont renvoyé aucun candidat. Aucune copie
valide n’a été récupérée. La séquence de recherche avait encore exécuté ses
requêtes restantes après le premier 429 ; ce dépassement de la consigne d’arrêt
est identifié. Tous les appels concernés sont désormais arrêtés. Un résultat
inconclusif sous quota ne prouve pas qu’aucune archive du document n’existe.

Les autres limites restent visibles : deux PDF d’origine répondent 404, deux
anciennes références d’images ne sont pas récupérées après délai réseau ou
échec DNS, et quatre occurrences de liens relatifs sont malformées. Les photos
effectivement affichées sur la page concernée ont été téléchargées ; aucune
identité entre celles-ci et les anciennes références n’est supposée. La copie
historique retrouvée est distinguée d’un fichier actuel. La couverture reste
partielle et aucune migration exhaustive n’est affirmée.

Les corrections d’import préservent extension, type et nom de téléchargement
des documents, avec URL de stockage déterministe. Les noms Unicode sont conservés
dans le téléchargement et le titre, sans casser les URL. Six SVG sont qualifiés
comme définitions de polices et un comme décoration ; leurs originaux sont
conservés sans exécution. Les preuves d’indisponibilité sont liées à la ressource,
au projet, à l’événement et à l’archive d’origine. Une future poursuite avec limites
demandera aussi les décisions natives du client fictif sur chaque URL concernée.

L’adaptateur candidat prépare un vrai WordPress, la correspondance de chaque
source vers sa destination, le contrôle des octets par HTTPS et la recette
propriétaire de publication/modification avec image, audio et vidéo. L’import,
cette recette, la revue visuelle et la livraison réelle n’ont pas encore eu lieu.
Les sources restent candidates ; aucun déploiement de production n’est annoncé.

Avant l’attente humaine, le récepteur et le lecteur PDF de campagne ont été
désactivés, leur original a été vérifié inchangé, le runtime a été arrêté et
l’interface normale du lab restaurée avec HTTPS 200. Sa base et son projet livré
précédent restent préservés. Le nouveau projet et son unique analyse en attente
sont conservés dans un checkpoint privé ; aucun appel modèle du cas n’a commencé.
La nouvelle cible n’a reçu aucun CMS ou contenu de cette recette.

## Orchestration et délégation

Le parent a repris les trois sous-agents internes chargés du collecteur et de
l’inventaire, des sources/prompts n 8 n, puis de l’import WordPress. Les tâches ont
été réparties par fichiers et coordonnées par copies d’audit privées. Des
sous-revues ciblées ont vérifié la révision, les SVG et références externes.
Une demande supplémentaire de revue a été refusée par la limite de threads ;
elle n’est pas présentée comme une revue exécutée.

Le parent a conduit les vrais échanges Gmail, vérifié les reçus et l’identité
du compte, qualifié le PDF natif, examiné les types et noms des ressources réelles,
et corrigé les reprises et contrôles du runtime. Ses revues ont relevé des écarts
entre fixtures et corpus réel : SVG de police, album Vimeo, script de lecteur,
noms Unicode et document Word invalide. Les correctifs ont été revus avant toute
installation ; aucun score, reçu client ou résultat de livraison n’est fabriqué.

La reprise préparée reste limitée à un job initial jamais réclamé et cinq sources
encore en attente. Elle refuse tout travail déjà demandé, ancien appel modèle,
admission d’archive, résultat, revendication de job ou effet final. La revue
indépendante a corrigé la liaison à l’identifiant natif du reçu et la recherche
des preuves dans les sous-dossiers. Un état de notification supprimé sans envoi
est distingué d’un envoi incertain. Le contrôle des métadonnées du checkpoint réel
passe ; cela ne qualifie pas le contenu de l’archive corrompue.

Les 44 tests de reprise, reçus et cycle de vie du parent passent ;18 tests ciblés
du lecteur passent. Les 47 tests d’import/publication et 23 tests de récupération,
types et rôles passent, avec deux helpers PHP syntaxiquement valides. Les 14 tests
de transfert UI antérieurs restent inchangés. Les contrôles du collecteur et
contrats n 8 n ont également été effectués. Ces résultats isolés ne constituent
ni une génération réelle ni un CMS livré.

Le parent et les sous-agents sont configurés comme gpt-6.1-sol, avec héritage
sans changement explicite de modèle. Le préflight natif de première phase utilisait
openai/gpt-6-luna ; aucun appel de ce modèle n’a encore traité le cas client.
Aucune session OpenCode depuis PIAgentControl ni modèle local de remplacement.
Les sources et preuves ont été conservées en privé, avec séparation des
modifications préexistantes. Aucun coût ou gain n’est inventé.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche de reprise, le protocole partagé, les annonces
pertinentes et les passations du portail, des sources et du transport mail ont
été consultés. Les réservations couvrent les dossiers nouveaux et les seuls
fichiers existants nécessaires. Les travaux concurrents, la production et le
site livré précédent sont préservés ; aucun ancien rôle réservé n’a été exécuté.

Le corpus réel a fait évoluer la méthode : extraction HTML/CSS, lecteurs audio,
originaux volumineux, redirections de CDN, index équivalents et liens historiques.
Les contrôles utilisent les empreintes et les URL observées, sans déduire une
équivalence à partir d’un nom ou réparer une destination supposée. Une copie
historique n’est pas un téléchargement actuel, et un type annoncé par un serveur
n’est pas une validation de format.

La reprise du transport a été autorisée explicitement. Le nouveau refus du
service d’archives a déclenché une demande humaine distincte conformément à la
règle du projet sur les quotas. Le contrat du document corrompu reste une
proposition non admise. La suite attend cette décision, puis une archive finale
qualifiée, les décisions client natives, la génération/revue et la recette
fonctionnelle réelle. L’interface normale et les données existantes restent
disponibles pendant cette attente.
