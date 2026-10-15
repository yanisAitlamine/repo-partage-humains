# Portail : tests end-to-end et correctifs — 15 octobre 2026

## Demande et résultat

Yanis demande une nouvelle campagne de tests end-to-end du portail et la correction
des bugs éventuels. Le périmètre conserve l’intégration de dialogue et de maquette
privée déjà installée ; il n’ajoute ni publication de site complet ni paiement.

Le parcours HTTPS réel passe huit groupes de contrôles : inscription et cookies,
déconnexion invalidant la session puis reconnexion, isolation des comptes et
validation de l’origine, concurrence et séparation des sites, conversation réelle
et blocage des demandes concurrentes, maquette privée et empreinte, retours avec
versions immuables et refus d’une ancienne approbation, puis conservation après
reconnexion sans activation de paiement. Deux comptes fictifs et trois opérations
modèle sont utilisés. Aucun accord de maquette n’est simulé dans la base active.

Les tests de panne sont exécutés sur une application et une base temporaires,
avec un transport déterministe à la place de n8n. Deux bugs d’interface sont
effectivement reproduits dans le navigateur avant correction :

- Une première génération échouée affichait un concept de démonstration sans
  signaler clairement l’échec. La fenêtre affiche désormais un message d’erreur
  ou de résultat incertain, sans faux aperçu, et un bouton de reprise explicite.
  Une ancienne maquette disponible reste conservée lors d’une nouvelle panne.
- Après un conflit de révision et le chargement d’une maquette plus récente,
  la case d’accord restait cochée. La confirmation dépend désormais du site,
  de la version et de l’empreinte de l’artefact. Le même scénario exige maintenant
  une nouvelle sélection et laisse le bouton d’approbation désactivé.

Les assertions navigateur passent après correction pour le changement de version,
la réponse invalide et le délai dépassé. Le rétablissement du transport puis le
clic volontaire de reprise produisent une maquette ; aucune relance automatique
n’est introduite. Les captures avant et après sont conservées dans les preuves
privées, sans reprendre une conversation cliente réelle.

Le dépôt contient désormais un banc HTTP E2E réexécutable. Par défaut, il démarre
le véritable backend, son stockage SQLite et son worker sur une boucle locale
temporaire. Dix groupes de scénarios passent sur Windows et sur le serveur cible.
Le mode HTTPS réel exige une option explicite et crée ses propres comptes fictifs.
Une fixture navigateur séparée et deux assertions sont également fournies ; elles
nécessitent encore le pilotage du navigateur et la préparation décrite dans le
guide. Il ne s’agit donc pas d’une suite navigateur autonome lancée en CI.

Trente-quatre tests Python passent sur les deux machines, dont la conservation
exacte d’un ancien artefact après une régénération invalide. TypeScript et les
compilations de production réussissent également sur les deux machines.

Les correctifs sont enregistrés sur une branche et présentés dans une demande
de revue distincte. Yanis autorise ensuite explicitement la release précise.
La file est vide au contrôle précédant la bascule ; une sauvegarde SQLite cohérente
avec contrôle d’intégrité est prise. La nouvelle recette du portail réalise treize
tâches sans échec. Le proxy reste identique, seul le portail redémarre et la nouvelle
version est vérifiée dans les fichiers installés ainsi qu’en HTTPS. Un échange
réel supplémentaire avec n8n réussit après installation. La session humaine déjà
ouverte est conservée ; les comptes fictifs de test restent indépendants.

Les workflows n8n, le backend produit, le réseau et les parcours mail ne sont pas
modifiés par ces correctifs. Les erreurs n8n simulées restent limitées à la fixture.
Les modèles de génération ne sont pas évalués sur un grand corpus ; la réussite
des cas décrits ne garantit pas tous les prompts, navigateurs ou interruptions.
La fusion de la demande de revue n’est pas effectuée implicitement.

## Orchestration et délégation

Codex réalise directement la lecture du contexte, le banc E2E, les reproductions
navigateur, les corrections, les vérifications et l’installation autorisée.
Aucun sous-agent, session PIAgentControl ou agent NOC n’est lancé. Les appels du
workflow utilisent sa connexion et son modèle existants. La campagne réelle
demande trois opérations initiales et une vérification de dialogue après bascule ;
aucun coût ou gain de consommation n’est déduit de ce nombre.

## Coopération et adaptation au contexte

Les consignes du portail, ses contrats, la passation de l’intégration et les annonces
machine récentes sont consultés. Une intention réserve les fichiers du portail
avant les écritures ; les extensions annoncent les reproductions, la documentation
et la release approuvée. Les travaux concurrents Drive, moteur de décision et VPN
restent sur leurs fichiers et leurs services propres.

Le rapport public ne contient ni identifiant interne, chemin opérationnel privé,
valeur secrète, cookie, mot de passe ni contenu client. Les preuves minimisées et
la passation technique utilisent des fichiers séparés pour préserver les autres
missions. Aucun append concurrent de passation globale n’est écrasé. Le serveur
local de panne est arrêté après contrôle et seuls les espaces de cette mission
sont libérés par l’annonce de fin. Aucun accès Kali, ancien rôle Ansible, ouverture
réseau, envoi à un tiers ou modification du fichier global protégé n’est effectué.
