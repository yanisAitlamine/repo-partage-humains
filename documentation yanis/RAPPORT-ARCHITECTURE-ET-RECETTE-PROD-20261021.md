# Architecture actualisée et préparation de recette production — 21 octobre 2026

## Suite de la recette — après nouvelle instruction humaine

Le demandeur ordonne explicitement de vider le compte de recette sans sauvegarde
ni export. Le seul ancien projet et90 lignes associées sont supprimés de manière
transactionnelle après vérification de l'identité, de la propriété et de l'absence
de traitement actif. Les données des autres comptes et les barrières externes de
publication restent préservées. La liste du compte est vérifiée vide avant de
créer le nouveau projet ; l'ancienne ressource est introuvable.

Un nouveau client fictif est créé par l'API normale, avec cinq pages et un journal
administrable demandé pour la livraison finale. La liaison mail est revalidée
par le vrai challenge reçu. Le connecteur conserve réellement l'alias de recette
dans l'identité d'expédition ; une autre adresse déjà liée à un compte distinct
est correctement refusée, sans contournement ni nouveau paramètre OAuth.

Trois réponses Gmail sont admises par les workflows de production : brief,
confirmation d'une interaction et confirmation du récapitulatif. L'analyse
native aboutit et les autres décisions client sont confirmées dans le portail.
Une réponse tardive à une ancienne question est rejetée sans nouveau job. Le
navigateur réel vérifie connexion et conversation propriétaire chargée, absence
de débordement mobile et d'origine/écriture inattendue ; TLS et sandbox restent
actifs. L'accès anonyme au projet est refusé.

La maquette est ensuite en génération au dernier état accessible. **Une coupure
de transport empêche la suite : l'hyperviseur et la production ne répondent plus,
et leurs sessions VPN disparaissent du serveur.** Le serveur d'origine reste
accessible. La cause précise distante n'est pas établie ; aucun service, réseau
ou pare-feu n'est modifié pour tenter de la contourner.

Le résultat du job est désormais inconnu à distance : ni sa fin, ni une maquette,
ni une livraison ne sont attestées. Il faut relire l'état au retour du transport
avant toute autre décision ; aucun job n'est réarmé. L'association opérateur du
nouveau projet attend aussi la validation par mail exigée. Aucun mail annonçant
la réussite de production n'est envoyé. Les paragraphes de précontrôle initial
ci-dessous décrivent l'étape antérieure, désormais dépassée pour le nettoyage.

## Demande et résultat

La demande porte sur la remise au propre de l'architecture privée et publique,
les machines et leur rôle, les services et points d'écoute, les dépôts et leur
code, les flux de données et les workflows. Elle demande ensuite une recette
réelle sur la production et un hébergement TEST externe, puis un mail au
collaborateur uniquement après réussite. La cible initiale est remplacée par
une cible déjà admise pendant l'attente de validation ; les autres règles sont
maintenues.

La documentation privée donne maintenant une vue courante en tête : inventaire
d'adresses et interfaces observées, écoutes et services, proxy et réseaux,
catalogue des workflows actifs avec versions enregistrées/publiées, dépôts,
copies de travail et releases réellement exécutées, fichiers fonctionnels,
stockages et ordre logique de reprise. Les sections anciennes sont conservées
avec un avertissement de portée historique. Le guide des identités distingue
emplacement, producteur, consommateur et état vérifié, sans valeur secrète.

L'[architecture publique](ARCHITECTURE.md) et le
[guide des workflows](WORKFLOWS-PIPELINE-PRINCIPAL.md) décrivent les mêmes rôles,
composants et flux, avec schémas, tableaux, limites de preuve et catalogue du
code. L'inventaire réel d'accès, les identités, versions internes, coordonnées,
chemins d'exploitation et secrets restent privés.

Le rôle du serveur d'origine est clarifié : passerelle et production de secours,
avec automatisations neutralisées ; le véritable lab est une VM séparée.
Partager la release et certaines identités fournisseur ne réplique pas les
données. Les trois boîtes mail sont une organisation prévue, pas trois boîtes
créées ou trois connexions OAuth attestées. Un seul environnement consomme
automatiquement la boîte de production ; le lab utilise son connecteur de
recette sans Telegram. Plusieurs alias dans une même boîte ne suffisent pas.

