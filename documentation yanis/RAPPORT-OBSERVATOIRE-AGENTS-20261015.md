# Observatoire des discussions et délégations — 15 octobre 2026

## Demande et résultat

L’utilisateur demande un outil permettant de suivre les sujets, ses prompts,
les échanges entre agents et les délégations, en incluant les espaces partagés
du projet. La mission autorise sa construction et son déploiement.

Un tableau de bord privé est construit et lancé sur le poste opérateur. Il
propose une recherche dans les discussions, une chronologie, un filtre montrant
les événements rattachés à un prompt, un arbre des sessions enfants, des favoris
locaux, le journal de coordination et les métadonnées des dossiers partagés.
Les dates, sources, erreurs de collecte et limites sont visibles. Les raccourcis
de lancement et de démarrage à l’ouverture de session sont installés.

La collecte distante utilise l’accès SSH existant en lecture seule. Elle ne
lance aucun agent. Les historiques de sessions sont lus sans ouvrir les
authentifications. Les différentes reprises d’une même session locale sont
fusionnées par identifiant, et les événements sont dédupliqués avant de calculer
les totaux et les relations. Les événements techniques de transport sont écartés
des prompts ; les réponses humaines aux questions structurées sont normalisées.

Les relations parent/enfant utilisent les identifiants des traces. Le lien
avec un prompt exige un appel de délégation correspondant. Une mention dans
une annonce demeure une référence textuelle, sans preuve de lancement ou de
réception. Une fin de tour ne signifie pas validation d’un livrable. Les états
historiques et les traces récentes sans fin attestée sont distingués.

Onze tests synthétiques passent : périmètre de lecture, fusion des reprises,
rattachement aux prompts, absence d’inférence sans preuve, exclusion du contexte
système et des raisonnements, masquage de formats de secrets connus, performance
sur un long texte et protections HTTP. La syntaxe JavaScript est vérifiée. La
collecte réelle des sources et l’écoute limitée à la boucle locale sont contrôlées.
L’interface est examinée dans le navigateur, avec ouverture d’un sujet et de
ses références de coordination. Ces contrôles ne prouvent pas l’exhaustivité
des informations produites par tous les agents ni la validité de leurs résultats.

Le tableau de bord reste personnel au poste. Les conversations privées des
autres machines ne sont pas accessibles ; seules leurs annonces partagées le
sont. Le masquage ne garantit pas de reconnaître toutes les valeurs sensibles
exprimées librement. Les longues sessions ont une limite d’événements affichés,
annoncée avec leur total ; les sources originales restent conservées.
Le code est conservé dans le projet local. Aucune sauvegarde indépendante ou
mise à disposition multiutilisateur n’est revendiquée.

## Orchestration et délégation

Codex réalise directement la conception, les collecteurs, l’interface, les tests,
le lancement et les vérifications. Aucun sous-agent n’est lancé pour cette
mission ; aucun recours à OpenCode depuis la base personnelle réservée à
l’utilisateur n’est effectué. L’outil observe les délégations existantes sans
en déclencher. Aucun coût ou gain n’est inventé.

Le premier chargement a révélé une expression de masquage trop coûteuse sur
certains longs textes. Son motif est borné et un contrôle de performance est
ajouté. La revue des relations a ensuite révélé plusieurs fichiers de reprise
pour les mêmes sessions : leur fusion corrige les doublons et rétablit les liens
avec les prompts, avec un cas de régression dédié.

## Coopération et adaptation au contexte

Les consignes du projet, les références d’architecture, la passation et les
rapports utiles sont consultés. Le protocole machine, son état documentaire,
les règles de coordination et des annonces récentes sont lus. Une intention
délimite le nouveau dossier et les collectes ; une extension réserve le présent
rapport public. Les lectures de journal sont distinguées de toute autorisation.

Les modifications préexistantes du projet et les réservations des missions
parallèles sont préservées. Aucun service applicatif distant, workflow, ancien
rôle d’administration ou machine personnelle de contrôle n’est modifié.
Les authentifications, prompts et conversations ne sont pas copiés dans ce
rapport ou dans le journal partagé. La publication porte sur ce seul document
anonymisé, après revue du contenu et du diff.
