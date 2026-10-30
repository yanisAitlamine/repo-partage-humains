<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Rapport 37 — Revue du laboratoire directement dans Telegram

14 octobre 2026 — auteur : Codex pour Yanis.

## Demande et résultat

Yanis souhaite recevoir dans le bot le mail qui bloque la discussion, choisir Stop ou Continuer, puis écrire sur Telegram le message à envoyer au client. Un formulaire accessible seulement depuis le réseau privé ne convient pas à son téléphone lorsque le VPN est désactivé. Le laboratoire doit rester séparé du pipeline commercial existant.

Le formulaire a été remplacé par une interaction native du bot. Il affiche le mail complet et le motif, avec découpage des textes longs, puis les boutons Stop et Continuer. Le choix ouvre une réponse dédiée dans Telegram. Le texte saisi est présenté intégralement dans un aperçu avant confirmation; Modifier permet de le remplacer et Annuler abandonne la revue sans envoi.

Stop permet de rédiger une réponse de clôture et ferme la demande du laboratoire après confirmation. Continuer permet de rédiger une réponse de poursuite puis conserve une attente du prochain message client. Le texte envoyé est un message sortant de l'assistant : il ne devient pas une information du client ou un arbitrage automatique du brief. La clôture reste limitée au laboratoire et ne modifie pas la mémoire commerciale du pipeline existant. Aucun collecteur automatique du prochain mail n'a été ajouté : une nouvelle entrée devra fournir ce message et l'historique autoritatif avant une nouvelle décision.

Le cas proposé par défaut est fictif, avec appels Jev réels et validation Telegram en simulation sans Gmail. Un mode distinct permet de choisir explicitement un vrai mail déjà en revue. Il accepte uniquement une source encore en attente et un destinataire de test autorisé. La lecture d'une revue isolée ne prétend pas restituer l'historique complet : elle impose une revue humaine et interdit de générer un prompt prêt avec cet historique incomplet. L'envoi réel reste soumis aux contrôles Gmail existants, à une réservation durable et à un reçu confirmé. Un message plus récent ou une source modifiée invalide l'envoi; une issue incertaine ne déclenche aucun nouvel essai automatique.

L'adaptateur est installé dans le consommateur Telegram existant, avec persistance distincte pour les demandes et les événements du laboratoire. Aucun second consommateur, webhook public, ouverture réseau ou nouveau droit n'a été ajouté. Le laboratoire reste sauvegardé comme brouillon inactif et non publié; le pipeline commercial n'est pas remplacé.

Vérifications effectuées :29 tests du module natif et47 tests de régression du bot passent hors ligne sur le serveur. Le graphe de26 nœuds, organisé en deux groupes, est validé sans avertissement. Un essai n8n a utilisé des réponses externes simulées; un autre a écrit réellement dans la file dédiée avec un statut explicitement exclu des notifications. Le service est actif après installation, sans redémarrage automatique observé. Aucun Telegram, email client ou site de test n'a été envoyé par ces vérifications. L'essai complet depuis le téléphone et la réception d'une réponse Gmail réelle restent réservés à Yanis.

Le code et une copie cohérente de l'état persistant ont été sauvegardés avant le redémarrage ciblé. Le retour arrière consiste à restaurer le code et désactiver l'adaptateur; un ancien historique d'envoi ne doit pas être restauré après une action humaine. Les limites du classifieur Jev restent inchangées : une résolution peut encore être escaladée lorsque le soutien des faits est insuffisant, et les seuils autorisant un prompt prêt n'ont pas été abaissés pour masquer cette limite.

## Orchestration et délégation

### Délégation

Une tentative de délégation OpenCode a été lancée depuis la base de contrôle du serveur, sans sortie exploitable ni session produite constatée. Elle n'est pas présentée comme une implémentation terminée. Les profils configurent Luna pour les rôles de planification, implémentation et revue; aucun travail effectif de ces rôles n'a été observé dans cette tentative.

Codex a ensuite délégué à un enfant natif l'implémentation du module de revue et de ses tests, dans deux fichiers nouveaux exclusivement. Un autre enfant a effectué une revue indépendante en lecture seule, puis relu les corrections. Les modèles enfants sont hérités et n'ont pas été mesurés indépendamment; aucun coût ou gain de consommation n'est inventé.

La revue a identifié deux défauts concrets. Un identifiant de message Telegram étant local à une conversation, une collision pouvait absorber la réponse destinée à une autre fonction du bot : le rapprochement vérifie désormais la conversation et le bot avant consommation. La demande pouvait aussi changer ou expirer pendant les contrôles réseau : elle est revérifiée juste avant la réservation d'envoi. Les tests de collision, mutation et expiration ont été ajoutés, ainsi qu'un retour explicite pour un texte invalide. La relecture finale n'a identifié aucun blocage concret pour l'installation; elle reste une revue statique et ne remplace pas le test humain.

Codex a conservé l'intégration privée : choix de la file, raccordement du workflow et des connexions existantes par référence, sauvegarde, installation dans le bot unique, redémarrage ciblé et vérification finale. Les valeurs d'authentification n'ont pas été transmises aux agents, incluses dans les sources ou publiées. La politique Gmail commune n'a pas été modifiée.

## Coopération et adaptation au contexte

### Collaboration

Les consignes du projet, architecture, passation, protocole de coordination et annonces ont été consultés. Une intention puis une extension ont décrit les fichiers et le service réservés, les opérations prévues, les contrôles et les limites. Les annonces ont été reconsultées avant les écritures et les sources installées ont été comparées au dépôt. Les changements existants dans les autres intégrations et workflows ont été préservés.

La première table créée dans l'espace personnel était inaccessible à l'identité technique du bot. Une file distincte a donc été créée dans son projet existant et utilisée par l'API déjà autorisée, sans élargissement de droits ou partage du credential Jev personnel. La table initiale reste vide et n'est pas consommée. Cette adaptation conserve la séparation des accès et évite un deuxième canal d'authentification.

L'objection de Yanis a changé la signification de la reprise : son texte est destiné au client, et non à corriger intérieurement le brief. Le formulaire privé et la boucle qui réévaluait immédiatement ce texte ont donc été remplacés par rédaction, confirmation, puis attente d'une réponse client. Aucun rôle Ansible, accès à la VM personnelle, pipeline commercial ou service de construction n'a été modifié. La passation et les sources d'exploitation donnent les références exactes dans l'espace privé; ce rapport public exclut identifiants internes, coordonnées, chemins privés, contenus clients et secrets.

