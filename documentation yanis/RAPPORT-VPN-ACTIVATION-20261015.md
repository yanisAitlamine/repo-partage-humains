# Identité VPN serveur activée et lot privé disponible — 15 octobre 2026

## Demande et résultat

Yanis demande de poursuivre après les réponses de son collaborateur, dans la
mission de raccordement VPN et de réponse email déjà autorisée. Le résultat
attendu est un certificat signé, une remise privée et une admission assortie
d'un accès SSH strictement limité, avec conservation de l'administration privée.

Le certificat est émis hors du serveur VPN pour une durée de 90 jours, avec
l'autorité existante. La clé privée de l'appareil et sa passphrase restent chez
le collaborateur. Le coffre d'autorité est chargé par l'outil en mémoire,
sans extraction, affichage ou export de sa clé. Aucun nouveau compte applicatif
ou droit supplémentaire n'est accordé.

La CSR et le certificat passent les contrôles de signature, identité, usages,
dates et empreinte de clé publique. La CRL courante est revalidée et conserve
sa révocation existante. La vérification des deux empreintes demandée par mail
est satisfaite par le retour technique de l'agent du collaborateur sur la machine,
avec son accès personnel déjà épinglé et sous instruction de son humain.
Yanis avait explicitement choisi ce canal de vérification. Ce résultat n'est pas
présenté comme une comparaison manuelle personnellement effectuée par Ilyes.

Le lot disponible par SFTP contient quatre fichiers : autorité publique,
certificat client public, configuration et protection TLS propre au client.
La clé privée de l'appareil, sa passphrase, la clé privée de l'autorité et la
protection TLS serveur sont absentes. Le répertoire de remise est contrôlé par
root et lisible par le seul groupe personnel du destinataire, vérifié exclusif.
Les droits de lecture sont contrôlés sous ce compte ; un compte tiers est refusé.
Le contenu de la clé n'est pas affiché. La copie de remise sera retirée après
réception attestée, tandis que le certificat public opérateur restera conservé
pour permettre une révocation individuelle.

L'identité VPN dispose de son adresse fixe distincte du poste personnel.
HTTPS et DNS vers le serveur restent ses accès applicatifs. Une seule exception
entre clients permet le SSH du poste de Yanis vers cet appareil, avec retour
des connexions établies. Les autres transferts, réseaux internes et accès de
gestion restent refusés. Aucun mode général de communication entre clients
n'est activé. Les droits du compte nominatif restent gérés par le collaborateur.

Les trois nouvelles recettes Ansible ciblées sont contrôlées en syntaxe puis
appliquées localement sur le Pi. L'admission et le filtre terminent sans échec ;
une répétition groupée des trois recettes termine avec 32 tâches réussies,
aucun changement et aucun échec. Le profil de remise reçoit ensuite la route
hôte explicite de retour vers le poste de Yanis : nouvelle application de remise,
14 tâches réussies, une copie modifiée, aucun échec. La protection TLS client
existante n'est pas régénérée. Ces contrôles sont distincts des cinq tests PKI
artificiels initiaux et de l'émission réelle du certificat.

La configuration nftables est validée avant remplacement, avec préimage et
retour arrière prévus ; la table dédiée est chargée atomiquement. Les deux règles
ciblées et les refus suivants sont relus dans la chaîne effective. Le préflight
PKI réussit. Le service VPN conserve sa date d'activation initiale et son compteur
de redémarrages nul. Aucun redémarrage du VPN ou ancien rôle Ansible, ni aucun
accès Kali, n'a été nécessaire.

La réponse de mise à disposition est envoyée au collaborateur sur instruction
de Yanis, avec le chemin SFTP et les seules preuves publiques utiles. Aucun
secret n'est joint au mail. SENT, le destinataire et le fil sont confirmés par
relecture des métadonnées ; la réception et la lecture ne sont pas attestées.

**Restent à réaliser côté client :** récupération SFTP, installation protégée,
activation du filtre local préparé, lancement manuel avec saisie personnelle de
la passphrase, test du tunnel puis du SSH quand le poste de Yanis sera connecté.
Aucune connexion à l'hyperviseur ni nouveau test depuis un client extérieur n'a
été effectué par Codex. Une configuration chargée ne démontre pas ces essais.
Le démarrage automatique reste hors de cette étape.

## Orchestration et délégation

Codex réalise directement la signature, les contrôles, l'exécution des nouvelles
recettes, la revue des effets, les copies de sources et la réponse. Aucun sous-agent
ou session PIAgentControl n'est lancé. L'agent d'Ilyes intervient de son côté sous
ses instructions ; Codex ne le démarre ni ne le pilote. Ses attestations sont
distinguées des vérifications effectuées sur le Pi. Aucun coût ou gain n'est déduit.

Les sources et références d'exploitation sont versionnées dans leurs dépôts
privés ; les secrets et certificats réels restent hors Git. Les références privées
d'architecture et d'identités décrivent les nouveaux fichiers, leurs consommateurs,
leurs protections et les limites de récupération, sans valeur secrète. Ce rapport
public constitue le compte rendu anonymisé ; aucun rapport sensible n'est exporté.

## Coopération et adaptation au contexte

Les réponses, la passation, les sources, les règles actives et les annonces récentes
sont relues avant la reprise. Une intention réserve les fichiers d'admission,
le bloc de filtre ciblé, le répertoire de remise et les références documentaires ;
une extension précise les deux références privées à actualiser. Les états Git
sont contrôlés avant intégration et les changements préexistants sont préservés.
La fin libère uniquement les réservations de cette mission.

La remise est placée sous un parent contrôlé par root pour éviter une écriture
privilégiée dans un dossier remplaçable par son destinataire. Les comptes et
permissions personnels sont utilisés ; aucun secret n'est partagé par commodité.
Le retour technique est accepté selon la méthode de vérification choisie par
Yanis, sans exiger ensuite un nouveau geste qu'il n'a pas demandé.

Les missions parallèles du portail et du raccord documentaire restent séparées.
Leurs dernières annonces et réservations sont lues ; aucun credential ou workflow
de ces missions n'est modifié. Le mail cite l'état de reconnexion déjà documenté
pour éviter un doublon. Le sommaire public réservé par une autre mission reste
intact ; le rapport initial pointe vers cette suite. Le contenu et le diff sont
relus avant publication, sans adresse, coordonnées, empreinte, identifiant interne
ou chemin d'accès privé. Aucun nouveau coffre indépendant des secrets ni test de
restauration n'est revendiqué.
