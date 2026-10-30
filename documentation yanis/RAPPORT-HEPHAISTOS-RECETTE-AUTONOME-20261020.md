<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Recette autonome du portail après migration — 20 octobre 2026

## Demande et résultat

**État de la reprise du 20 octobre.** La cible TEST est disponible, le transport
Gmail est corrigé et la politique limitant les mails automatiques est active.
Une nouvelle validation du client fictif a réellement traversé Gmail puis le
portail et déclenché la fabrication finale. Ce premier job s’est arrêté avant
écriture distante : une dépendance du navigateur manque sur le serveur restauré
et empêche le chargement des outils MCP. **Aucun site final n’est encore livré.**
La préparation du correctif est coordonnée avec la tâche d’administration ;
la désignation du laboratoire dédié reste nécessaire avant ses essais.

L’accès SSH de la nouvelle machine présentait la même ancienne clé que le Pi,
mais l’hébergement refusait sa provenance. Après une instruction humaine
explicite dans la tâche d’administration, une identité dédiée a été générée
sur la nouvelle machine ; seule sa partie publique a été inscrite, avec une
restriction de provenance. Les anciennes entrées ont été préservées. Les
preuves SSH/HTTPS ont réussi depuis le transport définitif, puis la seule
association du nouveau projet a été ajoutée avec sauvegarde et garde de
concurrence. L’API propriétaire et l’interface confirment la disponibilité de
la construction statique et du CMS. Aucun ancien site ni job n’a été remplacé.

Un troisième retour client fictif a servi de diagnostic, sans réponse portail
concurrente. Une lecture native des seuls en-têtes de ce courrier dans la boîte
du service a réellement vérifié : expéditeur égal à l’adresse vérifiée,
thread égal au reçu de notification, absence des labels spam, corbeille et
envoyés. Le corps et les pièces jointes n’ont pas été lus par cette sonde.
Les contrôles d’identité et de corrélation n’ont donc pas été assouplis.

Une sonde native distincte, avec le credential existant et un JSON vide
volontairement invalide, expirait entre le conteneur et le relais ; le relais
répondait immédiatement depuis son hôte. Le filtrage hôte ne comportait pas
l’admission du flux privé nécessaire. Une seule règle limitée au bridge,
à la source, à la destination et au port concernés a été ajoutée et persistée.
Après correction, le conteneur reçoit le refus sans authentification attendu ;
la nouvelle sonde authentifiée passe et confirme HTTP400 pour le schéma
invalide. Aucun message client ni travail n’est créé par ces sondes.
Un échange métier frais a ensuite confirmé ce transport : la décision de
validation et ses retours ont été reçus dans la conversation du portail, puis
un nouveau job final a été créé. Aucun ancien courrier n’a été rejoué.

La candidate supprimant les confirmations de traitement a été activée après
accord humain explicite sur sa version exacte, via le contrôleur officiel et
sa sauvegarde cohérente. Les 494 tests Python, huit tests mail et compilation
frontend passent. Le processus et le lien de release concordent, santé HTTPS200 ;
configuration et maquette V2 ont été préservées. Les notifications de simple
état sont supprimées de la file sans effacer les traces des anciens envois.
Un premier refus de sceau provenait uniquement de caches Python dérivés ajoutés
à l’ancienne release : ils ont été vérifiés et conservés en quarantaine, sans
modifier les sources ni les manifestes, avant une nouvelle vérification native.

Le runner a bien délégué l’implémentation mais ses deux tentatives ne disposaient
d’aucun outil MCP de construction/revue. Le diagnostic Node en lecture seule
confirme l’absence du module Playwright attendu par le lockfile. Le job est
terminal bloqué, aucune revue favorable ni livraison n’est inventée. Aucun ancien
job n’est réarmé. La préparation et la vérification du correctif doivent précéder
une intégration coordonnée, puis une nouvelle tentative traçable.

**Essai initial, nuit du 19 au 20 octobre — historique des preuves ci-dessous.**

Demande : exercer sans présence de l’utilisateur le parcours client sur la
production migrée, puis remettre la maquette. Des instructions permanentes ont
été ajoutées au fichier agents demandé : compte de recette réutilisable,
identifiants chiffrés, nettoyage préalable de ses projets et autonomie pour les
réponses et décisions du client fictif. Les autres modifications présentes dans
ce fichier ont été conservées ; lecture seule et règles d’accès ont été rétablies.

