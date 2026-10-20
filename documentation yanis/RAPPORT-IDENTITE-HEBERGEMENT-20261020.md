# Identité du serveur et admission d’une cible de recette — 20 octobre 2026

## Demande et résultat

La demande autorisait la création d’une identité SSH dédiée sur le serveur de production et l’inscription de sa partie publique chez l’hébergeur. Une restriction de provenance expliquait le refus de l’identité précédente depuis ce serveur.

La nouvelle identité reste sur son serveur. L’autorisation publique est limitée à sa provenance réseau ; les autorisations précédentes sont conservées. La connexion réelle SSH, la racine canonique et l’égalité des fichiers servis en HTTPS avec TLS valide ont été contrôlées. Une seule association de projet de recette a été ajoutée au registre opérateur, après sauvegarde ; le portail authentifié confirme la disponibilité de la création finale. Cette admission ne constitue pas une livraison de site.

Les recettes opérateur sont versionnées. Leur code Python et les différences ont été relus statiquement ; aucun test des anciens rôles Ansible réservés n’a été lancé. Un candidat applicatif demandé séparément a été préparé par le contrôleur officiel et comparé intégralement à son manifeste, sans être activé. Le diagnostic mail confirme un credential fonctionnel et un relais cohérent ; il n’établit pas encore la réception et le traitement des réponses. Aucune nouvelle sauvegarde chiffrée indépendante de la clé privée n’est attestée.

## Orchestration et délégation

Codex a réalisé directement la préparation opérateur, l’inscription publique, les preuves et la documentation. Aucun sous-agent ni session OpenCode n’a été lancé. Une autre conversation autorisée par l’utilisateur a fourni le périmètre du projet fictif et poursuit la recette client et les corrections mail. Ses sources et décisions applicatives restent distinctes de cette intervention d’accès.

Un workflow manuel temporaire a effectué une lecture du profil Gmail au moyen du credential existant, par le mécanisme natif de la plateforme ; il a ensuite été archivé. Aucun mail n’a été envoyé ou rejoué par ce diagnostic. Une tentative préalable de diagnostic autonome a échoué avant toute requête et a été abandonnée, sans export de credential.

## Coopération et adaptation au contexte

La reprise, le protocole partagé, les annonces pertinentes et les consignes du composant ont orienté l’intervention. Les réservations concurrentes et les modifications préexistantes du fichier de consignes ont été préservées. L’intégration des seuls outils opérateur a utilisé un arbre Git isolé, car le dépôt local avait pris du retard sur les changements concurrents.

La machine personnelle de contrôle est restée exclue. Le circuit administratif existant de l’hyperviseur a permis l’intervention bornée sans élargissement des permissions du compte de service. Les emplacements et éléments d’inventaire nécessaires à la reprise sont conservés dans la documentation privée, sans valeurs de secrets. Les preuves réseau attestent l’accès à la cible ; elles ne remplacent pas la recette complète du service.
