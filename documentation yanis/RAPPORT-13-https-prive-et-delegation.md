<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.

# Rapport 13 — HTTPS privé, DNS-01 et délégation tracée

**11 octobre 2026.** Yanis autorise le passage à DNS-01, la fermeture du HTTPS
public, la mise à jour documentaire/Git et une modification ciblée d’AGENTS
pour renforcer la délégation. OpenVPN reste indépendant sur UDP1194. La VM
est éteinte ; aucun rôle Ansible existant testé ou appliqué.

## Résultat réseau

Caddy2.11.7 comprend désormais `dns.providers.duckdns`, épinglé au commit
`paramètre privé à consulter sur le Pi`, compilation Go1.26.9 ARM64 avec
archive vérifiée SHA256. Binaire candidat/actif SHA256 :
`paramètre privé à consulter sur le Pi`.
Les modules standard sont conservés. Sources publiques `OpenVPNDeploy/caddy-dns/`.

Le domaine seul est servi sur LANl'adresse configurée et VPNl'adresse configurée ; site IP public
session Brave explicitement autorisée, sans affichage, puis enregistré hors
Git et installé dans `paramètre privé à consulter sur le Pi`, root:root0600. Le drop-in
`private-https.conf` retire `--environ` du service afin de ne pas journaliser
ce secret. Il impose le filtre avant Caddy.

La table dédiée `inet paramètre privé à consulter sur le Pi` admet HTTPS depuis LAN/VPN/loopback
et bloque TCP/UDP443 autrement, en IPv4 et IPv6. Aucune règle Docker vidée.
Unité activée au démarrage ; arrêter son service ne retire pas la protection.
Installation transactionnelle avec fichiers privés de retour arrière dans
`paramètre privé à consulter sur le Pi`. Ne pas restaurer une ancienne
configuration publique sans décision explicite. Aucun redémarrage OpenVPN :
un essai ou état interne et activation du 11 octobre à02:33:33 CEST inchangés.

**Limite routeur :** UPnP ne liste que UDP1194 et Delete443 renvoie714. Freebox
OS a été ouvert dans Brave en mode invité. Yanis prend en charge lui-même
le retrait de la redirection statique443 ; aucune autre action routeur déléguée.
Cette suppression n’est pas annoncée comme faite. Le filtre du Pi bloque
déjà le parcours public, confirmé par la connexion TCP extérieure qui expire.

## Validations effectives

- Candidat Caddy : compilation, version et module confirmés ; validation avec
  token factice avant application. Filtre : `nft --check` avant application.
- DNS-01 réel : certificat ACME staging obtenu avant fermeture ; certificat
  ACME de production obtenu dans un stockage isolé après fermeture, sans
  aucun port web public. Le Caddy actif conserve/renouvelle son état TLS privé.
- LAN et listener VPN : HTTPS200 avec vérification TLS et nom correct.
- N0C extérieur : TCP443 du domaine et de l’IPl'adresse configurée expirent. Le test
  IPv6 renvoie errno101 (absence de route N0C), **pas** une preuve de blocage
  IPv6 extérieur. Aucun listener Caddy IPv6 ; filtre inet actif.
- VPN UDP1194, n8n et bridge actifs. La sauvegarde cohérente a temporairement
  arrêté n8n/Caddy puis restauré leur état ; elle n’a pas arrêté OpenVPN.
- Reprise : cinq tests existants et quatre nouveaux tests isolés réussis ;
  revue indépendante et vérification réelle de l’archive décrites ci-dessous.
  Aucun site N0C construit, aucun workflow réel lancé pour tester cette mission.

La connexion UDP d’un vrai client extérieur, un redémarrage complet du Pi et
une reconstruction complète sur cible jetable restent à confirmer. Un curl
depuis le Pi vers son listener VPN n’est pas un test du client d’Ilyes.

## Délégation — sessions, missions et preuves

Codex a lu `PIAgentControl/AGENTS.md` et `opencode.json` avant lancement, fourni
un contexte autonome et des chemins absolus. Modèle observé dans les messages
des huit sessions : **gpt-6-luna**. Aucun agent n’a reçu le jeton DuckDNS, les
clés ou un mot de passe dans son prompt. Les missions de code ont conservé
leurs modifications existantes et n’avaient pas le droit d’appliquer un
service, restaurer la production, lancer Ansible, construire N0C ou publier Git.

| Session | Rôle et attribution |
| --- | --- |
| `paramètre privé à consulter sur le Pi` | Planificateur : cadrage, délégation, retours Codex, corrections et revues. |
| `paramètre privé à consulter sur le Pi` | Implementeur : collecte/restauration DNS-01, permissions et binaire. |
| `paramètre privé à consulter sur le Pi` | Implementeur : corriger chemin du drop-in, composants conditionnels et remplacement Caddy. |
| `paramètre privé à consulter sur le Pi` | Implementeur : traiter les constats de cette revue. |
| `paramètre privé à consulter sur le Pi` | Revue : vérifier ces corrections sans exécuter de test. |
| `paramètre privé à consulter sur le Pi` | Implementeur : SHA256 stock officiel, quatre tests et documentation. |
| `paramètre privé à consulter sur le Pi` | Revue finale : hash, conditions de remplacement, tests et limites ; aucun problème bloquant relevé. |

