<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 15 — Dossiers de lecture et contrôleur Kali

11 octobre 2026. Yanis demande le rangement du projet et la préparation de Kali
pour réaliser lui-même un redéploiement sur une autre VM. Cible prévue : Debian
13 ARM64, compatible avec les binaires du Pi. Aucun déploiement lancé.

## Où lire et où travailler

`Humain/` contient seulement les rapports et l'architecture globale, en Markdown
et PDF. Le dernier rapport donne les opérations récentes et la suite à réaliser.
`Technique/` regroupe les sources, outils, procédure de reprise, illustrations
et anciens scripts. La racine conserve les consignes globales protégées,
la passation et de petits points d'orientation pour les prochains agents.

Les anciens scripts sont rangés dans `Technique/archives/n8n/` ; ils servent
de contexte et ne sont pas des commandes actuelles à appliquer en production.
Les temporaires et fichiers privés locaux sont conservés à part, ignorés par Git.
Aucun secret n'est affiché, versionné ou transmis à Kali. Les sauvegardes privées
restent dans les coffres Windows existants. Aucun fichier utile supprimé.

Le dépôt privé existant conserve cette organisation sur `project-context` ;
créer un dépôt supplémentaire n'était pas nécessaire. Les sources n8n et les
workflows restent sur `main`, DevLinuxSetup et NOCAgent dans leurs dépôts propres.
Les chemins de production sur le Pi restent inchangés. Le registre des déplacements
est `Technique/outils/deplacements-paramètre privé à consulter sur le Pi.json`.

## Kali préparée

Accès SSH vérifié : `[ADRESSE-MAIL]`. Python système 3.14 et Ansible bêta conservés.
Environnement isolé : `paramètre privé à consulter sur le Pi`, Python 3.13.14,
ansible-core 2.19.14 ; community.docker 5.4.0 et sa dépendance
community.paramètre privé à consulter sur le Pi 1.1.5 dans le chemin utilisateur standard.

Les clones propres sont dans `paramètre privé à consulter sur le Pi` :

| Dossier | Branche | Commit livré |
| --- | --- | --- |
| DevLinuxSetup | master | paramètre privé à consulter sur le Pi |
| n8n-services | main | paramètre privé à consulter sur le Pi, puis actualisation documentaire |
| NOCAgentControl | main | paramètre privé à consulter sur le Pi |
| project-context | project-context | Organisation de cette livraison, rapports et sources VPN/Pi |

Les anciens clones `paramètre privé à consulter sur le Pi` sont laissés intacts. GitHub n'est pas authentifié
depuis Kali ; les clones ont été initialisés à partir de bundles publics transmis

## Ton futur essai sur Debian 13 ARM64

1. Créer une VM ARM64 Debian 13 dédiée et relever son IP ainsi que son empreinte
   SSH depuis sa console. Préparer le compte `yanis` UID/une référence interne, une clé publique
   de connexion et sudo. Garder ce test isolé de la production et de ses domaines.
2. Sur Kali, ouvrir `paramètre privé à consulter sur le Pi` et activer l'environnement :
   `source paramètre privé à consulter sur le Pi`.
3. Lire les README Ansible des trois dépôts, copier leurs exemples dans les
   emplacements locaux ignorés, puis renseigner uniquement la VM de test.
   Vérifier l'adresse avant chaque commande ; les exemples ne ciblent pas le Pi.
4. Réaliser toi-même les contrôles et essais des rôles sur cette cible neuve,
   puis une seconde exécution pour examiner l'idempotence. Ces essais n'ont
   pas été exécutés par les agents.
5. Pour tester les données réelles, suivre la procédure détaillée
   `Technique/documentation/REPRISE.md` dans le clone project-context.
   Déchiffrer depuis Windows avec la clé conservée dans le coffre ; transférer
   seulement vers un dossier privé de la nouvelle cible. Ne pas confier la clé
   à Kali. Conserver les workflows inactifs avant tout premier démarrage.
6. Adapter consciemment les IP et interfaces restaurées. Ne pas réutiliser l'IP
   LAN du Pi ni déplacer DuckDNS ou le NAT Freebox pour un simple test de reprise.
   La recette Ansible de provisionnement et la restauration complète sont deux
   parcours distincts : le rôle neuf refuse d'adopter une instance existante.
7. Consigner les résultats, différences et limites dans un nouveau rapport.
   Un clone Git ou un contrôle d'intégrité ne prouve pas une reprise réussie.

## Délégation

Agent Codex `prepare_kali`, modèle explicitement demandé GPT-6 Luna : lecture
des consignes et README actifs, inventaire Kali, environnement Python/Ansible,
collections et clones isolés. Périmètre : environnement utilisateur Kali et
un compte rendu local. Aucun droit de déployer, lancer des tests de rôles,
modifier les secrets ou les services du Pi. Aucun sous-agent créé par cet agent.

Codex principal : inventaire Windows, rangement avec contrôle des destinations,
correction des liens et outils, transmission de bundles publics depuis le Pi,
lecture du compte rendu, vérification indépendante du contrôleur, intégration
de la documentation/PDF et publication Git. La préparation ne nécessitait pas
de mission OpenCode sur le Pi : seules des lectures Git et exports publics y
ont été exécutés. Aucun coût de délégation annoncé sans mesure fiable.

Compte rendu technique détaillé : `Technique/documentation/preparation-kali.md`.
Constat utile de l'agent : Python système 3.14 ne convient pas à ansible-core
2.19 ; Python 3.13 déjà installé a permis d'éviter un changement système.

## Vérifications et limites

Version du contrôleur et liste des collections, commits et propreté des clones,
différences et exclusions Git, empreinte/protection du global, liens et PDF
contrôlés. Aucun playbook, syntax-check, lint, mode check ou test de rôle lancé.
Aucun service du Pi redémarré. La VM cible n'existe pas encore dans l'inventaire ;
son accès SSH et la reprise réelle restent à valider par Yanis.
