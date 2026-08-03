**FOOD SPOILAGE RISK PREDICTION USING MACHINE LEARNING**

**PROJECT OVERVIEW**

Food spoilage is a significant contributor to food waste and a source of significant financial losses across the perishable goods supply chain. Retailers lose margins from marked-down, unsold products and discarded stock, while poor visibility of spoilage risks leads to inefficient inventory and replenishment decisions. 

This project develops a machine learning model that predicts the spoilage risk of perishable products from storage, handling, packaging and product characteristics recorded at the point of purchase. The dataset used is perishable_goods_management.csv, a retail-transaction dataset of **100,000** records across **42** variables covering ten product categories (Bakery, Beverages, Dairy, Deli, Frozen Meals, Meat, Pharmaceuticals, Produce, Ready-to-Eat and Seafood) and five US regions.

The continuous variable **spoilage_risk (range 0.05-0.47, mean 0.20)** is used as the risk indicator. It is binned into three ordinal classes: **Low, Medium and High** using tercile thresholds, so the task is framed as a multi-class classification problem. A regression formulation on the raw score is retained as an optional extension. The model is intended to help retailers and supply-chain managers prioritise at-risk stock, reduce avoidable waste and improve food-safety decisions.

**PROBLEM DEFINITION** 

Retailers mostly rely on fixed expiry dates and manual inspection to judge whether perishable stock is at risk. These approaches are subjective, applied late, and do not combine the many other operational factors: storage temperature deviation, handling quality, packaging quality, distribution time, product sensitivity that jointly determine how quickly an item deteriorates.

The business consequence is measurable waste and lost margin: in this dataset, 19.4% of records were ultimately spoiled and mean waste reaches 38% of units for spoiled items. A model that estimates spoilage risk from information available at or before purchase would let businesses react earlier (markdown, redistribution, prioritised sale) instead of reacting after loss has occurred.

This project therefore develops a classification model that predicts the spoilage risk level of a perishable item from its storage and handling conditions and product attributes, using only features that are known before the sales outcome is realised.


**PROJECT GOAL**

The primary goal of this project is to develop and evaluate machine learning models that classify perishable items into Low, Medium or High spoilage-risk categories. The project also aims to: 

- Reduce food waste by supporting earlier identification.
- Improve food safety awareness and inventory decisions through data-driven risk scoring.
- Identify operational factors that most influence spoilage risk.
- Compare several machine learning algorithms and select the most effective one.
- Demonstrate a complete, leakage-aware, end-to-end machine learning workflow.

**RESEARCH QUESTION**

Can machine learning accurately predict the spoilage risk level of perishable retail products from storage, handling, and product features by using only information available before the sales outcome to support inventory management and reduce food waste?

**ABOUT THE DATASET**

File: synthetically generated |  Rows: 100,000  |  Columns: 42  |  No missing values.

The target used for modelling is spoilage_risk (continuous), binned into the ordinal classes Low / Medium / High. Because the dataset also contains commercial-outcome variables (see Data Leakage section below), features are split into three groups:

***Predictive features (safe - known at/before purchase)***:

•	category - product category (10 categories).
•	region - US region of the store.
•	shelf_life_days - labelled shelf life of the product.
•	days_remaining_at_purchase - remaining shelf life when purchased.
•	storage_temp - storage temperature (deg C).
•	temp_deviation - deviation from the recommended storage temperature.
•	spoilage_sensitivity - intrinsic sensitivity of the product (0-1).
•	temp_abuse_events - count of temperature-abuse events.
•	distribution_hours - hours spent in distribution.
•	handling_score - handling-quality score (higher is better).
•	packaging_score - packaging-quality score (higher is better).
•	daily_demand, demand_variability - demand context.
•	day_of_week, is_weekend, month - temporal context.
•	base_price, cost_price, initial_quantity, supplier_score - product/supplier context.

***Decision variables (exclude, taken after risk is assessed)**:

•	markdown_applied, discount_pct, selling_price, is_promoted (pricing actions that are themselves responses to perceived risk).