Une règle de coordination réciproque est documentée : côté demandeur, un mail
de validation de l'agent du collaborateur doit précéder une modification de
production. Les accords humains distincts restent requis lorsqu'applicables.
Le silence ou une annonce de coordination ne remplace pas cet accord.

**Précontrôle de production, sans nouveau build.** Connexion normale du compte
de recette et liaison mail vérifiées, santé du portail et identité de la release
exécutée confirmées. L'accès SSH strict à la cible TEST existante, la canonicalité
de sa racine, le certificat HTTPS et l'identité des octets de son index passent,
sans écriture du site. Le registre de livraison existant est distinct du registre
de maquettes : chaque nouveau projet exige une association opérateur explicite.

Le compte contient encore une ancienne tentative terminale, sans livraison
finale. La version installée ne propose pas de route normale d'archivage ou de
suppression du projet permettant le nettoyage demandé avant une nouvelle recette.
Aucune suppression SQL, remise en file d'un ancien job ou modification de
configuration n'est utilisée pour contourner ce constat. La solution de compte
de recette est soumise au demandeur ; la validation par mail du changement
d'association minimal est demandée au collaborateur. Une autre admission de
cible reste séparément proposée et non appliquée.

**Aucun succès de recette production n'est annoncé à ce stade.** Aucun nouveau
job de génération ou site n'a été créé, aucun mail de réussite n'a été envoyé.
Les preuves de la recette lab antérieure conservent leur portée locale ; elles
ne sont pas présentées comme des preuves de ce nouveau parcours de production.
Les contrôles de cette mission sont des lectures réelles et une revue des
différences documentaires, pas une nouvelle suite de tests produit.

## Orchestration et délégation

Codex réalise directement l'inventaire, l'analyse des sources et des versions,
la rédaction et la relecture. Aucun sous-agent de collaboration ni session de
la base personnelle de contrôle n'est lancé. Aucun modèle de remplacement,
nouveau fournisseur ou rôle Ansible historique réservé n'est exécuté.

Les lectures utilisent l'identité personnelle existante et un transport
d'administration autorisé pour les métadonnées privilégiées de la VM de
production. Les accès de l'hyperviseur ne servent pas à lire les secrets ni à
ouvrir de nouveaux services. Aucun accès au poste Linux personnel n'a lieu.
Les demandes de coordination par mail portent sur des changements concrets,
non appliqués ; elles ne délèguent pas un nouveau développement ou une bascule.
Leurs copies d'audit lisibles sont conservées dans l'archive privée autorisée.

## Coopération et adaptation au contexte

Les consignes applicables, fiche de reprise, protocole partagé et annonces
récentes pertinentes ont été lus ; les passations et README ont été consultés
sur les composants concernés. L'intention de mission réserve les seuls
documents visés et les preuves privées ; une extension annonce la nouvelle
cible de recette choisie par le demandeur. Aucune réserve concurrente active
sur ces documents n'a été identifiée au dernier contrôle.

Les relevés distinguent source, installation et publication. Les checkouts
utilisateur modifiés sont conservés ; aucun commit global de code concurrent
n'est effectué. Le statut publié des workflows est lu dans leur version active,
et non déduit d'une description qui contient encore le mot « brouillon ».
Les invités sans information réseau disponible sont marqués non vérifiés.
Une anomalie d'adresse et une unité secondaire en redémarrage sont consignées
en privé, sans réparation hors périmètre.

Un problème de fins de ligne lors du transfert documentaire a arrêté la première
vérification avant commit. Les préimages sont conservées ; seules les deux
copies préparées par cette mission ont été normalisées en LF, avec contrôle
de leurs octets et revue des différences avant publication. Aucun service n'a
été redémarré pour la documentation. La suite de la recette reste conditionnée
aux prérequis et accords explicités ci-dessus.
