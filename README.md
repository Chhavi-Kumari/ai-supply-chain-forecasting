# ai-supply-chain-forecasting
Comparative analysis of traditional vs. AI-enabled demand forecasting models in global supply chains.

## The Problem

Inventory mismanagement is one of the most costly inefficiencies in retail supply chains. Overstocking ties up capital and increases holding costs, while understocking leads to lost sales, customer dissatisfaction, and expedited shipping expenses. Traditional forecasting methods like static Excel-based models struggle to capture the complexity of real-world demand patterns driven by seasonality, pricing, and market trends.

This directed research project, completed as part of my final semester at USC, set out to answer a focused question:

"Can AI-driven forecasting models meaningfully outperform traditional statistical baselines for retail inventory planning?"

Using two years of Adidas retail sales data as the test case, I built, compared, and evaluated two forecasting approaches, a traditional statistical model and a machine learning model, to quantify the accuracy improvement and translate it into supply chain implications.

## Methodology
### Data Preparation
* Sourced 2 years of multivariate Adidas retail sales data covering multiple product categories, regions, and time periods
*	Aggregated raw transactional data into structured monthly time series by cleaning inconsistencies, handling missing values, and normalizing formats
*	Engineered lag-based features (prior month sales, rolling averages) to capture temporal dependencies for the ML model
*	Validated dataset integrity before modelling to ensure no data leakage between train and test splits

### Model 1 - Statistical Baseline: Simple Exponential Smoothing (SES)
SES was selected as the baseline because it represents the most common approach used in practice with weighted averages of historical observations that give more importance to recent data.
*	Built SES model in Excel using Solver to minimize RMSE through automated parameter optimization
*	Optimized smoothing parameter α to 0.8, indicating high responsiveness to recent demand signals
*	Used as the performance benchmark against which the ML model would be evaluated

### Model 2 - Machine Learning: Random Forest Regression
Random Forest was selected for its ability to capture non-linear relationships, handle multivariate inputs, and resist overfitting which are all critical for real-world retail demand data.
*	Built Random Forest model in Python (scikit-learn) with 100 decision trees
*	Applied train-test split methodology to simulate real forecasting conditions - model trained on historical data, evaluated on unseen future periods
*	Incorporated lag features, seasonal indicators, and pricing variables as input features
*	Evaluated model performance using RMSE as the primary metric for comparability with SES baseline

## Results

| 45% | 0.8 | 100 |
| :---: | :---: | :---: |
| RMSE Reduction | Optimal α (SES) | RF Trees |
| vs optimized SES baseline | High recency weighting | Random Forest ensemble size |

| Metric | SES Baseline | Random Forest |
| :--- | :--- | :--- |
| **Forecasting Approach** | Statistical (weighted avg) | ML (ensemble trees) |
| **Input Variables** | Historical sales only | Sales + lag features + pricing |
| **RMSE** | Baseline (optimized) | ~45% lower |
| **Non-linear patterns** | Cannot capture | Handles natively |
| **Scalability** | Manual recalibration needed | Retrainable on new data |

The Random Forest model achieved approximately 45% lower forecasting error than the optimized SES benchmark which is a significant improvement that has direct operational implications for inventory planning decisions.

## Supply Chain Implications

A 45% reduction in forecasting error is not just a modelling achievement, it translates directly into operational value across the supply chain:

| Supply Chain Area | Impact of Better Forecasting |
| :--- | :--- |
| **Inventory Planning** | Reduced overstock and stockout events lower: holding costs and fewer lost sales |
| **Procurement** | More accurate purchase orders reduce emergency buying and supplier strain | 
| **Warehouse Operations** | Better demand visibility enables smarter slotting and space utilization | 
| **Logistics & Distribution** | Reduced last-minute expediting costs from stockout recovery | 
| **Financial Planning** | Tighter forecast accuracy improves cash flow and working capital management | 

## What I'd Do Next

This project established a strong proof of concept. With more time and data access, the logical next steps would be:
*	Expand to SKU-level forecasting - aggregate monthly data masks important product-level variation that drives real inventory decisions
*	Incorporate external signals - weather, promotions, competitor pricing, and macroeconomic indicators as additional features
*	Test additional ML models - XGBoost and LSTM (for sequential time series) would be strong candidates to benchmark against Random Forest
*	Build a real-time pipeline - move from batch forecasting to a live model that updates as new sales data arrives
*	Quantify dollar impact - translate RMSE improvement into estimated inventory cost savings using average holding cost and stockout penalty assumptions

## Tools & Skills Demonstrated

| Skill Area | Application |
| :--- | :--- |
| **Python (scikit-learn)** | Random Forest model - feature engineering, train-test split, RMSE evaluation |
| **Excel + Solver** | SES baseline - automated α optimization to minimize forecasting error | 
| **Tableau** | Forecast vs actuals visualization for comparative model evaluation | 
| **Data Cleaning** | 2 years of raw retail data aggregated and structured for time series modelling | 
| **Supply Chain Thinking** | Translated model accuracy into operational inventory planning implications | 
| **Research Methodology** | Designed comparative study with clear baseline, evaluation metric, and validation approach | 
