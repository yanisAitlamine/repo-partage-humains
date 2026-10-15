# Accès collaborateur au portail et passation — 15 octobre 2026

## Demande et résultat

Le demandeur souhaite que son collaborateur et son agent puissent consulter et
modifier le frontend et le pipeline associé. Il autorise l'envoi d'un mail de
passation. La première tâche de l'agent destinataire doit être un résumé de
l'existant et de son fonctionnement, avant toute modification.

L'accès en écriture au dépôt privé existait déjà. La copie de travail était
ancienne et Git refusait son utilisation avec l'identité du collaborateur.
La propriété du dossier a été corrigée et les sources actualisées sur la branche
principale, en conservant la branche historique. Les vérifications sous son
compte confirment le fonctionnement de Git et l'écriture sur les sources du
frontend et les exports des workflows. Sa connexion depuis son propre poste
n'a pas été rejouée.

L'édition installée de l'automatisation ne permet pas le partage éditeur entre
espaces personnels. Les deux workflows dédiés au portail ont donc été transférés
dans l'espace personnel du collaborateur par l'API native. Les connexions y
étaient déjà présentes. Les définitions, versions publiées, états actifs et rôles
globaux sont conservés ; le propriétaire de l'instance garde son accès. L'accès
API avec l'identité du collaborateur est confirmé pour les deux workflows.

Une passation de collaboration est intégrée aux sources, avec priorité au résumé
initial, carte du code, tests, limites et distinction entre développement et
production. Le mail demandé a été envoyé ; le destinataire et le statut d'envoi
ont été revérifiés. Sa lecture par le destinataire n'est pas attestée.

Cette intervention ne déploie pas les corrections de produit récemment
fusionnées. Une future mise à niveau du portail et du validateur de workflow
doit rester coordonnée et autorisée pour une version exacte. Aucun workflow,
appel de modèle ou ticket client n'a été exécuté pour ouvrir ces accès. Les
contrôles de cette mission concernent les droits, les états et la documentation,
pas un nouveau parcours client réel.

## Orchestration et délégation

Codex a effectué directement la vérification des accès, la synchronisation, les
transferts natifs, la documentation et l'envoi explicitement demandé. Aucun
sous-agent ni session du collaborateur n'a été lancé. Le résumé attendu doit
être réalisé par son agent et lui être remis avant toute nouvelle intervention.

Les préimages locales permettent de comparer les définitions et propriétés
avant/après. Elles ne sont pas présentées comme des sauvegardes indépendantes.
La documentation seule a reçu une revue statique des chemins, liens et du diff ;
aucune nouvelle suite de tests produit n'était nécessaire pour cette modification.

## Coopération et adaptation au contexte

Les instructions du projet, la documentation du portail et les annonces de
coordination récentes ont été consultées. Une intention puis une extension de
périmètre ont réservé les seuls chemins et workflows concernés. Les travaux
concurrents sur d'autres pipelines sont préservés.

Deux faits ont guidé l'intervention : les droits du dépôt ne suffisaient pas à
rendre la copie Git utilisable, et l'accès au code ne donnait pas accès aux
workflows détenus par un autre espace personnel. Les corrections répondent à
ces deux blocages sans élargir le rôle global du collaborateur ni transmettre
de valeurs secrètes. Les détails d'accès restent dans la passation privée et le
mail autorisé ; ce rapport public ne contient aucune cartographie opérationnelle,
coordonnée personnelle, donnée client ou référence interne.
