<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Synchronisation TLS du secours après migration vers Nginx — 22 octobre 2026

## Demande et résultat

La demande humaine était de raccorder la synchronisation HTTPS du secours au
stockage de certificats utilisé par Nginx, en conservant les accès existants.
La correction a été qualifiée dans le laboratoire, revue indépendamment, intégrée
dans les sources canoniques puis installée par une recette Ansible ciblée.

L'ancien sender lisait encore la paire conservée par Caddy alors que le frontal
actif renouvelle ses certificats dans un stockage Nginx distinct. Il pouvait
donc recopier une ancienne paire. Ce défaut de raccord ne signifiait pas que
le certificat servi par le frontal actif était invalide.

Le sender lit désormais le certificat et sa clé dans **une seule version
publiée par Nginx**. Il prend une copie sous verrou partagé avec le renouvellement,
en ouvrant les fichiers depuis un même répertoire vérifié. Les contrôles portent
sur leur type, propriétaire, permissions, taille et stabilité pendant la lecture.
La validation utilise ensuite les octets copiés, sans rouvrir un chemin qui
pourrait désigner une autre version. Le verrou est libéré avant le transport.

La copie est vérifiée pour le nom attendu, les dates, la chaîne de confiance
et la correspondance entre certificat et clé. Une copie incohérente ou une
issue inconnue bloque l'envoi. Les anciens fichiers Caddy ne sont pas un
repli automatique.

Le receiver et sa configuration Caddy sont restés inchangés. Le contrat conserve
six membres fixes et le transport utilise toujours une identité SSH dédiée,
une clé d'hôte vérifiée et une commande de réception forcée. Les données VPN,
la liste de révocation et les sept entrées d'admission sont restées identiques.
Une empreinte temporairement épinglée au lot sortant et la suspension du timer
de copie ont borné l'intégration à la modification TLS autorisée.

| Étape | Résultat attesté |
| --- | --- |
| Qualification du candidat | 77 tests isolés réussis dans le laboratoire ; sources stables et revue indépendante favorable. |
| Transition Ansible | Préparation, prise de garde, installation et finalisation réussies. |
| Premier transfert sérialisé | Deux fichiers modifiés : certificat et clé HTTPS seulement. |
| Deuxième invocation | Aucun changement, résultat `changed=0`. |
| Réception et service HTTPS | Paire correspondante, chaîne identique à Nginx et certificat effectivement servi vérifié en TLS normal ; HTTP200. |
| Échéance du certificat | Passage du 7 au 19 janvier 2027 ; nouvelle expiration à 21:10 UTC. |
| Fin de transition | Timer de copie actif et activé comme auparavant ; pin temporaire retiré de l'environnement effectif, seul ajout permanent attendu conservé. |

La prochaine échéance normale du timer de copie a été observée à **13:12:16,
heure de Paris**, sans déclenchement manuel : exécution réussie et aucun changement
côté receiver (`changed=0`). Cette preuve concerne la copie périodique, pas un
renouvellement ACME à échéance.

Les fichiers de base du service et du timer n'ont pas changé. Les marqueurs
d'invocation, de démarrage, les PID et compteurs de redémarrage des deux VPN
et de Nginx sont identiques aux préimages. Aucun de ces services n'a redémarré.
Seul Caddy sur le secours a été rechargé ; son PID est resté inchangé.

La surveillance Windows du chemin principal a réalisé **1 166 contrôles HTTPS
normaux**, sur le portail et une cible de test, entre 12:36:52 et 13:08:32,
heure de Paris, sans échec. Deux contrôles directs supplémentaires sans proxy
ont également retourné HTTP200. Ces contrôles attestent la continuité pendant
la transition observée ; ils ne constituent pas un essai de panne générale.

