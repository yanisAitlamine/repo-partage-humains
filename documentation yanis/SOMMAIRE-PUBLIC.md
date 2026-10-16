> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Documentation publique

**État au 16 octobre 2026 :** [gel des changements et préparation du redéploiement Debian amd64](RAPPORT-GEL-REDEPLOIEMENT-20261016.md).
Les versions courantes et les limites de reprise sont distinguées dans
[l'architecture actualisée](ARCHITECTURE.md#état-au-16-octobre-2026--gel-des-changements-et-préparation-de-reprise).

Pour les agents : [fiche courte de reprise](REPRISE-AGENTS.md), puis les seules
références utiles à la mission.

- [Parcours simplifié de reprise — 15 octobre 2026](RAPPORT-REPRISE-COURTE-20261015.md).


## Comprendre le fonctionnement

- [Guide détaillé des workflows, du mail à la livraison](WORKFLOWS-PIPELINE-PRINCIPAL.md) : réception, dialogue, décisions Telegram, maquette et livraison.
- [Architecture complète, schémas et catalogue des fichiers](ARCHITECTURE.md) : machines, services, données et sauvegardes.

- [Bridge n8n/OpenCode : référence technique complète](BRIDGE-N8N-OPENCODE-REFERENCE-TECHNIQUE.md) : routes HTTP, jobs, preuve d’artefact, fonctions, workflow, unité et tests.
- [Worker Telegram : référence technique complète](WORKER-TELEGRAM-REFERENCE-TECHNIQUE.md) : poller, Gmail, validations, moteur de décision, reprise, fichiers, fonctions et tests.

Les guides expliquent le fonctionnement documenté. Les rapports ci-dessous conservent l’historique daté des interventions.

## Redéployer et restaurer

- [Implémentation du site et du dashboard](GUIDE-IMPLEMENTATION.md) : fichiers nécessaires, effet des recettes et distinction code, workflows et données.
- [Continuité](PROCEDURE-CONTINUITE-RUN.md) : diagnostic, redémarrage ciblé et fichiers de sauvegarde à récupérer.
- [Reprise](PROCEDURE-REPRISE-ACTIVITE.md) : ordre de restauration sur une machine neuve et remise en service.
- [Réécriture des procédures autour des commandes](RAPPORT-PROCEDURES-COMMANDES-20261015.md) : résultat et limites de la mise à jour.

Les commandes propres à la production sont dans les guides privés correspondants.

## Historique et procédures

- [Drive privé vers maquette livrée par mail — 15 octobre 2026](RAPPORT-DRIVE-MAIL-MAQUETTE-20261015.md) : trente pages, images et produits, construction revue, validation Telegram et réception du lien.

- [Alertes Telegram : étape et cause explicites — 15 octobre 2026](RAPPORT-ALERTES-TELEGRAM-20261015.md) : diagnostic précis, référence d’exécution et vérification du rendu sans envoi de test.

- [Portail : tests end-to-end et correctifs — 15 octobre 2026](RAPPORT-PORTAIL-E2E-CORRECTIFS-20261015.md) : parcours réexécutable, erreurs de génération explicites et accord lié à la version exacte.

- [Portail connecté à n8n et parcours client — 15 octobre 2026](RAPPORT-PORTAIL-N8N-20261015.md) : comptes, conversations réelles, maquettes privées versionnées et vérifications du service installé.

- [Portail client indépendant en HTTPS privé — 15 octobre 2026](RAPPORT-PORTAIL-CLIENT-20261015.md) : portail autonome, contrôles, versionnement et passation agents.

- [ARCHITECTURE.md](ARCHITECTURE.md)
- [PASSATION.md](PASSATION.md)
- [PROCEDURE-CONTINUITE-RUN.md](PROCEDURE-CONTINUITE-RUN.md)
- [PROCEDURE-REPRISE-ACTIVITE.md](PROCEDURE-REPRISE-ACTIVITE.md)
- [RAPPORT-01-installation-et-commandes.md](RAPPORT-01-installation-et-commandes.md)
- [RAPPORT-02-partage-securise-par-ip-publique.md](RAPPORT-02-partage-securise-par-ip-publique.md)
- [RAPPORT-03-mise-en-ligne-realisee.md](RAPPORT-03-mise-en-ligne-realisee.md)
- [RAPPORT-04-arret-et-demarrage.md](RAPPORT-04-arret-et-demarrage.md)
- [RAPPORT-05-mise-a-jour-et-assistant.md](RAPPORT-05-mise-a-jour-et-assistant.md)
- [RAPPORT-06-domaine-duckdns-et-gmail.md](RAPPORT-06-domaine-duckdns-et-gmail.md)
- [RAPPORT-07-neovim-deploiement-et-audit.md](RAPPORT-07-neovim-deploiement-et-audit.md)
- [RAPPORT-08-agents-et-ansible.md](RAPPORT-08-agents-et-ansible.md)
- [RAPPORT-09-openvpn.md](RAPPORT-09-openvpn.md)
- [RAPPORT-10-n8n-opencode.md](RAPPORT-10-n8n-opencode.md)
- [RAPPORT-11-git-et-reprise.md](RAPPORT-11-git-et-reprise.md)
- [RAPPORT-12-https-prive-preparation.md](RAPPORT-12-https-prive-preparation.md)
- [RAPPORT-13-https-prive-et-delegation.md](RAPPORT-13-https-prive-et-delegation.md)
- [RAPPORT-14-consignes-agents.md](RAPPORT-14-consignes-agents.md)
- [RAPPORT-15-rangement-et-controleur-kali.md](RAPPORT-15-rangement-et-controleur-kali.md)
- [RAPPORT-16-dns-lan-et-inventaire-secrets.md](RAPPORT-16-dns-lan-et-inventaire-secrets.md)
- [RAPPORT-17-opencode-cible-test.md](RAPPORT-17-opencode-cible-test.md)
- [RAPPORT-18-prototype-demonstration-mail-et-prototype.md](RAPPORT-18-prototype-demonstration-mail-et-prototype.md)
- [RAPPORT-19-mails-version-test-et-livraison.md](RAPPORT-19-mails-version-test-et-livraison.md)
- [RAPPORT-20-invitation-contact-test.md](RAPPORT-20-invitation-contact-test.md)
- [RAPPORT-21-compte-ilyes-et-swarm.md](RAPPORT-21-compte-ilyes-et-swarm.md)
- [RAPPORT-22-diagnostic-alertes-telegram.md](RAPPORT-22-diagnostic-alertes-telegram.md)
- [RAPPORT-23-acces-ssh-ilyes-et-coordination.md](RAPPORT-23-acces-ssh-ilyes-et-coordination.md)
- [RAPPORT-24-relance-gmail-deux-heures.md](RAPPORT-24-relance-gmail-deux-heures.md)
- [RAPPORT-25-capacites-annoncees-aux-clients.md](RAPPORT-25-capacites-annoncees-aux-clients.md)
- [RAPPORT-26-premiere-reponse-et-verification-pdf.md](RAPPORT-26-premiere-reponse-et-verification-pdf.md)

- [Rapport 27 — Architecture privée et rapports publics](RAPPORT-27-documentation-privee-et-rapports-publics.md)

- [Rapport 28 — Quatre références privées et guide Ansible](RAPPORT-28-quatre-references-et-guide-ansible.md)

- [Rapport 29 — Versionnement privé d’OpenVPN](RAPPORT-29-openvpn-versionnement-prive.md)
- [Rapport 30 — Traitement des mails sur événements](RAPPORT-30-mails-sur-evenements.md)

- [Rapport 31 — Telegram : blocages et maquettes](RAPPORT-31-telegram-blocages-et-maquettes.md)

- [Rapport 32 — Maquette produite avant validation humaine](RAPPORT-32-pipeline-maquette-avant-validation.md)

- [Rapport 33 — Ancien banc Gmail retiré et noms du pipeline](RAPPORT-33-ancien-banc-gmail-et-noms-pipeline.md)

- [Rapport 34 — Permissions de coordination et reprise de construction](RAPPORT-34-blocage-coordination-construction.md)

- [Rapport 35 — Lanceur manuel du cas club de foot](RAPPORT-35-lanceur-test-pipeline3-club-foot.md)

- [Rapport 36 — Diagnostic complet, livraison vérifiée et reprise de l’agent Ilyes](RAPPORT-36-test-reel-maquette-et-validation.md)

- [Rapport 37 — Revue native Telegram du laboratoire](RAPPORT-37-revue-laboratoire-telegram-native.md)
- [Rapport 38 — Jev dans le parcours commercial réel](RAPPORT-38-jev-parcours-commercial-reel.md)

- [Guide — Pipeline principal n8n](WORKFLOWS-PIPELINE-PRINCIPAL.md)
- [Rapport 39 — Documentation des workflows](RAPPORT-39-documentation-workflows.md)

- [Rapport 40 — Documentation claire et complète, publique et privée](RAPPORT-40-documentation-en-francais-clair.md)

- [Rapport 41 — Reprise immédiate après Telegram et diagnostic](RAPPORT-41-reprise-telegram-et-diagnostic.md)

- [Rapport 42 — Refonte des guides privés, continuité et reprise](RAPPORT-42-refonte-trois-guides-prives.md)

- [Rapport 43 — Correctifs et pause de l’essai Gmail et Telegram](RAPPORT-43-correctifs-et-essai-gmail-telegram.md)

- [Rapport 44 — Consolidation des documents et suppression des anciennes copies](RAPPORT-44-consolidation-documentation-et-retrait-humain.md)

- [Rapport 46 — Références techniques du bridge et du worker, sources versionnées](RAPPORT-46-references-techniques-bridge-et-worker.md)

- [Rapport 47 — Reprise du pipeline, validation humaine et livraison vérifiée](RAPPORT-47-reprise-pipeline-et-validation-maquette.md)

- [Rapport 48 — Réponses humaines contrôlées, tests et rappels à six heures](RAPPORT-48-robustesse-reponses-et-rappels-six-heures.md)

- [Préparation d'un accès VPN dédié à un serveur — 15 octobre](RAPPORT-VPN-SERVEUR-20261015.md)

- [Livraison d’un site complet, captures et recette réelle — 15 octobre](RAPPORT-SITE-COMPLET-REVUE-VISUELLE-20261015.md)

- [Jev et OpenAI Decisions : diagnostic et comparaison isolée — 16 octobre](RAPPORT-JEV-DECISIONS-20261016.md)

- [OpenAI Decisions intégré et essais mail — 16 octobre](RAPPORT-MIGRATION-DECISIONS-TESTS-20261016.md) : analyse débloquée sur deux cibles, première maquette revue, seconde bloquée dans la coordination NOC.

- [Deux pipelines mail vers maquette livrée — 16 octobre](RAPPORT-NOC-A-Z-TESTS-20261016.md) : correctifs de preuve et de navigation, deux revues finales réussies, recettes navigateur et mails reçus ; périmètre prototype TEST.

- [Portail : parcours complet et images IA préparés — 16 octobre](PORTAIL-E2E-IMAGES-PREPARATION-20261016.md) : sources testées et release préparée ; activation et essais réels encore attendus.
