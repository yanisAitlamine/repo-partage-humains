# Portail : dépôt PDF privé et reprise de plusieurs sites

État du 17 octobre 2026 : **candidate versionnée et testée, non activée**.
Le test réel demandé n’est pas encore effectué. Une cible de prévisualisation
explicite et l’accord sur la release exacte restent nécessaires.

## 1. Demande et résultat

Le demandeur souhaite reproduire depuis le portail un essai initialement envoyé
par mail, avec son PDF et plusieurs sites existants à regrouper. Il autorise les
adaptations nécessaires du parcours portail avant l’essai. Le document et les
sources du cas réel restent privés ; ils ne figurent pas dans ce rapport.

L’examen du code et des versions actives confirme deux écarts : le portail
recevait des dossiers Drive mais aucun PDF directement ; son constructeur ne
recevait pas la liste des sites sources selon le contrat du parcours mail.

La candidate ajoute un dépôt privé par projet, avec session, propriétaire,
Origin, révision et consentement. Le PDF original reste dans la base privée,
sans URL publique. Son empreinte est vérifiée avant extraction native page par
page. La provenance documentaire du dépôt web reste distincte de Drive et du
mail. Les textes et métadonnées sont contrôlés avant leur admission au moteur
de citations, sans devenir des instructions système ou des permissions.

Un PDF actif par projet est accepté, jusqu’à 1 Mio, 50 pages et 50 000 caractères
extraits. Le client choisit le PDF ou un dossier Drive comme source active,
sans fusion implicite. Une lecture incomplète, un scan sans texte ou un fichier
suspect bloque la suite. Aucun OCR ni extraction des images du PDF n’est promis.

Quatre sites sources consentis peuvent être liés au brief et au job. Une
inspiration autorise l’analyse ; une refonte exige une déclaration de
réutilisation des contenus. Les liens de l’assistant et ceux du document ne
donnent aucun droit de collecte. Le collecteur existant conserve ses contrôles
de réseau public, budgets, preuves de destination et nettoyage des temporaires.
Les sites sources ne sont jamais modifiés et ne deviennent pas les cibles de
déploiement. L’entrée mail conserve son budget propre.

Les changements sont committés et poussés sur les branches principales de
leurs dépôts canoniques. Cela ne signifie pas qu’ils sont exécutés : aucun
workflow actif, service ou fichier constructeur exécuté n’a été remplacé dans
cette étape. La préparation scellée de la release a réussi séparément. Le service actuel répond normalement. Un contrôle des releases a trouvé un cache Python supplémentaire dans la version active ; les sources scellées sont inchangées. La nouvelle candidate correspond intégralement à son manifeste. Le cache reste à archiver avant bascule, sans affaiblir le contrôle d’intégrité.

Contrôles réalisés : 226 tests Python et 270 tests JavaScript du portail,
77 tests ciblés après le dernier ajustement de l’adaptateur, 11 tests du
contrat constructeur et compilation frontend. Les deux SDK ont été validés
par n8n, sans avertissement final. Un contrôle local du document réel confirme
ses quatre pages textuelles admissibles ; cette extraction locale ne prouve
pas encore son traitement natif dans le workflow du portail.

Le premier contrôle du constructeur dans le worktree a refusé deux tests :
la copie de son plugin de contexte était modifiable par le groupe. La protection
de cette copie a été rétablie, sans affaiblir le garde ni modifier le service ;
les onze tests ont alors réussi. Les contrôles n’ont envoyé aucun mail,
appelé aucun modèle ni construit de site réel.

La génération réelle reste à faire après choix de la cible et activation
autorisée. Le clic de construction, la revue et le contrôle humain de livraison
conservent leurs rôles distincts. Un prototype ne prouvera ni une migration
exhaustive ni une administration de blog réellement connectée.

## 2. Orchestration et délégation

Codex réalise directement la recherche du message demandé, la comparaison des
contrats, les changements, leur revue, les tests, les commits et la préparation.
Aucun sous-agent n’est lancé dans cette mission. Aucune session PIAgentControl,
connexion Kali ou ancien rôle Ansible réservé n’est utilisé. Aucun coût ou gain
de tokens n’est déduit.

Les workflows et travaux d’autres sessions ont été consultés comme contexte,
sans les présenter comme une délégation de cette mission. Leurs retours et
correctifs récents sont distingués de nos vérifications. Les SDK validés et les
tests fictifs ne sont pas présentés comme une recette réelle.

## 3. Coopération et adaptation au contexte

Les consignes applicables, la fiche de reprise, le protocole, l’état partagé,
la passation du portail et les références sur sources, diagnostic, refonte et
déploiement ont été consultés. Les annonces pertinentes ont révélé une autre
mission de continuité du brief et une construction de test en cours : leurs
espaces et travaux sont préservés, et aucun essai concurrent n’est lancé.

Les intentions et extensions ont réservé des worktrees personnels et les blocs
précis avant modification. Les sources ont été fondées sur les correctifs déjà
versionnés, les versions actives ont été relues et sauvegardées en privé, et les
nouveaux graphes ont été comparés. Les brouillons mail et les changements
préexistants des checkouts canoniques restent intacts.

La cible n’apparaît pas dans le message source : elle n’a pas été inventée.
L’accord demandé pour la release exacte vient des règles de déploiement du
portail. Les références opérationnelles, captures de sauvegarde et empreintes
exactes restent dans la passation privée. Ce bilan atteste notre travail et ses
limites ; il ne certifie pas les opérations historiques des autres sessions.
