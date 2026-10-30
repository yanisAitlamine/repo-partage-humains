<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Préparation d'un accès VPN dédié à un serveur — 15 octobre 2026

Ce document conserve les étapes initiales de préparation et d'attente. L'état
actif ultérieur est décrit dans le [rapport d'activation et de remise privée](RAPPORT-VPN-ACTIVATION-20261015.md) :
certificat émis, identité admise, filtre ciblé appliqué et transfert client restant.

## Demande et résultat

Yanis demande de traiter le mail de son collaborateur puis de lui répondre.
La demande porte sur un appareil supplémentaire : identité OpenVPN distincte
du poste personnel, accès aux seuls services privés nécessaires, administration
du serveur conservée privée, procédure de raccordement et révocation individuelle.
Les secrets ne doivent pas passer dans la messagerie ni les conversations d'agents.

La préparation comprend un modèle de profil sans secret, une procédure de
génération de clé sur l'appareil, un outil de signature et révocation hors serveur
VPN, et une recette d'admission Ansible limitée à la nouvelle identité. L'adresse
prévue est libre dans les affectations inspectées et consignée dans la préparation
privée. HTTPS et DNS sont les seuls services prévus ; l'exception SSH du poste
personnel ne s'étend pas au nouvel appareil. Les comptes applicatifs restent
personnels. Les routes générales et le DNS global de l'hyperviseur sont préservés
par le modèle ; sa protection contre les connexions entrantes reste aussi à
contrôler dans son propre pare-feu.

**Aucun nouvel accès n'est activé.** La demande de certificat publique doit
d'abord être générée par le collaborateur sur son serveur, avec sa clé privée
conservée localement. Le certificat signé et la protection du canal seront ensuite
remis par transfert SSH personnel, après vérification des identités. Aucun secret
réel n'a été créé, consulté dans les sorties ou transféré pendant cette préparation.
Le coffre réel de l'autorité n'a pas été ouvert.

L'outil impose l'identité attendue et l'usage client, sans recopier les privilèges
éventuellement demandés dans la CSR. Il refuse une signature de CSR incorrecte,
un type de clé insuffisant, une CRL invalide et l'écrasement du fichier de sortie.
La révocation conserve les entrées existantes et s'appuie sur le certificat public
émis, absent du coffre historique. Une révocation ne coupe pas instantanément une
session existante : une déconnexion contrôlée reste à organiser si nécessaire.

Cinq tests synthétiques passent : émission sans privilège de CA malgré une CSR
qui le demande, conservation de la clé publique de l'appareil, refus d'une autre
identité, révocation sans perte ni doublon et refus d'une CRL étrangère. Un coffre
chiffré artificiel vérifie aussi le parcours de commande et le refus d'écrasement.
Ces tests ne constituent ni une émission réelle ni une connexion extérieure.

Les sources sont versionnées dans le dépôt technique privé et intégrées au clone
actif du Pi, avec vérification de leur état Git. Le modèle et les étapes ont été
envoyés au collaborateur dans son fil de mail, sur instruction explicite de Yanis.
Le retour Gmail et une relecture des métadonnées confirment SENT et le bon fil ;
la réception et la lecture par le destinataire ne sont pas attestées.

Restent la préparation du SSH par clé côté collaborateur, la réception et la
vérification de la CSR, la signature réelle, le transfert protégé, l'admission
opérateur et le test depuis le réseau extérieur. Aucun playbook Ansible, mode
check, syntax-check ou lint n'a été lancé. Les services et règles actives n'ont
pas été modifiés ; aucune connexion à l'hyperviseur ou à Kali n'a été effectuée.

Complément du même jour : sur une nouvelle instruction explicite de Yanis,
sa clé SSH publique personnelle existante et son empreinte vérifiée ont été
envoyées au collaborateur, dans le nouveau fil demandé. La clé utilise RSA
3072 bits ; la préférence Ed25519 du mail a été signalée et aucune nouvelle paire
n'a été créée. La clé privée n'a pas été consultée, copiée ou transmise.
L'adresse source prévue a été indiquée à partir de l'affectation serveur du
profil personnel, avec confirmation du tunnel restant à faire sur le poste.
Les métadonnées relues confirment SENT, le destinataire et le fil. L'exception
de réseau nécessaire reste à coordonner séparément ; aucun compte, droit,
filtrage ou routage n'a été activé par cet échange.

Nouveau complément : la CSR publique est arrivée. Sa signature, son sujet et
l'empreinte DER de sa clé publique correspondent aux éléments annoncés dans le
mail. Les certificats publics de l'autorité et la CRL courante ont été vérifiés
sans ouvrir le coffre privé réel. La confirmation humaine de l'empreinte par le
contact habituel, expressément demandée par le correspondant, reste à obtenir.
Elle a été demandée à Yanis ; aucune réponse n'est inventée à partir du silence.
Yanis a ensuite choisi explicitement de solliciter la confirmation par email.
Un second message demande au collaborateur de comparer et confirmer les deux
empreintes publiques, VPN et hôte SSH. Son envoi et le bon fil sont vérifiés ;
la réponse personnelle reste attendue avant les opérations dépendantes.

Deux nouvelles recettes préparent la remise SFTP et l'exception SSH entre les
deux seules identités concernées, avec retour établi. Le lot est prévu dans un
répertoire contrôlé par root et lisible par le seul groupe personnel vérifié du
destinataire. Le transfert ne doit contenir ni clé privée d'appareil, ni clé de CA,
ni protection TLS du serveur. La recette de filtre conserve les refus généraux,
prévoit validation préalable et restauration de préimage en cas d'échec.

Ces recettes et leur documentation sont versionnées dans le dépôt technique
privé et intégrées au clone actif, après revue statique et contrôle du diff.
Elles n'ont pas été testées ou exécutées. Aucun certificat n'a été émis, aucun
secret TLS client créé, aucun lot remis, aucune admission ou exception chargée.
Le service VPN n'a pas redémarré. La réponse envoyée au correspondant décrit
précisément cette attente ; SENT et le bon fil sont confirmés par relecture des
métadonnées. Les annonces de la mission de connexion externe concurrente ont été
lues et son périmètre préservé. Cette étape est une préparation complète des
opérations dépendantes, avec confirmation d'identité encore nécessaire.

## Orchestration et délégation

Codex réalise directement la lecture ciblée du mail, la préparation des fichiers,
la revue statique, les cinq tests PKI artificiels, l'intégration des sources et la
réponse autorisée. Aucun sous-agent ni session PIAgentControl n'est lancé.
L'agent du collaborateur n'est pas démarré ou piloté par Codex ; il recevra les
étapes par le mail adressé à son humain. Aucun coût ou gain n'est estimé.

## Coopération et adaptation au contexte

Les consignes du projet, l'architecture, la passation et le dernier rapport local
ont été consultés, ainsi que le protocole machine et les annonces récentes.
Les fichiers actifs et le dépôt propre ont été relus avant l'intégration. Les
réservations des autres missions, dont une reprise d'authentification externe,
ont été préservées ; aucun recoupement d'écriture n'a été constaté.

Une intention puis une extension déclaratives annoncent les nouveaux fichiers,
les copies, les validations et les publications. L'extension précise que la
révocation est traitée par un nouvel outil, sans modifier le gestionnaire
historique. Les nouvelles annonces sont relues avant les écritures concernées.
Le journal de fin ferme les réservations de cette mission ; il ne libère pas
celles des autres participants.

La documentation historique décrit certains accès différemment de la production
actuelle. La lecture de la configuration et des règles chargées permet de
distinguer l'exception personnelle existante du futur accès serveur. Le choix
de génération locale de clé répond à la demande de ne pas partager de secrets.
Le démarrage automatique du VPN est laissé à une décision ultérieure sur le
déverrouillage local ; aucun retrait silencieux du chiffrement n'est proposé.

Ce rapport public est anonymisé : la cartographie privée, les identifiants de
messages et les chemins d'exploitation restent dans les références privées.
Le contenu et le diff sont relus avant publication. Git conserve les sources ;
il ne remplace pas une sauvegarde indépendante des identités et états privés.

Ce complément a une intention et une fin déclaratives propres. Les dernières
annonces ont été relues, notamment celle du portail distinct ; leurs réservations
ont été préservées. Le suivi est ajouté à ce rapport et à la passation privée,
sans publier la clé, son empreinte, les coordonnées ou les paramètres d'accès.
