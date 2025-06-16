# Regression_Models_on_Used_Car_Price_Dataset

A study on how different regression models performed on a used car price dataset containing vehicle attributes and listing details to predict market value.

## Objective

The objective of this repository is to compare the performance of various popular regression models on a used car pricing dataset. The dataset includes features such as vehicle specifications, condition-related metrics, and listing details. The goal is to evaluate how well different models can predict the actual price of a used car using key performance metrics: MAE, MSE, RMSE, and R² Score. This comparison helps in identifying suitable models for real-world automotive price estimation, resale valuation, and online car marketplace pricing engines.

## Dataset

The dataset used in this project is a structured tabular dataset containing information about used car listings, including their specifications, condition indicators, and pricing.

- **Source:** [Used Car Price Prediction Dataset – Kaggle](https://www.kaggle.com/datasets/taeefnajib/used-car-price-prediction-dataset)
- **Total Records:** ~4,000
- **Target Variable:** price (numeric value in USD)
- **Features include:**  
   - Vehicle specs: brand, model, model_year, milage, fuel_type, transmission
   - Engine details: engine_hp, engine_liters (parsed from engine field)
   - Other attributes: accident, clean_title, age, milage_per_year

## Regression Models Overview

**1. Linear Regression:**
A basic linear model used as a benchmark. Assumes linear relationships and offers full interpretability.

**2. Kernel Support Vector Regressor:**
A powerful non-linear model that captures complex feature interactions. Ideal for smaller datasets with non-linear patterns.

**3. Decision Tree Regressor:**
Rule-based, non-linear model. Simple and interpretable but prone to overfitting.

**4. Random Forest Regressor:**
An ensemble of decision trees that improves generalization and handles outliers and missing data well.

**5. Gradient Boosting Regressor:**
A sequential ensemble model that incrementally improves performance by correcting errors from previous trees.

**6. XGBoost Regressor:**
An optimized boosting algorithm with regularization and fast performance. Great for handling structured/tabular data.

## Model Performance Comparison

| Model                      | MAE           | MSE                  | RMSE         | R² Score   |
|----------------------------|---------------|----------------------|--------------|------------|
| Multiple Linear Regression | $8,297.15     | $181,095,614.78      | $13,457.18   | 0.7447     |
| Kernel SVR                 | $12,379.70    | $462,253,717.81      | $21,500.09   | 0.3483     |
| Decision Tree              | $8,808.02     | $212,940,110.98      | $14,592.47   | 0.6998     |
| Random Forest              | $6,852.82     | $150,605,884.01      | $12,272.16   | 0.7877     |
| Gradient Boosting          | $7,488.05     | $138,461,956.39      | $11,766.99   | 0.8048     |
| XGBoost                    | $7,149.06     | $129,309,624.38      | $11,371.44   | 0.8177     |


## Key Insights

- **Multiple Linear Regression:** Multiple Linear Regression performed surprisingly well for a simple model, with an R² score of 0.7447, indicating that it was able to explain nearly 75% of the variance in car prices. Its MAE of $8,297.15 and RMSE of $13,457.18 show that while its predictions were relatively stable, it struggled to capture the complex, non-linear relationships that exist between vehicle attributes and their prices. This model is fast and interpretable, but lacks the flexibility needed for more nuanced price patterns.
- **Kernel SVR:** Kernel SVR delivered the worst performance among all models, with an R² score of just 0.3483, MSE exceeding $462 million, and the highest MAE ($12,379.70) and RMSE ($21,500.09). These results suggest that SVR did not generalize well on this dataset—likely due to its sensitivity to high dimensionality, limited scalability, and possibly insufficient hyperparameter tuning. While SVR can be powerful on smaller or well-scaled datasets, it’s not well-suited for this type of regression task out of the box.
- **Decision Tree:** The Decision Tree model offered moderate performance, with an R² score of 0.6998, MAE of $8,808.02, and RMSE of $14,592.47. It was able to capture some non-linear relationships, but its relatively high error metrics suggest that it may have overfit the training data or lacked proper pruning (e.g., depth control). While interpretable and easy to implement, Decision Trees often require ensembling to reach competitive accuracy levels.
- **Random Forest:** Random Forest significantly outperformed the previous models, achieving an R² score of 0.7877, the lowest MAE so far ($6,852.82), and an RMSE of $12,272.16. Its ability to combine multiple trees helped reduce overfitting and improved prediction stability. It handled both categorical and numerical variables efficiently and proved to be a strong choice for modeling car prices with minimal tuning.
- **Gradient Boosting:** Gradient Boosting continued the trend of performance improvement with an R² score of 0.8048, MAE of $7,488.05, and a lower RMSE of $11,766.99 than Random Forest. Despite a slightly higher MAE than Random Forest, it achieved better overall error reduction, reflected in its MSE and R². This suggests that Gradient Boosting was more effective at correcting prediction errors incrementally and is well-suited for structured regression tasks.
- **XGBoost:** XGBoost emerged as the best-performing model, with the highest R² score (0.8177) and the lowest RMSE ($11,371.44) and MSE ($129.3 million) among all models. Its MAE of $7,149.06 also reflects strong, consistent predictions. XGBoost’s built-in regularization, handling of missing values, and scalable training process gave it a performance edge. It effectively captured complex feature interactions and produced the most accurate price estimates, making it highly suitable for production use.


##  Conclusion

Among the models tested, **XGBoost** achieved the highest performance, with an **R² score of 0.8177** and the **lowest RMSE of \$11,371.44**, making it the most accurate and robust choice for predicting used car prices. **Gradient Boosting** and **Random Forest** also delivered strong results, striking a balance between low error and generalization, and are well-suited for real-world deployment scenarios. **Multiple Linear Regression** provided a reliable baseline with solid interpretability, but it struggled to capture the non-linear relationships inherent in the data. **Decision Tree** showed moderate predictive power but was less consistent, likely due to overfitting. **Kernel SVR**, while capable of modeling complex patterns, underperformed significantly—suggesting it may not be a practical option for this dataset without substantial tuning.

Overall, **XGBoost** stands out as the most production-ready model, offering a powerful combination of accuracy, efficiency, and scalability. Simpler models like Linear Regression remain useful for explainability and quick prototyping, while ensemble methods are preferred for achieving optimal predictive performance in used car price estimation.