Un compte de recette distinct a été créé par l’interface normale. Son état vide
a été vérifié avant de commencer ; aucune suppression d’un ancien compte ou site
livré n’a été nécessaire. L’adresse déjà liée à un compte précédent ne pouvait
être rattachée au nouveau : un alias de la même boîte du demandeur a été utilisé,
avec réception et confirmation effective du lien. Le mot de passe généré est
stocké dans un coffre Windows DPAPI CurrentUser, accessible seulement au
propriétaire et au système, hors Git et des rapports. Une vraie déconnexion puis
reconnexion depuis ce coffre a réussi sans intervention humaine ni affichage du
secret. La suppression de projets préexistants reste hors de cette recette,
puisque le compte neuf n’en contenait aucun.

Le nouveau scénario éditorial a suivi les sept points du cadrage, une analyse
réelle du message portail, les confirmations explicites du client fictif et le
récapitulatif distinct. Une maquette V1 de huit pages anglaises a été réellement
générée et importée dans l’aperçu privé ; son mail de disponibilité a été reçu.
Le contrôle d’import exécuté a été comparé au blob de la release : il exige une
revue authentifiée favorable, des notes entre 8 et 10 et un manifeste différent
de la passe précédente. Les valeurs détaillées de ces notes n’ont pas été lues
par cet opérateur ; aucune note particulière n’est inventée.

Les huit pages ont été parcourues dans le vrai navigateur en ordinateur puis
mobile, avec contrôles DOM dans les seize vues. Les captures retenues comme
preuves visuelles sont celles relues après stabilisation de la page ; des captures
rapides prises pendant le chargement ne sont pas comptées comme preuves visuelles. Titres distincts, absence
de débordement horizontal et absence de script, formulaire actif ou frame
imbriquée vérifiées dans chaque page. Le menu mobile est fermé au chargement,
contient huit liens en deux colonnes et ouvre réellement une page interne. La
sandbox garde allow-same-origin sans allow-scripts. Le projet et le fichier de
maquette sont refusés avec 401 sans session ; un projet d’un autre compte répond
404 depuis le compte de recette.

Un retour a demandé de retirer des notes internes dans deux pages. Il a ouvert
une clarification ; une nouvelle analyse réelle a reformulé les changements.
Une lecture API a confirmé que la V1 était conservée et que le seul nouveau job
était une analyse, avant toute régénération. Confirmation des précisions, puis
confirmation distincte du récapitulatif ont ensuite créé un nouveau job de V2.

La V2 est réellement livrée et son mail de disponibilité a été reçu. Les deux
pages visées ont été corrigées ; les styles restent identiques après normalisation
des espaces. Les cinq autres pages comparées ont le même texte, et la sixième
n'a changé que la typographie de guillemets d'une réponse de FAQ. Cette dernière
conserve une formulation explicative sur le nom d'une rubrique, améliorable dans
une future finition éditoriale. Les huit pages de V2 passent les mêmes contrôles
ordinateur/mobile, avec huit liens de menu et aucun débordement. Trois captures
stables de la V2 ont été remises dans un mail récapitulatif demandé : accueil
ordinateur, accueil mobile et menu mobile ouvert. La réception dans la boîte du
demandeur et les trois pièces jointes PNG de tailles attendues ont été vérifiées ;
aucun mot de passe ne figure dans ce mail. L'aperçu V2 est refusé avec 401 sans session ; ses huit
pages ainsi que celles de V1 restent accessibles en HTTP200 au seul propriétaire.
Les réponses servent une CSP sans scripts, réseau, formulaires ni frames imbriquées,
avec Cache-Control: no-store. Le projet reste en revue de maquette ; aucun succès
de site final ou de CMS n'est revendiqué pour cette nouvelle recette.

La recette ne peut pas être qualifiée entièrement réussie : deux réponses Gmail,
dont une avec le PDF de référence, ont été envoyées mais ne sont pas apparues dans
le projet. Leur cause n’est pas établie ; identité et corrélation de thread restent
à diagnostiquer, sans rejouer les messages. Le modèle a signalé l’absence du PDF
parmi les sources accessibles. Le client fictif a ensuite limité explicitement
la maquette aux décisions textuelles confirmées ; aucune lecture de ce document
n’est revendiquée. Le dépôt navigateur du PDF est bloqué par la permission
file-URL de l’extension ; celle-ci n’a pas été élargie.

Quatre mails de progression technique ont été reçus pendant ces deux cycles : le correctif préparé
précédemment est dans les sources mais absent de la release active. Les mails de
questions, récapitulatif et maquette sont bien reçus. Dix-neuf notifications natives ont été observées sur le destinataire de
recette, dont ces quatre messages techniques superflus ; la première tentative
de rattachement à l’adresse déjà occupée a également produit son mail de
vérification. Le détail des catégories reste dans les preuves privées, sans
publier les messages.

