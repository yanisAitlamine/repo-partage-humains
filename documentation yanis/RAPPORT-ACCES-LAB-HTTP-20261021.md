<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Accès au laboratoire par VPN et essai Gmail — 21 octobre 2026

## Demande et résultat

Yanis demande d'abord un accès direct au n8n du laboratoire par IP et port en
HTTP, puis un essai réel de raccord Gmail. HTTPS est envisagé si cet essai échoue.
Le lab dispose désormais de sa propre identité VPN et d'une adresse distincte.
L'accès est limité au poste opérateur connecté au VPN ; aucun accès Internet
à l'éditeur n'est ouvert. Santé HTTP, connexion propriétaire et tableau de bord
dans Brave ont été vérifiés. Les données et la version n8n sont conservées.
Le précédent relais local temporaire est arrêté.

L'essai OAuth est réellement effectué depuis le credential dédié. Google
répond400invalid_request en refusant l'adresse de retour sur IP privée en HTTP.
Le credential existe mais n'est pas raccordé à la nouvelle boîte. Aucun nouveau
poller Gmail autonome ni test client de bout en bout réussi n'est annoncé.
À la suite de ce refus, l'option HTTPS autorisée est mise en place sur un nom
distinct du lab, qui résout vers son adresse VPN. Le Caddy déjà installé sur
le lab utilise un certificat public obtenu par DNS01 ; aucun port public n'est
ouvert. HTTP reste utilisable. Santé HTTPS et connexion dans Brave sont vérifiées
sans désactiver la validation du certificat.

Un client Web OAuth séparé est préparé dans le projet Google du propriétaire,
avec un seul callback lab. Sa création reste en attente de la confirmation au
clic exigée par le skill navigateur pour un nouvel accès persistant. Le client
de production reste inchangé ; le nouveau client n'est pas encore créé et la
boîte du lab n'est donc pas encore raccordée. Les identifiants du projet, du
compte et du nom de service sont exclus de ce rapport.

Les recettes nouvelles sont versionnées dans leur dépôt canonique privé.
Les unités VPN et n8n sont actives et activées au démarrage, avec dépendances
ordonnées. Un contrôle quotidien de renouvellement du certificat est activé.
Aucun redémarrage complet du lab ni renouvellement réel n'a été utilisé pour
les qualifier.
La santé de production répond toujours après l'admission réseau ciblée ; les
traitements clients de production n'ont pas été relancés par cette mission.

## Orchestration et délégation

Travail direct de Codex ; aucun sous-agent de collaboration, PIAgentControl,
nouveau modèle local ou accès Kali. Les opérations d'administration sont
préparées et appliquées par des recettes Ansible dédiées, distinctes des
anciens rôles réservés. La clé VPN est créée et conservée sur la machine cible ;
seule la demande publique est signée avec l'autorité existante hors serveur.
La configuration conserve la liste de révocation et les identités existantes.
Aucun coût ou gain n'est déduit de ces contrôles.

## Coopération et adaptation au contexte

Les consignes, la passation, le protocole et les annonces pertinentes ont été
consultés. Le périmètre réseau a été annoncé avant les changements correspondants.
Les travaux parallèles de séparation de messagerie et de développement restent
préservés. Une adresse LAN ambiguë et l'écoute initiale limitée à loopback
expliquaient l'absence d'accès direct : une identité VPN propre remplace ce
chemin pour l'administration. La clé d'hôte SSH reste vérifiée.

Le résultat distingue l'accès navigateur, l'autorisation Google et la livraison
client. Une connexion Gmail dans le navigateur ne constitue pas un raccord
OAuth de n8n ; un credential créé ne prouve pas qu'une boîte est surveillée.
Les adresses, profils, paramètres privés et preuves détaillées restent hors
de ce rapport public. Aucune valeur de secret n'est publiée.
