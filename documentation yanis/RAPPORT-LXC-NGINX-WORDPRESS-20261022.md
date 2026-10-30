<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Conteneurs de test jetables, passerelle Nginx et blog WordPress livré

Rapport du 22 octobre 2026. L'infrastructure, la livraison du blog de recette et
l'intégration du code dans la branche principale sont vérifiées.

## Demande et résultat

La demande consiste à disposer de quatre cibles de test indépendantes pour
la technologie choisie par un client, sans créer de base avant le besoin de
l'application. Le Raspberry Pi assure la passerelle HTTPS, le DNS et le VPN ;
le remplacement de Caddy par Nginx doit conserver les services existants.
L'essai demandé est un vrai blog WordPress, avec base dédiée provisionnée à la
demande, administration native et accès propriétaire remis en privé.

### Infrastructure effectivement mise en place

Quatre conteneurs LXC Debian 13 non privilégiés ont été créés sur Proxmox.
Leur racine applicative était vide et l'absence de base a été vérifiée avant
la construction finale WordPress. Ces cibles sont génériques ; la quatrième
héberge désormais le blog et sa base locale, les trois autres restent disponibles
pour d'autres technologies. Une base n'est pas demandée au client.

Un domaine DuckDNS dédié permet de former les quatre noms de test. La résolution
privée les dirige vers la passerelle, qui route chaque nom vers son conteneur.
La répartition entre plusieurs répliques d'une même application reste une
évolution distincte.

| Composant | Fonction réellement exercée |
| --- | --- |
| Poste opérateur | Administration privée, navigateur et conservation chiffrée des accès |
| Raspberry Pi | Entrée HTTPS avec Nginx en conteneur, DNS et VPN |
| Serveur applicatif existant | Production applicative et services conservés |
| Proxmox et ses quatre LXC | Cibles Debian indépendantes et remplaçables |
| Laboratoire séparé | Préparation, qualification et parcours du client fictif |
| Base MariaDB du blog | Créée dans la cible après la validation finale, consommée par WordPress via son socket local |

Nginx fonctionne dans Docker sur le Pi. Caddy y est arrêté et désactivé après
la bascule. Les accès existants au portail, à l'Observatoire, à CarPrice et à
n8n conservent leur routage et leurs préfixes attendus. Les en-têtes nécessaires,
WebSocket et réponses progressives sont prévus ; WebSocket a été exercé au lab.
Les restrictions au réseau local et au VPN sont conservées.

Les certificats ont été réellement émis par validation DNS et leur renouvellement
est indépendant de Caddy. Les quatre noms de test utilisent un certificat
générique adapté à leurs sous-domaines. Un renouvellement futur à échéance
n'a pas encore été observé. Aucune nouvelle ouverture publique sur la box
n'est revendiquée par cette étape.

Le remplacement ponctuel de la quatrième cible a été exercé pendant une reprise.
Les helpers de récupération sont limités à cette opération et à ses preuves :
le cycle automatique générique de suppression et recréation entre tous les
essais reste à développer.

### Blog et remise propriétaire effectivement vérifiés

Le blog utilise réellement WordPress 7.1.3, un thème adapté aux huit pages
approuvées et un fil de publications dynamique. Sa base MariaDB et son utilisateur
dédiés ont été créés automatiquement après validation client et revue de la
maquette. L'isolation SQL locale et les identités du site ont été vérifiées.

La recette finale passe **16 contrôles de parcours** et **16 contrôles
propriétaire** : connexion à wp-admin, brouillon, envoi d'image, publication,
lecture anonyme de l'article et de son image effectivement chargée, présence
dans le fil du blog, modification publique, mobile sans débordement, déconnexion
et retour à une administration protégée. L'article publié a aussi été ouvert
anonymement dans Brave. Le format de date natif jour/mois/année et la présence
d'une seule publication finale ont été vérifiés.

La notification finale Gmail a remis l'URL du site, l'identifiant propriétaire
et un lien WordPress natif privé de réinitialisation. Le lien séparé vers
l'administration a été vérifié dans le portail et le blog. Le mot de passe
propriétaire et le lien privé de réinitialisation sont conservés dans un coffre
Windows chiffré réutilisable ; l'enregistrement et la relecture des deux éléments
ont été vérifiés sans affichage de leur valeur.
Le propriétaire peut ouvrir son administration, préparer un article en brouillon,
y joindre une image, le publier puis le modifier. Ce sont les opérations
effectivement exercées par la recette.

Le projet livré est consultable dans le service normal du laboratoire, actif
et activé au démarrage. Une procédure bornée a sauvegardé son ancienne base
vide, contrôlé le schéma et installé la base de recette par sauvegarde native.
La version applicative de ce service est restée inchangée. La vraie interface
HTTPS passe **40 contrôles avant et 40 après un redémarrage normal** :
liens du site et de son administration, huit pages privées sur ordinateur et
mobile, aperçus inertes, reconnexion et absence d'erreur navigateur.
La consultation ne dépend donc plus du processus temporaire de test.

