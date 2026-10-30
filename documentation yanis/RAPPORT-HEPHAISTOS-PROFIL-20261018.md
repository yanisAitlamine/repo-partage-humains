<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Héphaïstos : profil professionnel et sécurité du compte

État du 18 octobre 2026. Rapport public anonymisé.

## Demande et résultat

Yanis demande de poursuivre la candidate Héphaïstos sur la même branche, sans
la déployer en production. Une fois connecté, l’utilisateur doit pouvoir ouvrir
le menu de son avatar, accéder à Mon profil ou se déconnecter, modifier ses
coordonnées professionnelles et changer son mot de passe après vérification
de l’ancien et confirmation du nouveau.

Le menu propose exactement ces deux actions. La page de profil comprend un
formulaire de contact : nom, e-mail professionnel, société et identifiant de
société facultatif, téléphone et adresse postale structurée. L’identifiant de
connexion reste stable. Les informations sont conservées par compte avec un
contrôle de révision pour refuser l’écrasement des modifications d’un autre
onglet. Le mail professionnel reste une coordonnée déclarative ; aucune
vérification par envoi ou nouvelle fonction de messagerie n’est ajoutée.

Le formulaire de mot de passe est distinct. Le serveur vérifie l’ancien,
impose la confirmation et une longueur de 12 à 128 caractères, puis utilise
un nouveau sel et le hachage scrypt existant. Il révoque les anciennes sessions
et fournit un nouveau cookie pour conserver la connexion courante. Les échecs
sont limités par compte sur cinq minutes et cette limite persiste en base.
Les contrôles de session sont refaits dans la transaction d’écriture. Une
connexion en cours utilisant l’ancien mot de passe ne peut pas laisser une
session valide après son remplacement.

Le stockage est additif : les comptes et projets existants sont conservés.
Les coordonnées ne rejoignent pas automatiquement les exports de projet,
prompts ou envois de support. Aucun nouvel accès opérateur ni transfert externe
n’est créé par cette fonction. Les valeurs et mots de passe des tests ne sont
pas publiés dans ce rapport.

Vérifications : 255 tests Python réussis sur une copie personnelle du serveur,
dont 16 nouveaux tests des routes, du stockage et de la sécurité. Les 16 passent
également sur Windows. Les 70 tests frontend et la compilation de production
réussissent. La recette navigateur utilise uniquement un compte et des données
fictifs dans un serveur local isolé : menu, clavier et Échap, enregistrement,
persistance après rechargement, actualisation du nom, affichage mobile sans
débordement et déconnexion jusqu’à l’accueil. Les trois champs de mot de passe
ont été inspectés au navigateur ; le changement effectif et les révocations
ont été exercés par les tests HTTP synthétiques.

Les sources sont intégrées à la branche principale après la refonte. Aucun
mécanisme de préparation de release, déploiement ou redémarrage de production
n’est exécuté. Les contrôles prouvent la candidate, pas une migration réelle
des comptes de production. Les suites historiques émettent encore des
avertissements de connexions SQLite non fermées, sans échec de test.

## Orchestration et délégation

Codex effectue directement les lectures, la conception, l’implémentation et
les vérifications dans la continuité de la session de refonte. Aucun sous-agent
n’est lancé, aucun résultat d’un autre agent n’est présenté comme une revue
indépendante de ce changement. Aucun constructeur, modèle fournisseur, agent
OpenCode ou système de messagerie n’est sollicité par cette mission.

Le travail porte sur les composants de menu et de profil, les routes du serveur,
la validation des coordonnées et du mot de passe, les tests et la documentation.
Le premier contrôle Windows avait révélé une connexion de fixture SQLite
non fermée lors du nettoyage : la fixture a été corrigée, puis les contrôles
ont été relancés avec succès. Aucun coût ou gain non mesuré n’est annoncé.

## Coopération et adaptation au contexte

Les consignes, la fiche de reprise, la passation, le contrat API et les annonces
pertinentes ont été consultés. L’intention a réservé la copie personnelle déjà
utilisée pour Héphaïstos et ses fichiers ciblés. Les nouvelles annonces ont
été relues avant synchronisation et intégration ; les missions de construction
et de revue en cours restent dans leurs espaces séparés.

La base Héphaïstos et la carte d’aperçu précédemment préparée sont conservées.
Les modifications préexistantes des consignes et les autres copies ne sont ni
intégrées ni écrasées. Les sources vérifiées sont poussées normalement dans
la même branche, sans réécriture des commits déjà publiés. Aucun conflit
n’est rencontré et aucune réservation tierce n’est déclarée libérée.

Le rapport et sa seule entrée au sommaire sont publiés après contrôle de la
visibilité publique, relecture et revue du diff. La fin de mission consigne
les vérifications et l’absence de déploiement dans le journal de coordination,
en libérant uniquement les réservations propres. Les captures et les preuves
détaillées restent dans l’espace de travail privé.
