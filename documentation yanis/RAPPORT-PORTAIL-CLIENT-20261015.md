<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Portail client indépendant, déployé en HTTPS privé — 15 octobre 2026

## Demande et résultat

Yanis demande de commencer un produit de création et de maintenance de sites, puis précise de réaliser le portail client seulement pendant que la chaîne de production évolue. Il demande également le versionnement complet, la coopération avec Ilyes et ses agents, un email de passation, et une construction sur le serveur avec déploiement limité au réseau privé derrière le Caddy HTTPS déjà présent.

Le portail livré permet de créer son propre compte, saisir un brief, ouvrir un exemple fictif, conserver une conversation guidée, enregistrer des demandes de changement, consulter des prix proposés, accepter un devis sans paiement, examiner un concept et enregistrer un retour ou une approbation liée à sa version. Une exportation JSON des données conservées du projet est disponible. La conversation est guidée par des règles : aucun modèle n'est connecté. Le concept utilise un modèle de présentation local : ce n'est pas un site client généré et publié.

Le frontend React/TypeScript est construit sur le serveur. Un service Python autonome sert ses fichiers et une API locale, avec SQLite pour ses comptes et projets. Le service utilise un compte système séparé, un répertoire de données privé et une écoute de boucle locale. La nouvelle route est ajoutée à la branche privée du reverse proxy existant ; l'application préexistante conserve sa route racine. Aucun port public, DNS, certificat, workflow ou service de la chaîne n'est modifié pour raccorder le produit. Aucun hébergement externe du portail n'est publié.

Le code, ses dépendances verrouillées, les tests, la recette de déploiement et les instructions de contribution sont poussés dans un dépôt privé distinct. Une invitation d'écriture est envoyée au compte GitHub personnel d'Ilyes ; son acceptation n'est pas attestée au contrôle. Une copie Git partagée permet à son compte de lire et modifier les sources ; elle n'est jamais exécutée par la production et ne se synchronise pas automatiquement avec la version installée.

Quinze tests passent sous Windows puis sur le serveur : identités, cookies, mots de passe dérivés, invalidation de session, isolation des comptes, sauvegarde/relecture des projets, révisions concurrentes, origine des requêtes, taille et validation des entrées, limites de demandes, prix imposés côté serveur et approbation de version exacte. La compilation TypeScript et le build de production passent sur le serveur. Le parcours visuel compte/brief/demande et une largeur mobile sont contrôlés avec des données fictives locales ; la page HTTPS réellement déployée est ouverte dans le navigateur Windows.

La première validation de routage s'arrête avant modification du proxy à cause d'un chemin de binaire incorrect. La recette est corrigée, versionnée et appliquée avec succès. Une seconde application complète indique zéro changement et aucun échec. Le service est actif et activé, sans redémarrage automatique observé ; sa santé locale est bonne, le portail et la racine HTTPS répondent avec succès. Le filtre HTTPS existant et l'écoute de boucle locale sont contrôlés. Aucun nouveau test depuis un client VPN extérieur ou une connexion Internet extérieure n'est revendiqué.

Il reste à définir les conditions commerciales finales, l'éligibilité des modifications, la récupération et suppression de compte, les invitations d'équipe, les pièces jointes et les sauvegardes indépendantes de la base. Les tarifs sont des propositions ; une acceptation ne démarre ni abonnement ni paiement. La publication d'un concept et l'exécution d'un agent sont impossibles dans cette version. Les intégrations de paiement, IA, orchestration, construction et hébergement client attendent une nouvelle demande. Git conserve le code, pas les données vivantes ni une preuve de restauration complète.

## Délégation

Codex réalise directement l'implémentation, les tests, la mise en forme, le versionnement, la recette et le déploiement autorisé. Aucun sous-agent ou processus d'Ilyes n'est lancé ; aucun OpenCode depuis la base réservée à Yanis n'est utilisé. Le lot proposé à Ilyes concerne l'édition d'un brief existant, avec conservation de l'historique et invalidation des anciennes approbations et acceptations de devis lorsque le contexte change. Les critères, fichiers, commandes de développement et limites sont documentés pour ses agents, sans présenter cette invitation comme un travail déjà commencé. Aucun coût ou gain n'est déduit.

## Collaboration

Les consignes, l'architecture, la passation courante, le dernier rapport utile, le protocole partagé, l'état et les annonces récentes sont consultés. L'intention de portail précède ses écritures serveur ; les extensions déclarent le déploiement autonome et les ajouts documentaires. La mission concurrente de sources documentaires conserve son périmètre et ses modifications. Les réservations portent sur les nouveaux dossiers du portail, son unité, sa seule route de proxy et les sections documentaires ajoutées ; aucun ancien rôle de migration ou accès au contrôleur personnel n'est utilisé.

La précision humaine sur le serveur et Caddy remplace la première orientation technique. La version livrée devient autonome et utilise l'accès HTTPS privé existant. Les sources actives, la copie de coopération et les releases exécutées sont distinguées. Les permissions de code d'Ilyes sont contrôlées par son compte, sans copier de clé ou de credential de Yanis. Leurs agents doivent utiliser leurs identités et des branches avec revue, annoncer leurs fichiers et terminer explicitement leurs réservations ; aucun push ne déploie automatiquement le produit.

Les références d'exploitation et l'inventaire d'identités sans valeurs sont actualisés dans leur dépôt privé. Seuls ce rapport anonymisé et son entrée de sommaire sont publiés ici. L'email de passation demandé est une communication privée destinée à Ilyes ; il ne contient aucun mot de passe, cookie ou clé. Une clôture de coordination libère les réservations de cette mission à la fin des contrôles ; elle ne libère pas celles des autres agents.
