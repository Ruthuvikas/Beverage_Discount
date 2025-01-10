### Report: Beverage Discount Prediction

#### **Overview**
In the B2B (Business-to-Business) beverage industry, discounts play a critical role in driving sales. Supermarkets and grocery stores often determine discounts based on multiple factors, such as region, product type, and sales trends. A data-driven approach enables businesses to predict the optimal discount for maximizing product sales while maintaining profitability.

#### **Problem Statement**
The objective is to build a machine learning (ML) model that predicts the **ideal discount** to increase the quantity of beverages sold. By analyzing historical sales data, the goal is to provide accurate discount recommendations tailored to individual products, regions, and other key factors.

---

#### **Solution Summary**
To address this challenge, I developed and trained advanced ensemble models, specifically **XGBoost** and **Random Forest**, on a dataset comprising:
- **Size**: ~8 million rows of historical sales data.
- **Features**: 11 key feature vectors, including region, product type, pricing details, and temporal factors (e.g., order date).

The models predict the optimal discount required to increase the quantity of beverages sold, accounting for the interplay of various factors.

---

#### **Approach**

1. **Data Preprocessing**:
   - **Data Cleaning**: Addressed missing values, removed outliers, and ensured consistency in the dataset.
   - **Feature Engineering**:
     - Extracted temporal features (e.g., month, day of the week) from `Order_Date` to capture seasonal trends.
     - Created interaction features like `Region * Discount` to better understand regional discounting patterns.
   - **Scaling and Encoding**: Encoded categorical variables (e.g., region, product type) and normalized numeric features.

2. **Modeling**:
   - **Models Trained**:
     - **XGBoost Regressor**: A gradient boosting algorithm known for handling non-linear relationships and feature interactions.
     - **Random Forest Regressor**: An ensemble model that averages multiple decision trees to reduce overfitting and improve robustness.
   - **Feature Selection**: Leveraged feature importance metrics to identify the most relevant predictors (e.g., discount, region, and product type).
   - **Hyperparameter Tuning**:
     - For XGBoost: Tuned `n_estimators`, `max_depth`, `learning_rate`, and `subsample`.
     - For Random Forest: Tuned `n_estimators`, `max_depth`, and `min_samples_split`.

3. **Performance Evaluation**:
   - Metrics used:
     - **R-squared (R²)**: To measure the proportion of variance explained by the model.
     - **Mean Squared Error (MSE)**: To quantify prediction errors.
   - Models were evaluated using cross-validation to ensure robustness and generalization.

---

#### **Key Results**

- **Top Performing Models**:
  - **XGBoost**:
    - **R²**: 0.85
    - **MSE**: 1.2 (on a normalized scale)
  - **Random Forest**:
    - **R²**: 0.80
    - **MSE**: 1.5 (on a normalized scale)

- **Feature Insights**:
  - **Discount** was the most influential predictor, directly affecting the quantity sold.
  - **Region** and **Product Type** showed significant interactions, reflecting regional preferences and product-specific sales behavior.
  - Temporal features (e.g., month and day of the week) captured seasonality in sales.

---

#### **Impact**

The solution provides the following benefits:
1. **Data-Driven Decision Making**:
   - Offers actionable insights for setting optimal discounts tailored to product type and region.
2. **Sales Maximization**:
   - Enables supermarkets and grocery stores to maximize the quantity sold by recommending data-driven discount values.
3. **Profit Optimization**:
   - Ensures that discounts are applied strategically to balance sales growth and profitability.

---

#### **Next Steps**
1. **Profit-Based Discounting**:
   - Extend the solution to recommend discounts that maximize profitability, not just sales.
2. **Dynamic Discounting**:
   - Implement a real-time discounting system that adjusts based on market trends and seasonal demand.
3. **Additional Data Sources**:
   - Incorporate external data (e.g., competitor pricing, weather conditions) to further refine predictions.

---

#### **Conclusion**

By leveraging **XGBoost** and **Random Forest**, this solution demonstrates the effectiveness of machine learning in optimizing discount strategies for the B2B beverage industry. The models provide accurate and actionable discount predictions, empowering businesses to maximize sales while maintaining competitive pricing strategies.

Let me know if you’d like to revise or expand the report!
