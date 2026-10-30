<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Sites d’inspiration et refonte depuis le pipeline mail

État du 17 octobre 2026.

## Demande et résultat

La demande est de permettre au client de fournir un site comme référence
visuelle, ou son propre site à remanier, avec captures Chromium, récupération
des textes et médias, réorganisation pour une maquette puis un site livrable.
Les fichiers retenus doivent être stockés sur la destination du job ; les
temporaires de collecte doivent être identifiables puis supprimés.

Le raccord mail et les outils sont intégrés sur le serveur applicatif. Le
dialogue publié conserve son graphe ; seuls deux blocs de code changent.
Le constructeur reçoit une liste liée au brief vérifié, consulte les pages
dans Chromium et reçoit leurs captures desktop/mobile, textes, liens internes
et chemins des fichiers récupérés. La destination de livraison reste distincte
de la source et doit être autorisée dans le registre opérateur.

L’inspiration permet une analyse visuelle sans import des médias tiers.
La refonte avec réutilisation autorisée transfère les médias pris en charge
et le texte visible directement vers le dossier isolé du job. Les contrôles
de chemin, SSH, HTTPS, intégrité et revue restent requis. Le réviseur peut
consulter les sources sans importer ou modifier des fichiers à distance.
Les confirmations humaines de construction complète et de livraison demeurent.

Le profil Chromium temporaire est nommé par job et supprimé après réussite ou
erreur. Le worker effectue aussi son nettoyage terminal. Un appel ultérieur
élimine les profils orphelins d’un arrêt brutal après contrôle du processus,
en préservant les profils encore utilisés. Les médias collectés ne sont pas
conservés sur le disque du serveur applicatif.

Les contrôles ciblés passent : dix tests Python du nouveau contrat et de ses
raccords, sept tests Node dont une capture Chromium réelle sur fixture réseau
synthétique, cinq tests Node de revue et douze tests Python de preuve de cible.
La lecture HTTPS publique avec IP de connexion épinglée fonctionne également.
Une ouverture Chromium publique dans l’environnement de montage du service a
produit les deux captures et le texte, sans erreur ni profil temporaire restant.
Les outils installés et la version publiée du dialogue ont été relus.

Ces preuves ne constituent pas une refonte réelle de bout en bout : aucun mail
client, nouveau chantier distant ou Gmail de livraison n’a été déclenché.
Le parcours complet reste à essayer avec une source et une destination TEST
explicitement fournies et les accords humains habituels. La collecte est bornée
en pages, taille, durée et formats ; les ressources protégées ou inaccessibles
sont signalées, sans promesse de récupération exhaustive. La recette Ansible
dédiée est préparée seulement ; aucun ancien rôle n’a été testé ou appliqué.

## Orchestration et délégation

Codex a réalisé directement le diagnostic, le développement, les tests,
l’intégration et la revue des différences. Aucun sous-agent Codex, session
PIAgentControl ou constructeur de site n’a été lancé. Aucun modèle de
construction n’a donc été consommé pour cette mission. Aucun coût ou gain
chiffré n’est déduit de ces faits.

Les premiers candidats ont été testés avant intégration ; les contrôles ciblés
ont été complétés sur les sources installées et les paramètres publiés comparés.
Les préimages privées permettent un retour arrière ciblé. Elles ne constituent
pas une sauvegarde indépendante complète. Une validation humaine n’a jamais
été simulée pour produire une preuve de livraison.

## Coopération et adaptation au contexte

Les consignes applicables, la reprise commune, le protocole de coordination,
l’état partagé et les fins pertinentes des missions de construction ont été
consultés. La levée du gel documentaire du jour a été vérifiée. Une intention
et une extension ont réservé les seuls raccords et nouveaux fichiers nécessaires ;
les nouvelles annonces ont été contrôlées avant intégration.

L’examen a montré que Chromium et une revue liée à chaque job existaient déjà.
L’extension réutilise ce mécanisme avec des outils distincts pour les sources,
au lieu de modifier les permissions générales des agents. Les modifications
concurrentes déjà présentes et le brouillon d’une autre étape sont préservés.
Le rapport public est préparé séparément du checkout documentaire modifié.

Le rapport exclut les données clients, coordonnées, identifiants internes,
chemins privés et valeurs de secrets. Les preuves d’exploitation et le retour
arrière restent dans la passation privée du composant. Aucun accès à la VM
personnelle, changement des accès ou relance de service n’a été nécessaire.
