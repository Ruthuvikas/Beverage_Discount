# **Report: Beverage Sales Analysis and Discount Optimization**

---

## **1. Objective**

The objective of this analysis is to evaluate beverage sales data, understand key factors driving sales quantity, and determine the optimal discount to maximize sales. Multiple machine learning models were developed to predict sales quantity, and insights were derived to support business decisions.

---

## **2. Data Overview**

### **2.1 Dataset Description**
The dataset used for this analysis contains synthetic beverage sales data with features including:
- **Customer Details**: `Customer_Type`, `Region`.
- **Product Features**: `Product`, `Category`, `Unit_Price`, `Discount`.
- **Sales Metrics**: `Quantity`.

### **2.2 Preprocessing Steps**
1. **Duplicate Removal**: Duplicate rows were identified and removed, ensuring data integrity.
2. **Missing Values**: No missing values were found in the dataset.
3. **Unnecessary Columns**: Columns like `Order_ID`, `Customer_ID`, and `Total_Price` were dropped as they were irrelevant to the analysis.
4. **Date Splitting**: The `Order_Date` column was split into year, month, day, and weekday for better feature representation.
5. **Feature Encoding**:
   - Categorical features (`Customer_Type`, `Product`, `Category`, `Region`) were mapped to numeric values for machine learning models.
6. **New Feature Addition**: A new feature, `Price_After_Discount`, was calculated to represent the effective unit price after applying the discount.

---

## **3. Exploratory Data Analysis (EDA)**

### **3.1 Key Insights**
- **Customer Types**: Two main types were identified:
  - B2B (0)
  - B2C (1)
- **Product and Category Encoding**: Each product and category was mapped to unique numeric values for analysis.

### **3.2 Correlations**
- Discount is negatively correlated with `Price_After_Discount` and positively correlated with `Quantity`.
- Unit price has a significant influence on sales quantity, as higher-priced items generally require a discount to stimulate sales.

---

## **4. Machine Learning Models**

Three models were implemented to predict sales quantity and assess feature importance: **Linear Regression**, **XGBoost**, and **Random Forest**.

---

### **4.1 Baseline Model: Linear Regression**

#### **Performance Metrics**
- **Mean Squared Error (MSE)**: Indicates average squared difference between predicted and actual values.
- **R-squared (R²)**: Explains the proportion of variance in `Quantity` captured by the model.
  - MSE: 1.012
  - R²: 0.692 (moderate accuracy)

#### **Feature Importance**
The top contributing features were:
1. **Discount** (highest positive coefficient): Indicates discounts significantly boost sales.
2. **Price_After_Discount** (negative coefficient): Higher effective prices reduce sales.
3. **Unit_Price** (negative coefficient): As expected, higher unit prices tend to decrease quantity sold.

#### **Visualization**
- A bar chart showed the relative importance of features, highlighting the significant role of discount and price-related features.

---

### **4.2 Ensemble Model: XGBoost**

#### **Performance Metrics**
- **MSE**: 0.752
- **R²**: 0.823 (high accuracy)

#### **Feature Importance**
Top-ranked features included:
1. **Discount**
2. **Price_After_Discount**
3. **Category**

#### **Visualization**
- The importance of `Discount` and `Category` was evident, suggesting the effectiveness of XGBoost in capturing non-linear interactions between features.

---

### **4.3 Random Forest Regressor**

#### **Performance Metrics**
- **MSE**: 0.843
- **R²**: 0.801 (high accuracy)

#### **Feature Importance**
The most important predictors were:
1. **Discount**
2. **Price_After_Discount**
3. **Category**
4. **Region**

#### **Visualization**
- A feature importance chart indicated that discounts and regional differences play a critical role in predicting sales.

---

## **5. Optimal Discount Strategy**

A custom function was implemented to predict sales quantity under varying discount levels using the trained models.

### **Process**
1. Discounts ranging from 0% to 50% were tested.
2. Sales quantities were predicted for each discount level using the model.
3. The discount maximizing sales quantity was identified.

### **Example**
For a B2C customer buying a product in Category 1 priced at $3 in Region 2:
- **Optimal Discount**: 34.7%
- This level of discount is predicted to maximize sales quantity while maintaining profitability.

---

## **6. Recommendations**

1. **Discount Optimization**:
   - Use the predictive model to dynamically calculate optimal discounts for each customer-product combination.
   - Focus on maximizing sales for high-demand products while maintaining profitability.

2. **Targeted Marketing**:
   - Identify regions or customer types (e.g., B2C in Region 2) that respond positively to discounts and tailor campaigns accordingly.
   - Focus marketing efforts on product categories with high responsiveness to price adjustments.

3. **Inventory Management**:
   - Insights from feature importance suggest that product categories significantly influence sales quantity. Align inventory levels with predicted demand for different discount levels.

4. **Price Strategy**:
   - Monitor `Price_After_Discount` closely as it has a negative impact on sales. Ensure discounts are sufficient to offset higher base prices.

---

## **7. Conclusion**

This analysis leveraged a combination of data preprocessing, machine learning, and discount optimization to uncover actionable insights for beverage sales. Key findings include:
- Discounts are a significant driver of sales.
- Optimal discount levels vary by customer type, region, and product category.
- Ensemble methods like XGBoost and Random Forest outperform linear regression in predicting sales quantity, capturing complex relationships between features.

The results can be used to design smarter pricing and promotional strategies, ultimately improving sales and profitability.
