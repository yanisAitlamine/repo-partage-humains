<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Recette Héphaïstos et corrections — 21 octobre 2026

## Demande et résultat

L'utilisateur a demandé de corriger les blocages et de réaliser une recette
complète sur l'environnement de production, avec un nouveau client fictif et
une cible de test explicitement désignée. Il a expressément autorisé les
corrections de production nécessaires et demandé un déroulement autonome.

**Résultat : recette terminée jusqu'à la livraison réelle.** Le site de cinq
pages est publié sur la cible de test. Le portail affiche le projet comme
livré et le véritable mail de livraison a été reçu, avec le lien du site et
l'accès d'activation de l'éditeur. Une activation destinée au client reste
disponible ; les activations techniques du test ont été consommées séparément.

Le scénario exerce le cadrage, les réponses par Gmail et par le portail,
la confirmation du brief, une première maquette privée, une demande de
modification avec clarification et confirmation, une deuxième maquette,
puis sa validation et la réalisation du site avec CMS. Les spécifications et
les réponses sont celles d'un client fictif de recette.

Corrections intégrées dans les sources versionnées et dans les services utilisés :

- Diagnostic des échecs de transport limité aux métadonnées techniques utiles.
- Répertoire d'état OpenCode et profil Chromium accessibles dans le service.
- Dépendance du serveur d'outils installée et précontrôle au démarrage : présence
  des neuf outils et réalisation d'une capture Chromium dans le service réel.
- Conservation du journal public connecté au CMS ; interface de recherche réservée à
  l'administration ; contrôle structurel du journal avant publication.
- Matérialisation des pages de livraison dans la langue du site avec les
  véritables feuilles de style ; clarification des exigences de contact et de menu.
- Administration CMS en français et recherche réellement filtrée dans le serveur.

Les trois premières tentatives de réalisation finale ont révélé des défauts
distincts. Elles sont restées arrêtées ; chacune des reprises a utilisé un
nouveau travail après une nouvelle décision du client fictif. Le deuxième
prototype approuvé a été conservé. Deux redémarrages gracieux de la seule VM
applicative ont aussi été nécessaires après le blocage du canal d'administration
par le transport de scripts Unicode. Ce transport utilise désormais une
enveloppe ASCII décodée en UTF-8 dans la VM.

Contrôles déjà effectués : tests unitaires du transport, du publieur, du
matérialiseur et du CMS ; construction du frontend ; vérification syntaxique
PHP sur l'hébergement ; test de l'interface CMS dans Chromium avec API simulée ;
contrôle des cinq pages de la maquette privée sur ordinateur et mobile dans un
navigateur réel. Les tests simulés de l'interface ne sont pas présentés comme
une preuve du serveur CMS réel.

La réalisation finale a passé sa seconde revue indépendante sans constat
restant, avec des notes de 8 à 9 sur 10. La recette navigateur du site en
préparation, puis celle de l'URL finale publiée, ont chacune passé 205 assertions,
couvrant les cinq pages sur ordinateur et
mobile, les liens de contact, le menu au clavier, le journal connecté et
l'absence d'erreurs HTTP ou JavaScript. L'interface du CMS réel a aussi passé
l'activation, la recherche filtrée, l'enregistrement d'un article existant,
sa visibilité publique et la déconnexion, sur la préparation puis sur l'URL
finale publiée.

L'acceptation automatique du CMS réel a aussi attesté l'écriture authentifiée,
le refus d'un mauvais jeton de formulaire et d'une origine étrangère, l'usage
unique de l'activation, les recherches, la non-visibilité des brouillons,
la publication puis l'archivage de l'article technique et la déconnexion.
Une image PNG, un son WAV et une vidéo WebM ont été envoyés et relus avec
vérification exacte de leurs octets. L'article technique est archivé ; seuls
les trois articles fictifs du client sont publics. L'index racine préexistant
de l'hébergement est resté inchangé.

La maquette privée reste inerte et consultable dans le portail. Un autre compte
connecté n'a pas pu accéder au projet de recette.

La recette client a également créé trois articles explicitement fictifs via
l'API normale du CMS. Leur affichage public et les recherches administratives
positive et négative ont été contrôlés sur le véritable hébergement. Ils ont
été ajoutés par les actions du client de recette, et ne constituent pas une
preuve de génération automatique des articles par le pipeline.

Les notifications intermédiaires devenues inutiles ont été annulées ou
supprimées du parcours. Une réponse tardive à un ancien tour fermé a été
rejetée sans créer de second travail. Aucun échange Telegram n'a servi au test.
La rétention temporaire des erreurs du moteur d'automatisation a été rétablie
à sa valeur initiale après la recette ; le graphe du workflow n'a pas changé.

## Orchestration et délégation

Codex a directement réalisé les diagnostics, les correctifs, l'intégration,
les réponses du client fictif, les tests navigateur et les vérifications.
Aucun nouveau sous-agent Codex n'a été lancé pour cette mission.

Le parcours de réalisation a lancé ses rôles OpenCode natifs : planification,
implémentation et revue indépendante. Le modèle configuré et observé pour ces
rôles est `openai/gpt-6-luna`. Les rôles ont reçu le périmètre de la cible,
les fichiers issus de la maquette approuvée et les exigences du CMS pour
construire puis contrôler le résultat. Les premières exécutions bloquées ne
sont pas comptées comme des livraisons réussies. Aucun modèle local de
substitution n'a été installé, démarré ou utilisé.

## Coopération et adaptation au contexte

La passation, les consignes applicables et le protocole commun ont été lus.
Les intentions et extensions de périmètre ont été annoncées dans le journal
de coopération ; les nouvelles annonces ont été vérifiées avant les écritures.
Les corrections ont été préparées dans des espaces Git isolés. Les modifications
préexistantes des consignes et les travaux parallèles ont été conservés.

La demande courante autorisait les interventions de production nécessaires à
cette recette. Les corrections ont été intégrées par versions ciblées, sans
déployer l'ensemble des évolutions de développement. Les anciens travaux
incertains sont restés fermés. Les échanges lisibles disponibles des rôles
natifs sont conservés dans l'archive privée autorisée ; le présent rapport
publie uniquement les conclusions anonymisées.

Vingt-huit copies d'audit lisibles correspondant aux essais de cette mission
ont été vérifiées dans l'archive privée de référence. Elles sont identifiées
comme copies d'audit, sans prétendre être le déchiffrement d'anciens échanges.

La recette couvre la livraison initiale du site et les opérations CMS décrites.
Les demandes d'évolution après livraison n'ont pas été exercées dans ce parcours.
