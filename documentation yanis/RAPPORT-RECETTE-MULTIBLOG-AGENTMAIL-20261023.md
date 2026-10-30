<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Recette de migration multiblog par courrier électronique

État du 23 octobre 2026 : **quatrième tentative livrée par le parcours natif**. Une seule installation physique WordPress a servi à la livraison. Après correction du rendu et nouvel accord client par mail, le nouveau travail final a terminé ses contrôles ; le projet est livré. Les trois essais précédents sont fermés et le premier travail final échoué de la quatrième tentative garde son état d’échec.

Les sept cas photographiques et quatre captures publiques ont été vérifiés. Le mail final a été reçu, l’interface normale a été restaurée avec les projets existants, et les sources qualifiées ont été intégrées à la branche principale locale.

## Demande et résultat

La demande consiste à reprendre un PDF et quatre blogs dans un site WordPress administrable, en conservant les articles, photographies, enregistrements audio, vidéos et documents accessibles. La recette utilise un compte distinct et des échanges réels de courrier électronique. Le résultat attendu comprend le site public, l’administration native et la capacité de publier puis modifier les contenus.

Le corpus vérifié comprend **189 contenus canoniques, dont 14 billets**, ainsi que cinq alias. Les billets sont inclus dans les 189 contenus. Les **635 ressources téléchargées valides** se répartissent en **427 images, 168 audios et 40 documents**. Parmi les images, 420 sont des rasters et sept sont des ressources vectorielles. Les 47 références externes distinguent 43 vidéos individuelles, une playlist, une chaîne, un album et une dépendance de lecteur.

La couverture reste partielle et les réserves sont conservées : deux PDF absents, une image originale indisponible dont une copie historique distincte a été récupérée, deux anciennes références non récupérées et quatre occurrences de liens relatifs déjà invalides dans les sources. Un document Word réellement corrompu est exclu conformément à la décision humaine, avec son original et son diagnostic conservés en preuve privée. Les absences, la récupération historique et la corruption gardent des statuts distincts.

Les originaux et l’inventaire complet alimentent le scan intégral et l’import CMS déterministe. Le modèle reçoit des résumés de conception bornés, des extraits nommés, les compteurs, empreintes et réserves. Les 189 textes complets ne sont pas tous placés dans chaque prompt. L’import final conserve l’ensemble des contenus utilisables avec leurs associations, leur provenance et une correspondance entre chaque source et sa destination.

Un défaut concret empêchait les photographies originales d’atteindre le générateur de maquette. Il est corrigé par un champ natif optionnel, `sourceRasterAssets`, qui transporte séparément quatre JPEG sélectionnés explicitement à partir des sources : **129 934 octets inchangés**, avec descriptions et provenance. Le serveur conserve les binaires ; le modèle produit uniquement du HTML et du CSS et référence les chemins autorisés. Le raccord fonctionne dès la première version et conserve les images pendant les raffinements, sans duplication. Il est qualifié dans la recette isolée ; le raccordement opérationnel au parcours générique n8n reste distinct.

Le dialogue permet désormais de confirmer **deux à sept rubriques dans une seule réponse**. Le lot est atomique : une réponse valide applique toutes les rubriques ensemble ; un lot invalide n’en applique aucune. Les signatures standard sont séparées des décisions utiles. Le récapitulatif conserve une confirmation distincte.

La quatrième tentative a également mis en évidence **deux courriers récapitulatifs évitables** après des actions réalisées dans le portail authentifié. Les mêmes récapitulatifs étaient déjà visibles dans la conversation, avec leur tour de confirmation ouvert. Le correctif qualifié supprime seulement ces notifications synchrones du portail, pour le cadrage et les modifications ; il conserve le message, le tour ouvert et la confirmation par empreinte. Les réponses reçues par mail gardent leur récapitulatif envoyé, et les notifications d’action de vérification, de maquette et de livraison restent utiles. Les deux courriers de la quatrième tentative avaient été envoyés avant cette correction : ils restent dans son comptage réel. Les correctifs ont été recopiés dans les sources de lab après l’arrêt de la recette ; l’interface restaurée conserve sa release préexistante.

