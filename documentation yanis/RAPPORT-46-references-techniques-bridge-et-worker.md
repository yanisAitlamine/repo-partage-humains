<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Références techniques du bridge et du worker Telegram — 15 octobre 2026

## Demande et résultat

La demande humaine est de publier une documentation technique détaillée du
bridge n8n/OpenCode et du worker Telegram, en expliquant chaque fichier et
chaque fonction, puis de vérifier que le code est versionné. La publication
porte sur deux références publiques :

- [Bridge n8n/OpenCode : référence technique](BRIDGE-N8N-OPENCODE-REFERENCE-TECHNIQUE.md).
- [Worker Telegram : référence technique](WORKER-TELEGRAM-REFERENCE-TECHNIQUE.md).

Les guides expliquent les responsabilités, les appelants, les données en entrée,
les résultats, les effets externes, les gardes et les limites. Ils décrivent
également les tests existants et les préparateurs historiques. Les schémas
relient API, jobs, vérification des artefacts, décisions humaines, Gmail et
reprise durable. Les exemples sont fictifs ; les adresses, identifiants et
configurations de production ne sont pas reproduits.

Le code reste dans le dépôt source privé `n8n-services`. Une capture de
**52 fichiers** a été relue : **10 étaient déjà suivis**, **42 ne l’étaient pas**.
Ils sont d’abord enregistrés sur `main`, au commit
`0ef8e2eb78a16c19e26019de8ba8725d4f313abe`. Une correction applicative
stabilisée après la revue est ensuite intégrée au lot : la référence finale est
`666c8b5f240925da7cf91f31ed94205d7e1bc4dd`, dont la référence distante est
contrôlée. Un manifeste d’empreintes et un guide de versionnement accompagnent
les sources ; les règles d’exclusion couvrent les copies locales de
configurations privées et de bases. Les huit modules Python du worker installé
avaient exactement les mêmes octets que les sources capturées.

Deux limites conservées sont expliquées : les définitions générées du
laboratoire embarquent un moteur historique, et le chemin d’état de la
configuration exemple demande une adaptation au chemin exact accepté par le
chargeur actuel. La revue a également découvert une ancienne cible compilée
dans le module d’approbation Telegram : avec le contexte du workflow portable,
elle aurait provoqué un refus avant les boutons. Après transmission du constat,
la mission applicative parallèle a aligné cette seule constante et ajouté deux
tests portables de non-régression. L’agent documentaire a relu le delta, vérifié
la concordance d’empreinte du module installé, puis versionné ces fichiers et
actualisé les guides. Le code de production n’a pas été modifié par les agents
documentaires ; les opérations applicatives appartiennent à l’autre mission.
Cette lecture ne prouve pas un parcours humain complet et ne reproduit pas
les valeurs de déploiement. Les recettes de déploiement historiques
ne rétablissent pas, à elles seules, tous les modules et états du service actuel.

Les deux guides rassemblent environ **52 000 mots**, huit schémas Mermaid et
des sommaires internes cliquables. Le rapprochement avec les inventaires
statiques ne laisse aucun nom de fonction Python ou JavaScript nommé absent
du périmètre documenté. Les callbacks anonymes et les copies embarquées sont
expliqués par leur rôle et leur transformation. Ce contrôle des noms complète
les relectures ; il ne démontre pas à lui seul la justesse d’une description.

Les contrôles de cette mission sont la lecture des sources, l’inventaire
statique des fonctions, la comparaison des empreintes, la revue de
confidentialité, la vérification des liens et des différences Git, puis la
vérification des objets publiés. Les tests applicatifs décrits dans les guides
n’ont pas été exécutés par les agents documentaires. Ces agents n’ont lancé ou
redémarré aucun service, workflow, fournisseur IA, Gmail, Telegram, site ou
playbook. Les actions de la mission applicative et leurs résultats restent
distincts et relèvent de son rapport.

## Orchestration et délégation

Le parent Codex a fixé le périmètre, capturé les sources, préparé un clone
isolé, contrôlé la visibilité des dépôts et intégré les livrables. Trois enfants
Codex natifs, réutilisés après la fin de leur mission précédente, ont reçu des
fichiers distincts :

| Session et rôle | Travail confié | Résultat attendu et revue |
| --- | --- | --- |
| `public_architecture` : référence du bridge | Lire la capture du bridge, inventorier ses fonctions, décrire API, runner, artefacts, workflow, unité et tests. | Guide public du bridge, relu et intégré par le parent. |
| `workflow_docs` : référence du worker | Expliquer le poller, les accès Gmail/n8n, les validations humaines, les blocages techniques, les préparateurs et les tests. | Corps du guide Telegram, avec gardes et limites explicites. |
| `private_inventory_review` : décision et audit | Contrôler la liste des fichiers versionnables, chercher les données sensibles et expliquer les modules de décision et de reprise. | Avis privé de sélection et annexe publique intégrée au guide Telegram. |

