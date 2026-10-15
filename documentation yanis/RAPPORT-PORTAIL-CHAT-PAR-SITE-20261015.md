# Portail client : une conversation par site — 15 octobre 2026

## Demande et résultat

L'utilisateur souhaite simplifier le portail : supprimer la page de demandes et
le sélecteur d'espace de travail, afficher les différents sites dans Overview,
puis ouvrir l'assistant propre au site choisi. Le client doit pouvoir discuter
avant de payer. La référence du projet doit préparer une future intégration,
sans raccorder les pipelines à cette étape. Le versionnement, la collaboration
et le déploiement privé sur le serveur existant font partie du périmètre demandé.

Le portfolio et les conversations par site sont réalisés. Chaque conversation
regroupe messages, devis, changements et événements de revue du concept. Les
brouillons non envoyés restent séparés entre les sites pendant la session du
navigateur. Les liens directs et le retour arrière sélectionnent le bon site ;
un site indisponible affiche un état explicite. Les anciens devis et échanges
restent compatibles, sans remise à zéro des données.

La discussion simple ne vaut jamais acceptation d'un devis. Un sujet de service
explicitement choisi permet de décrire un changement et d'obtenir son offre dans
le même fil. Prix, rattachement au projet et transitions restent contrôlés par
le serveur. La référence portée par les nouveaux messages provient du projet
dont le propriétaire a été vérifié ; un identifiant envoyé librement par le
navigateur ne suffit pas à autoriser une opération.

La version est enregistrée sur une branche dédiée avec demande de revue,
construite sur le serveur cible et déployée dans une nouvelle release. Une
sauvegarde privée de la base a précédé la bascule. Le service utilise toujours
une écoute locale derrière le HTTPS privé existant. La configuration du proxy
est restée identique et le service préexistant reste disponible. La branche
est également disponible dans l'espace partagé ; les droits de lecture et
d'écriture du collaborateur sur les sources concernées ont été vérifiés.

Contrôles réalisés :

- 26 tests Python réussis sous Windows puis sur le serveur cible : comptes,
  sessions, concurrence, isolation des propriétaires et des sites, discussion
  avant paiement, validation stricte, devis et compatibilité des anciens messages.
- Vérification TypeScript et construction de production réussies sur les deux
  machines ; les noms des artefacts obtenus concordent.
- Vérification dans le navigateur avec deux sites fictifs locaux : création,
  navigation, brouillons séparés, devis intégré et acceptation, rechargement,
  ancien devis conservé, site inconnu, brief, concept et largeur mobile.
- Chargement réel du nouveau portail en HTTPS, sans erreur de console observée
  sur ce chargement. Les données fictives sont restées dans l'environnement local.
- Santé du service et HTTPS des deux applications vérifiés ; le contrôle serveur
  utilise explicitement l'adresse privée, le nom DNS ordinaire n'ayant pas permis
  ce contrôle depuis le serveur. La vérification navigateur fonctionne avec le
  nom habituel. Aucun élargissement réseau n'a été effectué.

Les réponses restent guidées et les concepts reposent sur un modèle visuel.
IA, paiements, souscriptions réelles, pipelines et publication de sites clients
restent déconnectés. Le portfolio montre donc des projets et échantillons, pas
des hébergements clients déjà actifs. La revue et la fusion de la branche restent
possibles ; le déploiement demandé utilise la version enregistrée de cette branche.

## Orchestration et délégation — Délégation

Codex a lancé un sous-agent interne pour le domaine, les contrats et les tests,
afin de traiter séparément les règles serveur pendant le travail d'interface.
Le même sous-agent a ensuite actualisé README, API, passation et backlog, puis
effectué une revue statique de l'interface. Ces travaux sont terminés, relus et
intégrés. Le modèle du sous-agent était hérité de la session ; aucune nouvelle
configuration de modèle externe ni session de construction payante n'a été lancée.

L'agent principal a réalisé le portfolio, les routes, la conversation et les
styles, intégré le contrat, exécuté les vérifications, versionné la livraison et
effectué la construction et le déploiement. La revue a identifié deux cas limites
corrigés : le défilement après atteinte de la limite d'historique et une réponse
asynchrone de concept pouvant rouvrir un aperçu après changement de site. L'offre
de création reste aussi accessible lorsque son message initial sort de l'historique.

Aucune session PIAgentControl ou OpenCode n'a été lancée ou reprise. La mise à
disposition d'une contribution au collaborateur ne prouve pas que ses agents ont
commencé à travailler. Aucun nouveau mail n'était nécessaire à cette modification.

## Coopération et adaptation au contexte — Collaboration

Les consignes du projet, la documentation du produit et le protocole partagé ont
été lus. Une intention a précédé les modifications ; des extensions ont précisé
les fichiers d'entrée, la sauvegarde et les emplacements de livraison. Les
nouvelles annonces des autres missions ont été relues avant les opérations serveur.
Les interventions simultanées sur les connexions externes et les accès réseau
ont conservé leur périmètre ; aucun de leurs fichiers ni de leurs services n'a
été modifié par cette mission.

Les états Git ont été vérifiés avant mutation. La source partagée n'ayant pas
d'authentification sortante utilisable, la version déjà publiée a été transportée
par bundle Git sans copier d'identifiants. Les sources partagées restent distinctes
de la release exécutée. Le compte rendu public est anonymisé, sans données clients,
contenu de mail, secret ni inventaire privé d'accès. Une fin explicite libère les
réservations de cette mission après livraison.