Dans la quatrième tentative, les premières revues automatiques avaient accepté une maquette dont un paragraphe s’écartait du brief. La lecture visuelle de l’orchestrateur a relevé cet écart ; une demande de modification réelle par mail, son récapitulatif confirmé puis une seconde maquette ont permis la correction. Le premier avis automatique ne suffit donc pas à attester la fidélité de présentation.

Les quatre essais successifs doivent rester distingués :

| Essai | Mails Atelier | Réponses client reçues | Appels modèles observés | Résultat au point de contrôle |
| --- | ---: | ---: | ---: | --- |
| Premier | 7 | 6 | 17 | Fermé sans publication après trois revues refusant le défaut photographique. |
| Deuxième | 1 | 0 | 0 | Rejet natif HTTP 400 avant création du projet ; seule la vérification mail a eu lieu. |
| Troisième | 6 | 4 | 16 | Fermé : un faux positif sur un JPEG valide a arrêté la validation préalable à l’installation. |
| Quatrième | 10 | 4 | 13 | Livrée après correction du rendu, nouvel accord client par mail et poursuite native des contrôles sur l’installation existante. |

Les quatre campagnes totalisent **24 mails Atelier, 14 réponses client reçues et 46 appels modèles**. Les appels observés utilisent openai/gpt-6-luna et ont tous terminé avec un code de sortie nul. Les trois avis photographiques refusés du premier essai restent des échecs de recette. Le deuxième essai a été interrompu par une erreur de préparation de l’orchestrateur : la demande initiale de huit pages était rejetée par le contrat de création. Cette préparation a été corrigée avant le nouvel essai.

Dans le troisième essai, sept rubriques ont été confirmées dans un même courrier et un seul événement, puis le récapitulatif a reçu sa confirmation séparée. Le paquet de sources a été réellement transféré : **813 fichiers, pour 854 056 574 octets**, avec les contrôles d’intégrité attendus. La validation du payload a ensuite pris une courte séquence d’octets d’un JPEG valide pour une ouverture de code. Le refus est intervenu avant les préimages, le reçu d’installation, le compte propriétaire et les effets WordPress ou base de données. Le validateur distingue désormais les rasters autorisés des contenus texte, tout en conservant les contrôles des formats, chemins et tailles.

La réconciliation a vérifié les preuves, l’intégrité du paquet et l’absence d’effets d’installation, puis déplacé seulement la réservation de l’essai échoué dans sa preuve dédiée. Les sources transférées et les entrées d’origine restent conservées. Le troisième essai garde son état échoué ; la poursuite utilise une nouvelle demande de finalisation.

Dans la quatrième tentative, WordPress a été installé et l’archive importée avec sa correspondance source–destination. La première page de la vérification publique a ensuite révélé un défaut de rendu : la typographie automatique transformait un tiret du titre en tiret typographique. La page et ses liens existaient, mais le titre source exact n’était plus retrouvé. Le correctif agit sur le rendu des titres et des corps archivés ; le vérificateur strict reste inchangé. Le diagnostic post-correctif confirme **189 titres, 189 corps et 189 titres de document exacts**, un titre principal visible par page et l’absence de lien de provenance, de média ou de bibliothèque manquant dans ce diagnostic.

La poursuite a ensuite utilisé une **adoption native de l’installation existante**, limitée au même projet, à la même archive, au même propriétaire et à la même maquette approuvée. Le préflight réel en a confirmé l’admissibilité. Le travail final qui avait échoué reste échoué ; une attestation distincte relie son installation physique au nouveau travail de livraison. Un nouveau tour a été ouvert et le client a réellement répondu par mail avec la validation attendue. Ce nouvel accord a autorisé le nouveau travail final, qui a terminé avec succès. L’installation n’a pas été rejouée et l’historique d’échec reste conservé.

