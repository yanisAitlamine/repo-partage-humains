> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 25 — Informer les clients des fonctions disponibles

12 octobre 2026. Yanis demande une explication du blocage d'le contact de test, puis limite la modification à la consigne des agents : expliquer les fonctionnalités de réception et de lecture non intégrées et proposer une alternative disponible. Après interruption, il demande expressément de reprendre sans MCP. Aucune validation de revue ou exécution commerciale n'est demandée dans cette reprise limitée aux consignes.

## Cause du blocage et capacités constatées

Le code de rattachement commercial déclenche une revue dès que `attachment_review.requires_clarification` est vrai, même si la liste des incohérences est vide. Le message « contradiction détectée » est donc trop général. Dans le cas inspecté, le document annoncé n'était pas disponible dans le message; cette absence a entraîné une demande de précision, puis le garde a bloqué le parcours. Il ne s'agissait pas d'une ambiguïté entre plusieurs projets. La règle de revue n'est pas modifiée par cette mission.

Le workflow actif sait déjà lire certaines pièces jointes directes : texte de PDF, fichiers texte, plusieurs formats Office et tableaux, ainsi que certaines images. Limites encodées : cinq fichiers au maximum, 5 Mio chacun et 10 Mio au total, avec refus des formats ou contenus non compatibles. Ces capacités de code ne prouvent pas la lecture réussie de tout fichier. Aucun lecteur de lien Google Drive ou autre stockage partagé n'a été intégré. Recevoir un lien ou une invitation ne signifie pas disposer de son contenu.

## Changement publié

Le workflow commercial `paramètre privé à consulter sur le Pi` est actif et publié en version `paramètre privé à consulter sur le Pi`, contre `paramètre privé à consulter sur le Pi` avant intervention. Trois ajouts de texte uniquement :

- `Comprendre le besoin et conseiller le client`, dans son message système.
- `Structurer les decisions commerciales`, dans son message système.
- `Accueillir et orienter le nouveau besoin`, dans son message système.

La politique impose de décrire les capacités effectivement intégrées, de ne jamais prétendre avoir ouvert un Drive, de ne pas demander simplement le même lien ou un élargissement des permissions et de proposer du texte directement dans le mail ou une pièce jointe compatible. Elle ne prétend pas que toutes les pièces jointes sont refusées. Elle s'appuie sur les résultats de lecture reçus, explique les fichiers absents/refusés/incomplets et n'invente pas de contradiction pour une simple absence. Une fonction future du site client reste une possibilité à discuter, distincte des outils actuels de collecte.

Formulation proposée par la consigne, à adapter au contexte : « Nous ne pouvons pas encore consulter les documents via Google Drive dans ce parcours. Vous pouvez copier le cahier des charges dans votre réponse, ou le joindre directement en PDF contenant du texte. » Cette limite ne doit pas être répétée dans chaque email lorsqu'elle n'est pas pertinente.

## Vérifications et limites

Intervention par SSH et API locale n8n, avec authentification utilisée uniquement en mémoire par le helper opérateur existant; aucune valeur d'identifiant n'est affichée, copiée dans un prompt ou versionnée. Aucun outil MCP utilisé pendant cette reprise. Le workflow live a été sauvegardé avant modification, version courante et publiée concordantes. Le script refuse un changement concurrent avant PUT.

Les comparaisons avant/après confirment que chacun des trois textes est exactement l'ancien texte suivi du bloc public; tous les autres paramètres et nœuds, les connexions et les settings sont conservés. Le workflow garde 81 nœuds. Après sauvegarde et activation API, la relecture confirme `active=true` et `activeVersionId=versionId`. Les exports inactifs et empreintes manifest sont actualisés; `git diff --check` sur les exports de mission réussit.

Aucun appel IA payant, test de mail, reprise d'exécution, approbation de revue, téléchargement externe, construction OpenCode, modification de relance, service, réseau ou Ansible. La rédaction réelle des agents sera à observer sur un prochain message; une consigne publiée n'est pas une preuve de conformité de toutes les réponses futures. La revue déjà créée pour le contact de test reste en attente et le texte qui y est enregistré n'a pas été réécrit. Aucun commit ou push.

## Sources et retour arrière

Politique et guide actifs dans `paramètre privé à consulter sur le Pi`. Exports `workflows/draft/paramètre privé à consulter sur le Pi.json`, `workflows/published/paramètre privé à consulter sur le Pi.json` et entrée correspondante du manifest actualisés. Copies Windows synchronisées dans `Technique/sources/n8n-services/`. L'outil opérateur est conservé sous `Technique/outils/capacites-clients.py`, avec la politique publique dans `politique-capacites-clients.txt`.

Snapshots privés avant/après et candidat dans `paramètre privé à consulter sur le Pi`, fichiers root-only hors Git. Retour arrière possible par la version antérieure, ou par restauration ciblée des trois textes, en préservant toute évolution ultérieure; ne pas réimporter aveuglément un export daté. Les autres modifications Git de l'utilisateur sont conservées, ainsi que les travaux d'Ilyes sur ses copies indépendantes.

## Délégation

Correction ciblée de trois consignes déjà comprises, réalisée directement par Codex. Aucune session OpenCode ni sous-agent lancé pour cette mission : il ne s'agit pas d'une nouvelle implémentation substantielle de lecteur ou de parcours. Le diagnostic, la politique, les assertions de préservation, la publication API, les exports et la documentation sont effectués par Codex. Les essais comportementaux payants ne sont pas lancés pour cette petite modification; aucune mesure de coût ou économie n'est revendiquée.

Coordination sous l'identifiant local déclaré `paramètre privé à consulter sur le Pi`, intention `paramètre privé à consulter sur le Pi`. Les intentions d'Ilyes concernent la préparation de lecteurs Drive sur ses copies sans publication; elles respectent explicitement la réservation des trois prompts et n'étendent pas les capacités actuelles de production. Le global Windows AGENTS reste intact.
