# Rapport 38 — Jev dans le vrai parcours commercial

14 octobre 2026 — auteur : Yanis / Codex.

## Demande et résultat

Après validation de la simulation mobile, Yanis a demandé que le parcours avec les agents de décision devienne le vrai workflow, puis que Codex s’arrête lorsque l’utilisateur peut faire son essai complet.

Le dialogue commercial est désormais actif et publié avec Jev. GPT conserve le triage, le conseil et la rédaction des réponses ; Jev sélectionne les citations du mail et de l’historique client, puis décide si la discussion doit continuer, si le brief suffit à une première maquette ou si une revue humaine est nécessaire. Les décisions incertaines restent bloquées. Un simple remerciement ou une demande de suivi ne relance pas une construction. Le prompt reprend les exigences sourcées du client.

Le vrai fil Gmail est relu, sans troncature silencieuse. Les messages effectivement envoyés par l’assistant restent distincts des exigences du client. Cela inclut les réponses saisies par un humain sur Telegram. Les données ou historiques insuffisamment attestés déclenchent une revue.

En cas de blocage, le bot existant présente le mail avec Stop et Continuer. L’utilisateur écrit sa réponse dans Telegram et confirme l’aperçu exact. Après réception Gmail SENT vérifiée, Stop ferme durablement le fil ; Continuer attend un nouveau mail du client et reprend ensuite le même parcours. Les destinataires TEST, le verrou, les réservations d’envoi et la validation humaine finale de la maquette sont conservés. Aucun accès public à n8n ni deuxième poller Telegram n’a été ajouté.

Un contrôle réel a révélé que l’authentification interne du bot et d’une connexion API était refusée. Elle a été réparée avec un accès enregistré du même principal, sans nouveaux droits ni modification du partage. Les files sont à nouveau lisibles par le service. Sauvegardes privées du code et de l’état avant installation ; l’état des envois n’a jamais été restauré.

Vérifications effectuées : 41 cas de l’adaptateur de décision, 56 du moteur, 37 de la liaison production, 4 des hooks, 47 régressions historiques Linux et 29 natives Linux réussis. Les corps Code du graphe enregistré compilent. Jev a réellement classé les trois états sur des mails fictifs. Les bancs intégrés ont vérifié rédaction adaptée, blocage sans rédaction automatique, fermeture sans appel fournisseur, lecture réelle du contrôle et appel entre les projets concernés. La publication a été relue ; le bot est actif. Les bancs temporaires ont été archivés et leurs autorisations retirées.

Le parseur structuré natif a rejeté des réponses alors que le modèle avait produit un JSON valide. Il a été remplacé pour cette nouvelle rédaction par un contrôle JSON direct strict ; un format invalide revient en revue humaine et désactive toute génération.

Le parcours est prêt pour l’essai de Yanis. Ces vérifications ne constituent pas un essai réel complet client → Telegram → Gmail → réponse client → maquette. Aucun mail, notification Telegram ou site n’a été envoyé ou construit durant cette vérification de production. Le parcours reste en TEST ; les pièces jointes et histoires non attestées demandent une revue. L’unicité ne couvre pas un écrivain externe qui contournerait le verrou. Les rôles Ansible n’ont été ni testés ni déployés.

## Orchestration et délégation

Codex a essayé la base OpenCode prévue par le projet. Les tentatives n’ont pas fourni de session terminée ni de résultat intégré attesté ; aucun travail ne leur est attribué.

Le relais a utilisé trois agents natifs : un agent d’implémentation de l’adaptateur et du graphe, un agent de liaison Telegram et installation, puis un agent de revue indépendante. Le modèle hérité de ces agents n’a pas été attesté séparément. L’agent de l’adaptateur a préparé les sources, les tests, le générateur du graphe et un banc fictif. L’agent Telegram a préparé la réservation durable, la politique Gmail, les tests de lifecycle, l’installation avec sauvegarde et un contrôle de lecture sans effet. La revue a examiné le rattachement, les autorisations, la clôture et la rédaction. Les premiers constats ont été vérifiés ou corrigés ; aucun blocage concret restant n’a été identifié dans la dernière revue statique.

Codex a assuré les lectures privées, les appels réels Jev, les tests n8n, les réparations d’authentification, les hooks du poller, la correction du parseur, les gardes de fermeture et de première maquette, l’installation ciblée, les publications et les lectures de confirmation. Le modèle GPT de rédaction conserve sa configuration Luna existante. Les résultats délégués ont été intégrés et vérifiés ; les preuves externes restent celles de Codex, distinctes de la revue statique. Aucun coût ou gain n’est estimé.

## Coopération et adaptation au contexte

Les consignes de reprise, architecture, passation, références n8n et règles de coordination ont été relues. Les annonces d’Ilyes ont confirmé que ses corrections PDF, Drive, mémoire et parcours après maquette restaient sur des candidats indépendants. Elles n’ont pas été annoncées comme déjà disponibles dans ce nouveau parcours. La différence entre brouillon et version publiée du constructeur a été constatée ; son parcours publié existant a été conservé.

Les intentions ont annoncé le périmètre des décisions, du poller et de la liaison humaine. Les extensions d’authentification ont été annoncées au moment du diagnostic. Les nouvelles annonces et les versions ont été vérifiées avant publication. Les travaux et exports non concernés ont été préservés. Les sources, exports ciblés et documentation de reprise ont été enregistrés ; le rapport public ne contient ni secrets, ni identifiants internes, ni contenus clients. La fin de mission libère les réservations. La prochaine preuve attendue est l’essai complet de Yanis.

