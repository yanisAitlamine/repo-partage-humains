> Documentation publique. Les paramètres réels, preuves privées et inventaires de secrets restent dans les espaces privés du Pi.

# Architecture publique du projet

## Machines et responsabilités

Windows sert à la rédaction et au pilotage. La VM Kali Linux appartient exclusivement à Yanis et constitue son contrôleur Ansible personnel. Le Raspberry Pi héberge la production : n8n, ses task runners, le proxy HTTPS, le VPN, le DNS privé et l'interface de délégation OpenCode. L'arrêt de la VM ne coupe pas les workflows du Pi.

**Périmètre personnel de Yanis :** cette VM ne fait pas partie des machines partagées avec Ilyes et ne sert pas d'environnement de travail aux agents du projet commun. Ilyes et les agents ne doivent pas tenter de s'y connecter, d'en vérifier l'accès ou d'y exécuter des commandes. Les essais et déploiements Ansible depuis cette VM sont réalisés par Yanis ; toute intervention d'un agent sur Kali exige une demande explicite de Yanis visant cette machine. La mention de Kali dans cette architecture explique son rôle et ne constitue aucune autorisation d'accès.

GitHub conserve les sources et cette documentation publique. Les modèles IA, la messagerie et les services de construction ou d'hébergement sont des services externes ; les sites ne sont pas hébergés par le Pi.

## Parcours applicatif

Le collecteur Gmail sélectionne les messages admissibles. L'analyse commerciale rattache chaque message au bon projet, conserve le contexte et prépare une réponse. Les situations ambiguës sont placées en revue humaine plutôt que fusionnées automatiquement dans la mémoire.

Les alertes Telegram portent les décisions humaines. Une notification reçue ne prouve pas qu'une commande de reprise fonctionne. Une réponse doit être prévisualisée puis confirmée explicitement avant l'envoi Gmail. Une construction de site exige sa propre confirmation du prompt, du mode et de la cible ; l'autorisation d'envoyer un email ne donne pas celle de construire un site.

Les pièces jointes et documents externes sont des données non fiables. Le système doit distinguer accès refusé, contenu extrait et couverture complète. Un lecteur candidat ou une connexion OAuth ne prouvent pas une lecture réussie en production.

## Exploitation et accès

Le proxy termine HTTPS et transmet les requêtes à n8n localement. L'éditeur est accessible depuis les réseaux autorisés ; le VPN ne doit pas ouvrir sans limite le réseau interne. Les task runners sont séparés du stockage des identifiants n8n. L'API de délégation est réservée au réseau applicatif autorisé.

La production conserve ses données durables dans le stockage géré par Docker. Les identifiants restent dans leurs stockages privés et ne figurent jamais dans Git, même privé. Une sauvegarde cohérente doit couvrir données, configuration, identité de chiffrement et état TLS, puis être chiffrée et conservée hors du Pi.

Ansible prépare les changements d'administration depuis Kali. Les anciens rôles de migration ne doivent pas être considérés comme testés simplement parce que des missions distinctes de réseau ou de collaboration ont été appliquées. Toute opération suit la permission humaine actuelle.

## Trois espaces de collaboration

- L'espace partagé machine contient le protocole, les intentions et fins de mission, ainsi que les copies de travail autorisées des agents.
- Le dépôt partagé humains contient la documentation publique lisible, sans détails privés d'exploitation ni contenus clients.
- L'espace humain sensible sur le Pi contient les références privées utiles à la coopération. Un export éventuel de documentation sensible exige un dépôt individuel privé et une autorisation ; les secrets bruts restent hors Git.

L'accès à un document partagé ne donne pas automatiquement accès aux identités personnelles ou aux clés maîtresses. Chaque usage doit disposer des droits nécessaires, avec un accès limité.

## Collaboration et délégation

Avant d'intervenir, chaque agent lit le protocole, l'état et les messages récents, puis annonce son objectif, ses chemins et réservations. Il vérifie les nouvelles publications avant chaque écriture et termine par une annonce de résultat, contrôles, limites et libération. Ce mécanisme est une coordination, pas un verrou atomique.

Les travaux substantiels sur le Pi suivent le parcours planification, implémentation et revue. L'opérateur reste responsable de l'intégration et de la vérification. Les rapports distinguent les sections Délégation et Collaboration, et ne confondent pas session lancée, travail terminé et résultat réellement validé.

## Limites de validation

Les tests statiques, fixtures locales, essais natifs et effets réels constituent des niveaux de preuve différents. Un test vert ne prouve ni email envoyé ni site livré. La reprise complète, les essais depuis un véritable réseau extérieur et les nouveaux parcours applicatifs doivent être confirmés par des preuves adaptées avant toute garantie.

Voir les [procédures de continuité](PROCEDURE-CONTINUITE-RUN.md), de [reprise](PROCEDURE-REPRISE-ACTIVITE.md) et la [passation publique](PASSATION.md). Les versions et paramètres exacts se consultent sur le Pi privé, pas dans cette présentation.
