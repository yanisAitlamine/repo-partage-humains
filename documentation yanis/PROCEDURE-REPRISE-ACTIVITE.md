> Documentation publique. Les paramètres réels, preuves privées et inventaires de secrets restent dans les espaces privés du Pi.

# Reprise après perte du serveur — procédure publique

## Préparer la reprise

Utiliser la dernière sauvegarde complète, chiffrée et vérifiée hors du Pi. Vérifier les autorisations et le point de récupération choisi. Annoncer la mission de reprise et ses réservations. Les inventaires, valeurs d'accès et commandes adaptées à la production restent dans les espaces privés.

Une copie Git permet de retrouver les recettes et documents ; elle ne contient pas le stockage n8n, les secrets ni les identités nécessaires à la restauration. Une sauvegarde conservée uniquement sur le serveur perdu ne permet pas de reprendre.

## Reconstruire une cible isolée

Préparer le système et le contrôleur Ansible. Relire les rôles, leur provenance et les limites de validation ; ne pas considérer une recette publiée comme déjà éprouvée. Utiliser une cible isolée et garder arrêtés les déclencheurs ou chemins pouvant produire des emails, notifications et constructions réels.

Restaurer données et configuration cohérentes, notamment l'identité de chiffrement originale requise pour les identifiants n8n. Restaurer aussi les comptes, groupes et droits, l'environnement d'agents, le protocole et les travaux partagés, ainsi que l'état TLS et les restrictions d'accès. Conserver les révocations les plus récentes lors de la reprise VPN.

Les fichiers de travail modifiables par d'autres comptes ne doivent pas être exécutés automatiquement avec les privilèges de l'opérateur. Les secrets bruts restent dans les stockages privés prévus ; ne jamais les recopier dans Git ou les messages de coordination.

## Reconstituer les dépendances actuelles

Inventorier séparément la pile n8n et son volume, les workflows publiés et connexions nécessaires, le proxy et ses filtres, le VPN et ses deux DNS, le bridge de construction, le worker Telegram et leurs états durables. Les adresses et fichiers précis sont dans la référence privée ; le catalogue fonctionnel est dans l’[architecture](ARCHITECTURE.md).

Le worker Telegram actuel utilise des modules provenant de plusieurs dossiers sources : réponse humaine, validation de maquette, blocages techniques, Jev, reprise immédiate et diagnostic. Une ancienne recette qui copie seulement le worker et un module ne reproduit pas cette installation. Reconstituer les dépendances, configurations privées et permissions sans créer un deuxième consommateur du bot.

Conserver les décisions humaines, les réservations, les envois confirmés et les états incertains. Une reprise ne doit ni rejouer toutes les anciennes réponses, ni réactiver des boutons terminés, ni renvoyer la réponse humaine. Les archives de mission sur le même serveur ne remplacent pas une sauvegarde indépendante.

## Recette sans effets externes

Vérifier intégrité des données, droits, disponibilité locale, DNS, HTTPS, accès autorisés et refus attendus. Vérifier séparément les refus réseau et les profils révoqués. Contrôler la mémoire, la file et les réservations d'envoi sans rejouer aveuglément un état incertain.

Tester les parcours applicatifs sur des fixtures et cibles autorisées. Distinguer extraction réelle d'un document, brouillon, confirmation humaine, envoi confirmé, construction et revue des artefacts. Une page HTTP accessible ne démontre pas toute la chaîne.

## Bascule autorisée

Traiter ensemble les changements d'adresse, domaine, certificats et connexions applicatives. Revalider les restrictions et cibles de test avant tout effet réel. Republier progressivement les workflows, avec une autorisation humaine couvrant les conséquences, et vérifier les nouveaux résultats.

Conserver un retour arrière et les preuves privées. Rendre compte des résultats et limites, puis clore les réservations. La réussite d'un déchiffrement ou d'un contrôle de configuration ne doit jamais être présentée comme une restauration complète validée.
