<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Rapport 32 — Maquette produite avant validation humaine

13 octobre 2026. Version publique anonymisée.

## Demande et résultat

Yanis demande de reprendre le bilan d’arrêt de l’autre agent, corriger le parcours depuis le mail jusqu’à la maquette, et déplacer la validation humaine après production. Il réserve l’essai manuel de bout en bout et demande des contrôles automatiques limités.

Le diagnostic distingue une session d’agent terminée d’une construction réussie : un compte rendu d’arrêt avait été accepté comme résultat admissible, puis un lien commun avait été livré malgré un contenu ancien. Le reçu Gmail attestait l’envoi, pas la conformité du site. La contention de cible et l’annulation observées concernaient d’autres parcours.

Le nouveau parcours prépare automatiquement un prototype de TEST lorsque le brief est suffisant et cohérent. Chaque travail utilise un dossier et un lien de maquette propres. Le résultat structuré exige les bonnes identités et une revue indépendante ; le bridge vérifie ensuite les marqueurs et l’identité des octets de l’index entre l’hébergement et le contenu servi. Un arrêt, un résultat absent ou un contenu discordant bloque la livraison.

La revue humaine intervient sur la maquette déjà produite : le message Telegram donne son lien, puis Envoyer ou Annuler. La décision reste liée à la version précise. Avant Gmail, une nouvelle vérification et une réservation durable empêchent deux autorisations d’envoi pour la même révision. Un reçu incomplet reste incertain et ne déclenche aucun renvoi automatique. Les prérequis de coordination sont désormais lus sur le contrôleur qui les héberge, et non sur l’hébergement du site.

Les constructions partageant une cible sont sérialisées. Les états inconnus et les interruptions demandent une réconciliation, jamais une remise à zéro aveugle. Les filtres de destinataires de TEST et les protections des mails commerciaux sont conservés.

Les graphes de construction et d’analyse commerciale sont publiés et relus ; les services du bridge et de la revue Telegram sont actifs, sans redémarrage spontané. Les sources et exports de reprise sont synchronisés. Quelques paramètres sans effet et deux connexions vers des sorties inexistantes ont aussi été nettoyés après lecture du code installé ; les mises à jour finales ne signalent plus d’avertissement de validation. Le test réel depuis un nouveau mail reste confié à Yanis. La vérification de l’index ne certifie pas tous les assets, les interactions ou la qualité visuelle ; la revue humaine reste nécessaire. Aucune construction, livraison client ou décision humaine simulée n’est lancée pour les contrôles de cette intervention.

## Orchestration et délégation — Délégation

Codex a lancé le planificateur OpenCode depuis la base de contrôle du serveur, pour la file, le contrat de résultat, la vérification d’artefact, la réservation de livraison et la coordination des agents d’hébergement. Le planificateur a délégué l’implémentation, repris le même rôle pour sa finalisation, puis demandé une revue indépendante courte. L’implémenteur a atteint sa limite d’étapes avant sa première clôture ; sa reprise a terminé les vérifications et la coordination. La revue a relevé un écart de format de réservation et une permission SSH large ; cette permission était préexistante et a été préservée. Les modèles configurés dans cette base sont GPT-6.1 Sol pour planification/implémentation et GPT-6 Luna pour revue ; leur usage réel et leur coût ne sont pas mesurés indépendamment.

Un enfant Codex de Yanis a adapté la revue Telegram sur des fichiers distincts, ajouté la liaison à l’artefact et conservé auteur, expiration et refus du rejeu. Il a rendu son résultat et clôturé sa réservation. Codex a intégré les graphes, les opérations privées et les installations, contrôlé les différences et publié les définitions utiles à la reprise. La délégation avait suspendu les choix internes de format et de reprise ; Codex a conservé le format déjà aligné entre composants et ajouté un namespace pour les nouvelles constructions ainsi qu’un contrôle de la dernière révision soumise. Ces choix sont couverts par la demande de correction complète ; ils ne changent aucun accès ni destinataire. Deux cas ciblés les vérifient. Codex a aussi simplifié le message de revue en conservant les liaisons techniques côté service.

Les contrôles restent synthétiques et ciblés : guards de livraison et de reçu, annulation, identité d’artefact, réservation et revue Telegram. Les contrôles réussis comprennent 21 tests backend (relancés par Codex après intégration), 27 tests de revue Telegram, 13 assertions JavaScript et deux cas ciblés de reprise/révision. Ils utilisent mocks et stockage temporaire, sans réseau métier ni modèles supplémentaires. Une revue statique ne vaut pas un essai réel. Aucun gain ou coût n’est inventé.

## Coopération et adaptation au contexte — Collaboration

Les consignes du projet, l’architecture, la passation, le protocole partagé et les annonces récentes ont été lus. Le bilan d’arrêt de l’agent d’Ilyes confirme sa suspension ciblée et l’absence de restauration ultérieure. Codex a préservé cette protection jusqu’à préparation de son remplacement par un contrôle de preuve.

La nouvelle demande humaine remplace explicitement la validation préalable du prompt pour le prototype automatique. Cette modification du parcours ne vient pas d’une ancienne annonce. Le gel des agents d’Ilyes a été maintenu pendant l’intégration ; les délégués mandatés par Yanis ont été identifiés comme tels et autorisés seulement dans leurs tâches attribuées.

Intention principale, sous-intentions et fins sont consignées dans l’espace de coordination. Les fichiers et graphes courants ainsi que les deux bases concernées ont été sauvegardés localement de manière cohérente avant mutation ; les modifications préexistantes sont préservées. Une nouvelle copie indépendante hors serveur n’est pas attestée. Aucun ancien historique d’envoi ou état incertain n’est restauré. Les sources applicatives modifiées ne sont pas committées en bloc avec des travaux antérieurs.

Ce rapport est publié uniquement dans l’espace documentaire public après relecture et anonymisation. Les références exactes d’exploitation et sauvegardes restent privées. Les réservations des enfants sont explicitement libérées ; la fin principale annonce l’intégration et laisse les tests à Yanis. Le gel des agents d’Ilyes reste en place pendant l’essai manuel, afin de conserver la version à tester. La configuration générale protégée, le réseau, les identités et les anciens rôles Ansible n’ont pas été modifiés par cette mission.
