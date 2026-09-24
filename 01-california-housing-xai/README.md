# Explainable AI — California Housing Regression

An Explainable AI project using an XGBoost regression model and four complementary explanation techniques.

## Overview

This project trains an `XGBRegressor` on the California Housing dataset from `scikit-learn` and investigates how the model arrives at its predictions.

The analysis combines:

- global feature importance
- global and local feature attribution
- marginal and instance-level effects
- counterfactual explanations

## Dataset

The California Housing dataset contains numerical socio-economic and geographical characteristics of California districts.

The target variable is:

`MedHouseVal` — median house value.

## Model

The project uses an **XGBoost regression model** (`XGBRegressor`) with a fixed random seed for reproducibility.

Model performance is evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R²

## Explainability Methods

### 1. Permutation Feature Importance

Permutation importance measures the decrease in model performance after randomly permuting individual features.

It provides a global view of which features are most influential for the model.

### 2. SHAP

SHAP (SHapley Additive exPlanations) is used for both:

- global feature importance
- local explanations of individual predictions

The project includes SHAP bar, beeswarm, and waterfall visualizations.

### 3. PDP + ICE

Partial Dependence Plots (PDP) show average marginal effects of selected features.

Individual Conditional Expectation (ICE) curves show how those effects vary across individual observations.

### 4. Counterfactual Explanations

DiCE is used to generate counterfactual examples showing how input features could change to move a prediction into a desired target range.

The project also discusses the realism and feasibility limitations of counterfactual explanations.

## Key Findings

Permutation importance and SHAP consistently identify **Latitude**, **Longitude**, and **median income (MedInc)** among the most influential variables.

SHAP provides directional information about feature contributions, while PDP and ICE reveal non-linear and heterogeneous relationships.

The counterfactual analysis demonstrates how the model responds to changes in input features, while also highlighting that some generated changes may not be realistic in the real world.

## Limitations

- Geographical variables can be correlated with other characteristics in the dataset.
- Feature importance should therefore not automatically be interpreted as causal importance.
- The target distribution has a ceiling effect that limits prediction quality for some high-value districts.
- Counterfactual explanations may suggest changes that are mathematically valid for the model but unrealistic in practice.

## Repository Contents

```text
.
├── README.md
├── xai_model_explanations.ipynb
└── requirements.txt
```

## Technologies

- Python
- NumPy
- pandas
- scikit-learn
- XGBoost
- SHAP
- DiCE
- Matplotlib
- Jupyter Notebook

## Academic Context

Developed as part of the Master's program in Artificial Intelligence at Johannes Kepler University Linz (JKU).
