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
compte. Aucune maquette disponible est signalée explicitement.

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

Au stade de préparation, la PR est ouverte, le nouveau workflow est en brouillon
et la production demeure sur sa version précédente. L’autorisation de mise en
service de la version exacte et d’un mail fictif au destinataire choisi est
demandée séparément. Aucun mail réel n’a encore été envoyé pour cette mission.
L’historique couvre au maximum les cent messages conservés ; le portail ne
propose pas encore de tableau de support partagé ou de purge automatique des
dossiers. Les sources versionnées ne sauvegardent pas les données d’exploitation.

## Orchestration et délégation

Codex réalise directement le formulaire, le serveur, la file, le workflow, les
tests, la revue et la préparation de livraison. Aucun sous-agent n’a été lancé.
Aucune session OpenCode ou PIAgentControl n’a été lancée ou reprise. Aucun coût
ou gain de consommation n’est déduit de ces vérifications.

## Coopération et adaptation au contexte

Les consignes de reprise, l’architecture de référence, la passation du correctif
précédent et les contrats du portail ont guidé la mission. Le protocole machine et
les annonces récentes ont été consultés ; une intention puis des extensions ont
réservé les fichiers de support et leur documentation. Les missions concurrentes
sur les documents commerciaux et les alertes ont été préservées ; aucun de leurs
workflows principaux ou fichiers réservés n’a été modifié.

La conception tient compte des liens privés : envoyer seulement leur adresse
n’aurait pas donné accès au support, d’où la copie protégée jointe au mail. Les
comptes ne contenant pas d’adresse e-mail, une adresse de réponse est demandée
dans le formulaire. L’envoi demeure explicite, sans notification automatique à
chaque panne et sans nouvelle exposition réseau. Le déploiement des anciens
rôles d’administration et l’accès à la machine de contrôle restent hors périmètre.
