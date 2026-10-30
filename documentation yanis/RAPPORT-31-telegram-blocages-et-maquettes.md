<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

# Rapport 31 — Telegram : blocages, décisions et maquettes

13 octobre 2026. Version publique anonymisée.

## 1. Demande et résultat

L’utilisateur demande de limiter Telegram aux blocages nécessitant une intervention humaine et aux maquettes réellement renvoyées au client. Une validation de maquette doit proposer **Envoyer / Annuler**. Une réponse mail bloquée par l’IA doit proposer **Envoyer / Annuler / Modifier** ; la modification revient au traitement pour un envoi explicitement confirmé.

Six workflows du parcours ont été actualisés : collecte mail, analyse commerciale, construction, journal des événements, réveil de travail et gestion des erreurs. Les messages ordinaires de prise en charge et de réponse commerciale sont consignés sans envoi Telegram. Le journal conserve le retour métier et la reprise technique autorisée après erreur. Le worker existant reste l’unique consommateur Telegram.

Une question explicitement facultative ne bloque plus la première maquette. Les contradictions et informations essentielles restent bloquantes. Une incohérence ou un prompt absent dans un résultat déclaré suffisant produit une erreur visible au lieu d’un arrêt silencieux.

Le worker installé reçoit maintenant les validations de construction et de revue finale. **Envoyer** approuve le prompt exact pour un prototype ; la validation finale autorise ensuite le mail de livraison. **Annuler** reprend réellement l’attente avec une décision d’annulation, sans construction ni mail. Les anciennes attentes par formulaire ont été remplacées par trois demandes natives, leurs anciennes exécutions arrêtées sans suppression de l’historique. Les boutons ont reçu un accusé de livraison Telegram.

Pour les revues mail, Envoyer confirme le texte exact déjà affiché. Modifier ouvre un champ de réponse lié au compte, au groupe et au message ; un nouvel aperçu affiche les trois boutons. Annuler est durable et clôt la revue et sa ligne entrante lorsque les contrôles le permettent. Un aperçu dont l’affichage échoue devient non confirmable : son nouveau texte ne peut pas être envoyé à partir des boutons d’un ancien aperçu.

Les blocages techniques, les traitements définitivement interrompus et les résultats d’envoi incertains sont surveillés et dédupliqués. Réexaminer relit les preuves ; Annuler clôt un message admissible ou marque explicitement la prise en charge d’une alerte. Une panne de service ou une réservation incertaine n’est pas réparée ou rejouée aveuglément. Les échecs IA admissibles avant envoi peuvent rejoindre la revue mail afin de recevoir une réponse humaine par Modifier.

La liste privée des destinataires du worker a été alignée sur les trois destinataires TEST déjà autorisés dans le workflow. Les identités d’approbation et les autres valeurs d’authentification restent inchangées. Les erreurs d’un workflow technique inaccessible au compte du worker passent par le gestionnaire d’erreurs existant ; aucun élargissement de clé API.

Une notification de livraison nécessite une revue finale approuvée, la réservation liée au travail et une lecture Gmail confirmant le message SENT, son destinataire et son fil. Les mails commerciaux ordinaires ne produisent pas cette notification.

### Contrôles et limites

Les suites hors ligne comptent **47 tests mail, 26 tests construction et 45 tests techniques**. Elles utilisent des données fictives et des adaptateurs simulés. Les essais JavaScript vérifient la question facultative, les refus essentiels et la provenance.

Un essai réel isolé n8n a vérifié la reprise signée : refus d’un jeton absent ou incorrect, décision reçue, jeton retiré des données de sortie et second POST refusé. Ce harnais n’envoyait aucun mail et ne construisait aucun site. Les requêtes natives de surveillance des erreurs et crashes ainsi que la collecte en lecture seule ont été vérifiées.

