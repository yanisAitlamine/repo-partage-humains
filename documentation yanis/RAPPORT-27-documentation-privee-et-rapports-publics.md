<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Rapport 27 — Architecture privée et rapports publics

13 octobre 2026. Ce rapport public décrit l'organisation documentaire, sans
cartographie privée des accès, inventaire de secrets ou données client.

## Demande et résultat

Yanis demande de renommer son dépôt privé en
`projet-n8n-documentation-humaine`, puis de limiter sa version courante à deux
documents : une architecture complète et un inventaire des secrets sans leurs
valeurs. Il demande aussi une description plus précise du but et de l'utilité
des fichiers et une règle imposant la publication des rapports dans le dépôt
partagé public.

La comparaison initiale avec les documents sensibles révèle six rapports de
Yanis absents du dépôt privé, six documents d'Ilyes absents et sept documents
Yanis différents. Avant leur import, Yanis change le périmètre : les rapports
ne doivent plus figurer dans son dépôt privé. Cette nouvelle demande remplace
le projet d'import initial ; aucun rapport manquant n'a été ajouté au privé.

Le dépôt est renommé en conservant sa visibilité privée. Sa version courante
contient seulement `ARCHITECTURE.md` et `secrets.md`. L'architecture conserve
les machines, flux et inventaires techniques et complète les intégrations
récentes, la coordination, les workflows et la reprise. Les descriptions
distinguent consommateur, entrées, sorties, finalité et effet d'une modification.
Les sources, copies installées, configurations actives et données persistantes
sont distinguées. Les fichiers du système et dépendances tierces sont regroupés
par fonction ; ce travail n'est pas un audit individuel de tout le système.

L'inventaire de secrets conserve emplacements, utilisateurs, destinataires,
producteurs et méthodes attestées, et ajoute les identités utilisées par le
worker de revue humaine. Les inconnues restent indiquées. Les valeurs de
secrets, clés privées, configurations d'authentification et bases clients
n'ont pas été ouvertes pour cette mise à jour.

Les vingt-six rapports historiques de Yanis disposent déjà de versions dans
le dépôt public partagé. Les copies du dépôt privé sont retirées de son arbre
courant ; cette opération ne réécrit pas son historique Git. Les originaux
sensibles historiques ne sont pas copiés aveuglément dans le public.

Les consignes imposent désormais trois sections aux rapports : demande et
résultat, orchestration et délégation, coopération et adaptation au contexte.
Tous les nouveaux rapports sont destinés au dépôt public partagé, après
anonymisation et revue ; le privé conserve les deux références techniques.

## Orchestration et délégation

Codex effectue directement la comparaison, la lecture ciblée des README et
sources, la rédaction, les modifications documentaires et les vérifications
Git. Aucun sous-agent ou agent OpenCode n'est lancé : la mission porte sur
des documents et leurs destinations, sans implémentation applicative à déléguer.
Les opérations d'identité et de publication privées restent sous le contrôle
de l'opérateur. Aucun coût, consommation ou gain supposé n'est présenté.

Le prompt humain initial demandait comparaison et ajout ; la correction
humaine impose ensuite deux documents privés et les rapports publics.
L'orchestrateur conserve cette correction comme périmètre déterminant et
abandonne l'import des rapports. La restitution porte sur les documents
publiés et les limites réellement vérifiées, pas sur une liste d'agents lancés.

## Coopération et adaptation au contexte

Les consignes du projet, l'architecture, la passation, le dernier rapport utile,
les règles du dépôt partagé, son README, le protocole et les annonces récentes
ont été lus. Les lectures de coordination confirment la séparation entre
documentation publique, références sensibles et copies de code candidates.
Elles indiquent également des missions concurrentes de diagnostic/envoi et
d'évaluation de candidats ; aucun de leurs fichiers applicatifs n'est modifié.

Une annonce récente signale une réponse humaine envoyée et la clôture de sa
revue ; l'architecture distingue ce constat communiqué d'une nouvelle
vérification directe du service. Le diagnostic signalé de relance reste hors
de cette mission. Cette lecture évite de décrire systématiquement l'envoi
humain comme encore non observé et n'autorise aucune correction métier.

La session locale déclarative `codex_docs_privees_20261013` a publié une
intention de comparaison, puis une reprise avec extension de périmètre après
l'interruption humaine. Les nouvelles annonces sont relues avant écritures.
Les dépôts documentaires sont réservés, les changements préexistants du projet
local sont préservés et l'ajout aux consignes globales reste ciblé sur la demande
explicite. Leur protection est rétablie après édition. La clôture de session
libère les réservations après les contrôles de publication.

## Contrôles et limites

Vérification de visibilité privée avant publication, état Git propre avant
préparation des dépôts documentaires, comparaison de fichiers, inspection
des sources publiques nécessaires, contrôle des liens locaux, du diff et
recherche de formats de secrets connus sans afficher leurs valeurs. Un scan
lexical n'est pas une preuve universelle d'absence de secret. Une alerte initiale
correspond à un chemin de montage de secret, pas à une valeur de credential.

Aucun playbook, suite applicative, redémarrage, workflow, construction de site,
rotation de secret ou connexion Kali n'est effectué par cette mission.
Les validations documentaires ne prouvent pas la validité des identifiants
actifs ni une restauration complète. L'état des branches distantes et le
contenu publié sont vérifiés à la clôture ; les modifications locales des
autres dépôts ne sont pas publiées en bloc.
