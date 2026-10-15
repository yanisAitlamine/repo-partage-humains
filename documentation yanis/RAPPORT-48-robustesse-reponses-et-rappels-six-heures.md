# Réponses humaines contrôlées et rappels à six heures — 15 octobre 2026

## Demande et résultat

Yanis demande des tests automatiques sans devoir répondre lui-même sur Telegram :
une réponse correcte doit permettre la reprise jusqu’à la review ; une réponse
incohérente ne doit pas partir au client ; une absence de réponse doit provoquer
un rappel après six heures. Les reviews doivent aussi être rappelées.

Les traitements sont installés dans le poller existant. Le texte humain est
contrôlé avant l’aperçu et avant la réservation Gmail. Le verdict est lié au texte
exact, à l’action et au contexte de la revue. Une modification invalide l’accord ;
sa réutilisation est limitée à quinze minutes. Un refus, une incertitude, une
réponse technique invalide ou une indisponibilité bloque Gmail et demande une
reformulation. Le système ne réécrit pas le texte à la place de l’opérateur.

Le nouveau service privé réutilise le modèle GPT déjà présent dans le dialogue.
Il retourne quatre booléens avec un schéma strict ; le parseur contrôle aussi le
statut terminé, l’unicité de la sortie, les clés, les types et l’absence de refus.
Le verdict est ensuite dérivé par le code. Le paramètre de stockage des réponses
est désactivé, comme la conservation des données d’exécution n8n de ce service.
L’authentification interne existante est réutilisée sans nouveau droit ou valeur
secrète exportée. Le format suit la
[documentation officielle Structured Outputs](https://developers.openai.com/api/docs/guides/structured-outputs?api-mode=responses).

Un premier contrôle textuel avec Jev refusait excessivement certaines réponses
correctes. Les essais et leurs échecs sont conservés dans les preuves privées.
Ce candidat n’est pas activé dans le worker. GPT contrôle finalement la réponse
humaine ; Jev conserve la décision métier sur le brief, avec ses seuils antérieurs.

Les rappels sont conservés dans SQLite et exécutés par la boucle existante :
premier rappel après six heures, puis toutes les six heures pour une étape
toujours en attente. Une nouvelle étape humaine recommence le délai. Les
reviews finales bénéficient du même mécanisme ; renouveler leurs boutons ne
réinitialise pas le compteur. Résolution, annulation, expiration ou changement
du contexte arrêtent les rappels. Aucune absence de réponse n’autorise l’envoi.

Une réservation durable précède Telegram. Un accusé de réception perdu ne
provoque pas un nouvel essai dans la même fenêtre. Le redémarrage conserve
l’échéance ; une indisponibilité ne déclenche pas une rafale de rattrapage.
Le délai réel dépend du prochain passage du poller et des services disponibles.

Les sources principales sont :

- `human_reply_guard.py` et les deux contrats JavaScript de validation.
- `review_reminders.py`, pour l’échéance et la réservation persistantes.
- `worker.py`, `decision_lab_native.py` et `build_approval.py`, pour les raccordements.
- `integrations/pipeline-e2e/`, pour le lanceur, les cas et leur documentation.

Les 23 tests Python nouveaux et le contrat JavaScript passent. Les régressions
existantes des quatre modules concernés passent également. Les 16 scénarios
intégrés passent depuis les sources installées avec le validateur GPT réel.
Les deux lots de texte fictif, douze puis dix cas, passent avec ce même contrôle.
Ils couvrent choix explicites, fautes et reformulations, clôture, absurdité,
insultes, hors sujet, réponse vague, consignes hostiles et engagements non autorisés.

**Limite du banc :** Gmail, Telegram et le parcours n8n/construction en aval sont
simulés. Les vrais modules de revue, de contrôle d’envoi, de réservation, de
reprise et d’approbation utilisent une SQLite temporaire ; le délai est avancé
avec une horloge injectée. Le banc ne démontre pas une nouvelle construction
réelle ni six heures d’attente physique. Il complète le précédent parcours réel,
sans le remplacer. Aucun callback fictif n’entre dans les demandes de production ;
aucun mail ou site réel n’est créé par cette campagne. Le petit corpus ne garantit
pas le classement de toutes les phrases futures.

## Orchestration et délégation

Codex réalise directement l’implémentation, les raccordements, les scénarios,
les tests, l’installation et les contrôles. Aucun sous-agent ou session
PIAgentControl n’est lancé pour cette mission. Les appels GPT et Jev des
évaluations sont des contrôles sémantiques, pas des sessions de délégation.
Le modèle GPT configuré est celui déjà observé dans le dialogue ; aucun coût
ou gain n’est déduit.

Les événements de test représentent volontairement des utilisateurs et un bot
fictifs dans le banc. Ils ne constituent jamais une décision humaine réelle.
Les tests vérifient aussi mauvais auteur, doublon, texte modifié après aperçu,
validation expirée, panne du validateur, reprise après redémarrage, expiration,
annulation et lecture incomplète de l’état distant.

## Coopération et adaptation au contexte

Les consignes, références et annonces récentes ont été relues. Une intention
déclarative est publiée avant les écritures et étendue pour le service privé,
le choix final du validateur, les exports et le rapport. Aucun chevauchement
d’écriture nouveau n’est observé.

Les modifications préexistantes sont capturées avant travail. Les empreintes
des sources et copies installées sont contrôlées avant installation. Aucune
opération d’envoi ou de confirmation n’est en cours au point contrôlé.
Le worker est arrêté brièvement, une sauvegarde SQLite cohérente et des
préimages privées sont conservées, puis les modules sont installés et le
worker redémarre une fois. Aucun état ancien d’envoi n’est restauré.

Le service reste actif sans redémarrage automatique. Sous son compte effectif,
le contrôle installé accepte une réponse correcte et refuse le texte absurde,
sans envoi Gmail ou Telegram. Les empreintes installées concordent ; la table
des rappels existe ; aucune demande fictive du banc ni nouveau job de construction
n’est constaté en production. Les journaux du contrôle final ne signalent ni
échec d’initialisation, ni erreur de scan des rappels, ni panne de polling.

Seuls les exports du nouveau service et son entrée de manifeste sont ajoutés.
Les trois graphes principaux et le brouillon utilisateur du constructeur restent
préservés. Le sanitizeur existant ne trouve aucun secret littéral dans ces exports.
Les sources applicatives restent modifiées et non committées ; les préimages
locales ne constituent pas une sauvegarde indépendante hors machine.

La passation est actualisée. Seuls ce rapport et son entrée de sommaire sont
publiés dans le dépôt humain public, après revue de confidentialité. Les détails
d’accès, configurations, identifiants internes et contenus clients restent privés.
Aucun accès Kali, test Ansible réservé ou changement des protections publiques
n’est réalisé.
