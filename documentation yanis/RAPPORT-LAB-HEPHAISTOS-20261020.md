<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Laboratoire Héphaïstos isolé — 20 octobre 2026

## Demande et résultat

La demande autorise un laboratoire dédié pour préparer une version passant une recette complète sans Telegram, en préservant les deux productions. Cette intervention porte sur le provisionnement et le runtime ; la correction applicative et la recette client restent une mission coordonnée distincte.

Une nouvelle VM Debian a été créée depuis le template propre. Les autres laboratoires et machines existantes sont préservés. Son amorçage utilise uniquement la clé publique personnelle autorisée, ses comptes de test et ses nouvelles identités locales. Aucun credential, workflow, consommateur ou historique de production n’est importé. L’accès SSH est épinglé, le mot de passe root verrouillé et les services applicatifs écoutent seulement en boucle locale, derrière un pare-feu dédié.

Le runtime comprend Node22, Python, PHP avec SQLite, Chromium, les dépendances Playwright verrouillées et un CLI OpenCode natif de version compatible. Une cible d’hébergement locale distincte respecte le contrat de rangement du CMS. Le frontal HTTPS possède sa propre autorité de test. Les erreurs initiales de permissions du certificat, d’extensions X509 strictes, d’imports MCP et de résolution DNS ont été corrigées uniquement dans le lab.

Vérifications réelles : connexion SSH, interrogation SQLite par PHP, égalité de l’index SSH et HTTPS, validation TLS stricte, lancement de Chromium avec sandbox et capture d’écran. Le serveur MCP démarre et annonce ses neuf outils sans appel de modèle ni invocation de job ou de cible. Les recettes Ansible dédiées ont été appliquées sans échec ; leur orchestration finale est validée syntaxiquement. Aucun ancien rôle réservé n’a été exécuté.

Ces preuves valident le runtime. Elles ne constituent ni une livraison de site client, ni un test fournisseur IA authentifié. Le CLI est installé sans import de connexion fournisseur ; les profils et une éventuelle nouvelle authentification restent à la recette. Aucun prompt payant n’a été lancé par cette intervention.

Une extension ultérieure prépare l’inférence locale après le refus explicite du gateway gratuit, sans tenter de contourner ce refus. La marge de l’hôte est vérifiée, les seules ressources du lab sont augmentées et son redémarrage est coordonné après libération des essais. Le modèle dispose d’un stockage séparé créé uniquement dans l’espace libre ; les partitions système existantes sont préservées. Ollama officiel fonctionne en boucle locale, cloud désactivé et ressources plafonnées. Le modèle vision [Qwen3.5:4b](https://ollama.com/library/qwen3.5:4b) est vérifié par son manifeste exact, sa quantification et ses capacités natives.

Deux véritables appels locaux successifs passent : un calcul simple puis l’identification correcte d’une forme, d’une couleur et d’un nombre dans une image de contrôle. Les réponses finales et compteurs natifs sont conservés ; aucun outil applicatif ou reçu de livraison n’est fabriqué. Ce résultat prouve l’inférence texte et image réelle. La validation du parcours client complet avec ce modèle reste à la recette coordonnée.

Pour préparer un essai plus léger, deux variantes2B sont ensuite téléchargées et vérifiées sans inférence. La variante explicite [2B Q4_K_M](https://ollama.com/library/qwen3.5:2b-q4_K_M) est retenue pour le prochain scénario, les modèles précédents restant conservés. Le transfert est isolé du groupe de ressources du modèle actif et ne redémarre aucun service. Après libération explicite des essais, la marge de l’hôte est revérifiée, puis les seules ressources CPU du lab et son quota d’inférence sont augmentés. Aucun réglage des autres VM ne change. Ni la performance ni la qualité du2B ne sont présentées comme validées par ce simple provisionnement.

Complément pédagogique demandé après présentation de cette évolution : **Ollama exécute le modèle ; Qwen produit les réponses et peut analyser les captures réalisées par Chromium.** Le but est de disposer d’un moteur local pour les essais de génération et de revue visuelle. Cette installation ne constitue pas un prérequis à la restauration de n8n ou des autres services sauvegardés. La variante plus petite vise à réduire le coût de calcul ; le téléchargement ne prouve ni sa vitesse ni la qualité d’un site complet. L’architecture privée distingue désormais explicitement les allocations initiales des ressources actuelles, ainsi que le modèle installé, le raccord applicatif et la recette de bout en bout.

## Orchestration et délégation

Codex réalise directement le provisionnement, les recettes, les contrôles et la documentation. Pendant ce provisionnement, aucun sous-agent ni session OpenCode n’est lancé. Une autre conversation, autorisée par l’utilisateur, conduit les corrections applicatives et la recette. Elle transmet les contrats attendus du frontend HTTPS, du stockage CMS et des dépendances ; les périmètres sont coordonnés avant chaque adaptation.

Les imports manquants proviennent d’une révision Git exacte, avec comparaison des blobs et empreintes avant installation. Les fichiers existants différents sont refusés. L’installation native utilise la distribution documentée par [OpenCode](https://opencode.ai/docs/fr/), sans exécuter ses scripts d’installation, puis vérifie uniquement sa version.

## Coopération et adaptation au contexte

La nouvelle séparation entre production et laboratoire remplace l’ancien usage du Pi comme lab. Les consignes, les annonces et les réservations pertinentes ont été consultées. La machine de contrôle personnelle et les sources applicatives concurrentes sont préservées. L’environnement déjà nommé « stage » n’est pas réutilisé faute d’état suffisamment attesté ; une nouvelle cible est réservée avant création.

Les sources des recettes sont préparées et vérifiées dans le lab, puis intégrées normalement dans Git. Les copies lisibles des échanges de délégation sont archivées en privé comme copies d’audit, sans prétention de déchiffrement natif. La documentation privée conserve les accès, l’ordre des opérations et l’inventaire des nouvelles clés sans leurs valeurs. Le lab reste remplaçable : cette opération ne crée pas une sauvegarde chiffrée indépendante de ses identités.

La clarification documentaire s’appuie sur les preuves de provisionnement et les dernières annonces de recette consultées. Elle est réalisée directement, après réservation des seuls blocs documentaires, sans changement de service ni nouvel appel de modèle. Les essais applicatifs restent distincts ; leur progression ne vaut pas certification de réussite globale dans ce rapport.