Des préimages privées du sender et une sauvegarde bornée de la paire TLS côté
réception ont été préparées avant transfert. Elles servent à un retour ciblé
après comparaison avec l'état courant, sans écraser des changements concurrents.
Elles ne remplacent pas une archive indépendante complète de l'infrastructure.

Le receiver existant remplace ses fichiers successivement ; cette correction
ne transforme pas ses écritures en transaction unique. Son rollback ne couvre
pas toutes les erreurs d'écriture intermédiaires. Un retour vers un ancien
certificat n'est pas forcé automatiquement et doit respecter les gardes de
fraîcheur. La récupération reste une opération ciblée à vérifier.

Le raccord TLS est donc corrigé pour la synchronisation attestée. Aucun
basculement client complet, redémarrage machine ou renouvellement futur à
échéance n'a été testé dans cette mission. La réplication reste asynchrone.

## Orchestration et délégation

L'orchestrateur a gardé la responsabilité de l'intégration et des opérations
réelles. Il a confié la préparation du sender et de la recette à un agent dans
un checkout de laboratoire distinct, la revue à des agents en lecture seule
et les documents publics à un agent documentaire.

Les revues statiques ont précisé les risques de mélange de versions, de
remplacement de fichiers pendant la lecture, de contention du verrou et de
validation de chaîne. Elles ont aussi signalé la limite héritée du receiver.
La préparation a été corrigée et qualifiée avant la revue indépendante finale
favorable ; le relecteur n'a pas présenté les tests de l'auteur comme les siens.

L'orchestrateur a ensuite vérifié la parité des données VPN, préparé les
préimages, suspendu la copie périodique et installé le seul sender concerné.
Il a déclenché deux transferts sérialisés par le même service, vérifié la
réception, le certificat servi et la continuité, puis finalisé la garde
temporaire et restauré le timer. Le receiver, les configurations VPN et
les règles réseau n'ont pas été remplacés par cette correction.

L'agent documentaire a rédigé ce rapport, ajouté son lien au sommaire et
actualisé uniquement le bloc du raccord et son travail restant dans
l'architecture publique. Il n'a lancé ni test, modèle, mail ou opération de
service. Les résultats réels et les comptes exacts ci-dessus proviennent
des preuves transmises par l'orchestrateur. Les modèles des sessions ne sont
pas déduits des fichiers ; aucun coût ou gain n'est inventé.

## Coopération et adaptation au contexte

Les consignes publiques, la fiche de reprise, l'état partagé, le protocole,
les annonces pertinentes et la documentation précédente ont été lus.
Cette dernière distinguait déjà le certificat actif de la copie de secours
restée liée à Caddy. La présente correction traite ce raccord opérationnel,
sans réécrire les preuves de la migration initiale.

Les réservations ont séparé sources, revues indépendantes, architectures et
rapport. Le périmètre documentaire a d'abord porté sur le rapport et le
sommaire, puis l'orchestrateur a transféré les seuls blocs concernés de
l'architecture publique. Les rapports historiques et les autres changements
ont été préservés.

Le brouillon maintenait les résultats en attente. Sa finalisation a attendu
la réussite de la dernière étape Ansible, la restauration du timer et le bilan
de surveillance. Les vérifications propres à la rédaction sont statiques :
structure, liens, diff, anonymisation et préservation des parties non attribuées.
Elles ne sont pas annoncées comme une nouvelle qualification des services.

Le texte emploie des rôles et composants génériques. Il ne publie aucune adresse,
identité de connexion, donnée client, chemin privé, référence interne, clé ou
valeur de secret. Les préimages, preuves détaillées et échanges lisibles restent
dans les espaces privés autorisés ; les copies d'audit ne sont pas présentées
comme un déchiffrement des anciens messages natifs.

L'agent documentaire a remis les trois fichiers à l'orchestrateur, qui en
assure la revue et la publication ; il n'a lui-même fait aucun commit ou push.
Aucun accès Kali ni session depuis PIAgentControl n'a été utilisé pour cette rédaction.
