# Catalogue Python — backend

Référence applicative : `4162a4fcd18ebf9f948d60cadc36ded52394b43f`. Référence distincte du pipeline de staging : `4165993e12b987590213b6a1e4c0e52ad0e2d51f`. Extraction intégrale depuis les objets Git, incluant fonctions imbriquées, méthodes et tests. Les noms de paramètres et les sorties sont relevés statiquement : les appels listés ne constituent pas des traces d’exécution. Les défauts littéraux ne sont pas reproduits.


Chaque ligne indique le nom qualifié, les entrées, la forme des sorties, les appels directs et les exceptions explicites. Le lien pointe à la ligne exacte du fichier versionné. Une sortie « implicite None » signifie absence de return explicite ; les effets sont décrits par les appels, sans prétendre exécuter le programme.

| Programme | Rôle | Statut | Fonctions |
| --- | --- | --- | --- |
| [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py) | Régression automatisée du composant nommé | Test ; non exécuté par la simple présence du fichier | 4 |
| [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py) | Régression automatisée du composant nommé | Test ; non exécuté par la simple présence du fichier | 4 |
| [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/run_native_shipping_acceptance.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/run_native_shipping_acceptance.py) | Régression automatisée du composant nommé | Test ; non exécuté par la simple présence du fichier | 1 |

## [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py)

Régression automatisée du composant nommé. Test ; non exécuté par la simple présence du fichier.

Imports déclarés : `argparse, json, os, secrets, time, urllib.request, uuid`, `http.cookies`, `pathlib`.

| Fonction / ligne | Entrées | Sorties relevées | Traitement et dépendances directes |
| --- | --- | --- | --- |
| `main` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py#L6](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py#L6) | aucun paramètre | None | Appels : `RuntimeError`, `SimpleCookie`, `argparse.ArgumentParser`, `args.state.exists`, `args.state.read_bytes`, `json.dumps`, `json.loads`, `os.umask`, `p.add_argument`, `p.parse_args`, `parsed.load`, `print`, `request`, `save`, `secrets.token_urlsafe`, `uuid.uuid4`, `wait` ; exceptions : résultat de RuntimeError |
| `main.save` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py#L10](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py#L10) | aucun paramètre | implicite None | Appels : `args.state.chmod`, `args.state.write_text`, `json.dumps` |
| `main.request` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py#L11](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py#L11) | path, body | tuple (résultat de json.load, response.headers) | Appels : `json.dumps`, `json.dumps().encode`, `json.load`, `urllib.request.Request`, `urllib.request.urlopen` |
| `main.wait` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py#L21](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/final_acceptance.py#L21) | expected | value | Appels : `RuntimeError`, `json.dumps`, `print`, `range`, `request`, `str`, `time.sleep`, `value.get` ; exceptions : résultat de RuntimeError |

## [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py)

Régression automatisée du composant nommé. Test ; non exécuté par la simple présence du fichier.

Imports déclarés : `PIL`, `argparse, base64, hashlib, io, json, os, secrets, time, urllib.error, urllib.request, uuid`, `http.cookies`, `pathlib`.

| Fonction / ligne | Entrées | Sorties relevées | Traitement et dépendances directes |
| --- | --- | --- | --- |
| `main` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py#L10](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py#L10) | aucun paramètre | None | Appels : `Constant.encode`, `Constant.join`, `Image.new`, `ImageDraw.Draw`, `JoinedStr.encode`, `RuntimeError`, `SimpleCookie`, `any`, `argparse.ArgumentParser`, `args.state.exists`, `args.state.read_bytes`, `base64.b64encode`, `base64.b64encode().decode`, `draw.ellipse`, `draw.line`, `draw.text`, `enumerate`, `hashlib.sha256`, `hashlib.sha256().hexdigest`, `image.save`, `io.BytesIO`, `json.dumps`, `json.loads`, `len`, `next`, `objects.append`, `offsets.append`, `os.umask`, `out.getvalue`, `parsed.load`, `parser.add_argument`, `parser.parse_args`, `print`, `request`, `response.read`, `save`, `secrets.token_urlsafe`, `str`, `str().encode`, `urllib.request.Request`, `urllib.request.urlopen`, `uuid.uuid4`, `wait` ; exceptions : résultat de RuntimeError |
| `main.save` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py#L14](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py#L14) | aucun paramètre | implicite None | Appels : `args.state.write_text`, `json.dumps`, `os.chmod` |
| `main.request` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py#L17](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py#L17) | path, body | tuple (résultat de json.loads, response.headers) | Appels : `json.dumps`, `json.dumps().encode`, `json.loads`, `response.read`, `urllib.request.Request`, `urllib.request.urlopen` |
| `main.wait` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py#L27](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/lab_acceptance.py#L27) | aucun paramètre | value | Appels : `RuntimeError`, `json.dumps`, `print`, `request`, `round`, `str`, `time.monotonic`, `time.sleep`, `value.get` ; exceptions : résultat de RuntimeError |

## [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/run_native_shipping_acceptance.py](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/run_native_shipping_acceptance.py)

Régression automatisée du composant nommé. Test ; non exécuté par la simple présence du fichier.

Imports déclarés : `argparse, hashlib, json, re, shlex, subprocess`, `pathlib`.

| Fonction / ligne | Entrées | Sorties relevées | Traitement et dépendances directes |
| --- | --- | --- | --- |
| `root` · [https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/run_native_shipping_acceptance.py#L8](https://github.com/yanisAitlamine/atelier-unifie/blob/4162a4fcd18ebf9f948d60cadc36ded52394b43f/backend/tests/run_native_shipping_acceptance.py#L8) | command, timeout | result.stdout | Appels : `RuntimeError`, `subprocess.run` ; exceptions : résultat de RuntimeError |
