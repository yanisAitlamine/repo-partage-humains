<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Gmail natif du laboratoire et recette autonome — 21 octobre 2026

## Demande et résultat

Yanis a fourni un client OAuth créé dans son nouveau projet Google, puis a
explicitement autorisé le consentement. La boîte dédiée au laboratoire est
connectée à n8n ; la lecture du profil Gmail confirme le compte attendu.
L'accès HTTP demandé a été conservé. Google refusant le retour OAuth vers
une IP privée HTTP, un accès HTTPS distinct et privé a été ajouté au lab.

Le transport utilise les nœuds natifs Gmail de n8n et l'API Gmail : envoi MIME,
lecture du message reçu, déclencheur de réception et admission applicative.
Les réponses du client fictif passent effectivement par Google et le déclencheur.
La recette utilise une seule boîte qui s'envoie à elle-même les messages :
les rôles sont simulés, le transport Gmail est réel. Elle ne démontre pas un
échange avec une deuxième boîte indépendante. Le filtre est limité à une
campagne de recette ; ce n'est pas une nouvelle entrée commerciale générale.

Le sixième essai indépendant réussit : **37 contrôles de parcours et 58 contrôles
réels dans Chromium**, huit pages, deux versions privées et 64 captures.
Seize notifications ont été réellement envoyées par Gmail et quinze appels
OpenCode au modèle API ont abouti. Le dernier essai n'a nécessité aucune
réémission corrective. Le mail final est relu dans Gmail, avec labels Inbox et
Sent et présence des liens du site et d'activation propriétaire. Aucun job ni
envoi ne reste en attente ou incertain.

Le CMS PHP/SQLite passe ses contrôles : écriture authentifiée, refus CSRF et
origine étrangère, activation à usage unique, brouillon invisible, recherche,
archivage du post technique et déconnexion. La revue navigateur vérifie aussi
les huit pages, la navigation mobile, le menu fermé par défaut et les deux
colonnes, les changements client, la conservation des versions privées et
l'absence d'erreur navigateur. Le contraste corail mesuré passe de 4,03 à 5,81.

Une vue privée en lecture permet de consulter le site depuis le poste autorisé.
Les octets de la page servie correspondent au fichier publié, TLS est vérifié,
et administration et POST sont refusés sur cette vue. Le flux Publications
charge réellement dans Brave. Le frontal n8n reste disponible. Après les
preuves, le déclencheur de campagne et le runtime temporaire sont arrêtés ;
les fichiers temporaires du compte sont retirés. Le credential reste installé.
Cela ne livre pas un consommateur commercial permanent.

Les premiers essais ont révélé un identifiant de capture mal recopié dans une
revue, un namespace Node incomplet pour la vérification finale, une référence
HTML invalide, un envoi de question devenu incertain, puis des délimiteurs JSON
supplémentaires à la fin d’une génération achevée. Les contrôles ont bloqué
les livraisons concernées. Les corrections lient les identifiants exacts au
schéma, autorisent une seule nouvelle revue complète pour ce défaut précis,
vérifient le vrai navigateur avant les appels payants, demandent au modèle une
correction complète bornée des références invalides, et arrêtent le simulateur
dès qu'un envoi est incertain. Aucun verdict n'a été fabriqué, aucun ancien job
ni envoi incertain n'a été réarmé. Les budgets réseau Gmail ont été augmentés,
sans ajouter de renvoi automatique. Une seule réémission complète par le modèle
est permise pour ce défaut de syntaxe achevé, partageant le budget de correction
des références. Le serveur ne répare pas le JSON et valide à nouveau la réponse.

Dix-neuf tests ciblés uniques passent : MIME/admission, transport n8n et
adaptateur fournisseur. La recette Ansible nouvelle a aussi vérifié le profil
Gmail et le vrai espace de résolution Playwright/Chromium. Ces contrôles ne
valident pas les anciens rôles Ansible réservés. Le moteur configuré utilise
OpenCode avec un modèle API GPT-6 Luna ; aucun remplacement par un modèle local.

L'hébergement exercé est une cible SSH/PHP isolée dans le laboratoire. Cela
ne vaut ni publication NOC externe ni modification de la production. Le jeton
Google reste soumis à l'expiration des applications en Testing, généralement
sept jours pour ce consentement Gmail. Une connexion actuelle réussie ne
prouve donc pas une autorisation permanente. Référence :
[Expiration des jetons Google](https://developers.google.com/identity/protocols/oauth2/#expiration).

## Orchestration et délégation

Codex a réalisé directement la configuration et les corrections. Aucun sous-agent
Codex n'a été lancé et aucune session PIAgentControl n'a été utilisée. Les appels
OpenCode appartiennent au moteur de recette existant ; les tâches et réponses
lisibles ont été archivées comme copies d'audit privées, sans raisonnement
interne ni prétention de déchiffrement des archives natives chiffrées.

Le client fictif prend les décisions du scénario autorisé, sans fabriquer une
approbation opérateur de production. Le collecteur du poste conserve seulement
les copies d'audit des échanges modèle ; il ne pompe pas les mails. Les secrets
OAuth restent chiffrés dans n8n, les fichiers privés hors Git. Aucun coût ni
gain de délégation n'est déduit de ces observations.

## Coopération et adaptation au contexte

Les consignes du projet, sa fiche de reprise, la passation du lab et les annonces
pertinentes du journal partagé ont été consultées. Les réservations ont distingué
le laboratoire des missions de production et d'hébergement simultanées.
L'ancien projet OAuth et les sources concurrentes ont été préservés ; les
corrections ont été intégrées dans une branche de travail séparée.

Les preuves des cinq essais échoués et de la recette réussie restent privées.
Chaque nouvelle recette utilise
une base isolée, conserve les protections d'appartenance, de révision, de réponse
unique et de confirmation séparée des modifications. Le receiver est dépublié
avant l'arrêt de sa passerelle et la copie temporaire du compte est retirée.
Les boîtes de production, Telegram, la VM personnelle de contrôle et les anciens
rôles réservés n'ont pas été utilisés pour contourner les difficultés du lab.
