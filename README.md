Ce dépôt rassemble trois projets pratiques réalisés avec Python. La progression va de l'interrogation d'une base de données à l'apprentissage supervisé, puis au clustering géographique et à l'optimisation combinatoire.

L'objectif est de construire une compréhension concrète d'une chaîne de travail data : charger des données, les contrôler, les transformer, produire une analyse, entraîner ou évaluer un algorithme, puis communiquer le résultat avec des tableaux et des graphiques.

## Projets réalisés

### Projet 01 - Analyse des vols et des réservations

Le notebook `Projet_01/projet_01.ipynb` construit une base SQLite en mémoire pour une compagnie aérienne fictive. Il crée et remplit les tables `passengers`, `flights` et `bookings`, avec des contraintes d'intégrité (`NOT NULL`, `UNIQUE`, `CHECK` et clés étrangères).

Les données sont interrogées avec SQL afin de :

- lister les vols au départ de Nice et les vols à moins de 100 euros ;
- compter les réservations par statut ;
- calculer le chiffre d'affaires et le nombre de réservations par destination ;
- repérer les passagers d'une destination, les passagers sans réservation et les clients fidèles ;
- comparer les prix des vols au prix moyen ;
- identifier une destination commerciale prioritaire et la représenter graphiquement.

**Compétences travaillées :** modélisation relationnelle, SQL, création de tables, insertion et validation de données, filtres, agrégations, `GROUP BY`, `HAVING`, jointures, sous-requêtes, contraintes d'intégrité, pandas et visualisation avec matplotlib.

### Projet 02 - Analyse et prédiction de matchs internationaux

Le notebook `Projet_02/projet_02.ipynb` exploite `Projet_02/data/results.csv` pour analyser les résultats de matchs internationaux entre 1994 et 2026, puis prédire l'issue de confrontations entre équipes.

Le travail comprend :

- la préparation des résultats et la création des variables `outcome` et `winner` ;
- l'étude de l'avantage du terrain, des équipes les plus victorieuses et de l'évolution du nombre moyen de buts ;
- le calcul de la forme récente de chaque équipe ;
- la création de variables numériques et d'écarts de performance entre les équipes ;
- la séparation temporelle des données d'entraînement et de test, puis leur standardisation ;
- l'entraînement d'une `RandomForestClassifier`, son évaluation avec l'accuracy et une matrice de confusion ;
- l'interprétation de l'importance des variables ;
- la prédiction de matchs individuels et la simulation d'un tableau de Coupe du monde 2026 jusqu'au champion estimé.

**Compétences travaillées :** exploration avec pandas, feature engineering, classification binaire, préparation d'un jeu d'apprentissage, standardisation, forêt aléatoire, comparaison à une baseline, évaluation de modèle, interprétabilité, probabilités et simulation basée sur un modèle.

### Projet 03 - Construction d'un parcours du Tour de France

Le notebook `Projet_03/projet_03.ipynb` utilise les 120 villages de `Projet_03/villages_2027.csv` pour concevoir un Tour de France 2027 en 21 étapes.

Les principales étapes sont :

- l'exploration de la répartition des villages par département et sa visualisation sur une carte ;
- la conversion des latitudes et longitudes en coordonnées approximatives en kilomètres ;
- la comparaison de K-Means et de la classification ascendante hiérarchique (CAH) ;
- l'évaluation des regroupements avec le score de silhouette et l'analyse de la taille des groupes ;
- la sélection et la renumérotation des 21 étapes ;
- le calcul des distances GPS avec la formule de Haversine et la construction d'une matrice de distances ;
- la génération d'itinéraires avec l'heuristique du plus proche voisin ;
- l'amélioration des itinéraires par recherche locale `2-opt` ;
- la production d'un roadbook, d'une carte du Tour et de statistiques sur les étapes.

**Compétences travaillées :** données géographiques, coordonnées GPS, visualisation cartographique, K-Means, CAH, score de silhouette, distances sur une sphère, heuristiques gloutonnes, recherche locale et optimisation de parcours.

## Compétences transversales

- Python dans des notebooks Jupyter et organisation d'un environnement avec `uv` ;
- pandas pour charger, filtrer, transformer et agréger des données ;
- matplotlib pour produire des graphiques et des cartes ;
- validation par assertions et contrôle des schémas ou dimensions attendues ;
- traduction d'une question métier ou opérationnelle en traitement de données ;
- comparaison de méthodes et interprétation des résultats.

## Structure du repo

```text
having_fun_with_ml/
├── Projet_01/
│   └── projet_01.ipynb
├── Projet_02/
│   ├── projet_02.ipynb
│   ├── utils.py
│   └── data/results.csv
├── Projet_03/
│   ├── projet_03.ipynb
│   ├── utils.py
│   └── villages_2027.csv
├── pyproject.toml
└── README.md
```

Les fichiers `utils.py` regroupent les fonctions de chargement, de calcul et de visualisation des projets 02 et 03, afin de garder les notebooks lisibles.

## Installation

Le projet demande Python 3.13.2 ou une version compatible indiquée dans `pyproject.toml`. Avec [uv](https://docs.astral.sh/uv/), depuis la racine du dépôt :

```shell
uv sync
```

Cette commande crée l'environnement virtuel et installe notamment `ipykernel`, `pandas`, `matplotlib` et `scikit-learn`. SQLite et `sqlite3` sont fournis par Python.

Dans VS Code, ouvrir un notebook, choisir le kernel de l'environnement `.venv`, puis exécuter les cellules dans l'ordre. Les assertions présentes dans les notebooks servent de contrôles rapides pour vérifier les résultats attendus.

## Données et limites

Les données des projets 01 et 03 sont intégrées au dépôt. Le projet 02 utilise `Projet_02/data/results.csv`; le module utilitaire indique également la source publique du jeu de données.

Les prédictions sportives et le parcours du Tour sont des exercices pédagogiques. Ils illustrent une méthode de modélisation et d'optimisation, mais ne constituent ni une prévision fiable d'un événement sportif ni un tracé officiel. Une piste d'amélioration pour le parcours du Tour serait de suivre des contraintes plus strictes respectant celles du Tour de France (exemple arrivée à Paris, distance max par étape 200km, ...) et de gérer les distances sur un trajet routier et non à vol d'oiseau.
