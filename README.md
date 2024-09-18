# Profils QGIS liés aux articles Geotribu

Cet entrepôt contient des profils QGIS et un scénario de déploiement compatible [QGIS Deployment Toolbelt](https://guts.github.io/qgis-deployment-cli/).

----

## Déployer les profils

### Prérequis

- QGIS Deployment Toolbelt (aka QDT) >= 0.34 (voir [la page installation](https://guts.github.io/qgis-deployment-cli/usage/installation.html))
- connexion réseau autorisée sur :
  - github.com
  - plugins.qgis.org

### Exécuter

#### Avec QDT installée sous forme de paquet Python (avec pip)

```sh
qdt -s https://raw.githubusercontent.com/geotribu/profils-qgis/main/qdt/scenario.qdt.yml
```

#### Avec QDT téléchargée sous forme d'exécutable autoporteur (sans installation préalable requise)

Sur Linux :

```sh
chmod +x qdt.bin
./qdt.bin -s https://raw.githubusercontent.com/geotribu/profils-qgis/main/qdt/scenario.qdt.yml
```

Sur Windows :

1. Renommer l'exécutable en `qdt.exe`
1. Exécuter :

  ```powershell
  ./qdt.exe -s https://raw.githubusercontent.com/geotribu/profils-qgis/main/qdt/scenario.qdt.yml
  ```

----

## Contribuer aux profils

### Prérequis

- Python >= 3.10
- connexion réseau sur :
  - gitlab.com
  - plugins.qgis.org
  - pypi.org

### Environnement de travail

Création d'un environnement virtuel :

```sh
python -m venv .venv
# Sur Windows :
# py -3 -m venv .venv

. .venv/bin/activate
# Sur Windows :
# .venv/Scripts/activate
```

Installation des dépendances :

```sh
python -m pip install -U pip setuptools wheel
pip install -U -r requirements.txt
pre-commit install
```

### Exécuter QDT

Depuis l'environnement virtuel dans le projet cloné :

```sh
qgis-deployment-toolbelt -v -s qdt\scenario.qdt.yml
```

### Vérifier la conformité des profils

> Vérification réalisée à l'aide des JSON Schema

```sh
check-jsonschema --no-cache --schemafile https://raw.githubusercontent.com/Guts/qgis-deployment-cli/main/docs/schemas/profile/qgis_profile.json profiles/*/profile.json --base-uri https://raw.githubusercontent.com/Guts/qgis-deployment-cli/main/docs/schemas/profile/
```

### Vérifier la conformité des scénarios à l'aide des JSON Schemas

> Vérification réalisée à l'aide des JSON Schema

```sh
check-jsonschema --default-filetype yaml --base-uri https://raw.githubusercontent.com/Guts/qgis-deployment-cli/main/docs/schemas/scenario/ --schemafile https://raw.githubusercontent.com/Guts/qgis-deployment-cli/main/docs/schemas/scenario/schema.json qdt/*.qdt.yml
```
