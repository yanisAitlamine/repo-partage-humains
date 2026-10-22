# Recette de migration de plusieurs blogs dans le lab

État du 22 octobre 2026 : le développement et les contrôles isolés ont avancé,
mais la recette complète par mail reste suspendue avant réception du cas client.
Le premier envoi client a été refusé par le connecteur Gmail avec HTTP 403 et
un quota de requêtes du projet Google explicitement dépassé. Aucun renvoi ni
changement de transport n’a été effectué. Une décision humaine a été demandée
conformément à la règle du projet sur les refus API.

## Demande et résultat

La demande porte sur la reprise d’un cas existant comportant un PDF et quatre
blogs à regrouper dans un site administrable. Le résultat attendu doit conserver
les articles, pages, vidéos, audios, photographies et documents accessibles,
avec une cible de recette explicitement choisie et un dialogue principalement
par mail. Le développement, les corrections et la recette sont limités au lab.

L’audit a établi que le PDF admis était déjà conservé dans le contexte, tandis
que les URL ordinaires n’étaient pas collectées par le parcours unifié. Le
collecteur historique lisait une page et un nombre réduit de liens et médias.
Le générateur privé n’avait pas d’outils de navigation : modifier son prompt
seul n’aurait donc pas permis une migration complète.

Les sources candidates ajoutent une collecte publique bornée, un inventaire
avec provenance et empreintes, le stockage temporaire privé par projet et la
conservation des originaux. Les prompts n8n demandent une fidélité explicite
aux ressources inventoriées. Un aperçu de conception reste limité à huit pages ;
l’archive complète doit être consommée séparément par un import déterministe
dans le CMS. Un extrait destiné à la conception est nommé comme tel et ne
remplace pas les articles d’origine. Une ressource inaccessible ou une borne
atteinte reste visible dans la couverture.

Un adaptateur de publication candidat prépare l’import intégral dans un vrai
WordPress, la correspondance source vers destination, la vérification des
fichiers et la recette de l’administration propriétaire. Son exécution finale
n’a pas eu lieu. Le récepteur de campagne et le lecteur PDF natif ont été créés
isolément puis désactivés ; leur récepteur original est resté inchangé.

Les effets réels attestés avant suspension sont la création d’un compte de
recette distinct, la confirmation du drapeau mail dans l’application et la
réception observée de deux notifications, l’admission technique de la cible vide
et un préflight du moteur
API natif. Celui-ci a répondu avec le modèle configuré openai/gpt-6-luna.
Aucune analyse, génération de site ou revue créative par ce moteur n’a commencé.
Les premières notifications ont été classées en spam puis remises dans la
boîte de réception. La première confirmation utilisait le jeton du courrier
sortant : elle ne prouve pas à elle seule le rattachement du jeton reçu côté
client. Le candidat exige désormais ce reçu entrant authentifié, lié au message
et au destinataire, avant confirmation ; cinq tests isolés couvrent ce garde.

L’interface normale du lab a été restaurée après arrêt du runtime de recette.
La base existante a été sauvegardée et son intégrité contrôlée ; l’accès HTTPS
normal a répondu 200. Aucun site existant, service de production ou ancien rôle
Ansible réservé n’a été modifié. La nouvelle cible reste vide.

Les tests ciblés couvrent l’admission des sources, les contrats n8n, les baux de
campagne, la fermeture du runtime, le collecteur et le compilateur d’import.
Ils ne constituent pas une migration livrée. Une collecte publique indépendante
est qualifiée séparément et n’est jamais présentée comme une source reçue par
mail ou admise dans le projet.

Le premier inventaire réel a atteint sa borne à cause des variantes d’adresses.
Ses preuves ont été conservées. Après correction du dédoublonnage et des ancres,
la seconde collecte compte 196 pages inventoriées, 687 références de ressources,
614 entrées de fichiers téléchargées correspondant à 586 fichiers distincts,
et 47 références vidéo externes. Les fichiers distincts représentent environ
835 Mo ; leurs empreintes et les liens de provenance ont été vérifiés.
La couverture reste partielle : deux documents d’origine répondent 404,
24 ressources externes sont refusées par la configuration des hôtes autorisés,
et sept pages renvoient un format refusé ou une erreur. Ces écarts restent dans
le manifeste. Cette collecte ne prouve donc pas une récupération intégrale.

## Orchestration et délégation

Codex a lancé trois sous-agents internes : inventaire et collecteur, admission
et prompts n8n, puis import et publication WordPress. Le premier a cartographié
les ressources et développé la collecte ; le deuxième a porté l’identité de
source, le scan et le contrat des prompts ; le troisième a préparé l’import,
les preuves et la recette propriétaire. Les responsabilités ont été séparées
par fichiers, puis soumises à des revues croisées.

Le parent a retrouvé le cas dans Gmail, lu et rendu les quatre pages du PDF,
vérifié le lab et la cible, préparé le compte protégé, le transport client et
le runtime isolé, exécuté les préflights et remis le service normal en place
après le refus Gmail. Il a corrigé un défaut de fermeture du bail de campagne
avec quatre tests de régression. Les revues ont aussi signalé des cas de
consentement négatif ou partiel, de texte transféré et de provenance orpheline.
Ces défauts ont été corrigés et couverts par des tests isolés avant admission.

Le modèle du parent est configuré comme gpt-6.1-sol ; les sous-agents ont été
lancés en héritant de cette configuration, sans changement explicite de modèle.
Aucune session OpenCode n’a été lancée depuis PIAgentControl. Les échanges
lisibles sont conservés sous forme de copies d’audit privées ; aucun
cryptogramme natif n’est présenté comme déchiffré. Aucun coût ni gain estimé
n’est déduit de ces opérations.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche de reprise, le protocole partagé, les
annonces pertinentes, les fins de mission de la livraison précédente et les
documents du portail, des sources et du transport mail ont été consultés.
L’état Git préexistant, les modifications natives Gmail et le travail parallèle
sur l’infrastructure ont été préservés. Les réservations ont porté sur les
nouveaux dossiers de collecte et de recette, ainsi que les seuls fichiers
existants nécessaires à l’admission des sources et aux prompts.

Les faits du lab ont modifié la méthode : les blogs utilisent Weebly, les
lecteurs audio et certaines photographies sont absents d’une simple extraction
de texte, et le corpus contient des fichiers volumineux. La collecte doit donc
examiner les ressources HTML et CSS, conserver les liens vidéo externes et
contrôler les fichiers d’origine. Les adresses avec et sans www et les pages
d’archives doivent être dédoublonnées sans fusionner des contenus qui possèdent
des médias différents.

Le refus du connecteur a interrompu le parcours mail avant le premier contenu
client admis. Les consommateurs temporaires ont été désactivés, les preuves ont
été conservées et les développements sans effet de mail ou de publication ont
pu être revus indépendamment. La reprise exige une décision sur le transport,
la vérification de l’envoi avant tout nouvel essai, puis un vrai événement
client liant le PDF et les quatre sources à l’archive. L’import final, le rendu,
l’administration et la livraison restent à exercer sur cette archive admise.