Après installation, le service est actif sans redémarrage automatique inattendu. Des clics humains réels ont fait avancer deux demandes jusqu’à la revue finale avant Gmail. Une autre demande a rencontré un refus du service de construction ; le blocage a été signalé puis pris en charge humainement. L’orchestrateur n’a pas simulé une approbation humaine ni relancé cette demande automatiquement.

Pendant la vérification finale, une décision humaine Envoyer a terminé le parcours : le workflow a enregistré le mail de maquette envoyé, le worker a vérifié ce message dans Gmail et Telegram a accusé la notification de livraison. Une décision humaine Annuler a terminé l’autre revue finale sans passage au nœud Gmail. Cette observation réelle est distincte des tests simulés. Un résultat réseau inconnu reste réservé, sans retry. Une panne empêchant tout accès au bot ne peut pas garantir une notification Telegram ; les traces et états incertains doivent être conservés.

Les sources et les exports des six graphes sont actualisés, avec copies locales. Le retour arrière concerne le code et les graphes, jamais la restauration d’une ancienne outbox après un envoi. Aucun ancien rôle Ansible, réseau ou contrôleur personnel n’a été testé ou modifié. Les sources applicatives n’ont pas été committées en bloc avec les changements antérieurs.

## 2. Orchestration et délégation

### Délégation

Une première tentative OpenCode a utilisé le rôle planificateur de la base existante. Sa configuration annonce un planificateur et un implémenteur GPT-6.1 Sol, une revue GPT-6 Luna. Après cinq minutes sans sortie ni nouvelle session identifiable, le processus de cette tentative a été arrêté. Aucun travail terminé ne lui est attribué ; coût et consommation non mesurés.

Trois agents Codex ont ensuite reçu des périmètres distincts :
- **Mail** : worker, politiques d’envoi, tests et documentation de revue.
- **Construction** : module de validation, préparation des Wait et tests.
- **Technique** : nouveau module de collecte des blocages, tests et documentation.

Leur modèle est hérité de la session ; aucune mesure indépendante de consommation n’est disponible. Ils ont travaillé uniquement sur les sources et mocks autorisés, sans installation, envoi réel ou publication de workflow. Leurs retours ont été intégrés par l’orchestrateur.

Des revues croisées en lecture seule ont trouvé l’incompatibilité des anciennes attentes, les blocages silencieux, les défauts d’ACK, une course d’annulation, une panne API récurrente non réarmée et le risque critique de texte d’aperçu différent du texte envoyé. Les constats ont donné lieu à corrections et tests ciblés.

L’orchestrateur a conservé les sauvegardes privées, les changements de graphes et leur publication, les tests natifs, la migration des attentes, l’installation du seul worker et l’alignement privé des destinataires. Il a également détecté les booléens API mal encodés et la différence de visibilité entre les comptes, puis fait corriger la collecte.

## 3. Coopération et adaptation au contexte

### Collaboration

Les consignes du projet, l’architecture, la passation, les références de production, les règles du dépôt cible et les annonces de coordination ont été consultées. Les annonces des travaux précédents confirmaient que les sources Telegram candidates ne constituaient pas une installation.

Une intention mère et les intentions/fins des trois agents ont annoncé les réservations de sources. Les nouvelles annonces ont été relues avant les mutations. Une mission concurrente de serveur indépendant travaillait dans un autre dossier et n’a pas été modifiée. Les changements utilisateur existants ont été préservés ; le global protégé reste intact.

La relecture des exécutions a séparé notifications ordinaires, attente de formulaire et refus causé par une question facultative. Les essais natifs ont ensuite conduit à deux adaptations : requêtes API strictes et surveillance compatible avec la visibilité réelle du compte de service. Les observations d’une copie ou d’un ancien rapport n’ont pas été utilisées comme preuve de production.

Les références exactes de sessions, exécutions, versions, sauvegardes et messages restent dans la passation et la coordination privées. Ce rapport ne contient ni contenu client, coordonnées, chemins d’accès privés, identifiants internes ou valeurs secrètes.