***Outcome/leakage variables (must NOT be used as predictors)***:

•	was_spoiled, quality_grade, units_sold, units_wasted, waste_pct, waste_cost, revenue, profit, profit_margin_pct (all realised after the sales period and hence unavailable at prediction time).

Note: identifier columns (record_id, product_id, product_name, store_id, supplier_id, transaction_date, expiration_date, days_until_expiry) are used only for reference and not as raw model inputs.

**MACHINE LEARNING WORKFLOW**

1.	Problem definition and target framing (bin spoilage_risk into Low/Medium/High).
2.	Data exploration and quality checks (types, ranges, duplicates, missing values).
3.	Data cleaning.
4.	Feature engineering and leakage audit (drop outcome and decision variables).
5.	Exploratory Data Analysis (EDA) with visualisations.
6.	Data preprocessing (scaling, one-hot encoding via a scikit-learn Pipeline).
7.	Stratified train/validation/test split and cross-validation.
8.	Model selection and training.
9.	Model comparison and evaluation (multi-class metrics).
10.	Model improvement (hyperparameter tuning, class-imbalance handling).
11.	Business interpretation and recommendations.

**MACHINE LEARNING TASKS**

The primary task is multi-class classification of spoilage-risk level. Supporting activities include:

Data pre-processing
•	Verify there are no missing values, remove exact duplicates if present.
•	One-hot encode categorical variables (category, region).
•	Scale numeric features for scale-sensitive models (e.g. Logistic Regression, SVM).
Exploratory Data Analysis
•	Analyse the distribution of spoilage_risk and the derived class balance.
•	Visualise relationships between features and risk (correlation, boxplots by class).
Feature engineering & importance
•	Apply the leakage audit to keep only pre-outcome predictors.
• Create new features if required	
•	Identify key drivers via correlation, Random Forest importance, and SHAP.
Model development, comparison & evaluation
•	Train multiple classifiers and compare them on a held-out test set.
•	Evaluate with class-aware metrics and inspect the confusion matrix.
Business interpretation
•	Translate results into recommendations on storage, handling, and packaging.

**MACHINE LEARNING MODEL**

Several supervised learning algorithms will be evaluated, including:

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- XGBoost

A majority-class baseline (DummyClassifier) is included as a reference floor: a useful and good model must beat it on macro-F1, not only on accuracy.

**VALIDATION STRATEGY 6 CLASS IMBALANCE**

•	Split the data into stratified train (70%), validation (15%), and test (15%) sets so class proportions are preserved.
•	Use stratified k-fold cross-validation on the training set for model selection and hyperparameter tuning.
•	With tercile binning, the classes are near-balanced.
•	Fit all pre-processing (scaling, encoding) inside a Pipeline on training data only to avoid information leakage from the test set.

**EVALUATION METRICS**

The classification models will be evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix
- ROC-AUC

**EXPECTED OUTCOME**

The expected outcomes from this project include:

- A cleaned and leakage-audited dataset
- Exploratory data analysis with visualisations
- A validated multi-class spoilage risk prediction model that beats the baseline
- Identification of key factors influencing spoilage risk
- Recommendations for storage, handling, and packaging practices

**TEAM MEMBERS**

- Gladys Genista Tchokogoueko Ngadjui
- Hansel Veigas
- Kanika Sethi
- Krishna Priya
- Teena Elvisha Ferrao

**TASKS ALLOCATION**

Gladys Ngadjui: data collection and cleaning
Krishna Priya: data pre-processing, EDA, data visualisation
Kanika Sethi: statistical analysis, correlation, feature engineering 
Hansel Veigas: ML model development, training and comparison
Teena Elvisha Ferrao: model evaluation, feature importance analysis, final report and presentation

**TECHNOLOGY USED**

Programming Language: Python 3
Libraries: Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, XGBoost, SHAP
Development tools: Jupyter Notebook, Git, GitHub, Visual Studio Code

**SUPERVISOR**
Ghosh Srinjoy






