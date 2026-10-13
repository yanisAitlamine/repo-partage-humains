> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 26 — Première réponse, PDF et dernier mail envoyé

12 octobre 2026. Yanis demande d'annoncer les moyens disponibles pour transmettre les contenus dès la première réponse commerciale, de prévoir l'actualisation de cette annonce lors de l'ajout de capacités, de vérifier le support PDF et de restituer le texte complet réellement envoyé à le contact de test. L'interdiction d'utiliser MCP reste applicable. Cette demande ne donne pas une autorisation d'envoyer un nouveau mail ou d'approuver la revue en attente.

## Dernier mail réel

Deux réponses commerciales ont été confirmées. Une nouvelle réponse reçue reste en revue humaine ; les consignes rédactionnelles nouvelles ne prouvent pas un nouvel envoi. Les contenus et références privés des messages restent dans le contexte d’exploitation.

## PDF : lecture réellement vérifiée

Le workflow actif comporte déjà `Lire le texte PDF`, nœud ExtractFromFile configuré en opération PDF, `joinPages=true`, `keepSource=json`, `maxPages=20`. Le lecteur s'appuie sur PDF.js et l'extraction de texte, pas sur un OCR de PDF scanné. La préparation des pièces jointes limite les fichiers à 5 Mio chacun, 10 Mio au total et cinq fichiers. La consolidation refuse une extraction vide ou partielle : plus de 20 pages ou plus de 18000 caractères pour un fichier produit PARTIAL, tandis qu'un total supérieur à 50000 caractères est également signalé pour revue.

Un PDF fictif d'une page contenant une chaîne de test a été créé. Un harnais appelle directement l'opération ExtractFromFile installée dans le conteneur n8n, avec ses dépendances réelles, les mêmes options que la production et des helpers binaires fictifs. Le résultat confirme une page et le texte attendu `CODEX_PDF_TEXT_OK`. Les avertissements sur canvas, ImageData, Path2D et les données de police n'ont pas empêché cette extraction. Ils ne sont pas présentés comme un test de rendu visuel réussi. Les deux fichiers temporaires déposés dans paramètre privé à consulter sur le Pi du conteneur sont ensuite retirés.

Ce contrôle prouve le fonctionnement du lecteur de texte installé sur ce document, pas le parcours complet Gmail/pièce jointe/IA sur tous les PDF. Aucun OCR, document scanné, PDF protégé ou interprétation des graphiques n'est validé. Il est donc incorrect de décrire la production comme acceptant uniquement du texte dans le corps du mail : le PDF contenant du texte est déjà une option vérifiée dans ces limites. Les autres lecteurs de pièces jointes existent mais ne sont pas tous retestés ici.

## Première réponse publiée

Le workflow commercial `paramètre privé à consulter sur le Pi` est actif en version publiée `paramètre privé à consulter sur le Pi`, après la version `paramètre privé à consulter sur le Pi`. Trois ajouts ciblés aux messages système de compréhension/conseil, structuration et accueil/clarification, en complément de la politique de transparence précédente. Les 81 nœuds, les anciens textes, les autres paramètres, les connexions et les settings sont conservés.

L'agent doit ajouter un court paragraphe à la première réponse concernant le nouveau projet, par exemple :

> Pour nous transmettre le contenu de votre site ou votre cahier des charges, vous pouvez écrire directement dans votre réponse ou joindre un PDF contenant du texte (20 pages maximum, 5 Mio par fichier). La lecture des documents par lien Google Drive n'est pas encore disponible.

Le paragraphe conserve le conseil personnalisé et n'ajoute pas de question. Le dialogue SENT confirmé du projet concerné permet de distinguer une première réponse d'un suivi; les brouillons, messages incertains, anciennes citations et autres projets ne constituent pas une preuve d'envoi pour ce projet. L'annonce ne doit pas se répéter dans tous les messages. Les autres formats de pièces jointes ne sont pas déclarés impossibles; ils restent soumis aux capacités et résultats réels.

La politique et sa documentation imposent de mettre à jour la liste et l'annonce dans les trois prompts lors de toute intégration d'une capacité effectivement déployée et vérifiée. Aucun mécanisme d'autodécouverte automatique de nouveaux lecteurs n'est ajouté. Les candidats Drive et Telegram d'Ilyes restent indépendants et inactifs; ils ne donnent aucune nouvelle capacité à cette production.

## Validation, sources et retour arrière

Intervention par SSH, API locale n8n et lecture Gmail ciblée, sans MCP. Les identifiants nécessaires sont utilisés exclusivement en mémoire par les outils opérateur et ne sont ni affichés ni versionnés. Version publiée et draft concordants avant mutation; arrêt prévu en cas de changement concurrent. Comparaisons après PUT et après activation : trois textes égaux exactement à l'ancien texte suivi du bloc ajouté, aucun autre changement de nœud, connexion ou setting, et activeVersionId identique à la nouvelle version. `git diff --check` des exports réussit. Aucun appel IA payant ou test d'envoi; le comportement rédactionnel sur une première réponse future reste à observer.

Sources publiques dans `paramètre privé à consulter sur le Pi` et `FIRST-REPLY.md`. Exports commercial draft/published et entrée manifest actualisés, copies Windows synchronisées. Outils de préparation et de contrôle dans `Technique/outils/`. Snapshots avant/après privés root-only hors Git sous `paramètre privé à consulter sur le Pi`. Retour arrière : restaurer les trois textes ou la version précédente en conservant les éventuelles évolutions ultérieures. Aucun commit/push.

Les gardes de revue, les destinataires, les réservations, la relance, la construction OpenCode, les autres workflows, services, réseau et Ansible ne sont pas modifiés. La mission ne réalise pas de sauvegarde globale externe du Pi et ne déploie aucun lecteur Google Drive.

## Délégation et coordination

Travail direct de Codex : diagnostic ciblé, lecture du seul mail envoyé demandé, essai du lecteur PDF sur fixture, ajout de trois consignes, publication et comparaison API, exports et documentation. Aucune session OpenCode ou sous-agent pour cet ajout circonscrit de texte; le harnais PDF vérifie une fonction existante et ne constitue pas une nouvelle implémentation du lecteur. Aucun coût ou économie inventé.

Session locale déclarée `paramètre privé à consulter sur le Pi`, intention `paramètre privé à consulter sur le Pi`. Les annonces d'Ilyes concernent des lecteurs Drive et validations Telegram sur copies et préparation indépendante; elles ne recoupent pas les prompts actifs réservés ici. Les nouveaux messages ont été lus et les modifications utilisateur préservées. Le global Windows AGENTS est intact.
