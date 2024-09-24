

# Is a football player's transfer value predictable?

## Basic Overview

Objective: This analysis considers player data from the computer game FIFA 22, to build, optimize and test a predictive model to identify the key features in a player's financial transfer/market value. 

Audience: This analysis will be useful to clubs trying to buy and sell players at suitable market values.

## Table of Contents

1. [Installation and Set-Up](#installation-and-set-up)
2. [Data Sources](#data-sources)
3. [Data Cleaning](#data-cleaning)
4. [Data Exploration](#data-exploration)
5. [Data Preparation](#data-preparation)
6. [Feature Selection](#feature-selection)
7. [Models on Best Variables](#models-on-best-variables)
8. [Model Optimization](#model-optimization)
9. [Feature Importance](#feature-importance)
10. [Models without dominant features](#models-without-best-features)

## Installation and set up

1. **Python Installation**: This project requires Python. Ensure you have Python installed on your system. You can download Python from the [official Python website](https://www.python.org/downloads/).

2. **Running Jupyter Notebooks**: The Python files for this project are in `.ipynb` format, which can be executed using Jupyter Notebook or Google Colab. To use Jupyter Notebook locally, you can install it via Anaconda or directly using pip:
   - **Using Anaconda**: Install Anaconda from [Anaconda's website](https://www.anaconda.com/products/distribution) and launch Jupyter Notebook from the Anaconda Navigator.
   - **Using pip**: Install Jupyter Notebook with the command:
     ```bash
     pip install notebook
     ```

3. **Required Packages**: This analysis requires several Python packages. You can install these packages using pip. The list of packages and their installation commands are provided below. 

      - `pip install pandas`
      - `pip install scikit-learn`
      - `pip install numpy`
      - `pip install matplotlib`
      - `pip install seaborn`
      - `pip install statsmodels`
      - `pip install xgboost`
      - `pip install interpret`
      - `pip install pydot`
      - `pip install ipython`
      - `pip install scipy`
      - `pip install shap`
      
Once these packages have been installed all import statements should run.

## Data Sources

Data was collected from Kaggle. It contains player data from the video game FIFA 22. 
https://www.kaggle.com/datasets/stefanoleone992/fifa-22-complete-player-dataset 

## Data Cleaning

Removed rows without target variable.
Dropped irrelevant columns (e.g., images, jersey numbers).
Excluded goalkeeping metrics.
Dropped National Team ID due to missing data.
Encoded data, grouped, and checked for null values.

Data was cleaned by dropping rows where the target variable was not stored. Any non-relevant columns i.e. images, jersey numbers etc were dropped. Goalkeeping metrics were also dropped as these represent a group quite distant from the majority of footballers and the data could distort results. National Team ID was dropped from the data as 96% of it's data was missing. Data was encoded, grouped and checked for null values to make regression analysis easier.

## Data Exploration

Summary statistics were found for each variable and distributions were plotted. Boxplots were created to identify outliers. Correlation heatmaps were created to identify metrics that are most closely linked to the target variable.

## Data Preparation

Data was shuffled and then split into X (predictors) and Y (target variable) datasets.

## Feature Selection

Forward, Backward and Best Subset feature selection techniques are implemented. The top features found with each technique are stored. 

## Models on best variables

Models are run on the features found in the subset found in the previous step. The model results are stored in a dataframe.

## Model Optimization

The previous models are optimized using GridSearchCV on key hyperparameters. The new model configurations and metrics are stored in a dataframe.

## Feature Importance

Feature Importance was run using the best model from the previous step. This was done using SHAP to rank the metrics in their effect on the target variable. These metrics were then examined to see how their values individually effected the tagret variable. 

## Models without best features

The previous step highlighted a number of dominant features which caused all other features to be insignificant when predicting player market value. These features were removed and the modelling/feature importance steps were repeated to get a more represenatative sample of the key metrics without the few dominant ones.