Les contrôles publics finaux ont vérifié **189 pages, dont 14 articles**, et **635 empreintes binaires pour 979 027 407 octets**. Ce volume public compte chaque entrée de ressource publiée. Le corpus source comporte **605 binaires distincts représentant 838 528 379 octets** ; les ressources partagées expliquent l’écart entre entrées et fichiers distincts. Les réserves de sources restent visibles et la couverture d’origine reste déclarée partielle.

La recette propriétaire du CMS a réussi **30 contrôles** : accès natif, publication et modification d’un article, ajout et vérification d’une image et d’un audio, ainsi que lecture vidéo native. Le WAV exercé représente **45 088 768 octets**. Les 43 vidéos individuelles sont conservées parmi les 47 références externes ; la lecture de chacune de ces vidéos n’a pas été exercée.

Les **sept cas photographiques de contrôle passent**. Quatre captures publiques de l’accueil et d’une page source photographique, sur ordinateur et mobile, ont été réellement regardées par l’orchestrateur. Les photographies et leurs légendes sont visibles ; aucun débordement horizontal ni problème bloquant n’a été observé dans ces vues.

Le courrier final de livraison a été reçu dans la boîte cliente. L’identifiant du compte et le lien d’activation ont été vérifiés ; l’empreinte exacte du lien correspond au coffre local. L’administration a été exercée séparément pendant la recette CMS. Le projet est livré dans le parcours natif et les contrôles de clôture sont terminés.

## Orchestration et délégation

L’orchestrateur conduit les échanges réels, vérifie les événements natifs, prépare les comptes et projets isolés et décide de la progression selon les résultats observés. Trois sous-agents interviennent dans des périmètres séparés : inventaire et provenance des ressources ; admission du contexte, prompts et transport des photographies ; import WordPress, contrôles finaux et protocoles de recette.

Le sous-agent chargé du contexte a identifié le manque de rasters, préparé le helper de sélection et de liaison au nouveau corpus, étendu le contrat natif optionnel et qualifié la chaîne jusqu’au bundle. Une revue indépendante a relevé une dépendance de test à un chemin personnel ; elle a été remplacée par le dépôt évalué ou une configuration privée vérifiée par empreinte. Les fichiers corrigés ont ensuite été figés pour intégration.

La qualification locale de la sélection conserve les quatre originaux. Les métadonnées de conception représentent 1 963 unités UTF-16. Sur le contexte de contrôle, leur ajout fait passer le brief de 35 312 à 37 291 unités, sous la borne native de 40 000. Un dépassement est refusé avec les tailles constatées, sans retirer silencieusement une source. Les garde-fous de revue, de notes et de liens restent ceux du contrat natif.

Les contrôles de socle enregistrés avant la dernière réconciliation comprennent 415 tests Python, deux suites Node de 42 et 18 tests, deux vérifications supplémentaires de médias et un build réussi. La sélection d’images possède aussi sa qualification locale du helper jusqu’au bundle et sa régénération SDK déterministe. La réconciliation possède 31 tests ciblés hors cible, couvrant notamment l’identité, les réservations, l’intégrité, les liens, les artefacts d’effet et l’interdiction des reprises automatiques.

L’inspection réelle et la réconciliation ont ensuite abouti. Un écart de transport venait de la copie de preuve déléguée au contrôleur : elle héritait d’une connexion SSH. La connexion locale a été explicitée, contrôlée syntaxiquement, puis exercée dans le passage réel. Cette réussite concerne la réconciliation. La tentative suivante a ensuite installé le site et importé son corpus ; sa poursuite native a terminé les contrôles publics et CMS.

Trois qualifications ciblées complètent ce socle : **24 tests du rendu exact des sources**, **63 tests de l’adoption et de ses frontières natives** et **76 tests du dialogue avec récapitulatifs**. La qualification d’adoption comprend 23 nouveaux tests dédiés, 16 tests de réconciliation native et 24 tests d’adaptateur final. Une contre-revue a requalifié indépendamment les 23 tests dédiés. La fusion additive de l’interface possède 30 tests distincts, suivis d’une revue indépendante ; les contrôles natifs d’identité et de conservation des anciens enregistrements restent appliqués pendant la fusion réelle.

