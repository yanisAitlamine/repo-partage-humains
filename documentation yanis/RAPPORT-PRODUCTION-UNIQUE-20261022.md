<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Production applicative unique : clarification documentaire — 22 octobre 2026

## Demande et résultat

Yanis a corrigé la review du projet : la production applicative se déploie
**uniquement sur prod-1**. Le Pi a pour rôle cible exclusif le **load balancer /
reverse proxy HTTPS, le VPN et le DNS interne**. Développement, corrections et
recettes restent sur des VM de lab distinctes. L'ancienne obligation d'aligner
les applications entre Pi et prod-1 est remplacée.

La documentation publique porte désormais cette décision dans les points où
commencent les humains et les agents :

| Point d'entrée | Pourquoi la règle doit y être visible |
| --- | --- |
| [README du dépôt](../README.md) et [sommaire](SOMMAIRE-PUBLIC.md) | Orienter immédiatement un lecteur humain vers l'organisation actuelle. |
| [AGENTS du dépôt](../AGENTS.md) et [fiche de reprise](REPRISE-AGENTS.md) | Donner la même cible aux agents avant leur mission. |
| [Architecture](ARCHITECTURE.md) et [passation](PASSATION.md) | Distinguer rôle cible, état hérité et preuves historiques. |
| [Implémentation](GUIDE-IMPLEMENTATION.md), [continuité](PROCEDURE-CONTINUITE-RUN.md) et [reprise](PROCEDURE-REPRISE-ACTIVITE.md) | Éviter qu'une procédure prépare ou restaure des applications sur le Pi. |
| [Workflows](WORKFLOWS-PIPELINE-PRINCIPAL.md), [bridge](BRIDGE-N8N-OPENCODE-REFERENCE-TECHNIQUE.md) et [worker](WORKER-TELEGRAM-REFERENCE-TECHNIQUE.md) | Prévenir une réinstallation fondée sur un ancien emplacement applicatif. |

Les rapports datés restent conservés sans réécriture des preuves. Les points
d'entrée actuels expliquent que leurs anciennes prescriptions de déploiement
sur le Pi, de Pi utilisé comme lab ou d'alignement applicatif sont dépassées.

Cette mission publique est documentaire : aucun service, code, configuration,
secret ou donnée n'a été modifié ; aucun déploiement ni test runtime n'a été
exécuté. Les applications, sources et archives encore présentes sur le Pi ne
sont pas déplacées ou retirées par cette correction. Une règle écrite ne prouve
pas à elle seule que le nettoyage opérationnel est terminé.

La finalisation par l'orchestrateur a aussi corrigé les consignes globales
protégées du poste, les trois points d'entrée partagés des agents, les références
humaines privées et les points d'entrée des sources applicatives et réseau.
La fiche de reprise publique, celle du poste et celle du journal partagé sont
identiques, vérifiées par empreinte. Les corrections documentaires sont publiées
dans les branches principales des cinq dépôts sources concernés, par mises à
jour normales sans forcer l'historique. Les copies de travail accessibles en
production et au lab portent également le rappel ; les sources modifiées avant
mission sont préservées. Les identifiants internes et chemins précis restent
dans les références privées.

## Orchestration et délégation

L'orchestrateur Codex a confié ce périmètre à un sous-agent interne dédié à la
documentation publique. Ce sous-agent a lu les consignes applicables, vérifié
le clone et sa branche distante, corrigé les treize fichiers publics réservés,
puis relu les différences et les liens. Le périmètre privé et les points
d'entrée des environnements sont traités séparément par l'orchestrateur et un
autre sous-agent. Aucun lancement OpenCode depuis PIAgentControl n'a été effectué.
Le modèle exact n'est pas consigné par cette mission ; aucun coût n'est déduit.

L'orchestrateur a revu ces résultats, corrigé les contradictions globales et
privées, synchronisé la reprise, rétabli les ACL et la lecture seule des
consignes protégées et publié les corrections Git des sources. La comparaison
des commits confirme que ces derniers ne changent que des fichiers Markdown.

## Coopération et adaptation au contexte

Le protocole, l'état et les annonces pertinentes ont été consultés avec
l'identité personnelle autorisée. L'intention de la sous-session documentaire
publique, rattachée à celle de l'orchestrateur, a réservé explicitement les
treize fichiers modifiés. Les travaux Cleanova du collaborateur concernent
d'autres chemins ; leurs fichiers et les rapports existants restent préservés.

La review précédente mélangeait une ancienne prescription d'alignement et
l'état hérité du Pi avec la cible actuelle. La correction humaine est désormais
en tête des références actives ; la présence d'archives ou de sources sur le Pi
est distinguée d'un droit ou d'une cible de déploiement applicatif. La revue
porte sur le contenu documentaire, les différences, la cohérence et les liens ;
elle ne certifie aucune migration opérationnelle. Une annonce de fin libère
les réservations publiques après la publication Git vérifiée.

Une annonce explicite demande aux agents dont les sessions sont déjà ouvertes
de relire la décision actuelle. La disponibilité de la règle dans leurs points
d'entrée est vérifiée ; la lecture de chaque session distante n'est pas attestée
sans accusé. Le présent résultat ne prétend pas avoir modifié leurs contextes
déjà chargés ni tous leurs fichiers locaux inaccessibles.
