<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# OpenAI Decisions intégré et essais mail

16 octobre 2026. Analyse corrigée sur deux essais ; une maquette est recevable pour validation humaine, l’autre reste bloquée.

## Demande et résultat

Yanis a demandé de corriger les questions répétées sur des informations déjà fournies, puis de poursuivre deux essais mail sur deux cibles distinctes, en conservant les validations humaines. Le [diagnostic précédent](RAPPORT-JEV-DECISIONS-20261016.md) comparait les fournisseurs sans changement en production.

Le service publié utilise maintenant l’API OpenAI Decisions avec `gpt-6-luna`. Aucun fine-tuning n’a été réalisé. Sources, copies embarquées du dialogue commercial et service publié sont synchronisés et versionnés. Les connexions existantes sont réutilisées sans copier leurs secrets. Le modèle et le schéma réels sont contrôlés ; le fournisseur n’est pas simplement réétiqueté.

Les faits restent liés à des citations exactes. Les rubriques explicites du dernier mail réduisent les candidats du champ concerné ; le catalogue complet reste disponible pour les autres contrôles. Les retours à la ligne du transport mail, les documents complets et l’arbitrage opérateur authentifié sont pris en compte.

Pour OpenAI, le serveur calcule désormais READY après les contrôles atomiques : six faits soutenus à au moins 0,90 ; intention à au moins0,90, confiance 0,80 et marge 0,20 ; conflit, ambiguïté et prérequis client au plus 0,10. STOP bloque. ACK et STATUS n’autorisent pas la préparation. L’ancienne question globale contradictoire est supprimée pour ce profil ; aucune probabilité READY n’est fabriquée. Le moteur autorise seulement la préparation du prompt. Construction, revue et accord humain de livraison gardent leurs contrôles distincts.

Vérifications effectuées :

- 37 cas ciblés OpenAI, 14 suites Node existantes, 20 copies embarquées et 77 tests Python réussis.
- Cinq évaluations API réelles positives : deux dialogues de test, un autre brief, un document de trente pages et un choix opérateur délégué. Toutes READY.
- Treize évaluations négatives, notamment arrêt, retrait, contradiction, ambiguïté, prérequis, citation hors sujet et arbitrage hors mandat. Aucune préparation autorisée.
- Paramètres publiés comparés au candidat ; brouillon utilisateur du constructeur préservé.

Les évaluations isolées ne construisaient aucun site. Deux nouveaux mails réels ont ensuite été envoyés une seule fois. Après un refus de quota du connecteur Gmail, l’absence du premier envoi a été vérifiée avant le repli par l’interface Gmail dans Brave. Les deux analyses ont reconnu le brief complet et lancé une construction sur la cible fournie dans leur propre mail.

| Essai | Résultat réel |
| --- | --- |
| Premier | Maquette construite, corrections appliquées, seconde revue indépendante réussie. Preuve fraîche SSH/HTTPS et captures liées aux octets vérifiées. Accord humain attendu avant mail final. |
| Second | Maquette construite et corrigée une fois. Deux revues refusées ; dernière vérification de transport incomplète. Les reprises de correction se sont arrêtées pendant la coordination. Résultat bloqué, livraison refusée par le workflow. |

Le bouton Contact du second essai arrive correctement à destination dans Brave sur ordinateur et mobile après stabilisation du défilement. Cette observation ne remplace pas la revue indépendante manquante. Les deux index racines sont restés inchangés. Aucun ancien job réarmé ni mail final de livraison envoyé.

Le second blocage concerne l’exécution NOC et sa coordination, après une analyse réussie. La compatibilité Telegram est préparée et testée en source seulement ; sa recette dédiée n’est pas appliquée et le poller reste arrêté/désactivé. Aucun ancien rôle Ansible réservé testé ou appliqué. Ces résultats ne prouvent ni tous les futurs briefs ni une restauration complète.

## Orchestration et délégation

Codex a directement implémenté, testé, publié et vérifié le correctif. Aucun sous-agent Codex ni session OpenCode depuis PIAgentControl n’a été lancé.

Le workflow NOC existant a lancé les constructions autorisées : planification, implémentations et revues indépendantes. Le premier résultat est terminé et vérifié ; le second est terminé bloqué. Les tentatives interrompues avant écriture ne sont pas comptées comme corrections réalisées. Les modèles des rôles NOC n’ont pas été relevés ; aucun coût ni gain inventé.

## Coopération et adaptation au contexte

Consignes, protocole, références des composants et annonces pertinentes ont été consultés. Intention et extensions ont réservé les fichiers concernés. Modifications étrangères, autres services et brouillons concurrents ont été préservés.

Les interruptions de coordination ont conduit à rappeler les consignes existantes : inventaire complet périodique et lecture des nouveautés avant écriture. Aucune règle permanente ni réservation n’a été supprimée. Le refus de revue est conservé.

Préimages, versions exactes, preuves et passation restent privées. Les bancs temporaires sont archivés. Les consignes et retours NOC lisibles sont conservés comme copies d’audit, sans prétendre déchiffrer des messages natifs. Les réservations de cette mission sont libérées à sa clôture.