Les enfants ont hérité du modèle du parent ; son identité exacte n’a pas été
mesurée indépendamment dans cette mission. Leurs lectures sont statiques : ils
n’ont ni importé les scripts à effets de bord ni exécuté leurs parcours de
production. Le parent distingue la production des brouillons, le code des
données, la capture des fichiers des preuves de fonctionnement et la rédaction
des livrables de leur intégration effective. Aucun coût ou gain de tokens n’est
déduit de cette organisation. Aucune session OpenCode depuis PIAgentControl
n’a été lancée, reprise ou déclenchée indirectement.

Les relectures ont été croisées : l’auteur de l’annexe décision a relu le bridge,
et l’auteur du bridge a relu l’annexe. Une troisième lecture indépendante porte
sur le socle du worker. Les corrections intégrées conservent les limites réelles
du code : une tête de projet absente n’est pas rejetée par certains contrôles de
livraison ; une mémoire hors fil peut omettre son rôle ; un callback routé vers
un module peut y être consommé avant le refus de son action. Deux comparateurs
temporels sont également précisés. Ces constats ont corrigé la documentation,
sans modifier les validateurs ni les données de la production.

La revue du socle précise aussi les notifications pouvant se répéter faute de
réservation préalable, les erreurs possibles de libération du bail, les champs
effectivement relus dans l’outbox et les dépendances obligatoires absentes des
recettes historiques. Les schémas ont été relus dans leur source Mermaid ;
ils n’ont pas été rendus pendant cette mission.

## Coopération et adaptation au contexte

La mission a repris les consignes applicables, les références d’architecture,
la passation et les annonces de coordination du Pi. L’intention déclarative
`codex_docs_bridge_worker_20261015`, publiée le 15 octobre à 02:37 UTC, réserve
deux nouveaux guides et ce rapport. Une autre mission poursuit ses corrections
métier et réserve le rapport 45 : ses sources vivantes et ses essais restent
de son ressort. La documentation est fondée sur une capture identifiée plutôt
que sur des lectures successives de fichiers susceptibles de changer.

Un accord explicite de coordination, publié à 02:53 UTC, partage les blocs
documentaires des deux index. Les liens vers les références techniques et ce
rapport sont ajoutés au README et au sommaire public ; le pointeur d’évolution
applicative et l’entrée du rapport 45 restent réservés à l’autre mission.
La préparation et les commits documentaires utilisent un clone isolé, après
actualisation et lecture des différences. Les règles d’agents concurrentes
ne sont pas incluses dans la publication.

L’extension de 02:43 UTC annonce les fichiers de suivi du versionnement et
l’avancement des seules métadonnées Git du dépôt source. L’opération exigeait
une branche attendue, aucun changement déjà préparé dans l’index, une ascendance
vérifiée et la conservation des empreintes. **181 fichiers existants** ont
conservé exactement leur contenu ; seules les exclusions Git prévues ont été
ajoutées, avec les deux nouveaux documents de suivi. Les autres modifications
et exports en cours sont restés présents et non inclus dans ce commit.

L’extension de capture finale, annoncée après l’intégration applicative de la
cible, ajoute seulement la constante alignée et ses deux méthodes de test.
Une comparaison AST confirme que les autres instructions du module de
production sont identiques. Le manifeste est actualisé, le commit final est
poussé, puis les métadonnées Git actives avancent de nouveau sans écraser le
code : **183 fichiers existants** sont conservés, avec la seule mise à jour
prévue du manifeste. La référence `origin/main` du poste Windows est également
actualisée par transfert Git, sans changer sa branche de contexte ni ses
modifications locales. Les corrections sémantiques encore au stade candidat
dans l’autre mission ne sont pas incluses dans cette capture.

Une seule normalisation CRLF vers LF concerne un test JavaScript, suivant la
politique existante du dépôt. Le manifeste conserve l’empreinte de capture et
explique cette différence. Les huit modules Python installés n’ont subi aucune
transformation. Les fichiers de règles d’agents et de protection ne sont pas
modifiés ; les espaces privés de secrets, bases, archives et échanges clients
ne sont pas ouverts. Aucun accès à Kali, test Ansible ou changement des accès
réseau n’a été réalisé.
