# Fournisseur OpenAI partagé et recette autonome du laboratoire

Mission du 20 octobre 2026. Acceptation finale : 21 octobre à 00 h 11 (Paris).

## Demande et résultat

Le demandeur autorise explicitement le partage des secrets fournisseurs existants
entre ses environnements, l'alignement du code des deux productions et une recette
complète dans le laboratoire avec échanges mail réels, sans Telegram ni intervention
humaine. Les copies sont effectuées par transport administratif authentifié, sans
afficher les valeurs. Les préimages privées sont conservées ; aucun secret n'est
versionné. Les identités différentes selon les consommateurs restent distinctes.

Le refus initial provenait de l'offre gratuite du fournisseur OpenCode : HTTP403,
classe FreeTierError. Il ne démontrait pas une clé OpenAI invalide ou un crédit
épuisé. L'identité OpenAI existante a réussi une inférence réelle puis le parcours
complet, avec le modèle gpt-6-luna et le CLI natif. Aucun modèle local de remplacement
n'a été utilisé ; son service reste arrêté.

Les deux productions exécutent la même release humaine précédemment approuvée,
avec santé et processus réel vérifiés. Une configuration historique incompatible
avec le contrôle de santé a été corrigée avant la bascule officielle. Le contrôle
n'a pas été assoupli. Les consommateurs automatiques restent sur une seule
production : cet alignement ne réplique pas les données clientes ni les files.

Le laboratoire utilise les sources courantes et une instance n8n isolée, de même
version que l'installation observée en production. Trois vrais webhooks
authentifiés transportent les opérations moteur, notification et admission mail.
La passerelle n'autorise que ces opérations ; aucune file de production n'est
importée. La conservation des données d'exécution et l'exposition MCP sont coupées.

La recette finale passe **37 contrôles du parcours** et **58
contrôles dans Chromium**, avec 64 captures privées et
4 captures d'acceptation. Elle comprend 15 invocations
du CLI pour les rôles modèles, 16 notifications réellement reçues via Gmail et
40 opérations achevées par le transport n8n. Elle vérifie la liaison
mail, une pièce jointe réellement reçue, la concurrence portail/mail, le refus
des réponses tardives, le cadrage, deux versions privées, les clarifications,
la validation, la livraison de huit pages et le CMS PHP/SQLite fonctionnel.
Il ne reste ni travail actif ni notification de livraison non réglée.

Les **533 tests Python** passent également. TLS et sandbox Chromium restent
actifs. La livraison utilise une vraie cible SSH/HTTPS locale isolée : elle ne
certifie pas un hébergement externe ni l'activation des graphes de production.
Le courrier passe par le connecteur opérateur autorisé et une boîte de recette ;
il ne s'agit pas d'un poller Gmail de production installé dans le laboratoire.

## Orchestration et délégation

Codex réalise directement les copies bornées, les nouvelles recettes Ansible,
les vérifications, les corrections, l'intégration Git et la documentation. Aucun
sous-agent de collaboration et aucune session PIAgentControl ne sont lancés.
Les processus OpenCode dédiés exécutent les rôles de direction, génération et
revue visuelle ; chaque appel utilise une session fraîche et les outils sont
refusés. La revue reçoit les vraies captures, indépendamment du générateur.

Plusieurs essais ont échoué avant la réussite : reçu mail mal identifié,
adaptation de rendu insuffisante, budget hors contrat, débordement mobile,
puis régressions de mise en page pendant les corrections. Un autre essai a isolé
un besoin de contact insuffisamment spécifié ; le client fictif fournit ensuite
un canal d'exemple approuvé, plutôt que laisser le modèle inventer des coordonnées.
Les essais terminés restent séparés ; aucun ancien job n'est réarmé. Une limite
CLI à une seule étape produisait aussi un résumé au lieu du JSON ; elle est
retirée, avec outils toujours refusés et délai natif conservé. Ce comportement
de résumé est décrit dans la [documentation OpenCode](https://opencode.ai/docs/agents/#max-steps).
Le moteur génère du HTML/CSS natif, conserve les fichiers et corrections
antérieures lors des raffinements,
et dispose d'une correction bornée après un défaut de capture connu. Un timeout
ou résultat inconnu n'est pas rejoué. La revue distingue la maquette inerte du
CMS installé et testé à la livraison ; les observations optionnelles ne
remplacent pas les défauts bloquants. Aucun
verdict ni score n’est réécrit par l’adaptateur. Les seuils, la limite de revue et les
contrôles de publication/CMS demeurent inchangés. Aucune capture diagnostique
ne remplace une preuve officielle. Aucun coût ou gain chiffré n'est inventé.

## Coopération et adaptation au contexte

Les consignes applicables, la fiche de reprise, le protocole de coordination,
les annonces pertinentes et les références techniques ciblées sont consultés.
Le périmètre est annoncé puis étendu explicitement aux nouvelles recettes et
au transport de laboratoire. Le travail parallèle sur un autre environnement
reste préservé, comme les modifications utilisateur et les anciennes réserves
sur les rôles de migration et le contrôleur personnel.

Les faits observés ont conduit à réutiliser l'identité API existante, résoudre
le propriétaire système par son nom, préserver les identités propres aux
consommateurs, corriger la configuration de santé et conserver les types JSON
sur le vrai transport n8n. Le bootstrap initial est ensuite capturé et réappliqué
dans une recette autonome. Les sources exécutées sont comparées octet par octet
au commit intégré ; l'état initial modifié demeure indiqué dans les preuves.

Les preuves détaillées restent privées. Les copies d'audit lisibles excluent
les secrets et le raisonnement interne. Les deux références d'architecture et de
secrets sont actualisées ; le présent rapport est la seule publication du bilan,
après anonymisation et revue. Les réservations de cette mission sont libérées
par son annonce de fin, avec les versions, contrôles et limites effectivement
observés.
