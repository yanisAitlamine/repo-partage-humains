<!-- BEGIN RUST-DOCUMENTATION-20261030 -->
> **Document historique.** Les faits et résultats ci-dessous restent ceux de leur date. La référence courante du projet Rust est [https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md](https://github.com/yanisAitlamine/repo-partage-humains/blob/main/documentation%20yanis/SOMMAIRE-PUBLIC.md).
<!-- END RUST-DOCUMENTATION-20261030 -->

> Version publique anonymisée ; détails d’exploitation réservés au Pi.


rendre le domaine n8n accessible depuis Windows sur le réseau privé, sans devoir
activer le VPN. L'inventaire  est complété et publié :
L'historique Git publié a été conservé sans push forcé lors de cette reprise.

## Diagnostic confirmé

Windows Wi-Fi : `paramètre privé à consulter sur le Pi`, DNS Freebox IPv4 `paramètre privé à consulter sur le Pi` et IPv6
`paramètre privé à consulter sur le Pi`. La Freebox renvoie `paramètre privé à consulter sur le Pi` pour
`paramètre privé à consulter sur le Pi`. Ce chemin atteint le port public désormais bloqué.
Le test Windows HTTPS avec résolution forcée vers `paramètre privé à consulter sur le Pi` répond200,
avec certificat vérifié : le service est accessible sur le LAN.

Le DNS du Pi écoute uniquement `paramètre privé à consulter sur le Pi:53`, via `n8n-vpn-dns.service`.
Il renvoie l'adresse VPN pour le domaine n8n. Sa configuration et le processus
OpenVPN un essai ou état interne doivent rester inchangés pendant cette mission.

## Choix de réalisation

Un résolveur LAN distinct utilise la même installation dnsmasq, avec un nom
exact pointant vers `paramètre privé à consulter sur le Pi`. Écoute IPv4 LAN seulement ; filtrage UDP/TCP53
depuis le réseau local. Le résolveur VPN conserve son adresse et ses réponses.
Sources : `Technique/sources/OpenVPNDeploy/lan-dns/`, copie du candidat Pi.

Windows utilise une règle NRPT limitée à ce domaine, avec les DNS privés LAN et
VPN. Les DNS généraux IPv4/IPv6 de l'interface restent inchangés. Le script
`Technique/outils/configurer-dns-prive-windows.ps1` préserve les autres règles,
sauvegarde l'état local, contrôle la résolution et permet un retour arrière
avec `-Restore`. L'application exige les droits administrateur Windows.

Références primaires : [règles DNS Windows](https://learn.microsoft.com/en-us/powershell/module/dnsclient/add-dnsclientnrptrule),
manuel dnsmasq (référence d’exploitation retirée).

## Délégation et revue

L'agent Codex `lan_dns_opencode`, modèle configuré GPT-6 Luna, pilote la mission
OpenCode sur le Pi depuis PIAgentControl. OpenCode doit utiliser planificateur,
implementeur puis revue. Périmètre : nouvelles sources DNS LAN et collecte/
restauration optionnelle dans n8n-services. Autorisation de contrôles des candidats,
sans application, publication Git ni redémarrage des services de production.
Aucun secret dans les prompts. Aucun rôle Ansible exécuté ou testé.

Windows/LAN, le script Windows, la revue des candidats, l'application autorisée,
les tests réels, la documentation et Git. Aucune économie de tokens inventée.

Constats transmis avant installation : caractère Markdown parasite dans une
configuration ; filtre global DNS qui bloquerait le VPN ; interface dnsmasq
trop large pouvant écouter IPv6 ; correspondance de domaine trop large ; besoin
de rechargement nft atomique ; retour arrière incomplet des modes, unités et règles.
La collecte doit aussi refuser une installation LAN partielle ou liée, tout en
acceptant les anciennes installations sans composants LAN.

## Validation finale

Codex a ajouté `pid-file=` pour préserver le fichier PID du DNS VPN, reproduit
statiques de l'installateur : **19 tests passent**. `dnsmasq --test` et `nft --check`
avec les droits requis passent. Les simulations et lectures statiques de rollback
ne sont pas un essai de panne sur la production.

Installation effective : sauvegarde root0700
`paramètre privé à consulter sur le Pi` (nom horodaté UTC).
Unités LAN actives et activées au démarrage. DNS LAN UDP/TCP testé depuis Windows :
`paramètre privé à consulter sur le Pi`. DNS VPN testé séparément depuis le Pi : `paramètre privé à consulter sur le Pi`.
Les DNS ne présentent aucune écoute IPv6. PID DNS VPN28580 et un essai ou état interne
inchangés, fichier `paramètre privé à consulter sur le Pi` conservé. Caddy reste actif.

**Windows :** règle NRPT appliquée après acceptation de l'élévation par Yanis,
le 12 octobre à 01:09. Résolution système vers `paramètre privé à consulter sur le Pi`, HTTPS200 sans
résolution forcée, puis page Assistant n8n effectivement chargée dans Brave.
Les DNS Freebox généraux restent inchangés.

La première demande d'élévation a ensuite été annulée par Windows
(`L'opération a été annulée par l'utilisateur`). Aucun script élevé n'a été
exécuté lors de cette première tentative. Les contrôles LAN UDP/TCP et HTTPS200
ont été reconfirmés après cette annulation. Yanis a demandé de relancer,
puis la deuxième élévation a réussi. Pour réappliquer manuellement, ouvrir PowerShell **en administrateur**,
se placer dans le dossier du projet, puis exécuter :

```powershell
& '.\Technique\outils\configurer-dns-prive-windows.ps1'
```

Le résultat local est conservé dans
`Technique/prive/dns-prive-windows-result.json`, hors Git. Le résultat actuel
indique `configured`, résolution `paramètre privé à consulter sur le Pi`. L'accès Brave a été vérifié
après rechargement, sans soumission de formulaire ni modification n8n.

Le DHCP de la Freebox n'est pas modifié. Les autres appareils LAN peuvent utiliser
le résolveur Pi, mais ne le sélectionnent pas automatiquement. Aucun DNS public
n'est ouvert. Le nouvel état DNS LAN n'est pas contenu dans le coffre privé du
11 octobre : les sources d'installation et les nouveaux chemins de récupération
sont conservés dans Git pour les prochaines sauvegardes/reprises.

## Sessions et limites de délégation

| Session OpenCode | Rôle |
| --- | --- |
| `paramètre privé à consulter sur le Pi` | Planificateur, attribution et traitement des retours Codex. |
| `paramètre privé à consulter sur le Pi` | Implémentation initiale DNS LAN. |
| `paramètre privé à consulter sur le Pi` | Récupération et rollback. |
| `paramètre privé à consulter sur le Pi` | Corrections d'implémentation. |
| `paramètre privé à consulter sur le Pi` | Corrections supplémentaires. |
| `paramètre privé à consulter sur le Pi` | Revue indépendante. |
| `paramètre privé à consulter sur le Pi` | Revue de correction. |
| `paramètre privé à consulter sur le Pi` | Revue de correction. |

Modèles configurés : GPT-6 Luna. Le lancement CLI attaché n'avait créé aucune
session ; après vérification, le lancement effectif a utilisé l'API locale
authentifiée, sans publier son mot de passe. Une dernière correction étroite
du rollback d'installation neuve a été faite directement par l'agent Codex
après la revue OpenCode : arrêter un service créé avant de retirer son unité.
Les contrôles statiques ont été relancés et la revue finale appartient à Codex
principal. Aucun coût fiable relevé ; aucun coût ou économie inventé.

Compte rendu de hand-off : `Technique/documentation/delegation-dns-lan.md`.
Les fichiers d'intégration OpenCode d'une autre mission ont été préservés ;
seuls les chemins recovery de cette mission sont ajoutés à sa publication Git.
