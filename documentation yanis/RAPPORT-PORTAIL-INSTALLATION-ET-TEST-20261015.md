<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Installation du portail et contrôles réels — 15 octobre 2026

## Demande et résultat

L'utilisateur a approuvé l'installation privée du chat unique, de la décision
Jev, du contexte Drive contrôlé et des diagnostics développeurs. Le contrôle
préalable a trouvé une divergence entre l'adresse attendue de la maquette et
l'adresse canonique réellement renvoyée par le constructeur. Une correction
testée a reçu un nouvel accord explicite avant installation.

Cette application corrigée est installée sur le serveur canonique. Une sauvegarde
cohérente de la base et des configurations précède la bascule ; son intégrité et
la conservation des comptes et projets existants ont été vérifiées. Les quatre
workflows web sont activés, le service utilise bien le code attendu et le HTTPS
privé répond. La recette propre au portail termine sans échec. Les anciennes
recettes et les paramètres réseau ne sont pas modifiés.

Le collaborateur dispose du lecteur limité aux métadonnées. Les contrôles sous
son identité réussissent ; le choix d'une autre base est refusé et la base brute
reste inaccessible. Le code et le guide des agents restent disponibles dans la
[copie publique assainie](https://github.com/yanisAitlamine/atelier-portal-public).

Le parcours HTTPS utilise deux comptes fictifs distincts. Inscription, cookies,
révocation de session, reconnexion, isolation, contrôle d'origine et refus des
textes ou sources invalides passent. Le premier message long est accepté mais
son analyse échoue : le workflow tente de décoder une réponse JSON que le nœud
fournisseur avait déjà décodée. Le portail conserve un état bloqué explicite.

Le correctif du workflow accepte les deux formes natives sous le même schéma
strict. Ses 36 tests d'adaptateur, 19 tests HTTP v2, la compilation et la validation
du graphe réussissent. La publication de cette version exacte est encore soumise
à l'accord humain. Le serveur applicatif installé n'a pas besoin de redémarrer
pour ce correctif. Un test isolé dans le vrai moteur de workflow confirme les
deux formes de réponse, sans appel extérieur.

Le parcours Drive fictif a également trouvé une incompatibilité : le moteur
masque les prototypes des objets, alors que le scanner utilisait leur identité
pour admettre les données. L'échec précède les images et la décision Jev. Une
première adaptation passant dans un moteur JavaScript ordinaire a été refusée
par le test du véritable bac à sable. Le contrôle est donc repris à cette
frontière, sans contourner son durcissement. La candidate combinée passe ensuite
les 80 tests Python, 157 tests Node, la compilation et la validation du graphe
à 26 nœuds. Son contrôle intégré dans le vrai moteur confirme les copies
détachées, les données bénignes conservées, les instructions hostiles bloquées,
le re-scan et les deux formats de réponse, sans appel extérieur. Il vérifie aussi
que JPEG/WebP nécessitant une revue retournent un blocage métier avant Jev.
Le workflow de contrôle temporaire est ensuite archivé. La publication exacte
de la candidate combinée reste soumise à l'accord humain ; le workflow actif
reste sur sa version précédemment approuvée. Aucun parcours Drive ou construction
web réussi n'est encore attesté ; le résultat ne constitue pas un parcours complet.

## Orchestration et délégation

Codex a réalisé directement sauvegarde, activation, configuration, installation,
vérification des sources exécutées et harnais HTTPS. Trois sous-agents internes
ont contribué : diagnostic indépendant du contrat et des erreurs, puis raccord
images ; plan de contrôle, puis scanner et régressions ; copie publique assainie.
Le parent a revu leurs changements et les a vérifiés ensemble sur le serveur
canonique et dans le contrôle isolé du moteur réel. Configuration héritée du
parent, sans modèle nominal supplémentaire relevé ; aucun coût n'est estimé.

Le contrôle indépendant a trouvé la divergence d'adresse avant la bascule, puis
prouvé le double décodage grâce au code installé et aux erreurs des seules
exécutions de test. Le parent a intégré les corrections et ajouté les régressions.
Aucun outil de délégation réservé à l'utilisateur n'a été lancé. Le parent
pilote les contrôles isolés ; les données utilisées sont entièrement fictives.

## Coopération et adaptation au contexte

Consignes du projet, architecture, rapports récents, guides du portail et annonces
partagées ont été consultés. Les sources et droits prévus ont été réservés avant
intervention. La mission distincte de réalisation par mail conserve l'hébergement
partagé : aucune construction web concurrente n'est lancée, et ses fichiers et
services restent hors périmètre de cette mission.
La nouvelle fiche de reprise courte et la modification des instructions locales
d'une autre mission ont été lues et préservées. Aucun changement global mêlé
aux fichiers applicatifs n'a été committé par cette mission.

L'API a publié automatiquement le workflow actif lors de la préparation du
correctif. La version précédemment approuvée a été rétablie et aucune nouvelle
exécution n'a utilisé cette publication transitoire. Le brouillon et la version
publiée sont désormais distingués explicitement. Une mise à jour future doit
tenir compte de cet effet de l'API avant son enregistrement.

La nouvelle consigne d'archivage privé des échanges lisibles a été lue à sa
publication ; la délégation suivante a été copiée avant envoi. Cette copie
d'audit ne prétend déchiffrer aucun message natif. Le rapport public exclut les
accès, données clients, coordonnées et configurations d'exploitation.
