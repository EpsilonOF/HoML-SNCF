# SNCF train regularity analysis

This project aims to predict various metrics related to SNCF train delays using machine learning techniques. In particular, the analysis focuses on predicting the number of late trains and the average delay as a function of different variables such as month, departure and arrival stations.## Data

The data used in this project come from two main sources:
- [Kaggle dataset on monthly TGV regularity](https://www.kaggle.com/datasets/elliotx1000/french-railway-monthly-tgv-regularity)
- [SNCF data on monthly TGV regularity (AQST)](https://ressources.data.sncf.com/explore/dataset/regularite-mensuelle-tgv-aqst/information/)

This project uses the CSV file in the Export section of the second link.

## Prerequisites

The project requires the following Python libraries:
- pandas
- numpy
- scikit-learn
- matplotlib
- pathlib

You can install these dependencies with the command :
```
pip install -r requirements.txt
```

## Project structure

```
.
├── project.py          # Main script
├── data/               # Folder containing data
│   ├── regularite-mensuelle-tgv-aqst.csv    # Raw data
│   ├── sncf_data.csv                        # Clean data
│   └── correspondance_gare.csv              # Index-station correspondence
├── meilleur_resultat.txt   # Optimized results
└── README.md           # This file
```

## Features

The script performs several sequential analyses:

1. **Data pre-processing**: Loading, cleaning and encoding of categorical variables
2. **Correlation analysis**: Identification of variables most correlated with targets
3. **Model training** to predict 4 distinct targets:
   - Number of trains late arriving
   - Number of trains delayed on departure
   - Average delay of all departing trains
   - Average delay of trains delayed on arrival
4. **Model evaluation**: Performance comparison via cross-validation
5. **Hyperparameter optimization**: Search for the best parameters via GridSearchCV
6. **Results visualization**: Graphs comparing predictions and real data

## Models tested

Several regression models are evaluated for each target:
- Simple linear regression
- Polynomial regression
- Ridge Regression
- Lasso Regression
- Random Forest
- Gradient Boosting

## Usage

To run the complete analysis, download the project and run the cells one by one, depending on the task you wish to perform. The project follows a guideline as you go through the notebook, so it's advisable to run it in order.

## Results

The best performance was obtained for the prediction of the number of late arriving trains, with an R² score of around 0.73, indicating a good predictive capability of the model.

The script saves the best hyperparameters found in a `best_result.txt` file, which can be viewed in the `data` folder.
