# Documentation détaillée de l'infrastructure — 22 octobre 2026

## Demande et résultat

La demande humaine est de rendre l'architecture cohérente avec l'infrastructure
finale et assez détaillée pour comprendre son exploitation. Ce travail concerne
la documentation ; il n'ajoute aucun service, site ou accès réseau.

La vue courante décrit le Pi passerelle, la production distante, la VM lab
distincte et les quatre LXC génériques. Elle explique DNS, VPN, Nginx, certificats
et renouvellement indépendant, services, stockages, bases selon la technologie,
parcours WordPress réel, versions de source et installations, sauvegardes et
diagnostic. Quatre schémas Mermaid et des tables rendent les flux et autorités
comparables sans publier de coordonnées.

La [vue du 22 octobre](ARCHITECTURE.md#état-courant-au-22-octobre-2026)
remplace la référence courante du 21. L'historique et ses états datés sont
conservés sans modification. Le
[rapport d'implémentation publié](RAPPORT-LXC-NGINX-WORDPRESS-20261022.md)
est préservé : ses tests restent des preuves antérieures, sans être présentés
comme exécutés à nouveau pour ce document.

Les distinctions devenues nécessaires sont explicites : applications sur le
serveur de production, interfaces héritées du Pi, HTTPS lab séparé, Caddy arrêté
seulement sur le Pi, cibles génériques et base à la demande. La livraison
WordPress a utilisé un adaptateur de lab fixé à une cible. La confirmation
technologique est dans le brief existant, pas dans un routeur générique déjà
déployé. L'UI durable consulte le résultat ; elle n'est pas un atelier permanent
avec builder, messagerie et nouvelle API de reprise configurés.

Les audits ont aussi précisé les limites : règles agents candidates non
attestées installées dans les bases actives, absence de restauration complète
WordPress et de reboot machine, lien de reset remis mais formulaire non exercé,
et helper du secours VPN consommant encore un ancien certificat Caddy.
Ce dernier point concerne la préparation du secours ; le TLS du frontal actif
reste vérifié. Aucun correctif opérationnel n'est effectué ici.

Les contrôles propres à la rédaction sont statiques : références, diff, liens
locaux, structure des diagrammes, anonymisation du texte ajouté et empreintes
des parties préservées. Aucun nouveau test réel de service, workflow, CMS,
modèle ou installation n'a été exécuté.

## Orchestration et délégation

L'orchestrateur a confié la documentation publique à un agent, l'audit réseau
à un deuxième et celui du parcours WordPress à un troisième. Les retours
en lecture seule ont précisé les trajets HTTPS, les états des services, les
capacités réellement qualifiées et les limites de reprise.

L'agent documentaire intervient uniquement dans l'architecture, ce nouveau
rapport et leur navigation au sommaire. Il a relu les consignes, la fiche
commune, le protocole, l'état partagé, les annonces pertinentes et les
références publiées. Il n'a lancé aucun agent supplémentaire ni prompt OpenCode
ou appel fournisseur pour cette rédaction.

L'orchestrateur a consolidé l'architecture privée : schéma opérationnel,
inventaire des fichiers et consommateurs, réseau, versions, données et reprise.
Il a corrigé les tableaux ambigus et les renvois Windows, synchronisé la fiche
de reprise Windows/serveur/public et ajouté un point courant à l'état partagé.
Les anciens blocs de cet état restent conservés ; aucune permission n'a changé.
Il a aussi fait actualiser deux README de recettes dont les mentions de
préparation réseau et de blocage OAuth étaient dépassées. Ces responsabilités
restent distinctes des trois fichiers remis par l'agent documentaire.

Les modèles exacts de rédaction et d'audit ne sont pas déduits des fichiers
consultés. Aucun coût ou gain n'est inventé. Les candidats remis ont été relus
par l'orchestrateur, avec une revue croisée WordPress, puis intégrés dans des
commits documentaires ciblés. Les publications et HEAD distants sont vérifiés,
sans changement de version applicative exécutée ni nouvelle recette modèle.

## Coopération et adaptation au contexte

La vue antérieure était encore ouverte sur un incident daté du 21 octobre
et des limites Gmail historiques. Le rapport d'implémentation publié apporte
les faits ultérieurs : Nginx sur le Pi, LXC créés, WordPress et base à la demande,
adoption avec échecs conservés, remise propriétaire et interface lab durable.
Ces références ont remplacé les affirmations devenues ambiguës.

La coordination a confirmé que le lab possède une entrée HTTPS propre et que
les règles agents en source ne prouvent pas leur installation. L'audit réseau
a identifié la dépendance résiduelle du secours au certificat Caddy ; l'audit
WordPress a séparé stockage de preuves et archive restaurable du CMS. Ces
retours ont été intégrés comme limites précises, sans élargir la mission.

Une intention a réservé les trois fichiers avant édition dans le périmètre
documentaire du parent. L'historique, le rapport d'implémentation et les travaux
concurrents sont conservés. Les fiches de reprise synchronisées par le parent
n'ont pas été absorbées par cette réservation.

Les schémas et explications emploient des rôles génériques. Aucun nom de
connexion, adresse, URL opérationnelle, identité client, contact, chemin privé,
identifiant interne ou valeur secrète n'est ajouté. Les consignes et réponses
lisibles restent des copies d'audit privées, distinctes des textes natifs chiffrés.

La fin de l'intervention transmet les trois fichiers au parent et libère leur
réservation. Aucun commit ou push n'est fait par l'agent documentaire.
Aucun accès Kali ou lancement depuis PIAgentControl n'a eu lieu.
