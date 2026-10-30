# Plan de reprise — Atelier Rust

## Ensembles à conserver

Conserver séparément la source Git, le paquet scellé et ses preuves ; les paramètres et états Terraform/Ansible ; les configurations installées ; les deux bases du portail et du backend ; les états/intentions du bridge et de publication ; les sources client ; les autorisations et sessions du modèle nécessaires ; les fichiers et bases des sites publiés. Les certificats et clés ont leur propre sauvegarde privée avec leurs permissions.

La documentation et les références d’emplacements ne prouvent pas l’existence d’une sauvegarde complète indépendante. Cette mission vérifie des sources et métadonnées ; elle ne réalise pas une restauration générale ni un exercice de perte totale.

## Ordre de restauration

1. Choisir une machine et une identité explicitement autorisées ; vérifier réseau, ressources et stockage. Identifier les projets à conserver avant toute réinitialisation.
2. Rétablir l’accès opérateur, la confiance des hôtes, le DNS/VPN et le HTTPS correspondant à la cible.
3. Reconstruire ou réinstaller exactement le paquet documenté avec Terraform/Ansible et ses paramètres privés. Une instance neuve ne reçoit pas automatiquement d’anciennes données.
4. Si une restauration de données a été demandée, restaurer les bases de manière cohérente avec leurs journaux SQLite, les sources et les états associés, sous leurs comptes de service.
5. Rétablir les autorisations du modèle, les jetons internes et le registre de publication ; vérifier leurs associations sans choisir une ancienne identité d’hôte.
6. Réconcilier les jobs incertains, intentions et reçus avec les sites réellement présents. Ne pas réarmer une livraison déjà réalisée.
7. Contrôler services, versions, propriétés, accès client, fichiers et maquettes ; exécuter une nouvelle recette autorisée avec un compte et une cible réservés.
8. Retirer uniquement les copies et processus créés par la reprise devenus inutiles, puis conserver les preuves et le retour à l’état antérieur encore nécessaires.

Un retour logiciel n’annule pas les effets sur un site distant. La reprise des données et le retour de version sont donc deux opérations distinctes.
