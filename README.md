# Repo partagé humains

Documentation publique du projet commun de Yanis et Ilyes. Les documents
présentent l'organisation, les décisions, les contrôles réalisés et leurs limites.
Les détails d'exploitation privés sont conservés sur le serveur Pi.

**Organisation actuelle — décision de Yanis du 22 octobre 2026 : la production
applicative se déploie uniquement sur prod-1.** Le Pi assure seulement le load
balancer / reverse proxy HTTPS, le VPN et le DNS interne. Développement et
recette restent sur des VM de lab distinctes. L'ancienne obligation d'aligner
les applications entre Pi et prod-1 est remplacée.

Lire d'abord la [fiche de reprise](documentation%20yanis/REPRISE-AGENTS.md),
l'[architecture courante](documentation%20yanis/ARCHITECTURE.md) et les
[consignes agents](AGENTS.md). Les anciennes applications, sources et archives
encore présentes sur le Pi sont un état à traiter séparément : cette mise à jour
documentaire ne prétend pas les avoir déplacées ou retirées. Le [rapport de
clarification](documentation%20yanis/RAPPORT-PRODUCTION-UNIQUE-20261022.md)
explique les points d'entrée corrigés.

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

Les valeurs secrètes restent dans les stockages privés de leurs services.
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

## Nouvelle organisation documentaire — 13 octobre 2026

Tous les nouveaux rapports sont publiés ici, après anonymisation et contrôle,
dans le dossier de leur auteur. Chaque rapport décrit la demande et le résultat,
l'orchestration et la délégation, puis la coopération et l'adaptation au contexte
lu. Les consignes détaillées sont dans [AGENTS.md](AGENTS.md).

Le dépôt personnel privé de Yanis, `projet-n8n-documentation-humaine`, possède
un sommaire d’accueil et six références : architecture générale, inventaire
de secrets sans valeurs, guide Ansible détaillé, configuration des agents
(chats exclus), procédure d’exploitation quotidienne et procédure de reprise.
Les inventaires sensibles et les valeurs de secrets ne sont pas publiés ici.

Références de compréhension actualisées le 15 octobre 2026 : [architecture complète et schémas](documentation%20yanis/ARCHITECTURE.md), [workflows expliqués pas à pas](documentation%20yanis/WORKFLOWS-PIPELINE-PRINCIPAL.md) et [mise à jour documentaire](documentation%20yanis/RAPPORT-40-documentation-en-francais-clair.md).

Références techniques du code : [bridge n8n/OpenCode, fichier par fichier et fonction par fonction](documentation%20yanis/BRIDGE-N8N-OPENCODE-REFERENCE-TECHNIQUE.md) et [worker Telegram, décisions et reprise durable](documentation%20yanis/WORKER-TELEGRAM-REFERENCE-TECHNIQUE.md). Elles détaillent les contrats, les états, les effets externes, les tests existants et les limites de la version de sources documentée. Le [rapport 46](documentation%20yanis/RAPPORT-46-references-techniques-bridge-et-worker.md) décrit leur publication et le versionnement du code dans le dépôt source privé.

Dernière évolution applicative documentée : [reprise après Telegram et diagnostic](documentation%20yanis/RAPPORT-41-reprise-telegram-et-diagnostic.md). Le [rapport 36](documentation%20yanis/RAPPORT-36-test-reel-maquette-et-validation.md) conserve les preuves du cas réel de construction et livraison. Ces rapports couvrent des étapes et des essais différents.

La documentation précise aussi le versionnement et la sauvegarde de chaque fichier décrit. [Rapport 28](documentation%20yanis/RAPPORT-28-quatre-references-et-guide-ansible.md).
