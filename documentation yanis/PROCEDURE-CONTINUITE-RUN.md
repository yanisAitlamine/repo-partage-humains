# Continuité et diagnostic — Atelier Rust

| Symptôme | Contrôle utile | Suite fondée sur le résultat |
|---|---|---|
| Domaine du lab inaccessible | Résolution DNS, tunnel, certificat et service HTTPS de la VM | Localiser DNS/VPN/TLS avant de toucher aux données |
| Interface disponible, conversation indisponible | Portail, adaptateur et service Rust ; autorisation interne ; état du job | Examiner la réponse et la révision avant de renvoyer le message |
| Job bloqué | État queued/working/uncertain, journal du bridge et session du modèle | Distinguer travail actif, refus fournisseur et résultat non confirmé |
| Maquette refusée | Contrat JSON, compilation, images, pages et empreinte de la réponse | Corriger le produit commun et rejouer la suite après nouvelle version |
| Publication échouée | Approbation, final-claim, registre, confiance SSH, intention et reçu | Vérifier l’effet réel sur la cible avant toute reprise |
| Site publié inaccessible | DNS du site, proxy Pi, redirection Proxmox, serveur du conteneur | Comparer le contenu servi et les octets approuvés |
| Campagne interrompue | État privé et identité exacte de la VM temporaire | Reprendre la commande cleanup de cette campagne |

Une tâche `uncertain` reste visible. La procédure d’acquittement administratif d’un job arrêté exige une preuve ciblée d’absence d’effet et conserve l’historique. Elle n’équivaut pas à une réussite ni à une reprise métier. Les gardes de maintenance sont réévaluées après tout changement de preuve.

La panne du Pi affecte le VPN, la résolution privée et les sites publiés passant par son proxy. Le lab possède son propre service HTTPS. Les journaux doivent être lus par job et service, avec horodatage et version ; les données client et autorisations restent dans les preuves privées.