Cette contre-revue a aussi corrigé deux écarts de liaison avant le préflight réel. La copie contrôleur et l’original cible du mapping avaient des encodages JSON différents : leur contenu canonique est maintenant comparé, avec leurs deux empreintes brutes conservées séparément et le digest PHP natif contrôlé. Le snapshot de validation utilise le même encodage que le parcours natif, y compris pour les caractères accentués. Ces corrections portent sur les preuves et la poursuite de recette ; elles ne remplacent aucun accord client.

La qualification locale des vraies données recoupe les **13 fichiers de maquette approuvés**, les 189 contenus, les 635 ressources utilisables, l’archive et le diagnostic exact. Le préflight de l’installation existante a ensuite été exécuté avec succès par l’orchestrateur. Le nouveau travail a ensuite exécuté les contrôles publics et CMS après la validation client réelle ; sa remise a été acceptée par le parcours natif.

Les sources qualifiées et la passation ont été intégrées à la branche principale locale. Cette intégration est locale, dans un dépôt sans distant configuré. Le checkout initial et son index ont été préservés.

L’interface normale a retrouvé sa release préexistante et répond en HTTPS. La fusion additive conserve les enregistrements et les autres projets déjà présents. Une connexion réelle au compte de recette, depuis son coffre local, a confirmé l’adresse vérifiée, le projet livré et le travail terminé, puis la session a été fermée. Le runtime isolé de recette a été arrêté normalement à la clôture.

Les qualifications du code, la réconciliation réelle, l’adoption, les contrôles publics et l’acceptation propriétaire ont chacun leurs preuves. L’ancien échec et le nouveau succès sont reliés explicitement, avec leurs états conservés.

## Coopération et adaptation au contexte

Les consignes courantes et les annonces pertinentes ont servi à répartir les réservations et préserver les changements concurrents. Les échanges lisibles entre agents sont conservés en copies d’audit privées. Les constats transmis par un agent ont été confrontés aux compteurs, aux états natifs ou aux preuves de contenu avant intégration. La clôture recoupe les 92 copies d’audit des appels modèles avec leurs acquittements d’empreinte.

Le premier message de recette était classé comme indésirable dans la boîte de réception de l’Atelier. Une recherche exacte a établi sa présence et ses labels. Le reclassement de ce seul message a permis sa prise en charge par le récepteur existant. Le dialogue utilise ensuite un transport client dédié et la boîte Atelier pour ses réponses.

Les essais fermés restent conservés. Les nouveaux essais utilisent leurs propres événements et une archive authentique rejouée avec des liaisons vérifiées ; ce rejeu n’est pas présenté comme une collecte réseau plus récente. La sélection de conception recoupe les nouveaux liens avec les pages, actifs, octets et provenances d’origine.

La coopération a également permis de corriger le plan de réconciliation. Une première inspection a constaté que le plan épinglait le validateur déjà corrigé, alors que la cible conservait encore sa version historique. Un plan successeur a repris l’empreinte historique vérifiée ; l’ancien plan et ses preuves ont été conservés. Le contrôle strict a ainsi produit un diagnostic exploitable sans remplacer les fichiers transférés.

Les photographies sont choisies depuis des légendes, noms de fichiers et contextes de pages explicites. Aucune identité supplémentaire n’est déduite d’un visage. Le défaut de transport des photographies a conduit à transmettre les vrais rasters, plutôt qu’à assouplir les revues. Les liens externes, les rôles des ressources et les diagnostics sont présents dans la bibliothèque WordPress finale ; la maquette conserve son contrat de liens locaux.

La livraison native, les contrôles publics et CMS, les vérifications photographiques et visuelles, la réception du courrier final, la restauration de l’interface et l’intégration locale sont établis. Les réserves d’origine et la limite de lecture des vidéos externes restent documentées.
