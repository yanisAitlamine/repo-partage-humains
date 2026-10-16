# Cible de recette fournie par le client — 16 octobre 2026

## Demande et résultat

La demande portait sur deux nouveaux sous-domaines de recette, la suppression
de la destination de test imposée dans les règles des agents, et un essai réel
du parcours mail pour chaque destination.

Les deux sous-domaines sont créés dans des dossiers distincts. Pour chacun,
HTTPS fonctionne avec un certificat vérifié et le contenu servi correspond
exactement à l’index du dossier distant. Le registre opérateur autorise les
deux associations ; sa consultation depuis le client technique du workflow
renvoie la correspondance attendue.

Le mail doit désormais contenir une ligne explicite :

```text
Sous-domaine cible : domaine-test.example.com
```

Une seule destination est admise. Le serveur retrouve ensuite les accès et
la racine dans son registre autorisé. Le mail ne donne aucun droit de choisir
un alias SSH ou un chemin. La même cible est conservée dans le job, les images,
les preuves, la revue et la livraison. Une cible absente, ambiguë ou inconnue
bloque la construction. Les confirmations humaines restent requises.

La règle est ajoutée à 23 fichiers de consignes et modèles actifs du projet,
répartis entre le poste de travail et le serveur. Les archives historiques et
dépendances ne sont pas réécrites. La protection du fichier global est rétablie.
Les sources du contrôle d’hébergement et de l’intégration sont committées et
poussées ; les modifications sans rapport déjà présentes sont conservées.
Les changements de brouillon préexistants restent non publiés.

Les deux scénarios mail utilisent des briefs fictifs distincts. Chaque scénario
comprend un premier mail et deux réponses aux questions reçues : six traitements
réels ont terminé et envoyé leur réponse commerciale. Les deux scénarios
restent toutefois en clarification : le décideur demande des informations déjà
présentes, puis refuse de préparer le prompt de construction. Aucun constructeur
n’a été lancé et aucune maquette ni livraison de site n’est attestée. Le choix
de corriger ce problème d’analyse a été présenté à l’humain ; aucun seuil n’a
été abaissé pour faire passer les essais.

Contrôles effectués :

- 26 tests Python ciblant les cibles, les images et les preuves : réussis ;
- 34 tests de validation des notifications : réussis ;
- 8 tests JavaScript du contrat et de la revue visuelle : réussis ;
- suite Python générale : 97 tests, avec les deux échecs et l’erreur déjà
  observés dans la référence initiale de 89 tests ; aucun nouvel échec ;
- validation n8n des modifications : aucun nouvel avertissement ;
- accès HTTPS, identité des deux racines et consultation réelle du registre :
  vérifiés.

Le composant de notification arrêté conserve son état. Son adaptation est
préparée et testée dans les sources ; sa copie installée n’a pas été remplacée.
Aucun ancien rôle Ansible n’a été testé ou appliqué. Aucun service n’a été
redémarré pour cette mission.

## Orchestration et délégation

Codex a effectué directement la création des domaines, les modifications et
les contrôles. Aucun sous-agent Codex ni session OpenCode n’a été lancé.
Les traitements d’analyse habituels des workflows ont été exécutés par les
mails de test ; leurs modèles ne sont pas inventoriés dans ce compte rendu.
Le blocage commercial a empêché toute délégation au constructeur d’hébergement.
Aucun coût ou gain de tokens n’est avancé.

## Coopération et adaptation au contexte

Les consignes, la fiche de reprise, la passation et les sections techniques
pertinentes ont été consultées. Une intention a précédé les mutations, puis
une extension a détaillé les copies de consignes concernées. Les annonces
de développement du prototype et de diagnostic du constructeur ont été lues ;
leurs fichiers réservés sont restés hors du périmètre de code de cette mission.

Les sources et les tests ont été préparés dans une copie isolée et comparés
à leurs préimages avant installation. L’état de référence a permis de distinguer
les échecs de tests antérieurs des régressions introduites et corrigées pendant
le travail. Les brouillons non publiés et les modifications concurrentes ont été
conservés. Les références précises, versions, préimages et résultats techniques
restent dans la passation privée. La fin de mission libère les réservations
de cette phase ; la correction du décideur constitue la suite à trancher.
