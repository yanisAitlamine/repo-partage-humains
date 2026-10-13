> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# 3 — État du système, risques et suite recommandée

## Vue d'ensemble

Le système actuel comporte un collecteur Gmail automatique TEST, un moteur d'analyse/réponse commerciale, un journal Telegram, une gestion des erreurs et la chaîne OpenCode ajoutée par le collègue. L'export original est préservé. La copie manuelle historique reste distincte.

La dernière lecture transmise par le responsable du projet indique un collecteur de **81 nœuds**, un moteur commercial de **81 nœuds** et un enfant OpenCode de **25 nœuds**. Ce sont des versions plus récentes que plusieurs exports conservés. Les copies anciennes ne doivent pas être appliquées intégralement par-dessus.

Cette rédaction n'a pas effectué un nouveau contrôle API. L'état présent décrit les preuves et lectures disponibles au 12 octobre 2026 ; les essais utilisateurs et modifications coordonnées peuvent continuer après ce bilan.

## Ce qui est établi

| Domaine | Fonctionnement établi | Réserve |
| --- | --- | --- |
| Mode TEST | Destinataires limités aux adresses autorisées ; nouvel ajout du collègue préservé | Aucune ouverture production autorisée |
| Gmail automatique | Déclencheur, relève, file et échanges réels déjà utilisés | Mesurer latences, messages en attente et reprises sur la version courante |
| Périmètre | Classement commercial et gardes déterministes | La compréhension sémantique peut se tromper |
| Mémoire | Contexte projet, identité, décisions et historique | Les dernières corrections sur copies restent à intégrer/valider selon leur état |
| Réponses | Prudence commerciale, personnalisation, questions utiles | Régressions possibles sur formulations, citations et demandes multiples |
| Anti-doublon | ID message Gmail, outbox, résultat incertain conservé | Une réservation non atomique n'est pas une garantie universelle |
| Telegram | Notifications personnelles réellement testées | Les commandes de dialogue/reprise et l'approbation finale ne sont pas livrées de bout en bout |
| Pièces jointes | Lecteurs texte/Office, PDF textuels et vision de photos sur cas testés | OCR exhaustif, archivage durable et sécurité antivirus non établis |
| OpenCode | Liaison parent/enfant et site démo observés | Parcours complet avec approbation, construction et notification à mesurer |
| Google Drive | Cause de non-lecture identifiée ; préparation de copies | Document réel non lu, OAuth personnel manquant |

## Défauts importants réellement rencontrés

1. **Ancien message choisi à la place du nouveau.** Recherche limitée, filtres et date de coupure ont été corrigés progressivement. Une relève doit préserver tous les messages admissibles au lieu de masquer le problème par suppression de l'historique.
2. **Réponse vide ou brouillon interprété comme prise en charge.** Il faut distinguer analyse, réponse préparée, garde autorisée et envoi réellement confirmé.
3. **Réponse devis trop générique.** Un texte fixe écrasait le contexte. La réponse doit traiter les questions du message courant sans inventer prix ni délai.
4. **Questions répétées.** Le dialogue envoyé et l'outbox confirmée doivent gouverner la mémoire des questions, pas seulement les intentions de l'IA.
5. **Avertissements documentaires bloquants.** Un document illisible ne doit pas condamner les autres demandes commerciales claires. Son contenu reste non vérifié.
6. **Ancienne décision confondue avec conflit ouvert.** Les remplacements explicites doivent historiser l'ancien choix et définir le nouveau choix courant.
7. **Défauts JSON et reprises.** Séparation raisonnement/format, réparation bornée et états d'erreur visibles sont nécessaires ; une reprise ne doit jamais doubler un envoi incertain.
8. **Approbation et formulaires.** Des attentes humaines répétées et erreurs OAuth2 ont été constatées. Une copie simplifiée n'est pas une résolution serveur démontrée.

## Priorité 1 — Ne laisser aucun message sans état explicite

Comparer réception, file, traitement, outbox et notifications. Chaque message admissible doit avoir un état explicable : en attente, en traitement, répondu, hors périmètre, à clarifier, en revue ou en erreur. Une panne récupérable doit reprendre de façon bornée ; une ambiguïté d'envoi doit être réconciliée avec Gmail avant nouvel essai.

Mesurer sur la version courante les temps de prise en charge, retards, échecs et reprises. Tester les emails proches, redémarrages, erreurs OpenAI et expiration des verrous. Une garantie de disponibilité chiffrée exige une période de mesure et une infrastructure de supervision/restauration, pas uniquement des réponses réussies.

