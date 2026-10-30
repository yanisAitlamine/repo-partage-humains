<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Héphaïstos — réduction des notifications par mail

19 octobre 2026. Correctif source testé et poussé ; activation distincte.

## Demande et résultat

Le demandeur a signalé trop de mails et demandé de supprimer les confirmations
automatiques de chaque étape. La lecture des seuls compteurs de sa recette a
confirmé vingt-sept courriers techniques : traitement, début de réalisation et
incident. Aucun corps de mail ni secret n'a été nécessaire à ce diagnostic.

Le serveur conserve les courriers utiles : vérification d'adresse, questions,
récapitulatifs à confirmer, maquette à décider, clarification des retours et
livraison finale avec les accès prévus. Création de projet, prise en compte,
traitement, début de réalisation, clôture et incident restent silencieux par
mail ; leurs états restent disponibles dans le portail.

Les nouveaux événements silencieux conservent leur clé d'idempotence, avec
statut supprimé de l'envoi et sans contenu ni destinataire. Au prochain traitement
de la file après activation, les anciennes notifications de statut encore non
envoyées seront neutralisées. La vérification d'adresse ne peut pas les libérer
à nouveau et reste limitée au compte concerné. Les envois déjà effectués, en
cours ou incertains ne sont pas rejoués. Le composeur refuse aussi directement
les types silencieux. Aucun courrier Gmail déjà reçu n'est effacé.

Contrôles : 435 tests de la suite globale et build frontend réussis ; après
resserrage de l'isolation par propriétaire, les 28 tests ciblés de contact et
d'envoi passent. Ils vérifient les types silencieux, l'ancien backlog, les états
incertains, les routes de réponse conservées et la vérification d'adresse. Bases,
destinataires et transport fictifs : aucun mail réel n'est envoyé pour ces tests.

Le correctif et son guide ont été commités et poussés normalement. Cela ne prouve
pas son activation : une autre mission réserve actuellement les services pour
leur sauvegarde et migration. Aucun redémarrage ni changement de la base réelle
n'a été effectué ici. L'activation reste à coordonner avec cette migration.

## Orchestration et délégation

Codex a réalisé directement le diagnostic ciblé, le code, les tests, la revue
du diff et le push. Aucun nouvel agent ni session PIAgentControl n'a été lancé.
La réserve de migration interdit une activation concurrente ; la transmission
d'une consigne à cette autre tâche nécessite l'autorisation explicite du
demandeur et ne doit pas être présentée comme un déploiement déjà effectué.
Aucun coût ou gain de délégation n'est inventé.

## Coopération et adaptation au contexte

Consignes applicables, fiche de reprise, passation du composant, protocole et
annonces récentes ont été consultés. L'intention réserve seulement les deux
modules de courrier, leurs tests, le nouveau guide et ce rapport. Les services,
données et documents de reprise réservés par la migration restent préservés.
Les modifications concurrentes et archives du checkout sont conservées ; seuls
les fichiers annoncés sont intégrés.

Un fichier d'intention a été déposé brièvement au mauvais niveau du dossier de
projet, puis déplacé immédiatement dans le dossier de mission avant publication.
Aucun fichier de travail n'y reste. La fin de mission distingue la source
disponible de l'activation non attestée et libère les réservations propres.
Cette version publique exclut les identifiants, coordonnées, chemins privés et
références de données du scénario.
