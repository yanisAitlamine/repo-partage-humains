# Comprendre les workflows du projet

Le système échange par mail avec une personne qui souhaite un site. Il cherche à comprendre son besoin, demande des précisions si nécessaire et peut préparer une première maquette. Une personne vérifie ensuite cette maquette avant que le système envoie son lien au client.

Un **workflow** est un enchaînement d’étapes dans n8n : recevoir un mail, vérifier son origine, demander une analyse à une IA, puis enregistrer le résultat, par exemple. Le **pipeline** désigne ici l’ensemble des workflows qui coopèrent pour réaliser ce parcours.

Version du texte : 15 octobre 2026. Le fonctionnement décrit repose sur les observations et rapports du 14 octobre. Les interventions encore en cours ne sont pas considérées comme terminées dans ce guide.

## Le parcours général

1. Un mail arrive et passe les vérifications d’entrée.
2. Le dialogue commercial lit la conversation et analyse le besoin.
3. S’il manque des informations, le système pose des questions et attend la réponse du client.
4. S’il ne peut pas décider de façon fiable, il demande l’aide d’une personne sur Telegram.
5. Si le besoin est suffisamment clair, il lance la construction d’une maquette de test.
6. Une personne examine la maquette et autorise ou refuse l’envoi de son lien par mail.

**La maquette peut être construite automatiquement avant cette dernière validation.** La décision de l’IA indiquant que le besoin est clair ne remplace pas l’autorisation humaine d’envoyer le résultat. Elle n’autorise pas non plus la mise en production d’un site complet.

## Les six workflows et leur rôle

Ces noms permettent de retrouver les workflows dans n8n. Le nombre d’étapes correspond à la version publiée observée le 14 octobre ; il pourra changer lors d’une évolution.

| Nom dans n8n | Ce qu’il fait | Étapes observées |
| --- | --- | ---: |
| PIPELINE — 1. Réception des mails et suivi | Sélectionne les mails autorisés, organise leur traitement et certaines reprises. | 89 |
| PIPELINE — 2. Dialogue commercial et brief | Comprend le projet, prépare les réponses et décide de la suite avec Jev. | 94 |
| SERVICE — Décisions Jev du dialogue commercial | Sélectionne les passages du client qui justifient une décision, puis rend cette décision. | 9 |
| PIPELINE — 3. Maquette puis validation humaine | Fait construire une maquette, contrôle le résultat et attend la validation humaine avant livraison par mail. | 28 |
| SUPPORT PIPELINE — Journal des événements | Enregistre ce qui se passe et peut déclencher la suite du traitement côté Telegram. | 11 |
| SUPPORT PIPELINE — Reprise ponctuelle | Attend un délai, puis rappelle la réception pour reprendre un travail prévu. | 4 |

Ces six workflows étaient actifs lors de la lecture. Cela indique qu’ils étaient activés dans n8n ; cela ne prouve pas que tous les parcours ont été testés avec un vrai client.

Leur ordre dans ce tableau n’est pas un ordre de passage obligatoire. Le journal peut être utilisé à plusieurs moments, et un mail ignoré ne passe pas par la construction.

## La réception du mail

### Vérifier que le mail peut être traité

La réception vérifie notamment le compte de test concerné, la date limite configurée, l’origine du message et les règles qui écartent les notifications automatiques. Le but est d’éviter de répondre à des messages hors du périmètre autorisé, à de vieux mails ou à certaines notifications produites par le système lui-même.

Un mail accepté rejoint une **file d’attente** : une liste de messages à traiter. Le système conserve ainsi le travail à faire même si le traitement ne commence pas immédiatement.

### Réserver le mail avant de travailler dessus

Avant de prendre un message, le système le réserve. Cette réservation est parfois appelée **claim**. Un **verrou** empêche les traitements qui respectent ce mécanisme de prendre simultanément le même travail.

Exemple : si deux déclenchements repèrent le même mail, la réservation doit empêcher qu’ils rédigent et envoient chacun une réponse. Cette protection ne couvre pas un autre programme qui enverrait des mails en contournant ces règles.

### Attendre le résultat du dialogue

La réception appelle le workflow de dialogue et attend sa réponse avant de poursuivre ce traitement. C’est le sens du mot **synchrone**.

À l’inverse, un appel **asynchrone** lance un autre travail sans attendre sa fin. C’est notamment le cas du lancement de la maquette depuis le dialogue commercial. Il faut donc suivre le résultat de cette construction séparément.

### Enregistrer le bilan du mail

| Bilan | Comment le lire |
| --- | --- |
| `REPLIED` | Le traitement classe le message comme ayant reçu une réponse. Pour vérifier un envoi réel, il faut aussi sa confirmation Gmail. |
| `REVIEW` | Le message doit être examiné par une personne. |
| `IGNORED` | Le message a été écarté ; ce n’est pas nécessairement une panne. |
| `ATTENTION` | Le traitement signale une situation qui demande une attention particulière. Il faut lire le motif enregistré. |

