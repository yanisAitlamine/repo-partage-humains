<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Deux parcours mail vers maquette livrée — 16 octobre 2026

## Demande et résultat

L'utilisateur a demandé de corriger les blocages puis de mener un nouveau pipeline de bout en bout sur chacune des deux cibles de test, jusqu'à des liens essayables. Deux nouveaux mails fictifs ont été envoyés une seule fois au compte pipeline autorisé, avec un sous-domaine explicitement fourni comme dans un brief client.

Les deux parcours ont abouti : réception du mail, analyse commerciale par OpenAI Decisions sans clarification bloquante, construction d'une maquette isolée, première revue indépendante, correction, nouvelle revue indépendante en `pass`, recette navigateur, envoi du lien et constat de réception dans Gmail. Les deux exécutions constructeur sont terminées en `success`. Les liens reçus ont ensuite été ouverts dans Brave.

Le périmètre effectivement testé est **mail vers première maquette livrée**, avec données fictives et aucun engagement réel. Le mode site complet n'a pas été lancé. L'autorisation finale provient du harnais d'opérateur TEST expressément borné à ces scénarios ; elle est enregistrée comme `USER_AUTHORIZED_TEST_HARNESS`, `human_click=false`. Aucun clic Telegram ni aucune validation client n'est simulé. Le poller Telegram est resté arrêté et désactivé.

Correctifs intégrés dans les sources canoniques du serveur et poussés dans Git :

- preuve de cible en lecture seule, liée au job et au registre opérateur : chemins canoniques, absence de symlinks, HTTPS sans redirection, égalité des octets SSH/HTTPS et marqueurs du job ;
- nouvelle preuve technique automatique au moment d'enregistrer une revue, afin de lier le verdict au contenu effectivement servi ;
- stabilisation du défilement avant capture et mesures de visibilité des ancres ;
- consignes de coordination : un inventaire paginé complet par tâche, puis lecture des nouveautés avant écriture ;
- mode prototype du harnais, contrat canonique pour les cibles dynamiques et exigence d'une recette navigateur valide avant livraison.

Les correctifs des maquettes ont porté sur la typographie et un libellé pour la première ; la navigation mobile, les ancres et le lien d'évitement pour la seconde. Les remplacements ont été précédés de sauvegardes hors racine web, vérifiées par empreinte et restauration non destructive. Les index racines des deux cibles sont restés identiques à leur état initial.

Validation : 12 tests Python de preuve, 5 tests Node dont un véritable navigateur pour le défilement, 9 tests du harnais ; parsing et revue des différences. Les deux recettes réelles ont réussi à 1440 et 390 px, avec 28 étapes par maquette : contenu, ancres visibles après clic, structure, absence de débordement, d'images cassées et de formulaire actif. Le manifeste, la révision, la preuve technique et la réception navigateur concordent. Une seule décision de livraison a été réservée par autorisation ; les deux envois sont enregistrés `SENT` et leurs liens ont été constatés dans la boîte destinataire.

Limites : ces essais ne prouvent ni le mode site complet, ni le parcours Telegram natif, ni un service client en production, ni tous les appareils ou besoins d'accessibilité. Aucun ancien rôle Ansible n'a été testé ou appliqué. Aucun réglage du modèle Jev n'a été entraîné pendant cette intervention ; l'analyse commerciale exécutée est celle d'OpenAI Decisions déjà intégrée.

## Orchestration et délégation

Codex a effectué directement le diagnostic, l'implémentation des correctifs, les tests ciblés, l'intégration Git, l'envoi des deux scénarios, leur suivi, la recette finale et la vérification des mails reçus. Aucun sous-agent Codex ni aucune session PIAgentControl n'a été lancé.

Chaque workflow constructeur a lancé son planificateur NOC existant, qui a confié la construction à un rôle d'implémentation et la revue à un rôle indépendant. Pour chaque scénario, quatre tâches terminées sont attestées : construction initiale, revue du premier tour, correction, revue du second tour. Le modèle configuré des rôles est `openai/gpt-6-luna` ; la configuration seule n'est pas présentée comme une mesure de qualité ou de coût.

Le constructeur écrivait uniquement la page dans son dossier de job sur l'hébergement autorisé ; le réviseur utilisait des preuves techniques et captures fraîches en lecture seule. Les premières revues ont demandé des changements ; les secondes ont enregistré `pass`. Codex a ensuite recontrôlé indépendamment les octets servis et les liaisons de preuves, inspecté les captures et constaté les résultats réels dans le navigateur et Gmail.

Les consignes et retours de tâches disponibles en clair ont été conservés dans l'archive privée autorisée : 18 événements `audit_copy` traités. Il s'agit de copies lisibles, pas d'un déchiffrement natif attesté. Aucun coût ni gain de tokens n'est inventé.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche courte de reprise, le protocole et l'état partagé ont été consultés, ainsi que les annonces utiles. Une intention principale puis des extensions ont réservé les fichiers de code, le harnais et le présent rapport. La mission parallèle de portail et les modifications préexistantes du dépôt ont été préservées ; les commits ont porté uniquement sur les fichiers de cette intervention.

Le blocage précédent combinait difficulté de preuve de cible, répétition coûteuse de l'inventaire de coordination et observations d'ancres pendant leur défilement. La correction a ajouté une preuve déterministe liée au job et clarifié les lectures du journal. Un premier candidat de preuve a dû être adapté à la version de Python de l'hébergement avant installation. Une tentative de patch de maquette a été arrêtée sans écriture par sa garde de correspondance, puis corrigée après revalidation de la sauvegarde.

La coordination des revues présente deux limites attestées : une première revue n'a pas terminé l'inventaire et la dernière revue de la seconde maquette n'a pas consulté ni publié dans le journal partagé. Elles ont travaillé en lecture seule. La réception technique a réussi, mais les contrôles opérateur ultérieurs ne remplacent pas ces actions historiques manquantes ; une conformité complète de coordination n'est donc pas revendiquée.

Les preuves exactes, les références d'exécution et la passation restent privées. Ce rapport public omet domaines d'exploitation, identifiants internes, chemins privés, adresses et contenus des mails. La clôture de mission libère les réservations ; la passation distingue les sources intégrées, les processus de test terminés, les preuves réelles et les limites.