### Incidents compris et reprises conservées

L'interface Proxmox était fonctionnelle. Le filtre VPN de l'hyperviseur
autorisait le SSH du poste utilisé, tout en réservant l'accès direct à l'interface
web à d'autres clients. Un tunnel SSH lié uniquement au poste local a permis
de l'ouvrir dans Brave. Aucune nouvelle permission directe sur son interface
web n'a été ajoutée. Deux mails de coordination ont été envoyés au collaborateur
concerné, d'abord pour l'investigation puis pour la cause confirmée.

Les transferts vers les conteneurs ont demandé une correction MSS bornée aux
flux SSH et HTTP concernés par le VPN. Les ajouts réseau conservent les
contrôles d'intégrité des helpers existants et restent propres aux cibles de test.

La bascule attend désormais l'ouverture effective de l'écoute TLS, avec une
échéance bornée et une validation du certificat. Les essais d'activation
infructueux avaient réellement restauré Caddy avant correction dans le lab.
Trois anciens chemins sans barre finale renvoyaient une réponse vide ; Nginx
les redirige vers leurs chemins canoniques. La réparation contrôle strictement
l'ancienne réponse vide, la destination, les paramètres et la réponse finale.
Les vrais chemins applicatifs gardent leur comparaison de statut stricte.

La première installation WordPress s'est arrêtée avant création de sa base,
de son utilisateur SQL et du site : une configuration MariaDB non secrète
avait hérité d'un mode privé qui empêchait le service de la lire.
Le contrôle de sa configuration effective a bloqué la suite. L'installateur
fixe explicitement son mode lisible, inhibe le démarrage prématuré pendant
l'installation des paquets et produit des reçus d'étape et d'erreur fixes.

Les preuves ont été archivées avant le remplacement de la quatrième cible.
La première opération a détruit le conteneur, puis s'est arrêtée sur deux
résidus standards de l'hôte. Une recette distincte de création seule a vérifié
les absences et les résidus exacts, les a archivés puis retirés avant la création
neuve. Les configurations des trois autres cibles et du réseau sont restées
inchangées ; la nouvelle identité SSH a été attestée et épinglée strictement.

Le second parcours a réellement installé WordPress. Son banc de recette a
ensuite attendu du JSON alors que le mode natif d'envoi média renvoie un
identifiant en texte. Une première reprise a correctement exercé une nouvelle
validation Gmail, un nouveau travail et l'adoption de l'installation ; elle
s'est ensuite arrêtée sur le sélecteur de lecture de l'URL du média.
Les deux verdicts échoués ont été conservés.

Le champ natif de l'écran d'édition de la pièce jointe a ensuite été vérifié
sur le site réel, et un parcours propriétaire complet a été exercé avant la
reprise suivante. Cette dernière a abouti : nouveau travail livré, deux anciens
travaux toujours échoués dans la base finale, aucun travail actif ni mail non réglé.
Le tout premier essai reste archivé séparément. Le clone de réception Gmail
du test a été désactivé et le workflow original est resté inchangé.

La reprise repose sur une opération native authentifiée, une révision courante,
l'approbation d'origine et les mêmes fichiers, revue et prototype. Une capacité
opérateur configurée vérifie l'installation ; sa preuve et le nouveau tour de
décision sont enregistrés atomiquement. Une nouvelle décision client crée un
nouveau travail et sa réservation. L'adaptateur recontrôle les faits et écrit
un reçu d'adoption distinct, lié à l'origine et au reçu précédent. La chaîne
est bornée et refuse les cycles. Aucun ancien statut n'a été réécrit,
aucun installateur ni modèle n'a été rejoué pendant les deux reprises.

### Vérifications et limites

| Vérification | Résultat et portée |
| --- | --- |
| TLS, routage, préfixes, en-têtes, WebSocket et filtrage du pair | 8 tests réels Docker avec certificats éphémères de lab |
| Bascule et retour arrière | 17 tests isolés, dont refus des mauvaises redirections et des régressions applicatives |
| Renouvellement DNS | 6 tests isolés de périmètre, propagation simulée et erreurs sans fuite |
| Préparation avant activation | 12 contrôles de routes réelles avec TLS vérifié |
| Remise à zéro ponctuelle et réconciliation de création | 9 tests isolés pour chacune des deux recettes, application limitée à la cible admise |
| Parcours natif, contrat final et reprise | 87 tests isolés, dont HTTP authentifié, révisions, idempotence, preuves immuables et nouveau travail |
| Paquet WordPress et adoption chaînée | 25 contrôles Python isolés, dont barrières, plusieurs reprises, reçu altéré, cycles et profondeur |
| Contrat d'envoi média | 9 cas isolés |
| Recette finale réelle | 16 contrôles de parcours et 16 de WordPress propriétaire, image anonyme et publication comprises |
| Interface normale durable | 40 contrôles HTTPS avant puis après redémarrage du service |
| Poste Windows | TLS normal et HTTP 200 sur l'entrée de production, les accès applicatifs contrôlés et les quatre noms de test |