`REVIEW` et `ATTENTION` ne doivent pas être fusionnés. Les sources de cette synthèse ne donnent pas une liste exhaustive des situations classées `ATTENTION` ; ce statut seul ne permet donc pas de choisir une correction.

## La compréhension du projet

Le dialogue vérifie à quel client et à quel projet appartient le message. Il relit le fil Gmail réel, c’est-à-dire la conversation conservée par Gmail. Une discussion déjà marquée comme clôturée (`CLOSED`) est ignorée sans nouvelle réponse ni nouvelle maquette.

GPT intervient pour trier, conseiller et rédiger. Jev sélectionne les passages du client qui appuient l’analyse et décide de la suite. Le dialogue attend la réponse de Jev avant de continuer.

Le système doit distinguer **ce que le client a demandé** et **ce que l’assistant a proposé**. Une phrase de l’assistant, même réellement envoyée, n’est pas une nouvelle exigence du client. Cela vaut aussi pour une réponse écrite par une personne dans Telegram puis envoyée au client. Le HTML d’un message de l’assistant est conservé tel quel ; il ne devient pas une citation du client.

Le **brief** est le résumé du besoin qui servira à construire la maquette. Il porte sur six sujets :

- l’objectif du site ;
- le public visé ;
- le type de site ;
- les pages souhaitées ;
- les fonctions attendues ;
- les contraintes à respecter.

Un sujet peut être explicitement sans exigence particulière. Le système vérifie que le résumé est justifié par les sources et cohérent ; il ne doit pas remplir arbitrairement les informations manquantes.

### Les décisions possibles

| Décision | Ce qui se passe ensuite |
| --- | --- |
| `CONTINUE` | Le système pose au plus deux questions, enregistre l’échange et attend un nouveau mail du client. |
| `READY` | Le besoin est jugé assez clair et les contrôles de sources et de cohérence permettent de préparer une première maquette de test. |
| `BLOCKED` | Le système ne peut pas poursuivre de façon fiable ; le message passe en revue humaine. |

Les catégories `ACK` et `STATUS` permettent aussi de reconnaître un accusé de réception ou une demande de suivi. Elles ne doivent pas lancer une nouvelle construction. Par exemple, « Merci, j’ai bien reçu votre message » n’est pas un nouveau cahier des charges.

Une source incomplète, une pièce jointe dont la lecture n’est pas établie, un projet ambigu ou un mail client uniquement en HTML sans version texte peuvent conduire à une revue. La confiance de la décision et la cohérence du besoin doivent être vérifiées avant `READY`.

La rédaction doit aussi respecter un format structuré appelé **JSON**, que le programme peut contrôler. Une réponse dans un format invalide bloque la suite : elle ne donne jamais le droit de construire.

## La réponse humaine sur Telegram

Cette intervention sert à répondre à un mail que le système ne sait pas traiter seul. Elle est différente de la validation finale d’une maquette.

1. Le mail est placé dans la file de revue avec une demande en attente, appelée `REVIEW PENDING`.
2. Le bot présente le mail complet et propose **Stop** ou **Continuer**.
3. La personne choisit si elle veut terminer la discussion ou poursuivre l’échange.
4. Elle écrit le texte à envoyer au client en répondant à la demande du bot. Le terme technique **ForceReply** désigne cette réponse rattachée à un message précis du bot.
5. Le bot montre un aperçu exact du mail et propose **Envoyer**, **Modifier** ou **Annuler**.
6. La confirmation autorise l’envoi du texte présenté, sous réserve des derniers contrôles.

Le système vérifie que la personne, la conversation Telegram, le bot, le message d’origine, le projet et la version du travail correspondent toujours à la demande. Il vérifie également sa durée de validité. Une demande expirée ou un ancien bouton ne doit pas autoriser une nouvelle action.

**Stop** ne ferme durablement la discussion qu’après confirmation de l’envoi Gmail prévu. La clôture est enregistrée sous verrou avant de classer le mail comme traité. **Continuer** laisse la discussion en attente d’un nouveau mail du client. Le texte rédigé par l’opérateur reste une réponse au client : il ne fournit pas artificiellement les exigences manquantes.

Le service qui reçoit les réponses Telegram est unique. Il interroge Telegram pour récupérer les nouveaux événements : c’est le sens de **poller**. Ce fonctionnement permet d’utiliser Telegram depuis le téléphone sans ouvrir l’éditeur n8n à Internet.

Les sources mentionnent aussi un mécanisme natif de revue humaine distinct. Elles ne détaillent pas ici tous ses usages. Un clic dans ce mécanisme ne doit pas être assimilé sans vérification à la confirmation Telegram décrite ci-dessus.

