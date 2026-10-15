# Maintenir les services et récupérer les sauvegardes

Pour une panne limitée, contrôler puis redémarrer le composant concerné. Pour une perte du serveur, suivre la [reprise](PROCEDURE-REPRISE-ACTIVITE.md). Pour réinstaller du code, suivre l'[implémentation](GUIDE-IMPLEMENTATION.md).

## Contrôler sans redéployer

Depuis le contrôleur Linux, avec la cible et l'identité personnelles du guide privé :

```bash
ansible all -i "$CIBLE," -u "$COMPTE" --become \
  -m ansible.builtin.command -a 'systemctl --failed --no-pager'
```

Pourquoi : localiser la panne. Aucun service ni fichier n'est modifié. L'état volontairement arrêté d'un composant n'est pas une panne ; le consommateur Telegram suspendu ne doit pas être réactivé par une commande générale.

## Redémarrer un seul service

```bash
ansible all -i "$CIBLE," -u "$COMPTE" --become \
  -m ansible.builtin.systemd_service -a "name=$SERVICE state=restarted"
```

Effet : redémarre le service choisi, conserve ses données et son code. Choisir les valeurs dans la procédure privée. Un traitement interrompu ou un envoi incertain doit être rapproché avant relance.

Les anciens playbooks d'exploitation ne sont pas automatiquement compatibles avec les helpers de la production actuelle. La procédure privée indique les appels utilisables et le précontrôle manquant ; ne pas fabriquer un marqueur pour contourner un refus.

## Télécharger une sauvegarde utilisable

| Ensemble | Pourquoi le garder |
| --- | --- |
| Archive du socle | Base et connexions n8n, clé maître, accès et configurations couverts par le collecteur historique. |
| Archive des ajouts récents | Comptes et données du portail, dashboard, textes lisibles conservés, worker et code réellement installé. |
| Empreintes et métadonnées privées | Identifier une génération cohérente et ses propriétaires. |
| Clé de récupération correspondante | Déchiffrer ; conservation protégée séparée. |
| Copie de l'hébergement | Retrouver les fichiers de sites absents de l'archive du serveur. |

La procédure privée `PROCEDURE-CONTINUITE-RUN.md` donne les chemins et les commandes de collecte, chiffrement, téléchargement et vérification. Elle distingue le snapshot existant de la collecte complémentaire à réaliser. Une ancienne archive ne contient pas les services ajoutés après sa date.

La collecte se fait pendant un arrêt cohérent des écrivains. Copier une SQLite active ou oublier ses écritures en attente peut perdre des décisions. Conserver une copie chiffrée vérifiée hors serveur, puis sur un second support indépendant. Le contrôle du déchiffrement ne remplace pas un exercice de restauration.

## Revenir au service

Reprendre l'état relevé avant maintenance, contrôler les interfaces en HTTPS privé et garder bloqués les envois/jobs incertains. Ne pas restaurer une ancienne base pour réparer une simple indisponibilité de page. Le guide privé indique les services et résultats attendus, sans exécution automatique.
