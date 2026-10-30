<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Production et laboratoire disponibles simultanément — 19 octobre 2026

## Demande et résultat

La demande humaine est de conserver la production migrée et de remettre
l'ancien serveur en service comme laboratoire, puis de transmettre les accès
aux deux opérateurs par mail privé. Les quatre interfaces web répondent sur
les deux environnements, avec noms distincts, TLS valide et accès réseau privé.
Les API privées du portail et de l'observateur refusent les accès anonymes.

Le laboratoire utilise sa copie des données du matin, sans synchronisation
inverse. Ses workflows sont dépubliés et ses anciennes exécutions suspendues
annulées. Le portail démarre sans intégrations ni travailleurs externes ; le
tableau de collecte reste consultable, collecteurs arrêtés. Les identifiants
stockés imposent encore de revoir les effets avant toute exécution manuelle.
Il ne s'agit donc pas d'une deuxième production automatique.

Une élévation Windows pour ajouter le nouveau nom au DNS privé a été annulée.
Le test HTTPS Windows à résolution privée forcée réussit ; la commande
administrateur reste à appliquer pour le lien normal sur ce poste. Les contrôles
depuis le contrôleur Linux réussissent sans résolution forcée. Aucun reboot ni
parcours client réel n'a été exécuté pour cette remise en service.

## Orchestration et délégation

Travail direct de Codex : sauvegardes cohérentes, recette autonome bornée,
application, vérification, documentation et brief privé. Aucun sous-agent ni
session de génération n'a été lancé. Les anciens rôles réservés n'ont pas été
invoqués. Aucun coût ni gain de consommation n'est estimé.

Le contrôle effectif de systemd a révélé un ordre de chargement défavorable
entre l'override lab initial et un ancien override applicatif. Le portail a
été arrêté, l'ordre corrigé et toutes les configurations d'intégration vérifiées
vides. La comparaison de toutes les tables avec la sauvegarde préalable n'a
montré aucune modification. La recette vérifie désormais cet état avant de
démarrer le service. Une correction distincte explicite l'URL des webhooks.

## Coopération et adaptation au contexte

Lecture du protocole, de l'état partagé, des consignes et passations utiles,
puis publication d'une intention bornée au laboratoire. Les travaux sources
concurrents et la réservation de déploiement portail de l'autre opérateur sont
préservés ; aucune candidate de release n'est activée par cette intervention.
Les sauvegardes, copies de données et détails d'accès restent privés. Le
compte rendu public omet adresses, chemins sensibles, identifiants et secrets.
