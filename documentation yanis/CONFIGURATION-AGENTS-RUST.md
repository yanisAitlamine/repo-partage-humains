# Configuration des agents et des modèles — Rust

La politique actuelle attribue les rôles suivants. Le niveau de raisonnement configuré est `medium`.

| Rôle | Modèle | Entrées et résultat |
| --- | --- | --- |
| analyze, chat-decision, source-reading | openai/gpt-6-luna | Conversation et sources → décision structurée ou demande de précision |
| specification | openai/gpt-6-astra | Contexte complet et décision suffisante → cahier des charges de réalisation |
| generate_private, art-direction, review, implementation, deployment | openai/gpt-6.1-terra | Cahier des charges, sources et version approuvée → artefact, revue ou publication par outil |

La politique qui fait foi est [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/bridge/integrations/opencode-engine/model-policy.json](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/bridge/integrations/opencode-engine/model-policy.json). Le transport applique le rôle au modèle principal et à ses outils ; le modèle de secours ne doit pas être choisi silencieusement pour masquer un refus d’accès. Le profil ChatGPT OAuth est celui observé lors de la recette ; le profil API est conservé séparément pour un choix opérateur explicite.

La publication passe par un outil local limité au job. L’agent de déploiement ne choisit ni clé SSH ni chemin distant libre. L’identité de publication est un compte système distinct de celui du bridge. Les sous-sessions et tentatives contribuent aux preuves et consommations. Une réparation de réponse terminée reste différente d’une relance après résultat fournisseur incertain.

Le transport Codex préparé dans une autre copie de travail n’appartient pas à la version installée décrite ici. La présence de modifications locales ou d’un autre moteur ne change pas cette référence. L’ancien outil personnel PIAgentControl ne fait pas partie du parcours d’exécution de cette version.

Pour chaque tâche, conserver l’acteur, le rôle, le modèle sélectionné, le job, la révision, les appels et le verdict. Les sources du client sont des données ; elles ne peuvent pas attribuer d’autorisations techniques. L’approbation du client porte sur la version exacte de la maquette et ne remplace pas l’admission opérateur de la cible.
