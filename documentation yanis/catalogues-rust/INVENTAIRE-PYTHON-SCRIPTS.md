# Catalogue Python — scripts

Référence applicative : `4162a4fcd18ebf9f948d60cadc36ded52394b43f`. Référence distincte du pipeline de staging : `4165993e12b987590213b6a1e4c0e52ad0e2d51f`. Extraction intégrale depuis les objets Git, incluant fonctions imbriquées, méthodes et tests. Les noms de paramètres et les sorties sont relevés statiquement : les appels listés ne constituent pas des traces d’exécution. Les défauts littéraux ne sont pas reproduits.


Chaque ligne indique le nom qualifié, les entrées, la forme des sorties, les appels directs et les exceptions explicites. Le lien pointe à la ligne exacte du fichier versionné. Une sortie « implicite None » signifie absence de return explicite ; les effets sont décrits par les appels, sans prétendre exécuter le programme.

| Programme | Rôle | Statut | Fonctions |
| --- | --- | --- | --- |
| [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py) | Outil ou module de scripts | Construction, administration ou recette ; lancement explicite | 2 |
| [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/check.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/check.py) | Outil ou module de scripts | Construction, administration ou recette ; lancement explicite | 0 |
| [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/package.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/package.py) | Outil ou module de scripts | Construction, administration ou recette ; lancement explicite | 0 |
| [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/verify_import.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/verify_import.py) | Outil ou module de scripts | Construction, administration ou recette ; lancement explicite | 0 |

## [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py)

Outil ou module de scripts. Construction, administration ou recette ; lancement explicite.

Imports déclarés : `argparse, hashlib, json, os, shutil, subprocess, sys, time`, `pathlib`.

| Fonction / ligne | Entrées | Sorties relevées | Traitement et dépendances directes |
| --- | --- | --- | --- |
| `output` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py#L9](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py#L9) | argv | résultat de subprocess.check_output().strip | Appels : `subprocess.check_output`, `subprocess.check_output().strip` |
| `run` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py#L16](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/build.py#L16) | argv, folder | implicite None | Appels : `json.dumps`, `print`, `str`, `subprocess.run` |

## [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/check.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/check.py)

Outil ou module de scripts. Construction, administration ou recette ; lancement explicite.

Imports déclarés : `argparse, json, os, re, subprocess, sys, time`, `pathlib`.

Programme exécuté au niveau du module ; aucune fonction déclarée.

## [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/package.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/package.py)

Outil ou module de scripts. Construction, administration ou recette ; lancement explicite.

Imports déclarés : `argparse, subprocess, sys`, `pathlib`.

Programme exécuté au niveau du module ; aucune fonction déclarée.

## [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/verify_import.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/scripts/verify_import.py)

Outil ou module de scripts. Construction, administration ou recette ; lancement explicite.

Imports déclarés : `hashlib, json`, `pathlib`.

Programme exécuté au niveau du module ; aucune fonction déclarée.
