> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 10 — Prompt final n8n vers OpenCode N0C

**11 octobre 2026.** Demande : lire le projet, examiner les workflows d’Ilyes et ajouter une construction de prototype ou de site complet à partir du prompt final, après la discussion client. L’utilisateur a demandé de privilégier l’API n8n et confirmé que cette intégration devait être réalisée directement sur le Pi, sans attendre sa VM éteinte. Aucun rôle Ansible existant n’a été testé ou appliqué.

## Résultat

Nouveau workflow **Ilyes - Prompt final vers OpenCode NOC**, ID `paramètre privé à consulter sur le Pi`, publié dans le projet personnel d’Ilyes. Il accepte le rapport d’analyse ou un prompt final saisi dans son formulaire privé. Le sous-domaine apparaît explicitement dans le prompt transmis à OpenCode. Le formulaire exige une confirmation de fin de discussion, l’approbation du prompt et le choix prototype/site complet.

Deux nœuds ont été ajoutés au workflow commercial actif `paramètre privé à consulter sur le Pi`, après **Rapport final de test**. La branche prépare le prompt seulement lorsque le brief et `opencode_ready` sont validés, sans questions essentielles/contradictions et avec un sous-domaine. Elle appelle le nouveau workflow sans attendre, pour ne pas bloquer Gmail. Ses nœuds et connexions d’origine sont préservés; une sauvegarde privée précède l’ajout. Aucun nouveau nœud d’envoi de message n’a été créé.

Une API TLS dédiée fonctionne sur `paramètre privé à consulter sur le Pi:8765`, accessible uniquement depuis le réseau Docker n8n. Le service `n8n-opencode-bridge.service` utilise le compte Yanis, sans capabilities ni acquisition de privilèges et avec des écritures limitées par systemd. Deux connexions n8n dédiées conservent l’authentification et le certificat de confiance, sans désactiver TLS. Ni Caddy, ni les ports Freebox, ni les conteneurs n8n n’ont été reconfigurés ou redémarrés.

## Cibles et limites

Le registre `paramètre privé à consulter sur le Pi` est **vide à la livraison** : aucune ancienne destination N0C n’a été adoptée. Pour chaque nouveau projet, préparer le sous-domaine et une racine de préparation sur N0C, vérifier leur association et enregistrer la cible avec `register-target.py`. La commande contrôle la clé d’hôte SSH et le chemin canonique, sans modifier N0C. Elle ne crée aucun sous-domaine et ne prouve pas à elle seule son association au dossier.

OpenCode travaille depuis `NOCAgentControl`, selon le parcours planificateur → implémenteur → revue. Le runner impose le domaine, l’alias et la racine enregistrés, évite les doubles lancements, refuse des travaux simultanés sur une même racine, limite temps/sortie et ne relance pas automatiquement un résultat incertain. Le statut final reste `completed_review_required`; aucune publication ou transaction réelle n’est autorisée. Les consignes d’agents ne remplacent pas un compte N0C limité.

Après interruption du Pi/service, inspecter les processus et sessions avant de réparer un état bloqué. Le certificat TLS privé expire le **11 octobre 2027**; renouveler le certificat et la connexion de confiance n8n avec marge.

## Réalisation et validation

OpenCode, lancé depuis PIAgentControl, a préparé les quatre fichiers initiaux avec implémentation et revues. Codex a examiné les fichiers réels et corrigé des défauts non détectés par cette revue : mode du formulaire, format des données retournées, paramètres SSH, propagation de la commande forcée et reconnaissance des événements CLI. Le transport final utilise HTTPS privé, avec authentification dédiée et certificat vérifié. Codex a ajouté le service, l’enregistrement des cibles, le raccordement API et les tests complémentaires.


**Aucune construction réelle N0C n’a été déclenchée pour ces tests.** Le parcours d’approbation et une construction complète restent à vérifier avec la première cible autorisée. La préparation déléguée a consommé des appels OpenCode; les tests de construction utilisent un exécutable factice et n’appellent pas les modèles.

## Sources et reprise

Sources actives : `paramètre privé à consulter sur le Pi`. Fichiers publics : `runner.py`, `server.py`, `workflow.json`, `commercial-guard.js`, `register-target.py`, `n8n-opencode-bridge.service`, `README.md`, `.gitignore`, `tests/test_runner.py`, `tests/test_workflow.js`. Le filtre commercial installé a également été exercé avec des fixtures sans exécuter le workflow Gmail : domaine du prompt, domaine collecté, saut de ligne et questions bloquantes. Copie publique Windows dans `n8n-services/integrations/opencode/`; l’état Git actif est celui du Pi. Aucun commit/push réalisé.


Retour arrière : désactiver le nouveau workflow et le service privé; restaurer puis publier la sauvegarde privée `commercial-workflow-before-opencode.json`, après inspection des exécutions. Préserver les journaux et les accès d’un travail potentiellement encore actif.