Une omission préexistante de résolution Windows affecte encore l'ancien nom
distinct des interfaces de secours du Pi. Son accès HTTPS privé a été vérifié
depuis le Pi ; il ne doit pas être présenté comme un succès du navigateur Windows.

La recette utilise un **adaptateur WordPress de laboratoire**. Elle n'atteste
pas que le graphe NOC de production possède déjà cette capacité, ni que toutes
les technologies et tous les cycles de conteneurs sont automatisés.
La consultation durable utilise la release UI existante ; elle ne prétend pas
y avoir déployé la nouvelle API de reprise du runtime de recette.
Le code final a été fusionné et poussé normalement dans la branche principale.
Cette intégration a passé 145 tests Python, 143 tests Node et le build frontend,
avec conservation des changements et index concurrents. Les empreintes du
runtime de recette sont conservées séparément de cette version finale.
Aucun déploiement applicatif Pi ou production n'est revendiqué. La persistance
a été vérifiée par redémarrage du service ; un reboot complet de machine
n'a pas été exercé.

## Orchestration et délégation

L'agent principal a conservé la responsabilité des actions réelles : interface
Brave, création des cibles, noms DNS, intégration réseau, bascule HTTPS et
vérifications depuis le poste opérateur. Il a envoyé les mails autorisés,
coordonné les reprises, contrôlé la consultation durable et conservé les accès
dans le coffre Windows.

Un agent a préparé la passerelle Nginx dans le laboratoire avec de nouvelles
recettes Ansible, conservation des routes, certificats indépendants, vérification
préalable et retour arrière. Il a ensuite implémenté la reprise native,
effectué les revues indépendantes WordPress et préparé ce rapport ainsi que
les références privées sans valeurs secrètes.

L'agent réseau a isolé les défauts de création et de transport, préparé les
corrections bornées et les gardes de récupération, puis pris en charge
l'intégration du code dans un checkout distinct pour préserver les travaux
concurrents. L'agent WordPress a préparé l'installateur, le parcours client,
le banc propriétaire, les adoptions et le handoff vers le service UI normal.

La revue croisée a fait corriger la racine admise par le validateur natif,
un sélecteur de preuve d'image incohérent, l'ordre des règles PHP, la
journalisation des liens privés et le rendu des maquettes sans élément
principal explicite. Elle a aussi fait vérifier le contrat intégré entre reprise
native et adaptateur, l'historique des appels et la chaîne des reçus.
Les tests isolés, revues et exécutions réelles sont distingués dans les preuves.

Les deux essais complets ont utilisé quatorze appels API via OpenCode et n8n.
Les sept du parcours ayant installé le blog couvrent analyse, deux directions
artistiques, deux générations et deux revues. Les deux reprises n'ont effectué
aucun nouvel appel modèle.
Les preuves utilisées ici ne donnent pas un modèle exact à attribuer à tous
les rôles ; aucun coût ni gain de consommation n'est inventé.
Aucune session n'a été lancée depuis PIAgentControl.

## Coopération et adaptation au contexte

Les consignes des dépôts, la reprise commune, le protocole, l'état et les
annonces pertinentes ont été lus. Les réservations ont séparé passerelle,
réseau, WordPress, code natif et documentation ; les dossiers de travail,
sources, installations et publications ont été distingués.

Les travaux Gmail et les autres changements présents ont été préservés.
L'intégration applicative utilise un checkout isolé, sans appropriation de
leurs index. Un écart de revue sur le test de cycle a été réconcilié par une
nouvelle lecture : le corps lu avait précédé une écriture concurrente,
et la version courante contient bien la vérification anticipée attendue.

Les échecs ont modifié les décisions suivantes : retour réel à Caddy avant
correction TLS, réparation étroite des chemins vides, réconciliation distincte
après destruction déjà accomplie, puis adoption d'une installation connue.
Les deux erreurs média ont conduit à lire le comportement natif et à exercer
un parcours propriétaire complet avant une nouvelle tentative. Les preuves,
barrières et verdicts ont été conservés ; la réussite finale ne les efface pas.

Les références privées décrivent les fichiers fonctionnels, leurs consommateurs,
les accès et leur génération sans valeurs. Ce rapport en exclut adresses,
noms opérationnels, chemins privés, identifiants internes, contacts, contenu
des mails et prompt client. Les échanges lisibles ont été archivés comme
copies d'audit privées, distinctes des textes natifs chiffrés. Les éléments de
cette mission ont été réconciliés par accusés et empreintes avant l'arrêt du
collecteur ; le volume historique n'est pas attribué à ce seul travail.

La livraison lab et l'intégration des sources sont vérifiées. Les limites
restantes portent sur le cycle générique des conteneurs, le graphe NOC de
production, le reboot complet et l'ancien nom distinct affecté par le DNS du
poste. Elles ne remettent pas en cause les contrôles réellement passés.
