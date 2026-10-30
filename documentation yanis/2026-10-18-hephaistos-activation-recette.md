<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Déploiement et recette du parcours commun Héphaïstos

## Demande et résultat

Yanis a autorisé le déploiement du portail puis une recette autonome avec son
compte, son navigateur et sa messagerie. Le scénario devait aller de la création
dans le portail jusqu'à la livraison d'un site, avec des réponses possibles par
mail et une maquette privée intégrée. La validation client et la revue réelle
doivent suffire au nouveau parcours ; aucune approbation interne supplémentaire
n'est fabriquée.

La release applicative approuvée a été déployée. Le service et l'accès HTTPS ont
été vérifiés. Cinq nouveaux workflows ont été publiés avec conservation du
contenu désactivée avant les données privées, séparation des anciens fils mail
et accès de gestion MCP refermé après configuration. Le renderer privé et les
raccordements nouveaux sont installés. Le contrôleur de déploiement protège
également les jobs et envois en cours du parcours commun.

La recette a réellement confirmé l'adresse du compte par mail, créé les projets
depuis le navigateur, reçu les notifications, admis une réponse Gmail avec PDF,
extrait et scanné son texte, puis accepté une réponse depuis le portail. Dans
les deux sens, une réponse tardive sur un tour déjà traité a été écartée sans
nouveau job ni réaffectation à la question suivante. Les sept décisions créatives
et leur récapitulatif distinct ont ensuite été confirmés dans le navigateur.

Trois défauts d'intégration ont été corrigés pendant la recette. L'adresse locale
d'un conteneur ne permettait pas de joindre le portail hôte : un relais privé
authentifié à chemin unique a rétabli la réception. Le nœud modèle renvoyait un
objet JSON déjà parsé : l'adaptateur accepte maintenant ce format avec les mêmes
contrôles. Enfin, une proposition sans citation exacte arrêtait tout le dialogue :
elle est désormais écartée et une clarification est demandée. Les contrôles de
consentement, de sources et de revue restent appliqués. Une réparation opérateur
a ouvert une nouvelle question après l'échec, en conservant son historique et
sans remettre l'ancien job en file.

La recette complète reste **en échec avant présentation de la maquette**. La
construction privée a été déclenchée puis arrêtée ; le portail et le mail
d'erreur ont été contrôlés. Aucun aperçu, verdict visuel, lien final ou accès
d'administration n'est revendiqué. Les boucles de modification, validation et
abandon n'ont donc pas été exercées sur une vraie maquette. Le motif détaillé de
construction n'est pas conservé par le worker actuel, ce qui limite le diagnostic
rétrospectif. Un diagnostic isolé supplémentaire est distinct du parcours livré.

Ce diagnostic a reproduit un faux positif du filtre CSS : `scroll-behavior`
était confondu avec la propriété héritée `behavior`. La candidate distingue les
noms exacts, sans autoriser les propriétés dangereuses ou les ressources externes.
Les huit pages sauvegardées du diagnostic passent alors la validation et leurs
seize captures réelles ordinateur/mobile passent les contrôles techniques.
Aucune n'est importée comme maquette client et aucun score de revue créative
n'est attribué. L'inspection de deux captures signale encore des chevauchements
de repères sur mobile, à traiter par la revue. La reproduction d'un défaut dans
ce diagnostic ne prouve pas rétrospectivement le motif perdu du job initial.

Deux autres limites empêchent la livraison demandée : un refus réseau du runner
final et un pont de livraison limité au statique alors que le scénario exige une
administration de contenu. La publication finale reste indisponible. Le test
n'est pas présenté comme réussi parce que les seuls mails et confirmations
fonctionnent.

Les 43 tests Node ciblés des intégrations communes et les cinq tests Python du
relais passent. La cohérence des SDK régénérés, les validations n8n et le diff
ont été vérifiés. Un appel fournisseur fictif distinct a validé le format JSON
corrigé ; il ne remplace pas la recette client. Les suites complètes et le build
de la release appartiennent à sa validation antérieure. L'upload par navigateur
reste non exercé faute de permission locale de l'extension ; le PDF a réellement
été envoyé par mail. Aucun dossier Drive réel n'a été testé.

La candidate CSS suivante passe également 420 tests Python et un nouveau build
TypeScript/Vite. Ses tests spécifiques vérifient à la fois le cas autorisé et
la conservation des refus dangereux. Les avertissements historiques de fermeture
de ressources dans les fixtures n'entraînent pas d'échec.

Les raccordements et correctifs sont versionnés dans
[le commit source 6417054](https://github.com/yanisAitlamine/atelier-portal/commit/6417054d7121617af0ffc82c3666e49f52645a38).
Le relais exécuté correspond à ce fichier versionné ; la release applicative
déployée et les workflows publiés restent des états distincts du dernier commit.
La suite consiste à diagnostiquer la construction avec des motifs techniques
persistants, rendre le transport final opérationnel et réaliser réellement le
CMS avant de reprendre une recette complète de livraison.

Le [correctif CSS 96a7374](https://github.com/yanisAitlamine/atelier-portal/commit/96a7374f80846c899638623a580b5a6d47efebc8)
est poussé et préparé séparément. Sa bascule attend l'accord humain sur la release
exacte imposé par les consignes du dépôt. Il n'est pas présenté comme déjà exécuté
par le portail.

Le contrôle final a également détecté des caches Python créés par le diagnostic
opérateur dans la release immuable. Une recette ciblée a vérifié qu'il s'agissait
uniquement de caches générés, absents du manifeste, puis les a retirés. Les
contrôles d'intégrité des releases réussissent à nouveau, sans modifier les
sources scellées ni redémarrer le portail. Les diagnostics futurs doivent
désactiver l'écriture de bytecode.

## Orchestration et délégation

Codex a effectué directement l'activation, les corrections, les vérifications,
les réponses client de test et la rédaction. Aucun nouveau sous-agent n'a été
lancé pendant cette mission. Aucune session OpenCode n'a été lancée depuis
PIAgentControl. Le moteur du parcours utilise le modèle configuré gpt-6-luna
avec un effort élevé. Aucun coût ni gain n'est inventé.

Les audits déjà présents dans l'historique appartiennent à la préparation
précédente. Les réponses de test sont allées uniquement au service et les
notifications au compte autorisé, sans contacter le client d'origine. Les
préférences graphiques inventées pour la recette ont été distinguées des faits,
contenus et droits réellement fournis.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche de reprise, la passation et les annonces
pertinentes ont été consultées. Les écritures ont été annoncées avant les
changements. Le transport commun a été réservé pendant la recette ; l'autre
mission a confirmé ne pas lancer de test concurrent. Son patch de présentation
et ses travaux de qualité n'ont pas été intégrés sans revue dans cette release.

Le checkout canonique modifié, les sources concurrentes et les anciens projets
ont été préservés. Le travail a été isolé et poussé sans réécriture de l'historique.
Les anciens rôles réservés et les machines hors périmètre n'ont pas été utilisés.
Le refus du runner n'a été contourné ni par une ouverture réseau ni par le
redémarrage d'un service sur des sources concurrentes non revues.

Ce rapport est anonymisé. Les coordonnées, données client, captures privées,
identifiants internes et preuves détaillées restent dans le dossier privé de la
mission, hors Git public. La fin de coordination libère les réservations après
la fin des appels réels et précise les blocages restants.
