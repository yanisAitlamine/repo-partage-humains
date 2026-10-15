# Restaurer les services après perte du serveur

La reprise utilise les fichiers du socle et ceux des ajouts récents d'une même maintenance. Git redonne le code ; les archives privées redonnent les comptes, données, accès et décisions.

## Fichiers à récupérer

| Fichiers | Résultat attendu |
| --- | --- |
| Sources et recettes aux versions choisies | Programmes et unités à installer. |
| Archive chiffrée du socle | n8n, base, clé maître et compléments réseau/accès prévus. |
| Archive chiffrée des ajouts | Portail, dashboard, archives lisibles, worker et sources locales. |
| Empreintes, métadonnées et clé correspondante | Vérification, déchiffrement et rétablissement des propriétaires. |
| Sauvegarde d'hébergement séparée | Fichiers et éventuelles données des sites distants. |

Une archive antérieure à l'ajout du portail et du dashboard ne peut pas restaurer leurs données. Sans ces fichiers, la reconstruction reste partielle.

## Ordre des commandes

La procédure privée `PROCEDURE-REPRISE-ACTIVITE.md` contient les commandes exactes, dans cet ordre :

1. Comparer les empreintes puis déchiffrer sur le poste opérateur. Aucun service modifié.
2. Transférer les archives par SSH vérifié vers une nouvelle cible isolée. Aucune clé privée transférée.
3. Extraire en préparation privée et recréer les identités correspondant aux propriétaires sauvegardés.
4. Installer le socle sans démarrage, puis restaurer le volume n8n vide avec sa clé d'origine.
5. Restaurer les compléments récents : code exécuté, bases du portail/dashboard, configurations et unités.
6. Garder les services métier bloqués, rapprocher les envois, décisions et jobs, puis ouvrir chaque capacité séparément.
7. Vérifier HTTPS privé et authentification, puis créer une nouvelle sauvegarde indépendante.

Chaque bloc précise son lieu d'exécution, pourquoi il est nécessaire et quels services ou fichiers il remet. Aucun déploiement ni test Ansible n'est exécuté par la lecture de la procédure.

## Workflows et effets externes

La base n8n complète conserve les workflows web et mail : aucun import supplémentaire n'est nécessaire. Si seuls les JSON survivent, importer inactif, recréer les connexions et vérifier les références ; ce n'est pas une récupération des données perdues.

Dépublier des workflows ne gèle pas toutes les exécutions déjà en attente. Garder les sorties isolées pendant le rapprochement. Un mail déjà confirmé envoyé ne doit pas repartir ; un état incertain ne devient pas un échec sans effet. Un ancien accord ne s'applique qu'à son résultat exact.

Le consommateur Telegram volontairement suspendu reste arrêté. Restaurer le dashboard conserve sa connexion propriétaire ; cela ne déchiffre pas les anciens messages opaques. Ne pas remettre une ancienne liste de révocation VPN à la place d'une plus récente.

## Vérification finale

Contrôler les versions exécutées, les données, les trois interfaces privées et les refus attendus. Le site hébergé peut avoir continué à évoluer pendant la panne : le comparer avant toute restauration distante.

Une lecture statique des commandes, une archive authentifiée et un exercice complet de restauration sont trois résultats distincts. Aucun exercice complet ni reboot restauré n'est revendiqué par cette mise à jour.
