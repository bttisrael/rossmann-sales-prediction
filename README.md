# Rossmann Sales Forecasting: Multi-Store Predictive Pipeline

*(https://public.tableau.com/app/profile/israel.a.o.buratto/viz/Rossmann-predict-sales/Painel1?publish=yes)*

<img width="100%" alt="Rossmann Sales Forecasting Dashboard" src="https://github.com/user-attachments/assets/7f43d130-4b61-42d8-b9f2-20fd17aaef5e" />

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Regressor-green.svg)](https://xgboost.readthedocs.io/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data_Science-150458?style=flat&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Tableau](https://img.shields.io/badge/Tableau-Visualization-E97628?style=flat&logo=tableau&logoColor=white)](https://public.tableau.com/)

## Introduction

This project implements an end-to-end Machine Learning pipeline to forecast daily sales for 1,115 Rossmann drug stores across Europe. The solution addresses a critical business need: providing the CFO with accurate 6-week revenue projections to determine the budget for store renovations.

Following the **CRISP-DM** methodology, the project covers everything from statistical data cleaning and hypothesis-driven EDA to advanced feature selection with the **Boruta algorithm** and hyperparameter fine-tuning of ensemble models like **XGBoost**.

## Features

* **CRISP-DM Framework:** Systematic approach to data science from business understanding to deployment.
* **Advanced Feature Engineering:** Creation of time-series features, cyclical transformations (sine/cosine), and competitive-environment attributes.
* **Boruta Feature Selection:** Automated selection of the most relevant variables to reduce model noise and training time.
* **Financial Forecasting:** Translation of technical metrics (MAE/MAPE) into financial scenarios (Best/Worst case) for executive decision-making.

## Installation

Clone the repository and install the required data science stack:

```bash
git clone [https://github.com/bttisrael/rossmann-sales-prediction.git](https://github.com/bttisrael/rossmann-sales-prediction.git)
cd rossmann-sales-prediction
pip install -r requirements.txt
```
## Usage & Sample Code
The main analysis is performed via the Rossmann.ipynb notebook. Below is a snippet of the Business Results logic used to convert model predictions into actionable financial intelligence:

```Python
# Calculating financial scenarios based on Mean Absolute Error (MAE)
df_results = pd.DataFrame()
df_results['predictions'] = model.predict(x_test)

# Business performance calculation
df_results['worst_scenario'] = df_results['predictions'] - df_results['MAE']
df_results['best_scenario'] = df_results['predictions'] + df_results['MAE']

# Aggregating for CFO-level view
total_predicted = df_results['predictions'].sum()
worst_total = df_results['worst_scenario'].sum()
best_total = df_results['best_scenario'].sum()

print(f"Total Predicted Revenue: ${total_predicted:,.2f}")
```
## Experiments and Diagnostics
The model evaluation focused on balancing generalization and precision across highly diverse store profiles:

* **Top Performer**: The XGBoost Regressor achieved a MAPE of ~9.0%, significantly outperforming baseline linear models.

* **Key Insight (Clustering)**: Exploratory analysis revealed that stores with closer competitors sell more on average, likely due to higher foot traffic in retail hubs.

* **Seasonality**: Identified a significant sales surge after the 10th day of each month and a decrease during school holidays (except for specific assortment types).

## Reference
[1] Chen, T., & Guestrin, C. (2016). XGBoost: A Scalable Tree Boosting System. KDD '16.

[2] Kursa, M., & Rudnicki, W. (2010). Feature Selection with the Boruta Package. Journal of Statistical Software.

[3] Hyndman, R.J., & Athanasopoulos, G. (2021). Forecasting: principles and practice, 3rd edition.
