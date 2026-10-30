<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Observatoire : messages reçus et délégations Codex — 15 octobre 2026

## Demande et résultat

L’utilisateur précise deux attentes : identifier les messages d’autres agents
qu’un agent a reçus lors de ses lectures, et consulter les délégations Codex
avec le prompt transmis, le destinataire et le modèle. La simple présence
d’une annonce dans un dossier partagé ne satisfait pas cette demande.

La vue « Messages lus » relie les publications partagées aux appels dont la
sortie contient le corps du message. La comparaison utilise les empreintes de
toutes ses lignes non vides hors en-tête auteur, un minimum de texte distinctif
et une publication antérieure au retour de lecture. Une commande qui cite un
identifiant sans retour de corps confirmé reste une lecture demandée seulement.
Les courts messages, sorties tronquées ou transformées et formats non reconnus
peuvent échapper à cette reconnaissance. Le contenu renvoyé au contexte ne
prouve pas sa compréhension ou son utilisation par le modèle.

Le collecteur traite aussi les enregistrements natifs de messages inter-agents
Codex : texte, auteur et destinataire conservés dans le journal du récepteur.
Les flèches utilisent l’heure de réception ; aucune heure d’envoi n’est inventée.
Une notification d’activité sans message sérialisé ne permet pas de reconstruire
une réponse manquante. Les copies d’historique présentes dans certains fichiers
enfants sont distinguées du travail propre à l’enfant : première identité
conservée, événements antérieurs à sa création ignorés. Les préfixes hérités
réhorodatés à la création du fichier restent exclus jusqu’à l’entrée native
d’une consigne destinée à l’enfant, sans être présentés comme son propre travail.

La vue « Délégations & tâches » donne le prompt complet filtré, le destinataire,
le modèle explicitement demandé et le modèle observé chez l’enfant. Ces deux
modèles ne sont pas confondus ; une information absente reste non attestée.
Au relevé, les traces du projet comprennent 59 appels de délégation, dont 58
rattachés à un enfant avec modèle observé, et 1 713 messages inter-agents reçus.
Ces nombres décrivent les journaux disponibles, pas une garantie d’exhaustivité.
Les nouveaux appels et messages enregistrés sont suivis par le collecteur existant.

Le code est committé et poussé dans le dépôt privé canonique du serveur, puis
installé en release immuable par la recette dédiée. Les 29 tests synthétiques
passent sur le poste et le serveur ; la syntaxe JavaScript est contrôlée.
Les tests couvrent notamment les historiques copiés, les modèles distincts,
les destinataires, l’ingestion, les lectures partielles, les publications futures,
le maintien des protections d’accès et l’absence de sorties brutes dans la projection.
Les sources privées et leur masquage conservent les limites déjà documentées.

Dans le navigateur authentifié, une lecture réelle d’annonce est inspectée avec
son auteur et sa preuve, puis une carte de délégation est dépliée. Son prompt
est visible et le modèle observé apparaît. La tâche enfant est ouverte et un
message natif reçu de son parent est inspecté dans le graphe. Les deux sources
de collecte fonctionnent, le service est actif, la version exécutée est contrôlée
et l’accès HTTPS anonyme à l’API reste refusé. Ces contrôles ne valident pas
l’exhaustivité des historiques ni les parcours de tous les navigateurs.

## Orchestration et délégation

Codex réalise directement le diagnostic, les corrections de collecte, les vues,
les tests, le versionnement et le déploiement. Aucun sous-agent n’est lancé pour
cette mission ; les délégations affichées proviennent de sessions préexistantes.
Aucun coût ou gain n’est inventé. Aucun agent externe, workflow ou envoi client
n’est déclenché pour produire des traces de démonstration.

L’inspection des formats natifs corrige le diagnostic initial incomplet sur les
messages et modèles manquants. Une correction du graphe retire également les
lignes du journal partagé de la vue consacrée aux tâches, où elles étaient inutiles.
Chaque correction déployée conserve la release précédente pour retour du code.

## Coopération et adaptation au contexte

Les consignes, architecture, recette dédiée, rapport précédent et protocole de
coordination sont consultés. Une intention réserve les seuls chemins de l’outil,
son service et sa documentation. La mission parallèle du portail et ses annonces
sont prises en compte ; ses fichiers et services ne sont pas modifiés.

Le serveur applicatif reste sur le serveur du projet ; le poste ne conserve
que son miroir et le collecteur des traces locales. Les anciens rôles réservés,
la machine personnelle de contrôle et la base d’agents réservée à l’utilisateur
ne sont pas utilisés. La connexion propriétaire et les restrictions réseau sont
maintenues. Les données de conversations restent hors Git. Le présent rapport
ne publie aucun prompt privé, identifiant de session ou chemin d’accès sensible.