Trois lancements CLI ont bloqué à l’initialisation sans session de mission
créée. Le parcours fonctionnel a utilisé un serveur temporaire loopback4097,
protégé par un mot de passe aléatoire en mémoire, puis un client attaché. Les
retours Codex ont été mis en file dans le parent via API locale authentifiée.
Après `/session/status` vide, le client resté en attente de fin de flux a été
arrêté ; son lanceur a terminé le serveur. Le code de sortie-15 du client ne
prouve pas les résultats : fichiers, sessions complétées, tests et revues les
établissent. Aucun serveur temporaire laissé actif.

**Constats et corrections :** Codex a trouvé un mauvais chemin de drop-in et
des nouveaux composants rendus obligatoires hors DNS-01 ; corrigés. Le premier
refus de remplacement Caddy empêchait la reprise après `deploy.sh --no-start` ;
une option explicite est désormais requise. La revue a relevé qu’ELF natif et
confirmation seuls ne prouvaient pas le stock : SHA256 officiels arm64/amd64
ajoutés, sans exécuter le binaire. La proposition de réduire le répertoire
`caddy.service.d` n’a pas été retenue : les drop-ins n8n/VPN sont nécessaires
dans l’archive privée chiffrée. La décision est documentée.

restore-extra.py,test_private_https.py,README.md}` et documents publics
`OpenVPNDeploy/caddy-dns/{README.md,delegation.md}`. Les revues ont lu le code et
les preuves ; elles n’ont exécuté aucune commande. Codex a reproduit les neuf
tests. `delegation.md` et `delegation-metadata.json` détaillent les métriques.
Le coût enregistré par OpenCode est une estimation logicielle, pas une facture
vérifiée ; aucune économie automatique ni gratuité des agents n’est affirmée.

**Travail direct Codex :** transport privé du token, tests ACME réels,
installateur transactionnel et application, probe public, collecte/chiffrement
et vérification privée, extension du vérificateur et `verify-sealed.py`,
intégration des documents/PDF, protection AGENTS, revue des diffs, commit/push.
Ces opérations sont conservées directement pour protéger les secrets,
coordonner les services et assumer la validation finale.

## Reprise et sauvegarde hors Pi

Le helper a produit `snapshot-paramètre privé à consulter sur le Pi-215238.s8on14`, avec SQLite intègre et
retour des services. La collecte complémentaire inclut conditionnellement le
anciennes archives restent compatibles ; la restauration sur cible neuve
exige architecture native, services arrêtés et confirmation explicite avant
remplacement du Caddy stock dont le SHA256 officiel est contrôlé.

La vérification réelle de la première archive a détecté un doublon du drop-in,
malgré les neuf tests et la revue finale. Cette archive a été refusée. Codex a
corrigé les racines imbriquées de collecte et remplacé le test synthétique par
un appel au vrai collecteur, vérifiant explicitement l'absence de doublons.
Les cinq tests existants et quatre tests HTTPS passent après cette correction.

Ciphertext distinct `project-private-dns01.enc` dans le coffre Windows privé
existante qui n’a jamais quitté Windows. L’ancienne archive est conservée.
Le vérificateur `verify-sealed.py` authentifie l’archive puis vérifie les
sommes/SQLite/composants DNS, sans créer d’archive déchiffrée nommée ; son
espace temporaire reste sous le coffre privé. SHA256 et rapport de vérification
sont enregistrés à côté du ciphertext. Voir le manifeste pour les résultats
et ne pas confondre intégrité avec restauration complète testée.

Les copies temporaires Windows de la mission précédente restent à nettoyer
manuellement comme demandé au rapport11 : leur suppression automatique avait
été refusée. Aucun contournement de ce refus effectué pour cette mission.

## Documents, Git et protection AGENTS

Outils de reprise et manifeste public publiés sur `main`, commit
`paramètre privé à consulter sur le Pi`. Le contexte Windows, les sources
Caddy et ce rapport sont publiés sur `project-context` du même dépôt privé.

Architecture Markdown/PDF, Mermaid, plan, README n8n/OpenVPN, REPRISE, sources
et passation actualisés. Les anciens rapports conservent leurs faits datés.
Les README main/Ansible signalent le nouveau mode sans modifier les rôles
réservés à Yanis. Les exports de workflows restent en Git et n’ont pas changé.

AGENTS a reçu seulement les paragraphes demandés sur délégation par défaut,
traçabilité des rapports et nouveau gel après exception autorisée. Nouvelle
empreinte : `paramètre privé à consulter sur le Pi`.
Protection rétablie ; ouverture en écriture refusée, lecture et empreinte
possibles, hook actualisé. Le helper applique uniquement la DACL protégée,
sans privilège de SACL ni ajout de Synchronize au refus d’écriture. Les ACL
restent un blocage ordinaire, pas une isolation contre un administrateur.

## Preuve finale de sauvegarde
