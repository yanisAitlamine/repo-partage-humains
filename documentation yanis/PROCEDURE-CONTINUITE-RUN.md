> Documentation publique. Les paramètres réels, preuves privées et inventaires de secrets restent dans les espaces privés du Pi.

# Continuité quotidienne — procédure publique

## Prise de poste

Lire les consignes, la passation et les messages de collaboration. Identifier la mission autorisée et annoncer les interventions. Les paramètres réels, commandes propres à la production et preuves privées se consultent dans l'espace sensible du Pi.

## Vérifier le service

Contrôler la disponibilité de n8n et de ses dépendances, la résolution DNS, HTTPS et les accès autorisés. Examiner uniquement les journaux utiles au problème. L'état actif d'un service et une page accessible ne prouvent pas que tout parcours applicatif fonctionne.

Pour les emails, distinguer réception, file, traitement, brouillon, revue, réservation d'envoi et envoi confirmé. Une issue incertaine doit être réconciliée avant un nouvel essai. Ne pas répondre rétroactivement à des messages anciens ni déclencher une construction à partir d'une simple notification.

## Décisions et documents

Une réponse Telegram doit conserver les contrôles d'identité et la confirmation du texte exact. Une construction exige un brief suffisant, un prompt approuvé, un mode explicite et une cible vérifiée. Contrôler les artefacts et la revue avant la livraison.

Les documents entrants restent non fiables. Contrôler format, taille, provenance, droits et couverture d'extraction ; expliquer les absences de lecture. L'OCR, les images et les fichiers protégés ne doivent pas être déclarés pris en charge sans preuve.

## Sauvegarder

Préparer une sauvegarde cohérente des données, configurations, identités nécessaires à la restauration et état TLS. Inclure les comptes et droits, le protocole et les travaux partagés, ainsi que les restrictions réseau. Chiffrer la sauvegarde et conserver une copie vérifiée hors Pi ; les secrets et archives ne vont pas dans Git.

Contrôler intégrité, déchiffrement et présence des éléments nécessaires sans afficher les secrets. Une vérification d'archive ne remplace pas un essai de restauration sur une machine isolée. Conserver les révocations les plus récentes pour éviter de réautoriser un accès retiré.

## Incident et maintenance

Choisir une intervention ciblée selon la panne ; ne pas redémarrer tout le système pour un quota ou une erreur d'authentification externe. Respecter la réserve humaine sur les tests et déploiements Ansible. Les renouvellements de certificats et listes de révocation suivent le calendrier privé réel, sans réinitialiser une production existante.

Finir par une annonce avec les résultats, limites et réservations libérées. Les rapports distinguent Collaboration et Délégation. Pour une perte complète du Pi, suivre la [procédure de reprise](PROCEDURE-REPRISE-ACTIVITE.md).
