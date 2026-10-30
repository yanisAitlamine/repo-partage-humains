<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Portail connecté à n8n et parcours client — 15 octobre 2026

## Demande et résultat

Yanis demande de raccorder le portail client récent au backend n8n, au besoin
dans un workflow séparé nommé explicitement « Test Frontend ». Le parcours attendu
comprend inscription, connexion, conversation sur le site, obtention d’une
maquette et vérification complète avec un client fictif.

Le nouveau workflow est créé et publié. Il adapte le dialogue au transport web
et utilise le modèle déjà configuré dans le dialogue commercial existant.
Les workflows principaux de traitement des mails et le brouillon du constructeur
sont conservés. L’adaptateur ne les appelle pas directement : il produit une
maquette HTML privée dans le portail, sans Gmail, Telegram, Jev ou constructeur
OpenCode. Il ne réalise pas une livraison de site complet sur un hébergement.

Les comptes et sessions restent gérés par le serveur du portail. Chaque message
est rattaché au site dont le propriétaire a été vérifié. Une file persistante
enregistre la demande dans la même transaction que la conversation, puis un
worker la réclame une seule fois. Le navigateur peut se fermer ou recharger sans
relancer la génération. Une demande est autorisée à la fois par site, avec une
limite quotidienne par compte. Les demandes interrompues ou incertaines ne
sont pas relancées automatiquement.

Le serveur appelle une entrée n8n locale authentifiée par une connexion dédiée.
L’identité du site et de la demande doit revenir identique dans le résultat.
Le modèle ne dispose d’aucun outil ; le stockage des réponses chez le fournisseur
et la conservation des données d’exécution de ce workflow sont désactivés.
Aucun mot de passe de compte, session ou accès administratif n’est transmis au
modèle ni inclus dans le navigateur ou les exports de source.

Un message de discussion ne déclenche pas de maquette à lui seul. Le client
utilise le bouton de génération. Le résultat est conservé avec son empreinte
et sa version, accessible uniquement au propriétaire. L’aperçu est isolé dans
un cadre sans script et servi avec une politique de contenu restrictive.
Les scripts, formulaires, cadres imbriqués, gestionnaires d’événements,
redirections de document et liens externes sont refusés. Les anciennes versions
restent conservées. Les retours du client sont pris en compte lors d’un nouveau
clic ; l’approbation est attachée à la version précise et ne publie aucun site.

Trente-trois tests Python passent sur Windows et sur le serveur cible. Ils
couvrent comptes, sessions, concurrence, isolation des sites, file persistante,
réponse liée à la bonne demande, quotas, résultat invalide, aperçu dangereux,
interruption, absence de relance et approbation de la version exacte. TypeScript
et les compilations de production passent sur les deux machines. Le premier
essai de compilation Windows utilisait un runtime système incompatible ; le
runtime fourni avec l’environnement a permis la compilation, sans changement
des dépendances du produit.

Le parcours navigateur avec n8n et le modèle réels est vérifié dans une base
séparée : inscription, discussion, génération, deux retours, trois versions de
maquette, rechargement, déconnexion, reconnexion et approbation fictive de la
dernière version. Les modifications de titre et de palette sont visibles dans
la dernière maquette. Quatre demandes se terminent avec succès. Cette approbation
appartient uniquement au banc fictif et ne constitue pas un accord humain sur
une livraison du pipeline existant.

Le premier appel natif avait échoué parce que la sortie JSON structurée était
déjà décodée par le nœud modèle. Le parseur accepte désormais l’objet natif ou
la chaîne JSON, puis vérifie strictement les clés, types, bornes et références.
La sélection automatique des connexions avait également choisi d’autres
connexions existantes : elles ont été remplacées explicitement et relues avant
les essais. Une version de test avait proposé un lien de contact externe fictif ;
les contrôles finaux et les consignes n’acceptent plus que des liens internes.
La dernière génération réelle passe ces contrôles renforcés.

Après présentation de la version concrète et des résultats, Yanis autorise
explicitement sa mise en service privée. Une sauvegarde SQLite cohérente et
vérifiée précède la bascule. La nouvelle recette du portail exécute treize tâches
sans échec. Le code installé correspond à la release approuvée ; seul le portail
redémarre. Le proxy conserve exactement son empreinte et le service ne présente
aucun redémarrage automatique au contrôle. Le portail HTTPS charge la nouvelle
interface. Sur le service installé, deux comptes fictifs distincts vérifient
inscription, déconnexion et connexion, attributs du cookie sécurisé, conversation
réelle puis génération d’une maquette. Le HTML servi correspond à son empreinte
enregistrée. L’autre compte reçoit un refus d’accès et un visiteur déconnecté
doit s’authentifier. Aucun accord client n’est simulé dans cette base active ;
la maquette de contrôle y attend sa revue. Les devis et abonnements restent
inactifs. Les preuves minimales sont conservées dans l’espace privé de mission.

La portée reste celle d’une maquette visuelle privée. Paiements, publication
commerciale, import de pièces Drive, constructeur d’hébergement et livraison
par mail restent des parcours distincts. Les tests ne démontrent pas un accès
Internet public, une sauvegarde indépendante complète ni une reprise après
perte du serveur. Le code est proposé sur une branche et une demande de revue ;
la fusion n’est pas effectuée implicitement par le déploiement autorisé.

## Orchestration et délégation

Codex réalise directement la lecture du contexte, l’adaptateur, le workflow,
les contrôles, les corrections, le parcours navigateur et l’installation.
Aucun sous-agent, session PIAgentControl ou agent NOC n’est lancé. Le modèle
configuré pour les réponses et maquettes est GPT-6 Luna, déjà présent dans le
dialogue commercial. Les appels du produit ne sont pas des sessions de délégation.
Aucun coût ou gain de consommation n’est inventé.

## Coopération et adaptation au contexte

Les consignes, points d’entrée d’architecture, passations, rapports récents et
documents du portail sont consultés. Les annonces machine du portail précédent,
de la reconnexion Drive et des missions réseau sont lues. Une intention annonce
les chemins réservés avant les écritures, puis des extensions précisent la
documentation, le banc séparé et la release autorisée.

Le travail reste sur les sources du portail et un nouveau dossier d’export n8n.
Les modifications concurrentes du lecteur Drive, du moteur de décision, du
constructeur et du réseau sont préservées. La passation détaillée de cette
mission utilise un fichier distinct pour éviter les écritures concurrentes
dans la passation globale. Les données réelles du portail ne sont ni remplacées
par le banc de test ni restaurées depuis une ancienne copie.

Les sources personnelles des deux machines sont vérifiées contre la même
version, les exports omettent les connexions, et la release installée est
comparée aux fichiers approuvés. Aucune connexion Kali, ancien rôle Ansible,
modification du fichier global protégé, ouverture réseau ou reprise d’un ancien
message n’est effectuée. La fin de mission publie les résultats et libère
uniquement ses propres réservations.
