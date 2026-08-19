This repository brings together three practical projects built with Python. The progression goes from querying a database to supervised learning, then to geographical clustering and combinatorial optimization.

The goal is to build a concrete understanding of a data workflow: loading data, checking it, transforming it, producing an analysis, training or evaluating an algorithm, and then communicating the results with tables and charts.

## Completed Projects

### Project 01 - Flight and Booking Analysis

The notebook `Projet_01/projet_01.ipynb` builds an in-memory SQLite database for a fictional airline. It creates and populates the `passengers`, `flights`, and `bookings` tables, with integrity constraints (`NOT NULL`, `UNIQUE`, `CHECK`, and foreign keys).

The data is queried using SQL in order to:

- list flights departing from Nice and flights costing less than 100 euros;
- count bookings by status;
- calculate revenue and the number of bookings by destination;
- identify passengers traveling to a destination, passengers without bookings, and loyal customers;
- compare flight prices to the average price;
- identify a priority business destination and represent it graphically.

**Skills covered:** relational modeling, SQL, table creation, data insertion and validation, filters, aggregations, `GROUP BY`, `HAVING`, joins, subqueries, integrity constraints, pandas, and visualization with matplotlib.

### Project 02 - International Match Analysis and Prediction

The notebook `Projet_02/projet_02.ipynb` uses `Projet_02/data/results.csv` to analyze international match results between 1994 and 2026, and then predict the outcome of matches between teams.

The work includes:

- preparing the results and creating the `outcome` and `winner` variables;
- studying home advantage, the most successful teams, and the evolution of the average number of goals;
- calculating the recent form of each team;
- creating numerical features and performance differences between teams;
- splitting the training and test data chronologically, then standardizing them;
- training a `RandomForestClassifier`, evaluating it with accuracy and a confusion matrix;
- interpreting feature importance;
- predicting individual matches and simulating a 2026 World Cup bracket all the way to the estimated champion.

**Skills covered:** exploration with pandas, feature engineering, binary classification, training set preparation, standardization, random forest, comparison with a baseline, model evaluation, interpretability, probabilities, and model-based simulation.

### Project 03 - Building a Tour de France Route

The notebook `Projet_03/projet_03.ipynb` uses the 120 villages from `Projet_03/villages_2027.csv` to design a 2027 Tour de France with 21 stages.

The main steps are:

- exploring the distribution of villages by department and visualizing it on a map;
- converting latitude and longitude into approximate coordinates in kilometers;
- comparing K-Means and hierarchical clustering (CAH);
- evaluating the clusters using the silhouette score and analyzing group sizes;
- selecting and renumbering the 21 stages;
- calculating GPS distances using the Haversine formula and building a distance matrix;
- generating routes using the nearest-neighbor heuristic;
- improving the routes using `2-opt` local search;
- producing a roadbook, a Tour map, and statistics about the stages.

**Skills covered:** geographical data, GPS coordinates, map visualization, K-Means, CAH, silhouette score, distances on a sphere, greedy heuristics, local search, and route optimization.

## Cross-Cutting Skills

- Python in Jupyter notebooks and environment management with `uv`;
- pandas for loading, filtering, transforming, and aggregating data;
- matplotlib for creating charts and maps;
- validation using assertions and checking expected schemas or dimensions;
- translating a business or operational question into a data processing workflow;
- comparing methods and interpreting results.

## Repository Structure

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
````

The `utils.py` files contain the loading, calculation, and visualization functions for projects 02 and 03, in order to keep the notebooks readable.

## Installation

The project requires Python 3.13.2 or a compatible version specified in `pyproject.toml`. Using [uv](https://docs.astral.sh/uv/), from the root of the repository:

```shell
uv sync
```

This command creates the virtual environment and installs, among others, `ipykernel`, `pandas`, `matplotlib`, and `scikit-learn`. SQLite and `sqlite3` are provided by Python.

In VS Code, open a notebook, select the kernel from the `.venv` environment, then run the cells in order. The assertions present in the notebooks serve as quick checks to verify the expected results.

## Data and Limitations

The data for projects 01 and 03 is included in the repository. Project 02 uses `Projet_02/data/results.csv`; the utility module also indicates the public source of the dataset.

The sports predictions and the Tour route are educational exercises. They illustrate a modeling and optimization approach, but they are neither a reliable prediction of a sporting event nor an official route. One possible improvement for the Tour route would be to follow stricter constraints that comply with those of the Tour de France (e.g. finishing in Paris, a maximum distance of 200 km per stage, ...) and to handle distances based on road routes rather than straight-line distances.
