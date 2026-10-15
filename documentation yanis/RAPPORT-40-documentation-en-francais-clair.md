# Rapport 40 — Documentation claire et complète des workflows et de l’architecture

15 octobre 2026 — auteur : Yanis / Codex.

## Demande et résultat

Yanis a signalé qu’un paragraphe sur la réception, le suivi et les reprises était incompréhensible. Après une explication en langage courant, il a demandé d’appliquer ce style à la documentation des workflows et à l’architecture. Il a ensuite précisé que la simplification devait conserver toute la profondeur utile : schémas des services, connexions réseau, protocoles, exposition, répertoires de travail et fichiers importants. La mission finale couvre les références privées et les guides publics, avec une rédaction longue, expliquée et lisible par une personne qui ne connaît pas encore le système.

### Les workflows expliqués dans leur ordre de fonctionnement

Le guide public commence par le parcours d’un mail jusqu’à la livraison d’une maquette. Il détaille ensuite la réception, les filtres, la file, le verrou, les appels synchrones et asynchrones, le rattachement au client et au projet, les rôles de GPT et de Jev et la provenance des exigences.

Il distingue les décisions sur le besoin, le bilan d’un message, les phases de reprise, l’état de construction et la confirmation d’un envoi. Ces familles de statuts répondent à des questions différentes. Les définitions et exemples expliquent pourquoi READY ne signifie pas maquette construite, pourquoi un accusé de prise en charge ne prouve pas la fin du dialogue et pourquoi UNKNOWN ne signifie pas que le mail n’est certainement pas parti.

Le parcours Telegram est décrit avec les actions humaines : lire le message, choisir Stop ou Continuer, répondre au champ attendu, examiner l’aperçu et confirmer l’envoi. La validation d’une réponse commerciale reste distincte de la validation finale d’une maquette déjà construite. Le contrôle d’une identité ou d’un ancien bouton est expliqué par son effet concret, plutôt que simplement nommé.

La construction est détaillée depuis le brief admissible jusqu’à l’artefact contrôlé : cible autorisée, file de jobs, révision, séparation des maquettes, revue indépendante, comparaison du fichier distant avec le contenu servi, approbation de livraison et reçu Gmail. Les limites de preuve sont conservées : contrôler l’index ne vérifie pas toutes les interactions du site et confirmer un envoi ne prouve pas sa lecture.

### Les corrections de fonctionnement intégrées à la description

La documentation tient compte du raccordement de reprise intégré le 15 octobre. Après Continuer et confirmation de l’envoi humain, le système peut réévaluer immédiatement le brief client existant. L’ancienne formulation imposant systématiquement d’attendre le prochain mail est remplacée pour ce parcours. La réponse saisie par l’opérateur conserve son rôle de message assistant ; elle ne devient pas une exigence client. Un nouveau mail peut rendre la reprise précédente obsolète.

Le dialogue publié compte désormais quatre-vingt-quinze étapes dans les exports consultés. Le guide ajoute le rôle du récepteur de reprise interne et ne présente plus la liste ancienne de six workflows comme un inventaire exhaustif de toute l’instance.

Le statut ATTENTION est expliqué à partir du classificateur : résultat insuffisamment sûr, nouvelle revue nécessaire ou réservation d’envoi empêchant une reprise. La reprise d’analyse IA est limitée aux codes et conditions prévus. La relance client après deux heures est décrite comme opportuniste : c’est un délai minimal examiné lors d’un événement utile, pas une promesse d’envoi à une heure exacte.

Les diagnostics Telegram sont décrits comme un suivi des étapes, codes et compteurs. Leur activité périodique dans le service existant est distinguée d’un nouveau cron n8n ou d’un deuxième consommateur du bot. Une trace reste une information de suivi, pas une confirmation de livraison.

### Une architecture détaillée pour chaque audience

L’architecture publique explique machines, conteneurs, proxy HTTPS, VPN, DNS, service Telegram, bridge OpenCode, modèles et hébergement. Elle contient des schémas et des catalogues fonctionnels de répertoires et de fichiers. Les noms de fichiers utiles sont expliqués avec leur consommateur, leurs entrées, leurs résultats et l’effet d’une édition. Les paramètres sensibles sont anonymisés.

L’architecture privée conserve les valeurs de cartographie autorisées : adresses, interfaces, ports, protocoles, domaines et chemins réels, sans valeur de secret. Elle distingue un listener observé, une règle de pare-feu et un accès réellement essayé depuis l’extérieur. Elle donne aussi les relations entre services et l’emplacement des données durables.

Les sources, copies candidates, fichiers installés, exports de workflows et archives de mission ne sont pas confondus. Les catalogues historiques restent disponibles, avec leur date et leur portée de sauvegarde. Un fichier installé mais non suivi par Git n’est plus présenté comme récupérable intégralement depuis un ancien commit.

Les trois références privées associées sont complétées sans effacer leurs catalogues. L’inventaire des secrets décrit le nouveau fichier d’authentification de reprise, ses consommateurs et sa protection, sans lire ni publier sa valeur. Le guide Ansible indique que les anciennes recettes Telegram ne reproduisent pas à elles seules les modules installés plus récemment. La référence agents distingue les bases de délégation, le bridge applicatif, le worker Telegram et le candidat de forum OpenCode.

