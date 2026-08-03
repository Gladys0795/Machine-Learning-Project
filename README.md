**Food Spoilage Prediction Using Machine Learning**

***Predicting whether a food product is likely to spoil using machine learning.***

**PROJECT OVERVIEW**

Food spoilage is a major cause of food waste, financial loss, and inefficient inventory management across the food supply chain. Identifying products that are at risk of spoiling before they become unusable helps retailers make better stocking, pricing, and storage decisions.

This project develops a binary classification machine learning model that predicts whether a food product is likely to spoil using product characteristics, storage conditions, demand, and supply-chain information.

The project follows a complete end-to-end machine learning workflow, including data preprocessing, exploratory data analysis (EDA), feature engineering, model development, evaluation, and interpretation.

The original dataset is a synthetically generated retail dataset containing information about perishable products.

Original Records: **100,000**
Original Features:**42**
Missing Values: **None**
Dataset Used: **Cleaned & Balanced**
Final Records: **38,884**
Target Variable: **was_spoiled**

Target Variable: 
    **0	- Not Spoiled**
    **1 - Spoiled**

The balanced dataset contains:
  **19,442 Spoiled products**
  **19,442 Non-spoiled products**
  **50:50 class distribution**

**Selected Features**

The model uses only information available before spoilage occurs.
    'category',
    'region',
    'shelf_life_days',
    'days_remaining_at_purchase',
    'storage_temp',
    'temp_deviation',
    'initial_quantity',
    'spoilage_sensitivity',
    'daily_demand',
    'demand_variability',
    'temp_abuse_events',
    'distribution_hours',
    'handling_score',
    'packaging_score',
    'supplier_score

**RESEARCH QUESTION**

Can machine learning accurately predict the spoilage risk level of perishable retail products from storage, handling, and product features by using only information available before the sales outcome to support inventory management and reduce food waste?

**Data Leakage Prevention**

Several columns were intentionally removed because they become available after spoilage or sales occur.

Examples include:

  Selling Price
  Discount Percentage
  Revenue
  Profit
  Units Sold
  Units Wasted
  Waste Cost
  Profit Margin

Removing these variables prevents data leakage, allowing the model to learn only from information available before prediction.

**Machine Learning Workflow**

The notebook follows these stages:

  Data Collection
  Data Cleaning
  Exploratory Data Analysis (EDA)
  Statistical Analysis
  Feature Engineering
  Data Preprocessing
  Train / Validation / Test Split
  Model Training
  Model Evaluation

**Exploratory Data Analysis**

The project includes visualizations such as:

  Target variable distribution
  Feature distributions
  Correlation heatmap
  Boxplots
  Histograms
  Count plots  

**Machine Learning Models**

The following supervised learning algorithms are evaluated:
    Logistic Regression
    Random Forest

**Model Evaluation**

Models are compared using:

  Accuracy
  Precision
  Recall
  F1-Score

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






