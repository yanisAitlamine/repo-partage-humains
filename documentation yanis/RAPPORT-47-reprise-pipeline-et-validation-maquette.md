<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Reprise du pipeline et livraison d’une maquette — 15 octobre 2026

## Demande et résultat

Yanis demande de reprendre le diagnostic des erreurs reçues sur Telegram après
une réponse humaine correcte, de corriger les causes puis de refaire le parcours
par un nouveau mail : intervention en cas de doute, reprise, maquette, validation
humaine et livraison du lien.

Les dernières exécutions montrent que la réponse humaine et la reprise
commerciale avaient réussi. L’échec se produisait ensuite dans la construction :
la revue avait trouvé une interpolation HTML non sûre, puis la commande SSH
destinée à la corriger était mal citée et avait été refusée avant exécution.
Un candidat préparé et relu dans la mission précédente était resté non installé.

Le correctif est intégré dans `integrations/opencode/runner.py` et
`integrations/opencode/tests/test_runner.py`. L’enveloppe opérateur fournit
un transport de script distant par entrée standard et heredoc local cité,
avec contrôle des frontières et du délimiteur. Elle demande des nœuds DOM,
`textContent` et des gestionnaires enregistrés pour les données saisies.
Les permissions, la cible et les validations humaines ne sont pas élargies.

Les 38 tests du runner passent après installation. La comparaison AST confirme
que seul `make_prompt` change dans le module actif. Des préimages sont conservées
hors Git ; aucun service n’a été redémarré. Ces tests vérifient le contrat et
des frontières de syntaxe, pas le comportement de tous les futurs modèles.

Un nouveau cas fictif a ensuite parcouru toute la chaîne réelle :

- Mail envoyé avec le plugin Gmail vers le compte de test.
- Doute volontaire sur un choix ; demande Telegram et arbitrage humain réel.
- Confirmation de l’aperçu, un seul envoi humain, reçu Gmail confirmé.
- Reprise automatique environ trois secondes plus tard ; brief accepté.
- Nouvelle maquette isolée, construction et revue indépendante terminées.
- Preuve machine : marqueurs exacts et mêmes octets entre index SSH et HTTPS.
- Validation finale effectuée par Yanis dans Telegram.
- Une seule livraison du lien, reçu Gmail valide, puis réception vérifiée dans
  le compte client de test avec le plugin Gmail.
- Notification Telegram finale « Maquette envoyée au client » confirmée.

Le workflow de construction termine avec succès. Un état local incertain après
le clic final est réconcilié par lecture vers la reprise confirmée ; aucun
second appel de reprise et aucun réarmement d’envoi ne sont effectués.
Les anciennes exécutions et réservations restent intactes.

La preuve concerne un scénario fictif complet. La lecture humaine du mail et
les interactions de la maquette dans un navigateur ne sont pas testées.
La revue du site est statique et vérifie ses contenus servis ; elle n’exécute
ni navigateur ni parseur JavaScript. Les modifications applicatives restent
non committées dans cette reprise. La publication de ce rapport ne les versionne
pas et ne constitue pas une sauvegarde indépendante.

## Orchestration et délégation

Codex reprend les lectures, vérifie le candidat existant, l’installe, exécute les
tests et suit le parcours. Aucun nouvel enfant Codex n’est lancé directement
pour cette reprise. Le candidat avait été préparé et relu par des enfants de
la mission précédente ; leurs rapports et empreintes sont recoupés, sans leur
attribuer de nouveaux travaux.

Le workflow de maquette lance son planificateur NOC habituel, qui confie la
construction à un implémenteur puis la lecture indépendante à un réviseur.
Les deux tâches sont observées terminées. Le rapport de revue et le résultat
du backend concordent sur les marqueurs, les empreintes et la sécurité DOM
statique. Les noms exacts des modèles n’ont pas été mesurés.

Les décisions Telegram appartiennent à Yanis. Aucune approbation humaine
n’est simulée. Aucune session PIAgentControl, connexion Kali ou exécution des
rôles Ansible réservés n’est lancée. Aucun coût ou gain n’est déduit.

## Coopération et adaptation au contexte

La reprise s’appuie sur les consignes du projet et des dépôts concernés,
l’architecture, la passation, le dernier rapport documentaire et les annonces
récentes de coordination. Une intention déclarative est publiée avant les
écritures, puis étendue pour ce rapport. Les réservations de notes de la mission
parent sont reprises explicitement ; les travaux des anciens réviseurs avaient
des fins publiées.

Les empreintes du candidat et des sources sont contrôlées avant installation.
Aucun job n’est actif à ce moment. Les changements préexistants, le brouillon
utilisateur distinct du workflow publié et les anciens états d’envoi sont
préservés. Le rapport candidat antérieur est conservé séparément.

La revue du nouveau site est achevée, mais sa publication de fin a été refusée
par la politique de son outil. Le parent constate cette limite dans le rapport
du réviseur et clôt explicitement cette réservation en qualité d’opérateur,
sur preuve de fin de tâche ; aucune permission n’est élargie pour contourner
ce refus.

Le navigateur a d’abord servi à préparer le mail. Après la précision de Yanis,
l’envoi et la vérification de réception utilisent le plugin Gmail. Le brouillon
préparé est envoyé une seule fois. La passation et les preuves privées sont
actualisées ; cette version publique omet les coordonnées, chemins d’accès,
identifiants internes et contenus de messages. Seuls ce rapport et son entrée
de sommaire sont inclus dans la publication documentaire.
