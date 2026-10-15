# Rapport 43 — Correctifs et essai Gmail / Telegram

Date : 15 octobre 2026. État : essai en pause à la demande de l’utilisateur ; correctifs de décision publiés, dernier correctif de rédaction encore isolé.

## Demande et résultat

L’utilisateur a demandé un essai réel partant de son propre mail, avec observation dans n8n et arrêt au moment d’une intervention Telegram. Il a ensuite précisé qu’un mail commercial valide ne devait pas nécessiter d’arbitrage humain, et que tout obstacle devait interrompre l’essai : corriger d’abord, puis repartir de la réception avec un nouveau message. La validation humaine de la maquette avant livraison reste obligatoire.

Le premier essai a révélé deux défauts distincts. Le dialogue normalisait les retours de ligne du mail, mais quatre copies du même adaptateur dans le service de décision utilisaient encore la comparaison précédente. Les deux représentations avaient un contenu identique après normalisation : le refus venait du logiciel. Les quatre comparaisons ont été alignées, en conservant les corps originaux et le refus d’une véritable altération.

La réponse Telegram a ensuite été envoyée une seule fois, avec reçu Gmail confirmé et reprise immédiatement soumise au dialogue. Cette reprise a rencontré un autre contrôle trop strict : les projets du client dans des fils sans rapport empêchaient le traitement d’un nouveau projet. La vérification distingue désormais ces projets étrangers des collisions sur le projet ou le fil courant. Les preuves de source, destinataire, reçu envoyé, action et révision restent nécessaires.

Un deuxième essai neuf a confirmé que le problème de retours de ligne était corrigé. Il a révélé une autre escalade excessive : le texte était découpé à chaque retour de ligne de transport, puis une hésitation sur le choix d’une citation devenait une erreur technique imposant l’opérateur. Cet essai a été arrêté avant tout envoi client ou construction.

Le correctif suivant conserve les phrases entières comme citations exactes, et distingue une information non confirmée d’un défaut de provenance. Une extraction incertaine laisse le champ manquant et produit un diagnostic ; le dialogue peut alors demander normalement une précision au client. Cela ne transforme pas une hypothèse en fait, et ne réduit pas les exigences de validation d’un brief prêt.

Un troisième essai a révélé une dernière confusion : une hésitation entre deux intentions commerciales compatibles était encore considérée comme un besoin d’opérateur. La règle a donc été généralisée. Une intention, une décision ou un soutien sémantique incertain conduit à une clarification automatique seulement si un arrêt, un conflit, un projet ambigu ou un choix de blocage ne sont pas plausibles. Les seuils nécessaires pour préparer une maquette restent inchangés ; la clarification ne peut jamais produire un prompt ni lancer une construction. Les anciens boutons des essais arrêtés sont invalidés sans envoyer de mail.

Le quatrième essai a atteint le dialogue commercial automatique, sans revue humaine. Une réponse Gmail a été envoyée et son reçu confirmé ; la trace de diagnostic a aussi été délivrée. La vérification du texte réellement envoyé a cependant trouvé un dernier défaut : le rédacteur avait omis les deux questions décidées par le moteur. Un simple accusé de réception aurait laissé le dialogue sans les précisions attendues. Cet essai a donc également été arrêté, en préservant l’envoi réalisé.

Le correctif de composition des questions est préparé et relu sur treize cas hors ligne. Il rend les questions autorisées obligatoires dans la réponse, sans modifier les branches de validation de maquette ou d’arrêt. Il n’est ni publié ni vérifié par un nouvel envoi réel : l’utilisateur a demandé de mettre l’essai en pause avant cette étape. Aucun cinquième essai n’a été lancé. Le parcours complet après Continuer jusqu’à construction et validation de maquette reste donc à vérifier.

La dernière demande réduit aussi Telegram : suppression des bilans systématiques d’exécution et des confirmations techniques de reprise acceptée. Une demande de décision conserve la raison de l’arrêt, le message client intégral et une explication française du point qui reste incertain. Une erreur de récupération est présentée comme un problème technique, sans prétendre que le client s’est mal exprimé. Les boutons et la confirmation de l’aperçu sont conservés.

Ce format est installé et les sources concordent avec les deux modules chargés par le service. Quinze tests de notice et huit tests de configuration et de notification passent sans réseau. Le service Telegram unique a été redémarré après sauvegarde cohérente de son état ; il est actif, sans redémarrage automatique. Aucun nouveau Gmail, appel de modèle ou site n’a été lancé pour cet ajustement. Les alertes d’incertitude qui nécessitent réellement une vérification restent actives.

## Orchestration et délégation

### Délégation

Codex a observé les exécutions, vérifié les reçus et les états persistants, arrêté les essais bloqués et préparé le correctif de rattachement. Un sous-agent Codex a audité la confirmation Telegram, identifié la divergence des copies de l’adaptateur, fourni les preuves de comparaison et préparé les correctifs isolés du service de décision et de son moteur. Un second sous-agent assure une revue indépendante de la distinction entre clarification et blocage.

L’audit de confirmation a distingué le résultat durable de l’envoi du simple acquittement visuel du clic Telegram. Un message de retour indisponible ne prouvait pas l’échec de Gmail ; le reçu confirmé et l’événement de reprise ont établi que l’action avait abouti.

Les premiers correctifs ont passé neuf contrôles spécifiques, quatre compilations des copies du service, les quatre-vingts assertions antérieures du parcours et six contrôles supplémentaires sur le cas réel de reprise. Les cinq nœuds modifiés ont été validés par n8n. Le moteur final passe 139 tests et 48 nœuds compilés. La revue indépendante a relancé 56 régressions et comparé 7 776 combinaisons : aucune nouvelle autorisation de préparation de maquette, aucune clarification hors des gardes prévues. Les huit copies modifiées ont été validées par n8n. Les différences ont été limitées aux propriétés prévues, puis les versions publiées ont été relues et comparées aux candidats. Les tests du parcours et du rattachement ont aussi été relancés avec le moteur final.

Aucune session OpenCode de la base personnelle n’a été lancée. Aucun coût, modèle de sous-agent mesuré ou gain de consommation n’est revendiqué. Les simulations ne sont pas présentées comme des essais réels.

## Coopération et adaptation au contexte

### Collaboration

Les instructions du projet et les annonces de coordination ont été relues. Une intention, les extensions de périmètre et les états d’attente ou d’arrêt ont été publiés avant les actions correspondantes. Les travaux documentaires concurrents, leurs fichiers réservés et les modifications préexistantes des sources ont été préservés. Le présent rapport constitue un fichier distinct ; aucun rapport d’un autre auteur n’est remplacé.

Les essais utilisent des fils neufs afin de préserver les réponses déjà envoyées et les réservations d’envoi. Aucun ancien mail, événement de reprise ou historique d’envoi n’est réarmé. Les préimages et les preuves contenant des données réelles restent dans l’espace privé de mission, hors du dépôt public. Les sources exportées sont mises à jour uniquement pour les workflows corrigés, sans commit applicatif global.

Les réserves sur Ansible, la VM personnelle et les accès externes restent inchangées. Les contrôles de provenance et la validation humaine finale ne sont pas contournés pour obtenir un résultat de test. Les conclusions décrivent les étapes réellement observées et leurs limites, sans publier de contenu de mail ni de paramètres internes.
