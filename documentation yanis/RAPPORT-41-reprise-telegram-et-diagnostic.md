<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Reprise commerciale après validation Telegram et diagnostic détaillé

15 octobre 2026.

## Demande et résultat

La demande était de reprendre immédiatement le dialogue commercial après le choix **Continuer** et l’envoi confirmé d’une réponse humaine. Auparavant, ce choix mettait la conversation en attente d’un nouveau courriel client. Il fallait aussi permettre au collaborateur d’accéder aux workflows manquants et rendre les messages Telegram suffisamment détaillés pour comprendre le déroulement.

La reprise est désormais publiée et installée. Après confirmation de l’envoi humain, le service enregistre un travail unique, relit le fil Gmail et réévalue le brief du client. La réponse humaine reste un message de notre côté ; elle ne devient pas une information déclarée par le client. Un brief incomplet conduit à des questions utiles ; un brief suffisant peut conduire à une première maquette de test. Un nouveau message client prend la priorité sur une ancienne reprise. **Stop** clôt la conversation ; une erreur technique suspend l’action concernée sans annuler le projet. La validation humaine avant livraison de la maquette est conservée.

Le courriel humain déjà envoyé possède sa propre réservation. La suite commerciale reçoit une référence distincte, tandis que les lectures et réponses Gmail utilisent toujours le véritable message source. Un résultat d’envoi ou de transmission incertain ne provoque pas de nouvel essai aveugle. Aucun ancien message client n’a été rejoué lors de l’installation. Un nouveau blocage après réévaluation reste signalé comme nécessitant un diagnostic ; l’ancienne revue résolue n’est pas automatiquement rouverte.

Dix workflows et une connexion de décision ont été transférés par l’API officielle vers l’espace personnel du collaborateur, sans changer leurs définitions ou leurs versions. Son API personnelle a pu lire les dix workflows. Le propriétaire de l’instance conserve son accès global. L’ancienne clé personnelle conserve cependant sa restriction de lecture des connexions par API ; la propriété dans l’interface n’équivaut pas à toutes les permissions d’une clé. Une table de laboratoire vide et abandonnée est restée hors transfert. Aucun rôle administrateur ni mécanisme de licence n’a été contourné.

Les diagnostics Telegram décrivent les étapes exécutées, l’état technique, les états métier, les codes de décision, les nombres de questions et d’informations manquantes, ainsi que le lien vers l’exécution. Les principaux états et codes sont expliqués en français. Ils distinguent une reprise acceptée d’un courriel envoyé ou d’une maquette livrée. Les corps des mails, prompts, sorties brutes des modèles et secrets sont exclus de ces traces. Le suivi conserve les exécutions longues en attente et borne sa pagination pour préserver la réactivité du service.

Une sauvegarde cohérente des bases et du code a précédé l’installation. Seul le service de revue Telegram a été redémarré ; il est actif sans redémarrage automatique constaté. Les anciennes réservations et les résultats incertains ont été conservés. Un retour arrière doit préserver l’historique des envois, plutôt que restaurer une ancienne base susceptible d’autoriser un doublon.

Vérifications réalisées :

- 142 tests simulés du backend, du parcours natif et des régressions ;
- 5 tests simulés des diagnostics, dont exclusion des données brutes et pagination bornée ;
- 41 cas de vérification de l’adaptateur de contexte ;
- 77 corps de code compilés ;
- un banc exécuté dans le moteur n8n : 10 véritables blocs du workflow, 80 assertions sur données fictives, sans fournisseur, mail, Telegram ou construction ;
- refus de l’entrée interne sans authentification et refus d’un message invalide, sans ajout de travail ;
- réception confirmée d’un message Telegram expliquant le comportement installé ;
- émission d’une trace par le module installé à partir de l’exécution réelle du banc fictif, avec reçu Telegram et état d’émission confirmé ;
- lecture de confirmation des versions publiées, des fichiers installés, de leurs permissions et des accès nécessaires au service.

Le banc de vérification a été désactivé puis archivé. Une première tentative avait rencontré une route non enregistrée ; le déclencheur a été corrigé avant l’essai réussi. Les sauvegardes de cette mission restent sur la même machine ; aucune nouvelle copie indépendante n’est attestée. Ces contrôles ne prouvent pas un nouveau parcours client réel jusqu’à la livraison : celui-ci reste à observer avec les confirmations humaines habituelles. Aucun courriel client ni site de test n’a été envoyé ou construit pour cette vérification. Aucun ancien rôle Ansible, accès à la machine de contrôle ou paramètre réseau n’a été modifié.

## Orchestration et délégation

La première préparation avait tenté une session OpenCode avec un planificateur configuré Luna. Elle est restée bloquée à l’initialisation, sans résultat de travail observé, puis a été arrêtée. Cette tentative n’est pas présentée comme une délégation achevée.

Trois agents Codex ont ensuite participé, sans modèle particulier imposé et sans coût fiable mesuré. Un agent a préparé les événements persistants, la transmission et les tests du backend, puis réalisé une revue indépendante des workflows. Un autre a préparé les modifications de workflow, leurs tests, la disposition des nouveaux nœuds et le banc n8n isolé. Le troisième a étudié les possibilités d’accès supportées, exécuté les transferts et contrôlé les lectures avec le compte personnel du collaborateur ; il a aussi relu le diagnostic Telegram.

La revue a reproduit un changement de projet possible et une arrivée de message client pendant l’envoi humain, alors que les premiers tests étaient encore verts. Les candidats ont été corrigés puis les cas ajoutés aux tests. Les contrôles de reçu Gmail et de preuve d’envoi ont été renforcés. Le suivi des longues attentes et la borne de pagination du diagnostic ont également été corrigés. La revue indépendante finale n’a plus relevé de défaut bloquant dans le périmètre examiné ; elle ne prétendait pas avoir vérifié le service réel.

Codex a conservé la lecture des mails autorisés, les opérations privées, l’intégration, les sauvegardes, la publication, l’installation, le message de diagnostic réel et les lectures finales. La documentation distingue les fichiers candidats, leur intégration et les vérifications réellement exécutées. Aucun gain financier ou de consommation n’est affirmé.

## Coopération et adaptation au contexte

Les consignes du projet, l’architecture, les notes de pause, les sources actives et la coordination ont été consultées. Les rapports historiques ont été traités comme des états datés. La correction préalable des retours à la ligne Gmail a été préservée et n’a pas été attribuée à cette intervention.

La tâche a été interrompue sur demande humaine, documentée et annoncée comme telle. À la reprise, les versions actives et les empreintes du code installé ont été relues avant toute application. Une nouvelle intention a réservé le périmètre ; les travaux de revue et de finition ont repris explicitement. Les modifications utilisateur déjà présentes dans les dépôts ont été conservées et n’ont pas été committées en bloc.

Les travaux documentaires menés en parallèle ont été identifiés. Leurs fichiers réservés n’ont pas été modifiés par cette mission. Le présent rapport est publié séparément, après anonymisation ; les notes privées de reprise, preuves techniques détaillées et sauvegardes ne sont pas diffusées dans le dépôt public. Les limites concernant les tests réels, les incertitudes d’envoi et les permissions de clé sont maintenues dans la restitution.
