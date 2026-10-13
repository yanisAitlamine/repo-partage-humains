> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 17 — Raccordement OpenCode et cible de test unique

12 octobre 2026. Yanis demande de raccorder la construction OpenCode à
`TEST AUTO - Assistant Gmail et Telegram`, sans modifier ce workflow sur lequel
travaille l’agent d’Ilyes. Il autorise le remplacement du site du sous-domaine
test pour ses prochains essais, la sauvegarde des règles NOC de production,
leur remplacement par des règles plus restrictives et la synchronisation des
dépôts Windows, Pi et Kali. Aucun email de test envoyé par Codex.

## Raccordement et cible

La chaîne existe déjà : `paramètre privé à consulter sur le Pi` (Assistant Gmail et Telegram) appelle
`paramètre privé à consulter sur le Pi` (analyse commerciale), qui appelle `paramètre privé à consulter sur le Pi`
(Prompt final vers OpenCode NOC). Le filtre de raccordement exigeait auparavant
un domaine client, alors que le registre opérateur ne contenait aucune cible.

La cible de cette mission est exclusivement `paramètre privé à consulter sur le Pi
alias SSH `la cible de test`, racine `paramètre privé à consulter sur le Pi`.
SSH avec vérification de clé d’hôte et chemin canonique confirmés. Le contenu
HTTPS obtenu avec curl correspond octet pour octet au `index.html` distant :
SHA256 `paramètre privé à consulter sur le Pi`.
Le client HTTP Python a reçu 403, contrairement à curl ; la vérification
d’association repose sur la réponse curl 200 et son contenu exact.

Le registre privé contient désormais cette cible enabled/staging. Le filtre
commercial source force le domaine test même lorsque le brief ne fournit aucun
domaine. Les contrôles de brief suffisant, questions, contradictions et
`opencode_ready` sont conservés. Le workflow OpenCode impose la même cible dans
la normalisation, le lookup et le formulaire. Le runner rejette toute autre
combinaison domaine/alias/racine, même si le registre l’autorise, et revalide les
travaux avant le lancement du processus OpenCode.

La fin de discussion, l’approbation du prompt et le choix prototype/site
complet restent nécessaires. Les futurs travaux peuvent remplacer et mettre
en ligne uniquement le site TEST après sauvegarde restaurable distante dans
`paramètre privé à consulter sur le Pi`, hors racine web, avec modes
0700/0600 et contrôle des liens. Aucune construction ni suppression du site
actuel n’est lancée pendant cette préparation. Le drapeau historique
`publication_authorized=false` interdit la publication en production ;
l’autorisation du site test est distincte et limitée à la cible fixe.

## Consignes NOC

`NOCAgentControl/AGENTS.production.md` conserve exactement l’ancien `AGENTS.md`.
Comparaison indépendante avec `git show HEAD:AGENTS.md` réussie avant commit ;
SHA256 `paramètre privé à consulter sur le Pi`.
Cette sauvegarde est inactive, réservée à une restauration opérateur explicite.

Le nouveau `AGENTS.md` limite les missions au site test, interdit les autres
maintient le travail distant via SSH et le parcours planification →
implémentation → revue. Ces consignes et les validations du runner ne créent
pas une isolation du compte SSH de l’hébergement.

## Délégation

OpenCode a été lancé depuis `paramètre privé à consulter sur le Pi`, rôle
`planificateur`, avec un prompt autonome sans secrets. Session principale
`paramètre privé à consulter sur le Pi`, reprise corrective dans la même session.
Les métadonnées observées indiquent `openai/gpt-6-luna`.

| Session | Rôle et travail |
| --- | --- |
| `paramètre privé à consulter sur le Pi` | Implémenteur : runner, filtre commercial, tests, sauvegarde et règles NOC. |
| `paramètre privé à consulter sur le Pi` | Première revue : accès aux fichiers insuffisant ; aucune validation de code revendiquée. |
| `paramètre privé à consulter sur le Pi` | Implémenteur correctif : workflow OpenCode explicitement autorisé, règles NOC et prompt runtime. |
| `paramètre privé à consulter sur le Pi` | Revue autonome avec les différences fournies dans son contexte. |
| `paramètre privé à consulter sur le Pi` | Correctif annoncé sur les entrées et les préconditions de sauvegarde ; preuves finales non confirmées par le planificateur. |
| `paramètre privé à consulter sur le Pi` | Dernière revue sur un extrait ; constate que les consignes de sauvegarde ne sont pas un verrou mécanique. |

La première réalisation était partielle : l’implémenteur avait confondu
l’artefact OpenCode autorisé avec le workflow Assistant interdit. Codex a
clarifié les IDs, demandé la modification du bon artefact et fait retirer les
interdictions de publication contradictoires avec la demande de site test.
La première revue sans accès n’a pas été assimilée à une revue réussie.
Le planificateur a terminé la reprise sans pouvoir certifier l’état final sur
disque. Codex a donc relu les différences réelles et exécuté lui-même les
contrôles. Le correctif de normalisation aurait rejeté la sortie minimale du
filtre commercial ; Codex a ajouté uniquement les indicateurs déterministes
déjà validés au payload, sans transmettre les emails ni l’historique.
L’entrée opérateur manuelle reste possible uniquement lorsqu’elle provient du
nœud de formulaire authentifié effectivement exécuté ; elle doit ensuite
franchir l’approbation humaine du prompt exact. Une entrée inter-workflow ne
peut plus contourner les contrôles avec un simple `final_prompt`.
Codex a ajouté les tests traversant ces adaptateurs et le format réel du lookup,
clarifié que les sauvegardes restent distantes et rendu la sauvegarde des
consignes de production explicitement inactive. Le runner ne vérifie pas
mécaniquement l’existence/restaurabilité de l’archive avant de lancer OpenCode :
cette obligation est imposée au builder et doit être vérifiée lors du premier
travail réel. Aucune isolation SSH par racine n’est revendiquée.

Périmètre des agents : fichiers publics `integrations/opencode/` et consignes
NOC, tests isolés seulement. Aucun droit d’appeler l’API n8n, modifier ses
pousser. Les rôles Ansible, le global protégé et les changements existants dans
l’intégration API, la revue finale et la synchronisation. Aucun coût ou gain
de tokens annoncé sans mesure consolidée fiable.

## Vérifications et limites

Codex a exécuté indépendamment les 12 tests Python du runner et les fixtures
JavaScript : succès. Tests avec OpenCode factice, sans appel IA pour construire
un site. Ils couvrent notamment la cible fixe, les approbations, la concurrence,
l’idempotence, la revalidation des travaux, les délais et les sorties bornées.
Le lookup TLS réel depuis le conteneur n8n retourne 200 et la cible exacte.
Le smoke test final a utilisé les nœuds réellement publiés et ce lookup TLS :
filtre commercial → normalisation → résolution de cible → préparation du
formulaire approuvé → validation du runner. Succès, sans soumission de job.
Deux POST réels invalides ont reçu 422 : autre cible et absence d’approbation.
Ils n’ont créé aucun job ni lancé OpenCode.

La publication par API a changé uniquement le nœud existant
`Préparer le prompt final pour construction` de l’analyse commerciale et les
nœuds concernés du workflow OpenCode, en conservant leurs connexions,
identifiants et autres paramètres. Sauvegarde privée préalable, relecture des
versions avant écriture/publication, absence de brouillon non publié vérifiée.
Version commerciale publiée : `paramètre privé à consulter sur le Pi`.
Version OpenCode publiée : `paramètre privé à consulter sur le Pi`.
Le workflow Assistant Gmail et Telegram n’a reçu aucune écriture ; version
`paramètre privé à consulter sur le Pi` et empreinte de définition inchangées :
`paramètre privé à consulter sur le Pi`.
Aucun redémarrage de n8n, du bridge, de Caddy ou du VPN nécessaire/effectué.

Aucun test de rôle Ansible, playbook, lint Ansible ou syntax-check lancé.
Le premier parcours avec un véritable email, l’approbation humaine et une
construction NOC réelle reste le test de Yanis.

Les sauvegardes des définitions n8n avant intervention sont privées sous
`paramètre privé à consulter sur le Pi`, non versionnées.
Une restauration doit préserver les modifications ultérieures d’Ilyes : ne
pas réimporter aveuglément un workflow entier depuis une ancienne sauvegarde.

## Git et synchronisation

| Dépôt | Commit publié et livré |
| --- | --- |
| n8n-services, main | `paramètre privé à consulter sur le Pi` |
| NOCAgent, main | `paramètre privé à consulter sur le Pi` |
| DevLinuxSetup, master | `paramètre privé à consulter sur le Pi` (déjà actuel) |

Commits et push effectués depuis le Pi avec son accès GitHub existant. Les
définitions actuelles des 11 workflows, dont six versions publiées, ont été
exportées en lecture seule et versionnées comme snapshots inactifs, sans
identifiants privés ni données d’exécution. Les différences importantes des
workflows d’Ilyes représentent son état courant exporté, pas des modifications
de ces workflows par Codex.

Les copies Windows dans `Technique/sources/` ont été actualisées à partir
d’archives Git des commits, avec sauvegarde préalable des anciennes copies
DevLinuxSetup/n8n-services dans `Technique/temporaires/sync-paramètre privé à consulter sur le Pi/`.
La copie NOCAgentControl est ajoutée ; ces trois copies de référence ne sont
pas des clones Git. Les bundles transfèrent les historiques publics aux clones
Kali sans clé privée ni fichier runtime. Les trois clones de
`paramètre privé à consulter sur le Pi` et les trois clones concernés de `paramètre privé à consulter sur le Pi` ont été
actualisés en fast-forward, après contrôle de propreté. Aucun test Ansible sur
Kali. Les références du contexte Windows sont également transférées par bundle.

Changements étrangers conservés sur le Pi, exclus de ces commits :
`Technique/outils/configurer-dns-prive-windows.ps1` est conservé et exclu du
commit documentaire. Les dépôts ne sont donc pas artificiellement déclarés
tous propres pendant le travail des autres agents. Le global protégé conserve
l’empreinte attendue `paramètre privé à consulter sur le Pi`.