### Contrôles et limites de cette mission documentaire

Les contrôles comprennent la lecture des documents et sources nécessaires, les métadonnées de services et d’écoute du Pi, les règles réseau ciblées, les métadonnées Docker, les états Git et les comparaisons de fichiers installés. Les rapports récents et leurs annonces de fin sont utilisés pour dater les changements applicatifs ; cette mission ne s’attribue pas leurs tests.

La relecture vérifie les liens, les diagrammes en source, la cohérence des statuts, les audiences et l’absence de paramètres privés dans les modifications publiques. Les publications sont contrôlées par comparaison des fichiers récupérés depuis les branches distantes. Les schémas décrivent les flux et ne remplacent pas un essai réseau extérieur. Leur source est relue ; aucun essai de navigateur n’est présenté comme réalisé pour cette rédaction.

Aucun workflow, envoi Gmail, notification Telegram métier, modèle IA externe, construction de site, test Ansible ou connexion à Kali n’est lancé pour réviser les documents. Les annonces de coordination sont distinctes des échanges clients. Les parcours réels réalisés par d’autres missions restent attribués à leurs propres rapports et périmètres.

## Orchestration et délégation — Délégation

La première explication et la première réécriture courte ont été réalisées directement par Codex. Après la demande explicite de profondeur, Codex a réparti le travail éditorial entre trois enfants natifs et conservé l’intégration et la publication.

Un enfant a préparé l’architecture publique détaillée : plan de lecture, cartes des services et protocoles, flux applicatifs, répertoires fonctionnels et fichiers importants, avec anonymisation des accès. Un autre a préparé le guide des workflows : parcours pas à pas, schémas, états, reprises, diagnostic, exemples et glossaire. Leurs propositions ont été écrites dans des fichiers distincts avant intégration ; ils n’ont pas publié ou modifié les services de production.

Le troisième enfant a effectué un inventaire et une revue privés en lecture seule. Il a contrôlé les modules installés, leurs sources, leurs permissions et l’état Git, puis relu l’introduction privée et le guide public des workflows. Ses constats ont corrigé le sens de certaines flèches réseau, la localisation du broker des runners, une garantie excessive sur le contenu d’une copie publique, le chemin source d’un module de blocage et les limites de reprise des recettes Ansible.

Codex a réuni les deux états de l’architecture privée : l’un contenait les ajouts locaux Jev et l’autre les corrections déjà publiées de construction et livraison. Les préimages ont été conservées, les changements étrangers préservés et les détails antérieurs maintenus. Codex a ensuite préparé les compléments des quatre références privées, intégré les propositions publiques, contrôlé les liens et l’anonymisation, puis publié et relu les fichiers distants.

Les trois enfants ont rendu un résultat exploitable. L’inventaire et les propositions ont été intégrés après relecture, plutôt que comptés comme terminés à leur seul lancement. La revue des workflows n’a trouvé aucun point bloquant après les corrections et a demandé de confirmer la fin de la mission de reprise ; cette fin et son rapport public ont ensuite été lus. Le modèle hérité des enfants Codex n’a pas été mesuré séparément. Aucune nouvelle session OpenCode payante n’a été lancée pour cette révision éditoriale ; aucun coût ni gain n’est inventé.

## Coopération et adaptation au contexte — Collaboration

Les consignes du projet et des dépôts documentaires, les règles de coordination, les documents existants et les annonces récentes ont été consultés. Les missions documentaires précédentes avaient publié leurs fins. Les fichiers visés ont été annoncés avant écriture, puis le périmètre a été étendu lorsque la demande a explicitement inclus les références privées associées.

Le travail utilise les sources du Pi par SSH, sans navigateur. Les copies de préparation sont séparées des fichiers actifs et des données de production. Les secrets n’ont pas été lus pour expliquer leurs emplacements. La réécriture publique ne contient pas les adresses, racines d’accès, identifiants internes, messages clients ou prompts privés de la version d’exploitation.

Une autre mission a intégré la reprise immédiate et le diagnostic pendant la rédaction. Le point d’intégration n’a pas été assimilé à une fin avant sa clôture. La publication du rapport 41 et la fin correspondante ont été vérifiées, puis le dépôt documentaire a été avancé sans écraser ce nouveau rapport. Les guides décrivent désormais cette évolution avec ses limites, au lieu de conserver la seule attente passive d’un nouveau message.

La comparaison des copies privées a également révélé un décalage entre le dernier commit connu par un ancien clone et le contenu déjà publié. La mise à jour réunit les apports au lieu de choisir arbitrairement une copie. Les versions locales et distantes antérieures restent récupérables. Les modifications d’autres auteurs, les fichiers sources applicatifs et leurs données ne sont pas committés en bloc par cette mission.

Les dernières annonces sont relues avant publication. Les essais réels éventuels d’une autre mission ne sont pas absorbés sans preuve ni présentés comme des effets de la rédaction. La clôture de coordination décrit les fichiers effectivement publiés et libère uniquement les réservations documentaires propres à cette mission.

Une autre mission a également réservé l’utilisation de PIAgentControl à Yanis personnellement. Sa clôture et la nouvelle règle ont été lues ; les références actuelles expliquent cette restriction sans modifier la chaîne NOC. Le changement concurrent du fichier de consignes du clone public est préservé hors des commits documentaires de cette mission.
