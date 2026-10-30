<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 19 — Mails de test et lien final du site

12 octobre 2026. Yanis demande deux changements dans la chaîne mail → site :
signaler la version de test dans tous les mails clients et ajouter un dernier
mail avec le sous-domaine de test. Publication des workflows autorisée par
cette demande ; aucun envoi d'essai, nouveau site ou redémarrage effectué.

## Résultat publié

Le workflow commercial `paramètre privé à consulter sur le Pi` ajoute **Version de test** directement
dans le HTML du Gmail reply, après rendu et échappement du texte dynamique.
La mention ne dépend donc pas du modèle IA. Son filtrage de destinataires et
ses réservations existantes sont préservés. L'assistant `paramètre privé à consulter sur le Pi`
ne contient pas d'envoi Gmail et reste inchangé.

Le workflow OpenCode `paramètre privé à consulter sur le Pi` comporte désormais 25 nœuds. Après
`completed_review_required`, un formulaire authentifié exige la confirmation
que le site a été construit et que sa revue est validée. Ce statut seul ne
prouve pas la construction, comme l'a montré la première tentative le prototype de démonstration.
Après confirmation, le workflow répond au message client d'origine :

> Votre site en version de test est disponible à l'adresse
> paramètre privé à consulter sur le Pi Il s'agit du sous-domaine de test provisoire.
> Vous pouvez le consulter et nous transmettre vos retours. Version de test.

Le contexte de notification contient uniquement l'identifiant Gmail, le fil,
l'expéditeur autorisé et le projet concordant. Il est conservé dans n8n,
séparé du prompt et du payload bridge. Échec, timeout, contexte invalide ou
absence de confirmation ne déclenchent aucun Gmail final. Les destinataires
test autorisés restent ceux de la configuration existante ; cette mission
n'élargit pas leur liste. Une saisie opérateur sans contexte Gmail ne permet
pas cette notification.

La table outbox existante réserve `opencode-job:<job_id>` avant l'envoi.
Une réservation existante bloque les reprises successives. Une erreur Gmail
reste `UNKNOWN` sans retry automatique. Le contrôle d'absence suivi de
l'insertion n'est **pas atomique** : deux exécutions concurrentes peuvent
encore envoyer le même résultat. Ne pas annoncer une garantie absolue
d'absence de doublons. Une primitive atomique du stockage demanderait une
évolution distincte.

## Publication, contrôles et retour arrière

Définitions courantes récupérées par API avant préparation ; dépôt Pi propre.
Sauvegardes privées : `paramètre privé à consulter sur le Pi`
et `*-before-publish.json`, dossier 0700 et snapshots 0600. Aucun secret de
connexion n'est affiché ; l'authentification opérateur reste en mémoire.

Publication par PUT puis activation API, OpenCode avant commercial. Relecture
API : les deux workflows sont actifs, `activeVersionId == versionId`, avec
nœuds et connexions attendus. n8n génère un `webhookId` pour le nouveau Wait ;
le premier contrôle strict a signalé cette seule différence. Codex l'a
identifiée et corrigé le comparateur, puis repris la publication commerciale
sans republier inutilement OpenCode. Les sauvegardes originales sont gardées.
Les deux workflows appartiennent au même projet n8n, contrôle SQLite en
lecture seule. Pas de service redémarré ni de rôle Ansible testé/appliqué.

Tests isolés des candidats : rendu HTML réel et échappement, confirmations,
source/projet/destinataire, échecs/timeouts, lien fixe, séparation du payload,
graphe de réservation et conservation des références de connexions réussis.
Fixtures JavaScript de l'intégration et 12 tests Python du runner réussis.
Après actualisation de la source portable, une fixture ancienne omettait le
nouveau contexte de `parse-submit` : corrigée par Codex, puis suite JS réussie.
`git diff --check` réussi. Exports ciblés sans secrets : zéro redaction.

Limites : pas d'exécution réelle du nouveau formulaire ou du Gmail final,
pas de test de concurrence. Aucun email envoyé pendant cette intervention.
Le parcours réel reste à vérifier lors de la prochaine construction approuvée.
Les exécutions déjà en attente conservent leur ancienne définition ; cette
publication ne relance pas rétroactivement le prototype de démonstration ni ne lui envoie un mail.
Retour arrière : restaurer les deux définitions sauvegardées par API et
réactiver après inspection ; ne pas effacer les réservations d'envoi incertain.

## Délégation

Base `paramètre privé à consulter sur le Pi`, `AGENTS.md` et `opencode.json` lus.
Planificateur, implémenteurs et revue observés sur `gpt-6-luna` ; aucune mesure
de coût consolidé ni économie annoncée.

| Session | Rôle et travail |
| --- | --- |
| `paramètre privé à consulter sur le Pi` | Planification, attribution, suivi et bilan terminé. |
| `paramètre privé à consulter sur le Pi` | Inspection puis implémentation : premier arrêt faute de contexte établi, seconde inspection résout la provenance, création des candidats et fixtures. |
| `paramètre privé à consulter sur le Pi` | Finalisation de génération, tests et résumé. |
| `paramètre privé à consulter sur le Pi` | Revue indépendante en lecture seule : course de réservation de gravité moyenne, aucun autre défaut bloquant trouvé. |
| `paramètre privé à consulter sur le Pi` | Analyse de la concurrence, sans élargir les écritures. |
| `paramètre privé à consulter sur le Pi` | Confirmation qu'aucune primitive atomique sûre n'est établie dans le périmètre ; limite documentée. |

Autorisations déléguées : candidats et outils dans le dossier de mission,
guard et tests dans `integrations/opencode`, contrôles isolés ; publication,
Le planificateur n'écrit pas et la revue n'exécute pas de commandes. Le
premier lancement CLI attendait son entrée standard, sans session créée ;
Codex l'a arrêté et relancé avec `paramètre privé à consulter sur le Pi` avant la session ci-dessus.

analyse indépendante des nœuds, acceptation de la limite concurrente dans
ce changement ciblé, correction de la note du workflow, publication,
relecture des versions actives, actualisation des sources/exports, correction
de fixture, copie Windows et documentation. Aucun commit/push effectué.

## Fichiers

Sources Pi sous `paramètre privé à consulter sur le Pi` :
`integrations/opencode/{README.md,commercial-guard.js,workflow.json,tests/test_workflow.js}`,
exports draft/published des deux workflows et `workflows/manifest.json`.
Copies Windows correspondantes sous `Technique/sources/n8n-services`.
Le workflow portable omet les références de connexions : remapper Gmail,
HTTP/TLS et outbox lors d'une importation hors restauration de la base.
Le script historique de finalisation HTTP seul ne configure pas Gmail.
Contexte Windows : ce rapport et `PASSATION.md`. Global protégé intact.
