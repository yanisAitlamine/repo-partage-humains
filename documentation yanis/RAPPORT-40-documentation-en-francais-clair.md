# Rapport 40 — Documentation des workflows et de l’architecture en français clair

15 octobre 2026 — auteur : Yanis / Codex.

## Demande et résultat

Yanis a signalé que le paragraphe sur la réception, le suivi et les reprises était incompréhensible. Après une explication en langage courant, il a demandé d’appliquer ce style à toute la documentation des workflows ainsi qu’à l’architecture. La mission porte sur les deux guides publics de référence, pas sur la réécriture des rapports historiques ou la modification du système.

Le guide des workflows est entièrement réorganisé : parcours général, rôle des six workflows, réception du mail, compréhension du besoin, intervention Telegram, construction, livraison, prévention des doublons et diagnostic. Les termes techniques sont expliqués au moment où ils apparaissent. Les tableaux séparent les décisions commerciales, le bilan d’un mail et l’état de son envoi. Des exemples montrent pourquoi un remerciement ne lance pas une construction et pourquoi un envoi incertain ne doit pas être recommencé automatiquement.

L’architecture explique le rôle des machines et des services, leurs échanges et les différences entre sources, configuration installée, données et sauvegardes. L’ancienne règle imposant une confirmation avant toute construction est remplacée par le parcours de prototype documenté : construction automatique possible, contrôle du résultat, puis validation humaine avant livraison par mail. Le guide maintient la distinction avec la mise en production d’un site complet.

Les observations applicatives restent datées du 14 octobre. La réécriture ne transforme pas les interventions encore en cours en résultats acquis. Les preuves du test réel de maquette et celles de l’intégration Jev sont distinguées. Les limites sur Drive, les pièces jointes et l’OCR sont conservées sans présenter les candidats comme déployés.

Les contrôles sont documentaires : relecture des textes et différences, correspondance des étapes avec les guides et rapports existants, vérification des liens locaux et recherche de données sensibles avant publication. Aucun workflow n’est exécuté, aucun mail ou site n’est produit et aucun service n’est redémarré pour cette mission. Le sens détaillé de toutes les situations classées ATTENTION reste à préciser dans la documentation technique ; le guide explique cette limite plutôt que d’inventer une règle.

## Orchestration et délégation — Délégation

Codex assure directement la réécriture, la comparaison et la publication des documents. Aucun sous-agent ni session OpenCode n’est lancé : il s’agit d’une révision éditoriale des références existantes, sans implémentation applicative. Aucun modèle délégué, coût ou gain n’est annoncé. La relecture finale est celle de Codex ; aucune revue indépendante distincte n’est revendiquée.

## Coopération et adaptation au contexte — Collaboration

Les consignes du projet et du dépôt public, les règles de coordination, les annonces documentaires précédentes, les deux guides et les rapports utiles ont été consultés. Les annonces de clôture de la précédente mission documentaire ont été vérifiées avant la réservation des guides. Une intention a annoncé les fichiers concernés et la préparation dans une copie Git isolée sur le Pi.

À la demande de Yanis, les sources documentaires sont reprises depuis le Pi par SSH. Aucun navigateur n’est utilisé. La consultation initiale de la liste des outils GitHub n’a ni ouvert ni modifié de document. Une première tentative de transmission de texte a échoué avant lancement à cause de la longueur de commande Windows ; elle n’a pas modifié les fichiers du Pi. Les textes ont ensuite été préparés dans des fichiers temporaires pour être transférés sans cette limite.

Les annonces d’autres missions montrent des interventions en cours sur les workflows et Telegram. Ces fichiers ne font pas partie de la présente révision. Les nouvelles annonces et l’état Git sont vérifiés avant écriture et publication ; les contenus des autres auteurs et les changements privés existants sont préservés. Le sommaire conserve ses liens et met les guides de compréhension en évidence. La source locale du guide public des workflows sur le Pi est synchronisée avec la version publiée ; les guides techniques et les références privées restent inchangés. La fin de coordination précise le résultat de publication et libère uniquement les réservations documentaires de cette mission.