## La construction et la livraison de la maquette

Quand la décision est `READY`, le dialogue peut lancer le workflow de maquette sans attendre sa fin. Le résumé transmis reste lié aux messages qui le justifient.

Le signal `opencode_ready` veut dire « le travail peut être soumis pour une première maquette ». Il ne signifie ni que la maquette est terminée, ni qu’un humain l’a approuvée.

Le parcours documenté est le suivant :

1. Vérifier le brief, ses sources et la cible de test autorisée, c’est-à-dire l’hébergement où la maquette peut être créée.
2. Envoyer une seule demande de construction au service OpenCode. Cette demande devient un **job**, autrement dit un travail identifié et suivi.
3. Consulter son avancement un nombre limité de fois, sans soumettre de nouveau la même construction à chaque consultation.
4. Vérifier le résultat produit, sa version et la revue effectuée.
5. Présenter la maquette à une personne pour validation finale.
6. Après approbation du bon résultat, réserver sa livraison puis envoyer son lien au client.
7. Vérifier la confirmation Gmail avant d’enregistrer l’envoi comme confirmé.

Le mot **artefact** désigne ici le résultat construit, notamment la maquette et son fichier d’entrée. Chaque maquette possède une adresse et un dossier propres. Elle ne doit pas remplacer automatiquement la page d’accueil de l’hébergement ou une maquette précédente.

La vérification compare notamment le fichier présent sur l’hébergement et celui réellement servi par HTTPS. Une **empreinte** est une valeur calculée à partir du contenu du fichier ; des empreintes identiques permettent de vérifier l’identité des contenus comparés. La **révision** désigne la version du travail concernée. L’approbation doit correspondre au bon job et au bon résultat : une approbation d’une ancienne version ne doit pas autoriser l’envoi d’une nouvelle.

Ces contrôles ne garantissent pas que tous les boutons, images ou fonctions ont été testés dans un navigateur. La déclaration de revue et de sauvegarde des agents reste distincte des vérifications automatiques du fichier d’entrée.

**L’ordre à retenir est : construire la maquette → la contrôler → obtenir la validation humaine → envoyer son lien.** Une maquette accessible pour examen reste un prototype de test ; cela n’équivaut pas à la mise en production d’un site complet.

Le formulaire opérateur et l’exemple manuel bloqué mentionnés dans les sources sont des parcours distincts. Ils ne remplacent pas cette chaîne automatique.

## La protection contre les envois en double

Avant l’envoi, le système réserve l’action dans un registre des messages sortants, appelé **outbox**. Cette réservation et le verrou servent à empêcher deux traitements de lancer le même envoi.

| État d’envoi | Signification | Conséquence |
| --- | --- | --- |
| `PENDING` | En attente. | Les contrôles du parcours restent nécessaires avant toute action. |
| `SENDING` | L’envoi a commencé. | Ne pas le remettre automatiquement en attente pour recommencer. |
| `SENT` | L’envoi a été confirmé. | Le conserver comme envoyé. Cela ne prouve pas la lecture par le destinataire. |
| `UNKNOWN` | Le système ne sait pas conclure sur le résultat de l’envoi. | Vérifier ce qui s’est réellement passé avant toute décision. |

Exemple : Gmail peut avoir accepté un mail juste avant une coupure. Si le système n’a pas reçu la confirmation, recommencer immédiatement pourrait envoyer le mail deux fois. C’est pourquoi `UNKNOWN` ne veut pas dire « certainement non envoyé ».

Il n’existe pas de garantie absolue qu’une panne entre plusieurs services puisse être corrigée automatiquement sans risque. Les états incertains demandent une vérification ciblée. Restaurer un ancien registre d’envois après une livraison peut faire oublier un mail déjà parti et provoquer un doublon.

## La différence entre reprise et relance

### Reprendre un traitement après une erreur

Certaines erreurs d’IA permettent un nouvel essai limité. Cela ne s’applique pas à tous les échecs et n’autorise pas à recommencer un envoi incertain.

Le workflow de reprise ponctuelle attend un délai puis rappelle la réception. Le déclenchement interne distingue le traitement des mails, la branche Telegram et une reprise explicite afin de choisir la bonne branche.

Ce workflow n’est pas une nouvelle tâche permanente qui rechercherait tous les échecs en boucle. Cela ne signifie pas qu’il n’existe aucune interrogation périodique ailleurs : la réception Gmail et le service Telegram ont leur propre fonctionnement.

### Relancer une discussion sans réponse

Pour une discussion encore ouverte, le système peut envoyer **une seule relance dans le même fil après deux heures**, si les conditions prévues sont remplies. Il doit notamment avoir confirmé l’envoi précédent et vérifier la source, le verrou et le registre des envois.

