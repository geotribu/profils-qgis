# Profils QGIS des articles Geotribu

Cet entrepôt contient des profils QGIS et un scénario de déploiement compatible [QGIS Deployment Toolbelt](https://guts.github.io/qgis-deployment-cli/).

----

## Démarrage rapide

### Prérequis

- Python 3.10+
- connexion réseau autorisée sur :
  - github.com
  - plugins.qgis.org

### Cloner ou télécharger ce dépôt

```sh
git clone https://github.com/geotribu/profils-qgis.git geotribu-profils-qgis
cd geotribu-profils-qgis
```

### Installer QDT

> De préférence dans un environnement virtuel

```sh
python -m pip install -U pip setuptools wheel
pip install -U -r requirements.txt
```

### Exécuter QDT avec le scénario Geotribu

```sh
qgis-deployment-toolbelt -v -s qdt/scenario.qdt.yml 
```

----

## Développement

- installer pre-commit et les git hooks
