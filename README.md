# Repo partagé humains

Documentation publique du projet commun de Yanis et Ilyes. Les documents
présentent l'organisation, les décisions, les contrôles réalisés et leurs limites.
Les détails d'exploitation privés sont conservés sur le serveur Pi.

- [Documentation Yanis](documentation%20yanis/SOMMAIRE-PUBLIC.md) : architecture,
  continuité, reprise et historique des interventions.
- [Documentation Ilyes](documentation%20ilyes/SOMMAIRE-PUBLIC.md) : préparation
  des lecteurs Drive, évolution du projet et limites des essais.

## Trois espaces distincts

| Espace | Contenu | Accès |
| --- | --- | --- |
| Dossier partagé machine | Protocole des agents, annonces et copies de travail | Collaborateurs autorisés sur le Pi |
| Repo partagé humains | Documents publics vérifiés et anonymisés | Lecture publique GitHub ; contribution Yanis et Ilyes |
| Dossier partagé humain sensible | Documentation d'exploitation complète et catalogue confidentiel | Collaborateurs autorisés sur le Pi ; export éventuel vers un dépôt personnel privé explicitement autorisé |

Les valeurs secrètes restent dans les stockages privés des services du Pi.
Elles ne vont dans aucun dépôt Git, même privé, ni dans les messages partagés
ou les prompts. Chaque personne garde ses propres identités ; la coopération
passe par des permissions adaptées aux services et aux tâches.

## Lire les documents

Les rapports sont des états datés. Une préparation ou un test simulé ne prouve
pas un déploiement ou un fonctionnement réel. Les versions publiques sont
anonymisées et peuvent contenir des synthèses ; les originaux, procédures
d'exploitation, coordonnées et inventaires sont réservés à l'espace sensible.
Les PDF d'exploitation originaux ne sont pas publiés.
Les blocs de commandes historiques anonymisés sont explicatifs ; ils ne sont
pas des recettes directement exécutables sur la production.

Les candidats Drive d'Ilyes décrivent un développement et des essais : leur
présence ici ne les active pas dans la production. La première validation
Telegram et les évolutions courantes restent décrites par leurs preuves réelles.

## Contribuer

Avant d'intervenir dans les espaces partagés, lire le protocole et les nouvelles
annonces sur le Pi, publier l'intention et les fichiers concernés, puis vérifier
les modifications concurrentes. Après le travail, publier une fin explicite,
avec résultats, limites et réservations libérées, même après une interruption.

Chaque nouveau rapport comporte deux sections distinctes **Délégation** et
**Collaboration**. Elles donnent les sessions, rôles, modèles observés, chemins,
annonces de début et de fin, validations et limites. Ne jamais inventer une
preuve de conformité, de fonctionnement ou d'économie.

Avant une publication, relire le contenu et les liens, contrôler les données
sensibles et vérifier la visibilité du dépôt. Un fichier supprimé du dernier
arbre peut rester dans l'historique Git.
