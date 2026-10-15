# Préparation d'un accès VPN dédié à un serveur — 15 octobre 2026

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
