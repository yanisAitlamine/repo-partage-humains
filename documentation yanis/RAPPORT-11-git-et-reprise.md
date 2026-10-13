> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 11 — Git, sauvegarde hors Pi et AGENTS figé

**11 octobre 2026.** Nouvelle demande : versionner les travaux récents, les workflows et la procédure de reprise après destruction du Pi ; figer le `AGENTS.md` global et déplacer les informations de passation vers un fichier distinct. Commit/push et création d’une sauvegarde hors Pi sont autorisés. Aucun rôle Ansible existant testé/appliqué, aucune construction N0C lancée.

## Git




## Sauvegarde privée indépendante du Pi

Le helper de production `n8n-sauvegarder` a créé **`snapshot-paramètre privé à consulter sur le Pi-192541.cBTEWf`**, avec arrêt gracieux temporaire puis retour des services. Aucun workflow en exécution ni travail OpenCode actif n’était présent au contrôle. L’API bridge a été arrêtée pendant cette première collecte puis redémarrée ; n8n healthy, runners, Caddy, VPN et bridge confirmés actifs après l’opération.



Le déchiffrement réel a été vérifié, puis les trois archives du snapshot contrôlées par SHA256, la base n8n testée avec `PRAGMA integrity_check` et les 11 workflows retrouvés. Base OpenCode supplémentaire également intègre. Les tests publics de chiffrement comprennent mauvais destinataire, altération, troncature et refus d’écrasement. Les tests de chemins refusent traversée, chemin absolu, doublon et lien. **Cinq tests passent.** La vérification réelle sur Windows a détecté un verrou SQLite lors du nettoyage ; la fermeture explicite des connexions a été corrigée et la vérification complète a ensuite réussi.


## AGENTS et passation

**Le contenu du `AGENTS.md` global n’a pas changé.** SHA256 : `paramètre privé à consulter sur le Pi`. `tools/protect-agents.ps1` applique attribut lecture seule et ACL refusant écriture/suppression ordinaires pour le compte courant. Une ouverture en écriture a effectivement été refusée, sans écrire d’octet. `.githooks/pre-commit` contrôle cette même empreinte sur le fichier de travail et l’index. Après clone, activer le hook et réappliquer l’ACL Windows ; Git ne transporte pas l’ACL.

**`PASSATION.md`** reçoit désormais dernier rapport, état récent et informations pour le prochain agent. `ARCHITECTURE.md` et le README orientent la reprise vers ce fichier ; l’ancienne consigne de réécriture d’AGENTS dans l’architecture a été remplacée. Aucun agent ne doit modifier le global ou lever sa protection. Ce verrou n’est pas une isolation contre un propriétaire/administrateur capable de modifier l’ACL ou désactiver Git ; la séparation des comptes est nécessaire à une garantie contre un agent utilisant volontairement les mêmes privilèges.

## Parcours et limites


Les helpers `extract-private.py`, `restore-extra.py` et `restore-bridge.sh` préparent une restauration explicite sur une nouvelle machine, sans démarrage automatique des services. **Une reconstruction complète sur une cible jetable n’a pas été exécutée** ; ne pas annoncer une reprise testée de A à Z. Déchiffrement et intégrité sont validés, pas l’ensemble du provisionnement. Toujours vérifier IP/domaines, renouvellements, comptes tiers/OAuth et opérations externes avant réactivation. La VM reste éteinte et les tests Ansible réservés à Yanis.
