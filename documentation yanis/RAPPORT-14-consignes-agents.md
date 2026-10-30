<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 14 — Nom unique des consignes

11 octobre 2026. Demande explicite de Yanis : utiliser uniquement `AGENTS.md`
pour les consignes et corriger les noms de fichiers, références et configurations.

## Changements

Les consignes complètes PIAgentControl sont conservées dans son `AGENTS.md`,
qui remplace le précédent point d'entrée court. Un seul fichier de consignes
subsiste dans cette base, sur Windows et sur le Pi. Les références et prompts
d'`opencode.json` chargent ce fichier ; le README décrit cette organisation.

La même consolidation est faite dans les sources DevLinuxSetup embarquées
dans `Ansible/roles/devlinuxsetup/files/control/`. Les deux listes de fichiers
du rôle et ses README décrivent désormais quatre fichiers publics. Aucun rôle
Ansible n'est exécuté, testé ni déployé ; la base Pi est corrigée directement
conformément à cette demande. Aucun service de production redémarré.

Les références documentaires, y compris le rapport précédent et l'architecture
PDF, sont corrigées. L'exception ciblée autorise la correction du fichier global ;
sa protection est rétablie avec une nouvelle empreinte, synchronisée dans
PASSATION, le hook, le helper et le manifeste public de reprise. Les anciennes
empreintes des rapports restent des preuves historiques datées.

## Délégation

Aucune session déléguée lancée pour cette correction mécanique déjà comprise.
Codex réalise directement l'inventaire, la consolidation sans perte des consignes,
les remplacements, la lecture des différences et la publication Git. Aucun modèle
OpenCode appelé pour implémenter ; aucun coût API de délégation annoncé.
Ce choix correspond à l'exception prévue pour les petites corrections.

## Vérifications et limites

Recherche des noms et références dans les sources et documents actuels ; contrôle
JSON des deux profils corrigés ; diagnostic OpenCode sans prompt payant ; lecture
statique des listes Ansible ; vérification des différences Git et des branches
publiées. PDF régénéré, texte contrôlé et page concernée relue visuellement.
Les consignes complètes sont conservées à l'identique lors de la consolidation.

Les anciens commits Git et archives privées de récupération restent historiques :
ils ne sont pas réécrits. Une reprise depuis l'archive privée restaure l'état privé,
puis utilise les dernières sources et configurations publiques publiées dans Git.

Empreinte globale rétablie : paramètre privé à consulter sur le Pi. DevLinuxSetup publié : paramètre privé à consulter sur le Pi. La modification distante préexistante de Yanis a été intégrée par rebase, sans écrasement ni push forcé.
