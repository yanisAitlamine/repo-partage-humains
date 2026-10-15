# Portail : formulaire de support avec conversation et maquette — 15 octobre 2026

## Demande et résultat

L’utilisateur souhaite contacter le support lorsque la génération échoue. Le
mail doit transmettre la conversation du site et l’adresse de sa maquette. Il a
fourni directement le destinataire temporaire, conservé hors des sources.

La version préparée ajoute un formulaire dans chaque site et après une erreur
de génération. Le client indique son adresse de réponse, décrit le problème et
confirme le partage du contexte. Le serveur contrôle le propriétaire et la
révision, puis fige les messages conservés, le brief, l’état de génération et la
dernière maquette enregistrée. La conversation est jointe au format texte et la
maquette au format HTML avec une politique bloquant scripts et ressources réseau.
Le message contient aussi les liens du site et de la maquette. Ces liens restent
privés ; la pièce jointe permet au support d’examiner la maquette sans partage de
compte. L’absence de maquette est signalée explicitement.

Le workflow de support est indépendant de la génération et du pipeline principal.
Il ne lance aucun modèle ou constructeur. Une file durable, un identifiant stable,
une prise en charge atomique et des quotas limitent les doublons. Seul un reçu
lié au ticket avec confirmation d’envoi du fournisseur permet d’afficher
« E-mail envoyé ». Un reçu perdu reste « Envoi non confirmé » sans renvoi
automatique. Le reçu prouve l’acceptation par le service, pas la lecture du mail.

Validation du candidat :

- 42 tests Python réussis sur les deux machines, dont un parcours HTTP complet
  de support, l’isolation, le consentement, les quotas, les doublons concurrents,
  les pièces jointes, la perte de reçu et la reprise après interruption.
- Dix groupes de parcours HTTP isolés réussis sur les deux machines ; contrôle
  TypeScript, compilation et tests hors ligne des nœuds de support réussis.
- Cinq nœuds et workflow validés par le serveur d’automatisation.
- Parcours navigateur sur données fictives : génération échouée avec ancienne
  maquette, formulaire, consentement, capture de la conversation et de la copie,
  confirmation simulée, absence de maquette, reçu perdu, persistance après
  rechargement et nouveau consentement après conflit de révision.

Après revue du candidat, l’utilisateur autorise explicitement la version exacte,
l’activation du workflow et un mail fictif au destinataire choisi. Une sauvegarde
cohérente de la base est réalisée avec contrôle d’intégrité ; la file de génération
est vide avant la bascule. La recette du portail termine treize tâches sans échec,
avec six changements. Le portail redémarre, la configuration du proxy reste
identique et les accès HTTPS au portail ainsi qu’à l’application principale
répondent correctement. Les sources installées correspondent au commit approuvé.

Le parcours réel crée un compte fictif distinct, mène un échange avec le modèle,
génère une maquette privée puis soumet le formulaire. Un seul mail est envoyé par
le workflow de support : Gmail fournit un reçu confirmé. La soumission répétée
avec le même identifiant retrouve le ticket existant. Le dossier contrôlé contient
quatre messages fictifs, les deux liens, la conversation jointe et la copie HTML
de la bonne maquette, avec empreintes vérifiées. Deux appels modèle sont utilisés
pour ce parcours. La réception ou la lecture dans la boîte destinataire n’est pas
vérifiée directement ; le reçu atteste l’acceptation de l’envoi par Gmail.

La PR reste ouverte ; aucune fusion n’est effectuée implicitement. Le workflow
de génération préexistant conserve sa version publiée. Aucune relance automatique
ou mise en production d’un site client n’est déclenchée.
L’historique couvre au maximum les cent messages conservés ; le portail ne
propose pas encore de tableau de support partagé ou de purge automatique des
dossiers. Les sources versionnées ne sauvegardent pas les données d’exploitation.

## Orchestration et délégation

Codex réalise directement le formulaire, le serveur, la file, le workflow, les
tests, la revue, la préparation et la mise en service autorisée. Aucun sous-agent
n’a été lancé.
Aucune session OpenCode ou PIAgentControl n’a été lancée ou reprise. Aucun coût
ou gain de consommation n’est déduit de ces vérifications.

## Coopération et adaptation au contexte

Les consignes de reprise, l’architecture de référence, la passation du correctif
précédent et les contrats du portail ont guidé la mission. Le protocole machine et
les annonces récentes ont été consultés ; une intention puis des extensions ont
réservé les fichiers de support et leur documentation. La préparation est clôturée,
puis une nouvelle intention réserve l’activation après l’accord humain. Les missions concurrentes
sur les documents commerciaux et les alertes ont été préservées ; aucun de leurs
workflows principaux ou fichiers réservés n’a été modifié.

La conception tient compte des liens privés : envoyer seulement leur adresse
n’aurait pas donné accès au support, d’où la copie protégée jointe au mail. Les
comptes ne contenant pas d’adresse e-mail, une adresse de réponse est demandée
dans le formulaire. L’envoi demeure explicite, sans notification automatique à
chaque panne et sans nouvelle exposition réseau. Le déploiement des anciens
rôles d’administration et l’accès à la machine de contrôle restent hors périmètre.
