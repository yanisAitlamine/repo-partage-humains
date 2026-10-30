# Installation, maintenance et retour à la version précédente

## Préparer une version

Utiliser une copie propre du dépôt à la révision choisie, la chaîne de compilation documentée et les dépendances verrouillées. Construire le serveur Rust et le portail, exécuter les contrôles locaux communs puis sceller le paquet et son manifeste. Les scripts refusent une source, un binaire ou une interface qui ne correspondent pas aux preuves de construction.

[https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py) ; [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/check.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/check.py) ; [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/package.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/package.py).

## Lab permanent

Le lanceur sépare les phases : prérequis, inspection, préparation des droits, construction, plan Terraform, création, épinglage de la clé d’hôte, installation Ansible et vérification. Les anciennes phases de retrait ne doivent pas servir de raccourci pour réinitialiser le lab actuel. Les plans de destruction sont liés à une identité et à une empreinte précises ; toute opération effaçant les projets exige sa propre instruction humaine.

Une installation neuve reçoit un système minimal, un seul dépôt, une release et les données initiales. La configuration privée fournit adresses, comptes, clés, certificats et autorisations. Terraform gère les ressources ; Ansible configure le système, les services et les modèles. Une lecture ou un mode sans modification ne certifie pas une installation exécutée.

Une mise à jour conserve les bases et autorisations. Le contrôleur vérifie les travaux en attente, actifs ou incertains, prend un verrou, exporte une préimage privée puis remplace la version. La vérification précède le retrait de l’ancienne copie. Une erreur provoque la restauration de la préimage ; un retour explicite conserve les données applicatives actuelles.

Une mise à jour limitée au bridge peut réutiliser les binaires si les arbres source et les dépendances compilés sont identiques. La preuve de compilation d’origine reste intacte ; une preuve supplémentaire relie la nouvelle version du bridge aux composants réutilisés. La version étudiée a utilisé cette procédure.

[https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/infra/lab/README.md](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/infra/lab/README.md) ; [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/infra/lab/scripts/run.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/infra/lab/scripts/run.py).

## Staging temporaire

La capture compare les octets réellement installés à ceux du paquet. Une VM neuve reçoit ce logiciel exact et des bases vides. Playwright réalise l’inscription puis les scénarios du catalogue, avec alternance entre deux conteneurs admis. Les paramètres opérateur, secrets référencés, certificats, états Terraform et preuves restent privés.

Les actions `validate` et `list` inspectent la préparation. L’action `run` crée et configure la VM, exécute les parcours et publications, collecte les preuves puis détruit la VM. Les actions `status` et `cleanup` permettent de lire l’état et de reprendre uniquement la clôture. Une clôture incomplète conserve l’étape bloquée ; elle ne rejoue pas les messages ou publications.

Les règles réseau et permissions temporaires sont identifiées par campagne, avec préimage et reçu. Leur retrait préserve les changements concurrents. Le profil d’authentification renouvelé est conservé avant destruction. Les preuves sont exportées et leurs empreintes comparées avant retrait des données de recette.

[https://github.com/yanisAitlamine/atelier-unifie/blob/4165993e12b987590213b6a1e4c0e52ad0e2d51f/infra/staging/README.md](https://github.com/yanisAitlamine/atelier-unifie/blob/4165993e12b987590213b6a1e4c0e52ad0e2d51f/infra/staging/README.md) ; [https://github.com/yanisAitlamine/atelier-unifie/blob/4165993e12b987590213b6a1e4c0e52ad0e2d51f/infra/staging/scripts/run.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4165993e12b987590213b6a1e4c0e52ad0e2d51f/infra/staging/scripts/run.py).

## Distinguer les formats de paquet

Le paquet du lab permanent est scellé par [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/infra/lab/ansible/roles/build/files/seal_release.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/infra/lab/ansible/roles/build/files/seal_release.py) et installé par [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/infra/lab/ansible/roles/application/files/install.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/infra/lab/ansible/roles/application/files/install.py). Le lanceur [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/package.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/package.py) appelle un ancien préparateur du staging : son archive intermédiaire et le paquet installé ne sont pas des formats interchangeables. Pour la reconstruction actuelle, suivre le lanceur du lab et son manifeste attendu.
