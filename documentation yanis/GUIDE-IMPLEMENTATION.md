# Redéployer le site web et le dashboard

Le site client et le dashboard sont deux applications distinctes. Le site utilise des workflows web dédiés ; la chaîne mail garde ses propres workflows. Réinstaller une application ne restaure aucune base et ne republie aucun workflow.

## Choisir les fichiers

| Besoin | Fichiers à récupérer | Effet |
| --- | --- | --- |
| Étudier le portail | [Code public du portail](https://github.com/yanisAitlamine/atelier-portal-public). | Produit et exemples ; aucun accès ni donnée de production. |
| Redéployer le portail | Source privée à la release approuvée, recette Ansible, configurations privées existantes. | Installe serveur et interface, redémarre le portail, recharge le proxy si nécessaire. |
| Redéployer le dashboard | Source privée à la release approuvée et recette dédiée. | Installe et redémarre le dashboard ; conserve son stockage. |
| Retrouver comptes et historiques | Archives chiffrées indépendantes et clé correspondante. | Restaure les données selon la [procédure de reprise](PROCEDURE-REPRISE-ACTIVITE.md). |
| Retrouver les sites hébergés | Sauvegarde de l'hébergement. | Restaure les fichiers distants ; la sauvegarde du serveur d'orchestration ne les contient pas. |

## Commandes de déploiement

Le guide privé `GUIDE-IMPLEMENTATION.md` fournit les SHA, chemins, variables d'intégration et commandes complètes de la production. La forme des appels est :

```bash
# Dans le checkout exact du portail, après compilation.
ansible-playbook -i localhost, -c local Ansible/deploy.yml \
  -e portal_release=SHA_APPROUVE

# Dans le checkout exact du dashboard.
ansible-playbook -i localhost, -c local Ansible/deploy.yml \
  -e observatory_release=SHA_APPROUVE
```

Remplacer les paramètres et ajouter les références de configuration depuis le guide privé. Ces exemples ne réinstallent ni n8n ni le réseau. Une source plus récente que la release exécutée doit recevoir son propre accord avant déploiement.

## Workflows du site

Le portail utilise une entrée dialogue/Drive/maquette et trois dépendances : lecture des sources, images et décision avec citations. Le support explicite reste séparé. Une sauvegarde complète de la base n8n conserve leurs IDs, versions et connexions. Les JSON seuls servent à une reconstruction partielle, avec import inactif et connexions à recréer.

Le brouillon et la version publiée peuvent différer. Une mise à jour API d'un workflow actif peut republier immédiatement : ne pas utiliser cet appel comme simple enregistrement. Le dernier correctif préparé du parcours web reste distinct de sa publication.

## Résultat à vérifier

Comparer release choisie et release exécutée, contrôler le service, son accès HTTPS privé et le refus d'accès anonyme aux données. Aucun envoi, construction de site ou traitement payant n'est nécessaire pour ces contrôles. Le redéploiement ne corrige pas à lui seul un défaut du workflow publié.

Les commandes opérationnelles réelles restent dans le dépôt privé ; ce guide public n'expose aucun inventaire d'accès. Les recettes dédiées et une restauration complète sur cible neuve ont des niveaux de validation différents.