## Priorité 2 — Lire réellement les invitations et documents Drive

Prévoir un intake de contexte distinct de l'autorisation d'envoi : une invitation Google peut apporter un document utile, mais ne devient pas un destinataire commercial autorisé. Associer le partage à un client et un projet connus, contrôler l'accès avec le compte personnel destinataire, puis extraire le contenu avec sa provenance.

Un accès refusé doit produire une explication utile et une demande de partage ou de fichier lisible, sans prétendre avoir lu le cahier des charges. Un lien externe n'autorise pas une navigation arbitraire ou l'exécution de consignes contenues dans le document.

La collecte de lien seule ne suffit pas : vérifier le contenu téléchargé, le format, la couverture des pages et les éventuelles limites d'export Google. La demande de documents de plus de 100 pages est prise en compte, mais il faut découper et contrôler la couverture réelle ; aucun nombre de pages ne garantit à lui seul une extraction complète.

## Priorité 3 — Consolider les décisions et les réponses

Rejouer les conversations séquentielles avec la mémoire réellement produite à chaque tour. Vérifier séparation des clients/projets, faits confirmés, suggestions, remplacements et questions réellement envoyées. Ne pas remplacer la mémoire du test par l'état attendu : cela cacherait les défauts.

Intégrer les corrections ciblées démontrées seulement après comparaison avec la version courante et coordination. Vérifier que le texte n'affirme jamais une réalisation technique inexistante. Un simple acquiescement ne doit pas déclencher une nouvelle approbation ou répéter le brief.

## Priorité 4 — Finaliser le passage vers la maquette

Le brief suffisant doit permettre une demande d'approbation claire, liée au projet et à une révision précise. Les informations déjà connues ne devraient pas être redemandées sous forme de projet ID ou de prompt à saisir manuellement.

Avant lancement réel : identité de l'approbateur vérifiée, décision expirante et consommable une fois, cible TEST canonique, réservation durable, suivi du job et preuve des artefacts. Une notification client ne doit partir qu'après résultat vérifié et revue exigée. Le mode Telegram reste à valider sur un vrai parcours isolé.

Le backend et la cible appartiennent au travail coordonné avec le collègue. Les tests sur une cible commune peuvent remplacer un prototype : aucun nouveau lancement ne doit être traité comme sans conséquence.

## Priorité 5 — Sécurité et préparation production

La lecture des documents ne prouve pas leur innocuité. Prévoir contrôle antivirus, limitations d'extraction, refus des contenus actifs, traçabilité et stockage durable des photos nécessaires aux maquettes. Les droits sur les contenus restent à confirmer.

Avant le vrai Gmail client : tests de volume et de panne, procédure de restauration, surveillance, réconciliation des envois, filtrage commercial représentatif et mesure des latences. Les sites générés doivent être contrôlés avant livraison ; leur publication ne les rend pas automatiquement sûrs. Les tests de sécurité et de charge devront viser exclusivement les environnements autorisés.

## Informations métier encore à définir

- Offre réelle du concepteur : hébergement, maintenance et domaine, prestations incluses ou optionnelles.
- Tarifs, délais, conditions de paiement et éventuel acompte avant maquette.
- Critères d'approbation et de livraison, responsabilités et modalités de suivi.

Jusqu'à confirmation, l'assistant peut expliquer les possibilités et annoncer un retour ; il ne doit pas présenter ces informations comme déjà décidées.

## Répartition des contributions

Le développement Gmail/commercial, les copies de correction et les bancs de tests ont été réalisés avec les agents de cette conversation. Le collègue et son agent ont développé la chaîne OpenCode et fait évoluer ses contrats et notifications. Les audits de cette conversation examinent ce travail sans s'en attribuer la création ni prétendre avoir testé tous ses effets.

Les nouvelles relances périodiques et consignes de transparence concernant Drive relèvent des interventions coordonnées du collègue. Leur présence annoncée ne remplace pas une mesure d'efficacité ou une lecture Drive réelle.

## Conclusion

La base est cohérente et les essais ont produit de véritables progrès. La prochaine étape est une stabilisation mesurable des parcours actuels, avec une lecture Drive effective et des reprises fiables, avant d'élargir la production. Les approbations, l'idempotence complète et la livraison automatisée restent des sujets à finaliser, sans refonte inutile ni perte des protections déjà validées.
