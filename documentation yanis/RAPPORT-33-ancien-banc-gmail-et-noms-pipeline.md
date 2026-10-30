<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Rapport 33 — Ancien banc Gmail retiré et pipeline clarifié

13 octobre 2026. Version publique anonymisée.

## Demande et résultat

Yanis signale des réponses récentes à d’anciens mails, précise ensuite le nom du banc manuel concerné, puis demande des noms compréhensibles pour la chaîne principale.

Le banc manuel était une ancienne copie autonome : il recherchait jusqu’à vingt-cinq messages dans une fenêtre historique, avec ses propres tables de suivi. Il ne voyait donc pas les réservations de la chaîne actuelle. Son registre contient au moins six envois marqués réussis avec identifiant, sur des messages historiques, pendant la dernière exécution manuelle. La réception dans la boîte destinataire n’a pas été inspectée. La trace conservée atteste une exécution finalement annulée, pas une boucle infinie ; le lot historique explique la durée et le retraitement possibles.

La copie est maintenant réduite à un déclencheur et une notice sans effet, puis archivée. Elle ne contient plus aucun lecteur Gmail, modèle, connexion privée ou envoi. Son état archivé et l’absence d’exécution encore active sont vérifiés. Sa définition antérieure est sauvegardée ; les historiques et tables d’envoi restent conservés, notamment les résultats incertains.

Les trois étapes sont désormais :

1. **PIPELINE — 1. Réception des mails et suivi**.
2. **PIPELINE — 2. Dialogue commercial et brief**.
3. **PIPELINE — 3. Maquette puis validation humaine**.

Les trois auxiliaires portent **SUPPORT PIPELINE** : Reprise ponctuelle, Journal des événements, Alertes et erreurs. Les identités techniques, graphes, connexions et réglages sont préservés et comparés lors du renommage. Ils restent appelés par la chaîne ; l’utilisateur commence son essai avec un nouveau mail, sans lancer le banc archivé.

## Orchestration et délégation — Délégation

Codex réalise directement ce diagnostic ciblé, le retrait du vieux banc et les changements de noms. Aucun nouvel agent ni appel modèle de test n’est lancé, afin de respecter la demande de contrôles sobres. Lectures : métadonnées d’exécution, définitions et registres d’envoi nécessaires, sans publier corps de mails ou données clients. Contrôles : sauvegardes, comparaison avant/après des six graphes, lecture des états archivage/activation et des exports. Aucun mail, construction ou reprise n’est lancé pour vérifier.

## Coopération et adaptation au contexte — Collaboration

La passation et les annonces partagées sont lues, une intention est publiée. Le premier diagnostic visait la chaîne automatique ; il ne permettait pas d’attribuer les réponses historiques. La précision humaine a identifié l’autre copie et son registre distinct. Codex adapte alors le périmètre à ce banc, puis intègre la demande complémentaire de renommage.

Les états d’envoi et modifications préexistantes sont préservés, sans réinitialisation de déduplication ni restauration d’ancienne base. Les changements fonctionnels restent limités à la copie retirée ; les workflows actifs sont renommés sans modification de leur comportement. Les exports sont synchronisés et la fin de coordination libère les réservations. Le gel des agents concurrents reste annoncé pendant l’essai manuel. Les autres copies de développement ne sont pas supprimées en bloc.
