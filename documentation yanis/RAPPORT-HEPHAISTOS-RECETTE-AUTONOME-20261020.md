# Recette autonome du portail après migration — 20 octobre 2026

## Demande et résultat

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
stables de la V2 sont préparées pour remise : accueil ordinateur, accueil mobile
et menu mobile ouvert. L'aperçu V2 est refusé avec 401 sans session ; ses huit
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

Travail direct de Codex : lectures et coordination, modification ciblée des
consignes, compte et coffre de recette, actions navigateur et Gmail, contrôles
HTTP authentifiés et anonymes, captures et compte rendu. Aucun nouveau sous-agent
Codex lancé et aucune session PIAgentControl utilisée. La génération, l’analyse
et la revue proviennent des workflows applicatifs déjà actifs ; elles ne sont
pas présentées comme une délégation Codex supplémentaire. Aucune consigne n’a
été envoyée à une autre tâche en l’absence d’autorisation explicite. Aucun coût
ou gain de temps supposé n’est chiffré.

## Coopération et adaptation au contexte

Les consignes applicables, la reprise commune, les passations du parcours, le
protocole et l’état partagé ont été consultés. Les annonces de migration, de
déploiement et d’approbation concurrentes ont été lues dans leur périmètre utile.
L’intention de reprise, les points et l’extension du rapport ont distingué la
production applicative du lab, réservé le projet de recette et ses preuves,
et préservé les projets concurrents ainsi que les travaux de profil et de revue.

La release exécutée et les services ont été vérifiés ; les fichiers du garde de
maquette et de résolution de cible finale correspondent aux blobs attendus.
Aucun code, service, workflow publié, réseau ou donnée d’un autre projet n’a été
modifié dans cette reprise. Aucun ancien job, envoi incertain ou décision inconnue
n’a été réarmé. Les archives de captures et de reçus restent privées, hors du
dépôt documentaire public. Ce rapport est anonymisé et ne contient ni coordonnées,
identifiants de projets/exécutions, chemins d’accès privés, corps de mail ou
identifiants de connexion.
