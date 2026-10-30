<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# L’Atelier : identité visuelle du laboratoire — 21 octobre 2026

## Demande et résultat

Renommer l’application L’Atelier et faire évoluer sa présentation vers un
futurisme vert-bleu ouvert sur la nature, avec trois illustrations montrant
une personne qui construit un site web à l’aide d’outils tactiles.

Le nom, le symbole, les textes d’accueil et de connexion, la navigation,
l’assistant, la vérification e-mail et les métadonnées ont été mis à jour.
Trois images originales sont intégrées : création sur table tactile, composition
des pages et contenus, puis aperçu du site et de ses formats mobile et tablette.
La palette conserve un futurisme sombre avec des accents menthe et turquoise.

La version visuelle est installée uniquement dans le laboratoire dédié. Un
service distinct permet de la consulter en continu, avec une base neuve dédiée
et sans intégration ou consommateur externe. La route est ajoutée au HTTPS privé
existant ; son rechargement a nécessité un redémarrage bref du proxy du lab.
Les environnements de production n’ont pas été déployés ou redémarrés.

Contrôles réussis : compilation TypeScript/Vite, 26 tests applicatifs ciblés,
9 tests des supports marketing, accès HTTPS depuis le poste propriétaire,
Chromium avec sandbox et validation TLS, affichages ordinateur et téléphone,
chargement de toutes les images, filtre des inspirations, ouverture/fermeture
de connexion, absence de débordement horizontal et d’erreur JavaScript.
L’attente réseau globale du premier contrôle navigateur a expiré ; la reprise
avec attente du DOM et des images a réussi. Les captures restent privées.
Cette vérification visuelle ne constitue pas une nouvelle recette de génération.
Les sources sont intégrées et poussées ; la version exécutée du lab est identifiée
séparément de l’intégration documentaire ultérieure. Le retour arrière est décrit.

## Orchestration et délégation

Codex a effectué directement les lectures, modifications, exports WebP,
compilation, vérifications, installation lab et intégration Git. Aucun sous-agent
ni session OpenCode n’a été lancé. Les trois images ont été produites avec
l’outil image_gen intégré ; les prompts sont conservés avec les sources.
Aucun coût ou gain de consommation n’est estimé.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche courte, la passation, les éléments de recette,
le protocole et les annonces récentes ont été consultés. Les changements de
recette et de transport présents dans le checkout ont été préservés et exclus du
commit visuel. Les empreintes des fichiers de présentation ont été vérifiées
avant leur remplacement. Les intentions et extensions ont été annoncées ; aucune
réservation de développement concurrente n’a été reprise.

Le portail du lab ne tournait pas en continu : cela a conduit à préparer un
service séparé et une recette Ansible spécifique. Les sources canoniques et la
documentation publique ont été intégrées dans des checkouts isolés, en conservant
les fichiers déjà modifiés ailleurs. Aucun ancien job n’a été réarmé. Les
réservations de cette intervention sont libérées par l’annonce de fin.