Cette relance est un nouveau message de suivi. Elle est différente d’une nouvelle tentative du même envoi après une panne. Elle n’autorise pas à réarmer un ancien `SENDING` ou `UNKNOWN`.

### Conserver les événements du traitement

Le journal des événements garde les informations utiles au suivi. Il peut ensuite déclencher le traitement côté Telegram sans attendre sa fin.

Une trace dans le journal prouve qu’un événement a été enregistré. Elle ne prouve pas à elle seule qu’une notification a été reçue ou qu’une réponse a été envoyée au client.

## Les pièces jointes et les lecteurs Drive

Il faut distinguer un lecteur existant, un candidat en développement et une capacité vérifiée dans le parcours concerné.

Un lecteur de PDF contenant du texte avait été vérifié sur un document simple dans une version antérieure, comme l’explique le [rapport 26](RAPPORT-26-premiere-reponse-et-verification-pdf.md). Ce test ne prouve pas que le parcours Jev actuel exploite correctement toutes les pièces jointes. Si leur lecture ou leur source n’est pas établie, le message doit passer en revue.

Les candidats Drive, PDF et mémoire documentaire développés séparément ne sont pas automatiquement intégrés à la chaîne active. La lecture du parent réalisée le 14 octobre n’a pas établi d’appel Drive opérationnel dans ce parcours. Le contrat permettant de transmettre séparément les citations de documents à Jev n’y était pas établi. La lecture des documents scannés par reconnaissance de caractères, appelée **OCR**, n’est pas validée non plus.

Le laboratoire Jev est un environnement d’essai distinct du service Jev utilisé par le dialogue commercial. Son workflow était inactif et non publié lors de la lecture. Un résultat obtenu dans ce laboratoire ne prouve pas une intégration à la production.

## Examiner un blocage avant de relancer

L’ordre de diagnostic documenté est le suivant :

1. Vérifier le message d’origine et la version publiée du workflow qui l’a traité.
2. Vérifier si un traitement détient encore le verrou ou la réservation temporaire. Une réservation temporaire est aussi appelée **lease**.
3. Examiner la réservation du travail et sa place dans la file d’attente.
4. Pour Telegram, vérifier la personne, la conversation, le bot et la demande concernée.
5. Vérifier si la demande a expiré. Le terme **TTL** désigne sa durée de validité.
6. Examiner ensuite l’erreur éventuelle du fournisseur d’IA ou d’un autre service externe.

Une erreur n’autorise pas à supprimer un verrou, élargir les destinataires autorisés, forcer `READY` ou remettre un envoi incertain en attente. Il faut comprendre le motif et disposer de l’autorisation adaptée à la correction. Comparer uniquement le corps de deux mails ne suffit pas non plus à décider qu’ils représentent le même travail.

## Modifier un workflow sans confondre les versions

Une **version publiée** est celle retenue pour le fonctionnement actif ; un **brouillon** est une version de travail. Le constructeur avait un brouillon différent de sa version publiée, bien que les deux comptent 28 étapes. Les cinq autres définitions correspondaient à leurs versions publiées lors de la lecture. Il faut refaire cette comparaison avant une modification.

Avant une évolution autorisée, l’opérateur doit relire les versions courantes, vérifier les appels entre workflows, les permissions et les contrôles de sources, puis préparer un retour arrière et une sauvegarde adaptés. Les vérifications de configuration précèdent les essais réels autorisés. Un candidat ne doit pas être publié automatiquement parce qu’il existe dans un dossier de travail.

Les essais doivent rester séparés des autres projets et conserver les contrôles des destinataires. Un essai avec un nouveau mail de test et les étapes Telegram pourrait vérifier le parcours complet ; cette réécriture ne le lance pas. Les rôles Ansible historiques restent soumis aux réserves documentées.

## Les preuves disponibles

Les rapports portent sur des périmètres différents :

- Le [rapport 36](RAPPORT-36-test-reel-maquette-et-validation.md) décrit un essai réel de construction, validation humaine, livraison Gmail et notification. Il ne prouve pas la lecture du mail par le destinataire ni tous les usages du site.
- Le [rapport 38](RAPPORT-38-jev-parcours-commercial-reel.md) décrit l’intégration de Jev, ses essais contrôlés et ses limites. Il ne valide pas le parcours complet d’un vrai échange client jusqu’à la maquette.
- Le [rapport 39](RAPPORT-39-documentation-workflows.md) et la lecture des six définitions expliquent l’origine du guide initial. Lire une définition ne revient pas à exécuter le parcours.

Cette réécriture ne produit aucun nouvel envoi ou site. Le rangement des fichiers évoqué dans les missions précédentes reste un travail distinct, déclaré partiel dans leur bilan.

Pour comprendre où tournent les services, lire l’[architecture expliquée](ARCHITECTURE.md).
