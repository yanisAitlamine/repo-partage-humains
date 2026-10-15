# Observatoire : déploiement serveur et graphes de tâches — 15 octobre 2026

## Demande et résultat

L’utilisateur corrige la première livraison : l’application doit être versionnée
et déployée sur le serveur du projet, et non sur son poste. Il demande que cette
règle soit ajoutée aux consignes et que chaque sujet ouvre un graphe montrant
messages, fichiers consultés ou écrits, échanges entre agents et délégations
dans une frise retraçant l’évolution de la tâche.

Le dépôt canonique est créé sur le serveur, committé et poussé dans un dépôt
Git privé dont la visibilité est vérifiée. Une recette d’administration autonome
installe une release immuable et une unité dédiée. L’application est disponible
derrière le HTTPS privé existant ; son API refuse l’accès anonyme. Le serveur
local de la première version est arrêté et les raccourcis sont actualisés.

Le poste garde uniquement un collecteur pour ses traces locales. Il transmet
par SSH personnel une projection filtrée au stockage privé du serveur. Les
sources natives continuent d’être collectées sur le serveur lorsque le poste
est éteint ; la projection du poste est alors datée et signalée ancienne.
Les conversations privées d’autres postes ne sont pas rendues accessibles.

Le clic sur un sujet ouvre une frise SVG avec une ligne par session ou agent,
des nœuds de prompts, messages, délégations et opérations sur les fichiers.
Le clic sur un nœud montre le contexte et le niveau de preuve. Le flux des
tâches possède sa propre fenêtre de navigation. Filtres, zoom, inventaire des
fichiers, messages et références de coordination sont disponibles. Les événements
sont ordonnés et datés ; leur espacement visuel n’est pas proportionnel au temps.

Les chemins proviennent d’outils structurés et d’une extraction statique limitée
des commandes. Les instructions, raisonnements internes et sorties brutes des
outils ne sont pas projetés. Une demande d’écriture reste distincte d’une réussite
attestée ; le résultat global d’un lot ne prouve pas chaque opération. Une
écriture réussie puis une lecture déclarée par un autre agent permet un lien
de passage possible, sans prouver l’identité des octets ni l’intention initiale.
Chemins calculés et formats non reconnus ne peuvent pas être reconstruits.

La connexion propriétaire emploie l’identité SSH existante pour émettre un ticket
éphémère à usage unique, puis une session HTTPS. Les valeurs ne sont ni affichées
ni versionnées. Les données et empreintes restent hors Git. L’ajout demandé aux
consignes est réalisé ; l’empreinte de référence et la protection sont rétablies.

Les 22 tests synthétiques passent sur le poste et le serveur. Ils couvrent
notamment causalité, fusion des reprises, projection native et locale, extraction
de fichiers, passage entre agents, échec d’écriture, accès anonyme et usage unique
du ticket. La syntaxe des deux scripts JavaScript est vérifiée. Les applications
voisines, le service dédié, la version exécutée, les sources et le HTTPS sont
contrôlés séparément. Dans le navigateur authentifié, un sujet et son graphe sont
ouverts, le filtre de fichiers et son inspecteur sont utilisés, puis le flux
d’une tâche comportant des agents enfants est affiché. Ces contrôles ne prouvent
ni l’exhaustivité des traces ni tous les usages sur tous les appareils.

## Orchestration et délégation

Codex réalise directement collecte, graphe, authentification, tests, Git,
déploiement et vérification. Aucun sous-agent ni session d’agent externe n’est
lancé dans cette mission. Aucun coût ou gain n’est inventé. Les agents visibles
dans l’outil proviennent des sources observées, pas d’une nouvelle délégation.

Le contrôle réel révèle une variable de résultat réutilisée dans le collecteur
natif : elle est corrigée et un test de collecte sur base synthétique est ajouté.
La navigation du graphe et le traitement prudent des résultats de lots sont
ajustés. Les corrections sont committées, poussées puis installées comme releases
distinctes. Les anciennes releases sont conservées. Les erreurs intermédiaires
ne sont pas présentées comme des validations réussies.

## Coopération et adaptation au contexte

Les consignes, références d’architecture, passation et rapport de la première
version sont relus. Le protocole machine et les annonces récentes sont consultés.
Une intention réserve les nouveaux chemins, le service et la seule route HTTPS
de cet outil ; une extension réserve le rapport et le fichier de reprise.
Les modifications préexistantes et la mission parallèle du portail sont préservées.

Seule la nouvelle recette est appliquée localement sur le serveur. Les anciens
rôles réservés et la machine personnelle de contrôle ne sont pas utilisés.
Le proxy est rechargé avec validation préalable ; les protections réseau et
les applications tierces ne sont pas élargies par cette intervention. Aucun
workflow, modèle, mail ou site client n’est exécuté pour tester le suivi.

Le code versionné ne sauvegarde pas les conversations. Le masquage des formats
connus ne garantit pas la reconnaissance des secrets libres. Sauvegarde complète
indépendante et reprise après panne ne sont pas revendiquées. Le présent rapport
est publié seul après revue d’anonymisation ; les détails d’accès restent privés.
