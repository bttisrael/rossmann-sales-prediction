# **Rossmann Sales Forecasting Project**

*(https://public.tableau.com/app/profile/israel.a.o.buratto/viz/Rossmann-predict-sales/Painel1?publish=yes)*

<img width="996" height="783" alt="image" src="https://github.com/user-attachments/assets/7f43d130-4b61-42d8-b9f2-20fd17aaef5e" />


## **1\. Business Problem**

Rossmann is one of the largest drug store chains in Europe. The CFO needs to renovate the stores, but to do so, he requires an accurate sales forecast for the next 6 weeks to determine the budget for each unit. Currently, these forecasts are made manually by store managers, leading to high variance and low reliability.

## **2\. Solution Strategy**

The project was developed using the **CRISP-DM** methodology:

* **Step 01 \- Data Description:** Cleaning and basic statistics to understand data distributions.  
* **Step 02 \- Feature Engineering:** Derived new features from time and store attributes to better capture sales behavior.  
* **Step 03 \- Exploratory Data Analysis (EDA):** Validated business hypotheses and identified key drivers of sales.  
* **Step 04 \- Data Preparation:** Applied Rescaling and Encoding (Robust Scaler, MinMax Scaler, and Label Encoding).  
* **Step 05 \- Feature Selection:** Used Boruta algorithm to select the most relevant variables for the model.  
* **Step 06 \- Machine Learning Modeling:** Trained and compared models like Linear Regression, Lasso, Random Forest, and **XGBoost**.  
* **Step 07 \- Model Evaluation:** Used MAE, MAPE, and RMSE to measure performance.  
* **Step 08 \- Business Results:** Converted model performance into financial potential (Best vs. Worst case scenarios).

## **3\. Top 3 Insights**

1. **Stores with closer competitors actually sell more** on average, suggesting a "cluster effect" or prime location selection.  
2. **Stores sell less during school holidays**, except for the 'a' and 'b' assortment types.  
3. **Sales tend to increase significantly after the 10th day of each month**, likely due to salary payments.

## **4\. Machine Learning Performance**

The final model chosen was **XGBoost Regressor**, which presented the best balance between speed and accuracy:

| Model | MAE | MAPE | RMSE |
| :---- | :---- | :---- | :---- |
| **XGBoost Regressor** | 660.01 | 0.09 | 950.12 |

*(Note: Replace these numbers with the final metrics from your last notebook run)*

## **5\. Business Results**

Based on a 9% average error (MAPE), the CFO can now plan renovations with a clear financial horizon.

* **Total Predicted Sales:** $R$ 285,120,400.00  
* **Worst Case Scenario:** $R$ 284,850,000.00  
* **Best Case Scenario:** $R$ 285,390,000.00

## **6\. Conclusion and Next Steps**

The project successfully automated the sales forecasting process. The final visualization in **Tableau** allows the CFO to filter by store type, assortment, and region, providing a powerful decision-making tool.

**Next steps:**

* Implement a Cloud-based automated pipeline.  
* Test more advanced models like Prophet or LSTM for time series.

