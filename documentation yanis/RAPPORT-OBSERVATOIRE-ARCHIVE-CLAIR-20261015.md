<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Observatoire : chiffrement et archives lisibles — 15 octobre 2026

## Demande et résultat

L’utilisateur signale que des échanges et consignes de délégation Codex affichés
sont chiffrés. Il demande de les déchiffrer si la clé est détenue, de conserver
les textes lisibles sur le serveur pour les relire et d’ajouter une règle durable
aux consignes des agents.

Le diagnostic confirme le chiffrement des arguments Multi-agent v2 et de certains
contenus natifs. Le [code officiel de Codex](https://github.com/openai/codex/commit/5f4d06ef186b896d316620556e561d59206c3ebf)
décrit un déchiffrement côté OpenAI, dans Responses. L’Observatoire ne détient
aucune clé correspondante ; aucun déchiffrement local n’est réalisé. Les clés
d’authentification ne sont pas recherchées ou employées comme clés de messages.
Les anciens cryptogrammes ne sont donc pas restitués en clair.

Le rapport précédent ne prouvait pas la lisibilité des prompts : des cryptogrammes
étaient affichés comme leur texte, et des enveloppes lisibles pouvaient accompagner
un corps chiffré. Cette lecture était incomplète. Le collecteur distingue désormais
texte disponible, contenu chiffré et contenu indisponible. Il masque les cryptogrammes
à l’affichage, conserve auteur/destinataire et signale explicitement la limite.
Les anciennes projections ne peuvent pas remplir l’archive avec ces seules enveloppes.

Un stockage privé durable du serveur conserve les textes disponibles en clair
dans des fichiers JSON lisibles, avec contexte et provenance. Un index distingue
les textes natifs lisibles des copies d’audit déclarées. Pour les contenus opaques,
seules leurs métadonnées et empreintes sont indexées ; aucun cryptogramme n’est
enregistré comme texte clair. La vue « Archives en clair » reste accessible par
la connexion propriétaire et permet une relecture indépendante des journaux sources.

La règle demandée est ajoutée aux consignes globales puis leur protection et
leurs empreintes sont rétablies. Les agents doivent consigner les futures consignes
lisibles avant envoi et les réceptions lisibles au moyen du helper prévu, avec
provenance d’audit explicite. Une copie d’audit ne prouve ni déchiffrement ni
égalité avec un corps chiffré. Les informations indisponibles ne sont pas inventées.

Le code et la recette dédiée sont versionnés dans le dépôt privé canonique du
serveur. Les 35 tests passent sur le serveur ; le poste exécute 34 tests et écarte
le seul contrôle de permissions POSIX. Les contrôles couvrent persistance,
déduplication, refus des cryptogrammes comme audit lisible, droits, liens symboliques,
migration des anciennes projections et refus HTTP anonyme. La syntaxe JavaScript
est vérifiée. Le stockage n’est pas une sauvegarde indépendante : sa restauration
complète après perte du serveur n’est pas attestée.

Le déploiement exécuté correspond au commit privé `67c4ed6`. La vue est vérifiée
dans le navigateur authentifié : ouverture d’un texte natif, provenance, bascule
vers les métadonnées opaques et avertissement explicite d’indisponibilité.
Le contrôle du stockage confirme 253 fichiers lisibles, tous privés, sans
cryptogramme brut ; ce relevé est daté et peut évoluer avec les collectes.
Le service est actif et l’API des archives refuse les requêtes anonymes.

## Orchestration et délégation

Codex réalise directement le diagnostic, les corrections, les tests, la règle,
le versionnement et le déploiement. Aucun sous-agent n’est lancé pour cet essai.
Aucun coût ou gain n’est inventé ; aucune conversation artificielle d’agents
n’est présentée comme une délégation réelle. L’outil ne contourne pas le chiffrement
et ne dispose d’aucun accès de déchiffrement supplémentaire.

## Coopération et adaptation au contexte

Les consignes, recette, précédent rapport et annonces de coordination sont lus.
Une intention réserve uniquement le périmètre de l’Observatoire, sa nouvelle
archive et ses documents. Les opérations parallèles du portail et de la chaîne
de livraison sont préservées. La recette appliquée est propre à cet outil ;
les anciens rôles réservés et la machine personnelle de contrôle ne sont pas utilisés.

L’archive est réservée au compte opérateur, hors Git et hors journal partagé.
Le service dispose d’une autorisation d’écriture limitée à ce nouveau stockage.
Le compte collaborateur est refusé sans lecture du contenu. Les textes restent
filtrés selon les protections existantes ; les secrets libres non reconnus
demeurent une limite. Le rapport public ne contient aucun message privé,
identifiant de session, valeur secrète ou chemin opérationnel de l’archive.
