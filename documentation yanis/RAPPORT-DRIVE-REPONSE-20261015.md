# Réponses commerciales et reprise de l’essai Drive — 15 octobre 2026

## Demande et résultat

L’utilisateur a demandé de corriger une réponse commerciale maladroite et de reprendre le test d’un dossier Drive privé contenant des images, un cahier des charges de trente pages et des données produit fictives.

Le diagnostic a établi que le contrôle final remplaçait entièrement la réponse rédigée par un gabarit générique. Cela supprimait les conseils et l’explication sur les documents indisponibles. Les questions étaient fabriquées à partir de libellés incomplets, sans les articles et accents nécessaires.

La correction est publiée : questions complètes au vouvoiement, texte contextuel conservé, insertion des deux seules questions autorisées avant la formule de politesse. Le rédacteur produit séparément le corps et la politesse, sans questions libres. Une sortie malformée, une question supplémentaire ou un état incohérent passe en revue sans envoi. Les seuils de décision, les confirmations humaines et les permissions de construction et de publication restent protégés.

Vérifications réalisées : 309 régressions existantes réussies, deux tests ciblés supplémentaires sur les formulations et l’assemblage, compilation des 49 nœuds de code concernés, puis appel réel du rédacteur dans un banc isolé. Le résultat conserve le conseil produit et l’explication Drive, avec deux questions correctes. Ce banc ne comporte aucun envoi ni construction ; il a été archivé après vérification. Les versions publiées ont été relues, les huit copies embarquées du moteur synchronisées et les exports ciblés actualisés.

La première reprise Drive avait échoué : l’ancienne connexion n8n disposait d’un jeton expiré sans renouvellement disponible, puis les nouvelles connexions préparées ne possédaient pas encore de jeton utilisable. La connexion Gmail existante ne donnait pas les autorisations suffisantes pour lire Drive. Ces échecs n’ont pas été présentés comme des lectures réussies.

La suite a identifié une erreur concrète de configuration : l’URI de retour OAuth de n8n manquait dans le client Google, ce qui provoquait un refus de redirection. Après confirmation humaine au moment des actions, cette URI a été enregistrée et le consentement Drive en lecture seule a été confirmé pour le compte attendu. Le parcours Google normal a été poursuivi dans un autre onglet du même profil de navigateur, sans contourner les contrôles d’authentification ou de consentement. La connexion native n8n affiche désormais un compte connecté ; aucun secret n’a été recopié.

Un essai réel dans le banc privé a ensuite réussi. Les assertions contrôlent l’identité du compte via Drive, les cinq fichiers du dossier synthétique privé, les trente pages du PDF et l’exigence située précisément sur sa dernière page. Les deux images PNG ont été téléchargées intégralement, avec contrôle des tailles et signatures. Les trois produits ont été relus dans le fichier de données et leurs références, prix, devise, images associées et exigence particulière vérifiés. Une condition manquante fait échouer le test ; un simple succès technique du workflow ne suffit plus. La preuve minimale ne contient ni texte intégral des documents ni données d’authentification.

Ce banc manuel ne possède aucun envoi, message de validation ou constructeur et n’active pas Drive dans le parcours commercial. Le renouvellement après expiration du nouveau jeton n’a pas encore été observé. La connexion personnelle n’a pas été partagée avec les lecteurs d’un autre collaborateur. Restent à terminer : raccordement des sources documentaires au dialogue, transfert contrôlé des images et test réel jusqu’à la maquette avec les validations habituelles. Aucun nouveau mail de test ni site n’a été produit pendant cette correction et cette reprise de connexion.

## Orchestration et délégation

La première correction commerciale a été réalisée directement par Codex, sans sous-agent. Le rédacteur déjà configuré dans le workflow a été appelé pour le seul essai de composition.

Pour la reprise de connexion, l’agent Codex principal a assuré les opérations dans le navigateur, la préparation et l’enregistrement du retour OAuth après accord humain, le consentement, l’intégration des contrôles et l’essai réel du dossier synthétique. Un sous-agent Codex a effectué des lectures ciblées des métadonnées et du code n8n non secret, un contrôle isolé de connexion resté sans jeton utilisable, la revue du banc, la proposition des assertions strictes et cette actualisation du rapport. Les assertions ont été relues puis intégrées par l’agent principal avant l’essai réussi. Le sous-agent n’a modifié aucun credential ni workflow de production.

Aucune session OpenCode n’a été lancée depuis la base réservée à l’utilisateur. Aucun coût ou gain n’a été estimé. Les sauvegardes et preuves détaillées restent dans les espaces privés de la mission ; aucune donnée d’exécution ni référence client n’est publiée ici.

## Coopération et adaptation au contexte

Les consignes globales et du dépôt, l’architecture, la passation, les README applicables, le dernier rapport utile et le protocole partagé ont été consultés. Une intention puis une extension documentaire ont précédé les modifications. Les annonces de la mission indépendante de portail ont été lues ; ses sources, services et documents réservés ont été préservés. Le brouillon utilisateur du constructeur et les changements existants dans les dépôts n’ont pas été remplacés.

La reprise a distingué les premières exécutions techniques des lectures documentaires réellement achevées : les refus OAuth sont restés des échecs, puis les assertions de lecture ont établi la réussite de l’essai isolé. La lecture du code installé a permis de distinguer la sauvegarde d’une configuration du retour OAuth qui enregistre effectivement le jeton. Elle a aussi écarté une navigation directe non adaptée à la route d’authentification de l’éditeur ; aucun cookie ou en-tête de session n’a été extrait ou réutilisé.

Les annonces du collaborateur qui examinait ses propres lecteurs Drive ont été consultées. Les périmètres sont restés séparés : aucune ancienne référence de ses lecteurs n’a été remplacée et aucun partage de la nouvelle connexion n’a été déduit de leur accessibilité. Les intentions ont été étendues pour la connexion, le consentement, le banc et la documentation ; le clone documentaire était propre avant l’édition de ce seul rapport. Les sauvegardes et preuves ont été conservées sans recopier de valeurs secrètes. Aucun rôle Ansible réservé, accès à la VM personnelle ou changement réseau n’a été effectué. Le raccordement de production et la vérification du renouvellement restent explicitement à réaliser, sans rejouer les anciens envois.
