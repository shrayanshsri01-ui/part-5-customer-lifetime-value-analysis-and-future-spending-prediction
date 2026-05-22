# Part 5: Customer Lifetime Value Analysis and Future Spending Prediction

## Project Title
Customer Lifetime Value Analysis and Future Spending Prediction

## Business Problem
The company aims to increase revenue organically by focusing on maximizing the value of existing customers rather than relying on expensive new customer acquisition strategies. Customer Lifetime Value (CLV/LTV) represents the total expected revenue from a customer. By predicting future spending and understanding customer behavior, the business can effectively segment users, allocate resources efficiently, and target high-potential customers while reducing churn.

## Dataset Description
The dataset contains customer behavior, profiling, and transaction history, focusing on future spending prediction. 
**Key Features:**
- Customer profiling: `Age`, `AnnualIncome`, `LoyaltyTier`
- Customer behavior: `WebsiteVisits`, `AppSessions`, `DaysSinceLastPurchase`
- Value metrics: `PreviousOrders`, `AverageOrderValue`, `Year1Spending`
- Target variable: `FutureSpending`

## Data Cleaning and Feature Engineering Summary
- Dropped all rows with missing values to ensure data consistency.
- Removed duplicate rows.
- Created `TotalEngagement` by aggregating `WebsiteVisits` + `AppSessions`.
- Created `TotalPreviousSpending` as a product of `PreviousOrders` * `AverageOrderValue`.

## EDA Insights
- **Future Spending Distribution:** The distribution is somewhat right-skewed, showing that the majority of customers spend moderately, while a smaller group spends exceptionally high amounts.
- **Income vs. Future Spending:** There is a positive correlation between `AnnualIncome` and `FutureSpending`, heavily influenced by the `LoyaltyTier`. Gold and Silver tier members tend to exhibit higher future spending.

## Customer Segmentation Summary
Customers were segmented into three tiers based on their predicted/actual Future Spending:
- **High-Value:** Top 25% of spenders.
- **Medium-Value:** Middle 50% of spenders.
- **Low-Value:** Bottom 25% of spenders.

## Regression Model Summary
A `RandomForestRegressor` pipeline was built. The categorical features were encoded using `OneHotEncoder`, and numerical features were standardized using `StandardScaler`. The Random Forest was chosen for its robustness against non-linear margins and its lack of reliance on strict data normality.

## Model Evaluation Results
- **MAE:** 1136.26
- **RMSE:** 1418.67
- **R² Score:** 0.9045

The model accounts for approximately 90.45% of the variance, indicating very strong predictive capabilities on unseen data.

## Final LTV Growth Strategy (Business Recommendations)
1. **Premium Offers:** Target 'High-Value' customers for VIP access and premium items since their purchasing behavior indicates a strong willingness to spend.
2. **Discount Interventions:** Use targeted discounts effectively on 'Medium-Value' customers who exhibit high `TotalEngagement` but average `TotalPreviousSpending`. These customers have intent, but may need incentives.
3. **Re-Engagement:** Customers with high `DaysSinceLastPurchase` and a previously high `AverageOrderValue` should receive immediate re-engagement campaigns.
4. **Avoid Expensive Offers:** Customers categorized as 'Low-Value' with high `CancellationRate` should be excluded from high-cost retention campaigns to maximize ROI.

## How to Run the Project
1. Clone the repository.
2. Ensure you have the required packages installed: `pip install -r requirements.txt`.
3. Open `notebook.ipynb` in Jupyter Notebook or VS Code.
4. Run all cells sequentially to view the data processing, visual charts, and model results.