Enfin, le passage au site final est indisponible pour ce nouveau projet : l’API
retourne FINAL_TARGET_NOT_CONFIGURED. Une tentative négative de validation au contrat exact a été refusée avec
HTTP409 / PRIVATE_FINAL_TARGET_MISSING ; révision, job et tour ouvert sont restés
identiques après lecture de contrôle. Un premier appel du probe sans requestId
avait été refusé400, sans mutation ; le probe a été corrigé avant de qualifier
le garde de cible. Aucun job final ni site public n’a été créé. Le CMS final,
la branche d’abandon et le Drive privé ne sont pas validés par cette nouvelle
recette.
Une demande opérateur ciblée a été préparée pour le rattachement à une cible TEST
existante et la lecture des seuls reçus d’ingress concernés. L’accès personnel
SSH disponible n’a pas sudo ; la connexion root par sa clé est refusée. Le lecteur
MCP n8n confirme l’activation des workflows mais refuse leurs détails et
exécutions fermés en MCP. Aucune permission n’a été élargie et aucun autre compte
n’a été utilisé. La voie d’administration ou la transmission à une autre tâche
reste à préciser humainement ; ce n’est pas une validation client simulée.

## Orchestration et délégation

Travail direct de Codex pour les consignes de recette, le compte et son coffre,
les actions navigateur/Gmail, les contrôles HTTP, les captures et les tests de
code. Aucun nouveau sous-agent Codex ni session PIAgentControl n’a été lancé.
L’analyse, la génération et les revues des maquettes utilisent les workflows
applicatifs existants.

La reprise a reçu une autorisation explicite de transmettre la demande à une
tâche opérateur existante. Celle-ci a traité l’identité SSH, l’association de
cible, la correction réseau et la préparation de release par son circuit
administratif existant. La tâche principale a revu les résultats et les
helpers de diagnostic, signalé les limites d’un inventaire filtré et d’un
parcours de timestamps trop peu profond, puis vérifié elle-même la disponibilité,
les en-têtes côté destinataire et le transport authentifié réparé.

Quatre workflows de diagnostic manuels ont été créés puis archivés : profil
du service, première sonde de transport, enveloppe du courrier et recontrôle
après réparation. Ils n’ont jamais été publiés ; les exécutions sont configurées
sans conservation avant utilisation. Ces sondes n’ont reçu ni corps de courriel ni credential brut, et n’ont
réinjecté aucun ancien événement ou déclenché de construction.
Aucun coût ni gain de temps n’est inventé.

## Coopération et adaptation au contexte

Les consignes, la reprise commune, les passations, le protocole et les annonces
pertinentes ont été consultés. Les intentions et fins de la tâche opérateur
ont permis de séparer la configuration de cible, le réseau, les sondes mail et
les preuves de recette. Les travaux concurrents sur le profil, la revue et
une machine de développement distincte ont été préservés. Les checkouts déjà
modifiés n’ont pas été réinitialisés et les intégrations utilisent des copies
isolées.

Le diagnostic distingue les identifiants de courriers propres à chaque boîte,
les en-têtes réellement reçus et les métadonnées d’exécution. Une absence de
ligne d’historique ne prouve pas l’absence d’exécution lorsque la conservation
est désactivée. Le timestamp de poll a été retrouvé dans la structure imbriquée,
et le profil natif a confirmé la boîte du service ; ces faits ont évité de
modifier les contrôles de sender ou de thread sur une supposition.

Une exploration du menu de comptes du navigateur a affiché trop de métadonnées
dans la trace privée. L’onglet a été fermé et ses variables temporaires effacées ;
ces informations ne sont pas reproduites dans ce rapport. Les sorties des
sondes ont été limitées ensuite à des assertions et résultats techniques.

Les demandes directes à la tâche opérateur ont été archivées avant envoi.
Les réponses lisibles disponibles sont conservées en copies d’audit privées ;
certaines annonces de coordination ont été copiées après leur publication. Ces copies ne sont pas présentées comme un déchiffrement
de messages natifs. Les sources de sonde, reçus et captures restent privés ;
le rapport public ne contient ni coordonnées, cible d’hébergement, chemins
d’accès privés, identifiants runtime, marqueurs de mail ou valeurs secrètes.

Le passage au site final, la preuve du CMS livré, la réception du mail final
restent à vérifier ; le nouvel échange Gmail après réparation est confirmé. Aucun ancien
mail, job échoué ou accord opérateur inconnu n’a été réarmé.

La nouvelle règle humaine sépare désormais le laboratoire des deux serveurs de
production. Aucun correctif du runtime n’a été installé : une VM est à désigner
pour ses essais. Le journal et la fiche commune présentent encore des états
historiques divergents ; la consigne humaine récente prévaut. Les preuves et
la passation privées ont été actualisées pour éviter tout rejeu à la reprise.
