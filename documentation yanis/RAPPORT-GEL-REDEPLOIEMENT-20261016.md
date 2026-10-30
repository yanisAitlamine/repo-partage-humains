<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Gel des changements et préparation d'un redéploiement Debian amd64

16 octobre 2026 — état relevé en début de soirée, Europe/Paris.

## Demande et résultat

La demande humaine porte sur un gel temporaire des modifications, une mise à
jour des documentations privée et publique, et la création d'une VM Debian
amd64 sur l'hyperviseur du collaborateur si les accès le permettent. L'opérateur
réserve à son propre essai le redéploiement. La mission ne modifie aucun code,
service, workflow ou règle réseau et n'exécute aucun rôle ou test Ansible.
Le gel est annoncé dans la coordination, sans verrou technique global.

Les références privées d'architecture et d'inventaire des secrets sans valeurs
reçoivent un état daté : versions sources, versions exécutées et publiées,
changements locaux à préserver, limites de sauvegarde, diagnostic d'accès et
préparation de l'exercice amd64. Des avertissements sont placés dans les guides
privés existants et leur sommaire. L'architecture publique, le guide des workflows
et le sommaire sont actualisés avec ce rapport. Les anciens guides restent datés ;
le nouveau point de reprise précise les écarts avant de suivre leurs commandes.

Le portail, l'Observatoire, l'orchestration, le proxy privé et le VPN sont actifs.
Les sondes de santé du portail et du dashboard répondent en local et en HTTPS
privé avec vérification TLS. La revue Telegram reste arrêtée et désactivée.
Ces sondes ne déclenchent ni envoi, ni construction, ni nouvel appel de modèle.

Les passations distinguent deux nouveaux parcours mail jusqu'à une maquette
reçue, déjà terminés, du futur parcours portail avec image puis site complet.
Ce dernier reste préparé, non activé et non éprouvé de bout en bout. Les deux
livraisons mail précédentes avaient une autorisation opérateur TEST explicite,
sans clic Telegram natif. Deux défauts du portail relevés lors d'une revue
antérieure restent documentés sans correction pendant ce gel.

**Aucune VM n'est créée.** Le poste opérateur n'a pas de tunnel VPN personnel
actif ; la tentative SSH expire avant authentification. Le statut VPN récent
du serveur montre aussi l'absence de l'hyperviseur du tunnel. Le rétablissement
des deux connexions est nécessaire avant de vérifier les droits de création,
le stockage, le réseau et un identifiant de VM libre. L'état actuel n'établit ni
un refus de permissions sur l'hyperviseur ni l'arrêt de cette machine. Aucun
élargissement d'accès, transfert de clé privée ou envoi au collaborateur.

Pour l'exercice : installer une Debian 13 amd64 neuve et isolée, puis distinguer
réinstallation du code et reprise des données. La procédure ARM64 existante ne
peut pas être rejouée telle quelle : le helper de restauration refuse le proxy
compilé pour une autre architecture ; les autres exécutables et dépendances
natives doivent également correspondre à la VM. Aucun parcours complet de
restauration entre architectures n'est validé par cette rédaction.
Le [guide officiel Debian](https://www.debian.org/releases/trixie/amd64/)
sert de référence pour l'installation du système.

Une reprise des données demande un lot cohérent actuel et une copie indépendante
vérifiée. Aucun lot récent complet n'est certifié ici. Les anciens coffres
précèdent des ajouts récents et Git ne contient pas toutes les sources locales.
Les sorties métier doivent rester bloquées avant le premier démarrage de la
copie, avec workflows inactifs et réconciliation des attentes et envois.
L'exercice et la restauration réelle restent à effectuer par l'opérateur.

## Orchestration et délégation

Codex effectue directement les lectures, le diagnostic réseau, la rédaction,
la revue des différences, l'anonymisation et la publication documentaire.
Aucun sous-agent n'est lancé pour cette mission. Aucun OpenCode depuis la base
réservée à l'opérateur et aucun accès à sa VM personnelle ne sont utilisés.
Les sessions de construction décrites dans les passations sont des résultats
antérieurs ; elles ne sont pas relancées. Aucun coût ni gain n'est estimé.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche courte de reprise, les procédures de
continuité/reprise, le protocole, l'état partagé et les annonces pertinentes
sont lus. Les fins des missions de construction, de préparation du portail et
de revue sont distinguées des anciennes intentions. Une intention propre
annonce le gel et réserve les seuls blocs documentaires et ce rapport ; une
extension précise les avertissements ajoutés aux guides existants. Les annonces
utiles déjà lues sont conservées tardivement en copies d'audit privées. L'extension
est archivée avant envoi ; aucune égalité avec un texte natif chiffré n'est attestée.

Les états Git et les versions installées/publiées sont consultés avant écriture.
Les workflows non accessibles en MCP ne sont pas exposés : seules leurs
métadonnées sont lues par un accès local en lecture seule. Les modifications
préexistantes des sources et de la fiche publique de reprise sont préservées
hors des commits de cette mission. Les travaux personnels du collaborateur
sur ses autres services ne sont pas modifiés.

La revue de publication retire les paramètres d'accès, chemins privés,
identifiants techniques, données clients et secrets de ce rapport. Les
références exactes restent privées. La fin de coordination libère les seules
réservations documentaires de cette mission ; le gel demandé reste applicable
à nos changements applicatifs jusqu'à une nouvelle instruction humaine.
