# Héphaïstos : portail déployé et parcours commun candidat

18 octobre 2026 — rapport de Yanis, avec assistance Codex.

## Demande et résultat

La demande portait d'abord sur la mise en service de la version déjà présentée
du portail : identité Héphaïstos, présentation de l'usine à sites et gestion du
profil professionnel. Cette version a été poussée puis déployée. Le service,
la révision exécutée et la santé HTTPS ont été vérifiés ; la route de profil
refuse bien un accès sans session.

La seconde partie demandait un parcours de création unique, démarré depuis un
compte du portail, puis poursuivi par le portail ou par mail. Le choix humain
complémentaire est d'automatiser après revue indépendante et validations client,
sans seconde validation interne pour ce nouveau parcours.

Le code candidat apporte :

- une adresse professionnelle vérifiée, une boîte d'envoi durable et des
  références de réponse liées à chaque question ;
- une admission atomique : la première réponse gagne, les réponses concurrentes
  et anciennes ne sont pas reportées à la question suivante ;
- le cadrage créatif en sept sujets et un récapitulatif confirmé séparément ;
- les pièces et dossiers Drive contrôlés avant utilisation des textes ;
- des maquettes statiques privées, multipages, intégrées au portail, avec
  captures ordinateur/mobile et revue indépendante avant présentation ;
- les décisions valider, modifier après clarification et confirmation, ou
  abandonner avec retour facultatif ;
- la conservation des fichiers de la maquette précédente et des textes admis
  lors d'une modification, avec de nouvelles preuves de revue ;
- un pont candidat de réalisation et de livraison finale, lié à la validation
  exacte et à une destination explicitement configurée ;
- le site livré dans le portefeuille et l'enregistrement des demandes de
  fonctionnalités, sans lancer leur réalisation.

Un changement d'adresse pendant un travail ne fait pas perdre son résultat.
Les notifications attendent la vérification de la nouvelle adresse ; seuls les
états encore actuels sont ensuite envoyés. Un envoi déjà incertain n'est jamais
remis en file automatiquement.

Les contrôles associent 418 tests Python réussis sur Linux, 344 tests Node
réussis, compilation du portail et essais dans un navigateur réel sur des
données fictives. Les essais
ont couvert l'aperçu multipage, le mobile, la vérification du mail dans une boîte
locale fictive, deux réponses concurrentes, un réessai après coupure, la boucle
de modification et l'absence de job de fonctionnalité. Ils ont conduit à corriger
un doublon d'en-tête HTTP qui masquait l'aperçu et un message d'erreur réseau.
Les contrats des nouveaux workflows ont aussi été validés statiquement.

Cette évolution reste une **candidate non activée**. Aucun nouveau workflow n'a
été publié ou exécuté, aucun mail client envoyé et aucune nouvelle publication
de site déclenchée par les tests. Les recettes d'administration sont préparées
uniquement, sans exécution, contrôle de syntaxe ni lint. La configuration privée,
les destinations et un essai réel de bout en bout restent à vérifier lors d'une
activation autorisée de la release exacte.
Les sources ont été commitées et poussées normalement sur la branche principale.

Le premier pont final couvre les sites statiques ; il ne provisionne pas de
backend ni de compte client. Le contrat prévoit des informations de connexion
et un lien d'activation pour une future capacité vérifiée, jamais un mot de passe
permanent. Les nouvelles images jointes ne sont pas encore réutilisées dans la
génération. Les sources et captures ont des budgets explicites ; un dépassement
arrête le travail sans troncature silencieuse. Ces limites empêchent de présenter
le parcours complet comme déjà exploité en production.

## Orchestration et délégation

Codex a effectué directement l'intégration serveur, la liaison des adresses, le
routage et la réception des mails, les sources, les recettes, les vérifications
globales et le déploiement de la version déjà autorisée.

Trois agents Codex internes ont été lancés et leurs résultats intégrés après
revue :

- **creative_brief** : cadrage, états du parcours et interface, puis essais
  navigateur. Cette délégation réunissait le contrat client et ses contrôles
  visibles.
- **mail_audit** : audit du pipeline existant, verrou des réponses, notifications,
  adaptateurs et candidats n8n. Il a aussi relu les contrôles d'identité et le
  changement de contact.
- **preview_audit** : stockage et rendu privés, revue des maquettes, pont final,
  puis revue du raccord worker. Il a identifié et corrigé l'absence du contexte
  de la maquette précédente.

Les agents ont hérité de la configuration de modèle de la session ; aucune
mesure indépendante du modèle effectivement servi, de coût ou d'économie n'est
annoncée. Leurs tests externes utilisent des doubles explicitement fictifs. Les
copies d'audit lisibles des délégations ont été conservées dans l'archive privée ;
elles ne prétendent pas restituer des échanges natifs chiffrés.

Aucune session OpenCode n'a été lancée depuis PIAgentControl, et aucune mission
n'a été confiée indirectement à cette base.

## Coopération et adaptation au contexte

Les consignes du projet et du portail, la fiche de reprise, le protocole partagé,
les annonces pertinentes et les références du déploiement ont été consultés.
Les périmètres ont été annoncés et réservés ; le travail s'est effectué dans
un checkout distinct. Les changements concurrents des checkouts canoniques et
la passation réservée par une autre mission ont été préservés.

La mise en service de la version précédente a attendu la fin d'un travail de
construction déjà actif : aucun job n'a été arrêté ou réarmé pour forcer la
bascule. Les vérifications HTTPS ont conservé la validation du certificat et
l'accès privé existant. Aucun élargissement réseau n'a été réalisé.

Le filtre candidat d'entrée du pipeline historique conserve seulement une liste
opérateur de conversations préexistantes et exclut les messages du nouveau
parcours. Son plan est lié aux empreintes du workflow observé et refuse un
brouillon divergent. Il reste à appliquer dans une fenêtre d'édition réservée,
après réconciliation de la file ; aucune ancienne conversation n'a été rejouée.

Les résultats présentés distinguent donc la version réellement déployée, les
sources candidates intégrées et les effets externes encore non vérifiés.
