# Gift Shop Customer Behavior Analysis


## Project Overview 
### Objective
Understand customer purchasing behavior in a gift shop by:
- Identifying product co-purchases and communities.
- Predicting repeat purchases with machine learning.

Insights help inform merchandising, marketing, and cross-selling strategies.
### Data
Dataset: the **Online Retail dataset** (UCI Machine Learning Repository), that contains transactional records from a UK-based online gift shop (Dec 2010 – Dec 2011).  
Key fields: **InvoiceNo**, **StockCode**, **Description**, **Quantity**, **InvoiceDate**, **UnitPrice**, **CustomerID**, **Country**.

## Tools & Technologies
- **Python** – primary programming language  
- **Pandas & NumPy** – data manipulation and feature engineering  
- **Matplotlib & Seaborn** – data and network visualization  
- **NetworkX** – product network analysis and Louvain community detection  
- **Machine Learning** – CatBoost (classification), FP-Growth (market basket analysis)

## Methodology
1. **Exploratory Data Analysis (EDA)** – purchase/return distributions, quantity vs price, retail/wholesale segmentation.  
2. **Cohort Analysis** – customer retention over time, seasonal trends.  
3. **Predictive Modeling** – CatBoost classifier for repeat purchase prediction.  
4. **Product Relationships & Communities** – FP-Growth for frequent itemsets, Louvain method for network communities, product co-purchase visualizations.

## Key Insights
### 1. Returns
   Although returns per transaction are rare (~2%), more than a third of customers (~37%) have made at least one return.
   ![Returns by Transactions and Customers](images/purchases_vs_returns_1.png)
### 2. Retail vs Wholesale
   Retail orders are much more often; wholesale orders correspond to large-quantity purchases with volume discounts.
   ![Order Size and Unit Price](images/unit_price_by_quantity.png)
### 3. Retention
   Retention drops quickly after the first purchase; Dec 2010 cohort shows stronger repeat behavior.
   ![Cohort Retention](images/cohorts.png)
### 4. Repeat Purchase Prediction Model
   The CatBoost repeat-purchase model achieved a ROC AUC of 0.78, enabling identification of customers likely to make repeat purchases.
### 5. Product Communities
   A few popular products drive most co-purchases, forming coherent communities (herb markers, hand warmers, bags).
   ![Top 3 Louvain Communities](images/product__top_communities.png)

## Business Recommendations
- **Customer Retention:** Focus on early engagement and seasonal campaigns, especially during the first purchase period, to reduce early churn (see Cohort Retention in Key Insights)  
- **Marketing & Personalization:** Target likely repeat buyers using predictive modeling results. The Catboost model (ROC AUC = 0.78) can help identify high-probability repeat customers, enabling more effective personalized campaigns (see Repeat Purchase Prediction Model)  
- **Product & Merchandising:** Bundle tightly connected products; use popular items for cross-selling; recommend similar products (based on Top 3 Louvain Product Communities).

## Appendices
### Table 1: Louvain Community Node Explanation (Top 3 Communities)

| #  | Community 16                  | Community 0                 | Community 26                |
|----|-------------------------------|-----------------------------|-----------------------------|
| 1  | 85099B: JB RED<br>JUMBO BAG RED RETROSPOT       | 22916: HM THYME<br>HERB MARKER THYME            | 22633: HW UNION<br>HAND WARMER UNION JACK       |
| 2  | 20725: LB RED<br>LUNCH BAG RED RETROSPOT       | 22917: HM ROSEMARY<br>HERB MARKER ROSEMARY      | 22866: HW SCOTTY<br>HAND WARMER SCOTTY DOG DESIGN |
| 3  | 22383: LB SUKI<br>LUNCH BAG SUKI DESIGN       | 22918: HM PARSLEY<br>HERB MARKER PARSLEY       | 22865: HW OWL<br>HAND WARMER OWL DESIGN        |
| 4  | 20727: LB BLACK<br>LUNCH BAG BLACK SKULL      | 22920: HM BASIL<br>HERB MARKER BASIL           | 23439: HW RED<br>HAND WARMER RED LOVE HEART    |
| 5  | 22386: JB PINK<br>JUMBO BAG PINK POLKADOT    | 22919: HM MINT<br>HERB MARKER MINT             | 22867: HW BIRD<br>HAND WARMER BIRD DESIGN     |
