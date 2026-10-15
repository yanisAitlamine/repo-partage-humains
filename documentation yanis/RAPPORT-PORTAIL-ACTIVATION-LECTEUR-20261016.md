# Activation du lecteur de sites publics du portail — 16 octobre 2026

## Demande et résultat

Yanis a demandé de traiter le nouveau mail de son collaborateur, puis d'y
répondre. Le lecteur sécurisé était déjà inclus dans la version déployée ; son
option de démarrage manquait. Le contrôle préalable avec un compte fictif
confirmait que sa disponibilité était désactivée, malgré une santé HTTPS à 200.

Une recette opérateur ciblée a ajouté cette seule option via un complément
systemd. Le contrôle des tâches et une sauvegarde cohérente de SQLite, de l'unité
et des configurations ont précédé le redémarrage du seul portail. Les empreintes
de l'unité de base et des configurations sont identiques avant et après ; la
release applicative est conservée. Aucun droit supplémentaire n'a été accordé.

Vérifications : 20 tests du mécanisme réussis sur Linux, syntaxe Ansible validée,
revue indépendante sans défaut bloquant concret repéré, puis application réelle
terminée sans erreur. Le processus utilise la version attendue avec l'option
active, la santé HTTPS répond 200 et le contrôle authentifié annonce le lecteur
disponible. L'accès anonyme, les demandes sans consentement et les adresses
privées sont refusés. Les comptes fictifs et leurs sessions ont été supprimés.
Ces refus ont été contrôlés sans lecture externe, analyse ou construction.

Une réponse a été envoyée dans le fil du collaborateur avec l'état appliqué,
les contrôles et les références du guide privé. Aucun workflow, seuil de
qualification, projet client, site distant ou accès réseau n'a été modifié
par cette mission. Le fonctionnement complet d'une lecture publique et d'une
refonte n'a pas été exercé ici. Les protections existantes, dont le filtre
d'injection heuristique, ne constituent pas une garantie de risque nul.

## Orchestration et délégation

Trois agents internes ont travaillé sur des fichiers distincts : helper et
tests, revue de sécurité en lecture seule, rapport et relecture de la recette.
Ils ont terminé ; leurs résultats ont été relus et intégrés. Codex a préparé
la recette, récupéré les contributions concurrentes, exécuté les tests Linux,
appliqué l'activation et réalisé les contrôles authentifiés et la réponse.
Les modèles exacts n'ont pas fait l'objet d'un relevé indépendant ; aucun coût
ni gain n'est estimé. Aucun OpenCode ni accès à la VM personnelle n'a été utilisé.

Les scénarios de panne et de restauration sont testés avec des données fictives.
La recette réutilise le contrôleur de déploiement vérifié et son verrou ; elle
refuse une version ou une configuration inattendue. Une interruption brutale
nécessite une reprise opérateur. Le complément de démarrage persiste lors des
changements de code : les futures versions et retours arrière doivent accepter
cette option. Sa désactivation reste une intervention opérateur distincte.

## Coopération et adaptation au contexte

Les consignes applicables, fiches de reprise, passations pertinentes, protocole
partagé et annonces récentes ont été consultés. Une intention a délimité le
changement avant intervention. La préparation d'une autre version menée par le
collaborateur a été préservée ; ses changements ont été récupérés sans les
activer ni reprendre ses fichiers réservés. Aucun conflit de fichiers rencontré.

Les changements testés et leur documentation ont été intégrés directement à
la branche principale. La fiche de reprise déjà modifiée dans le dépôt public
est conservée et exclue du commit de ce rapport. Les commandes et preuves
détaillées restent dans les espaces privés ; les échanges lisibles et la réponse
sont conservés en copies d'audit privées. Aucune clé, donnée client, coordonnée
personnelle, référence d'accès privée ou copie de mail n'est publiée ici.

L'annonce finale clôt uniquement les réservations de cette mission et distingue
l'activation vérifiée des travaux de refonte et de clarification encore séparés.
