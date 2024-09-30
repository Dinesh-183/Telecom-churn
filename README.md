# Telecom Churn Case Study

## Problem Statement

### Business Problem Overview

In the telecom industry, customers can choose from multiple service providers and frequently switch operators. This competitive landscape results in an annual churn rate of 15-25%. Since acquiring a new customer is 5-10 times more expensive than retaining an existing one, customer retention has become increasingly important. For many established operators, retaining high-value customers is the primary business goal.

To reduce customer churn, telecom companies must predict which customers are at high risk of leaving.

This project will analyze customer-level data from a leading telecom firm to build predictive models that identify customers at high risk of churn and highlight the main indicators of churn.

### Understanding and Defining Churn

The telecom industry primarily operates under two payment models: postpaid (where customers pay a monthly or annual bill after using services) and prepaid (where customers pay or recharge in advance). 

In the postpaid model, customers typically inform their provider before switching, making churn easy to identify. However, in the prepaid model, customers can stop using services without notice, complicating the determination of whether they have actually churned or are temporarily inactive (e.g., traveling).

Thus, predicting churn is particularly critical for prepaid customers, especially since this model is predominant in India and Southeast Asia, while postpaid is more common in Europe and North America.

### Definitions of Churn

Churn can be defined in various ways:

- **Revenue-based churn**: Customers who have not utilized any revenue-generating services (like mobile internet or outgoing calls) over a specific timeframe. A common metric is identifying those who generate less than INR 4 per month. However, this definition may overlook users who primarily receive calls without generating revenue.

- **Usage-based churn**: Customers who have not engaged in any usage—incoming or outgoing—over a period. A limitation of this definition is that if usage ceases for a defined period (e.g., two months), it may be too late for retention efforts.

For this project, we will use the usage-based definition to define churn.

### High-value Churn

In the Indian and Southeast Asian markets, approximately 80% of revenue comes from the top 20% of customers (high-value customers). Therefore, reducing churn among these individuals can significantly minimize revenue loss. We will define high-value customers based on specific metrics and focus our churn predictions on this group.

### Understanding the Business Objective and the Data

The dataset contains customer-level information over four consecutive months: June (6), July (7), August (8), and September (9). The objective is to predict churn in September using data from the preceding three months. Understanding typical customer behavior during churn will enhance prediction accuracy.

### Understanding Customer Behavior During Churn

Customers usually do not switch providers suddenly; rather, they transition gradually. In churn prediction, we categorize customer behavior into three phases:

1. **Good Phase**: Customers are satisfied with the service.
2. **Action Phase**: Customer dissatisfaction arises due to factors like competitive offers or service quality issues. Identifying high-risk customers during this phase allows for corrective actions.
3. **Churn Phase**: Customers are considered to have churned. Data from this phase is not available during prediction; thus, we label churn based on this phase and exclude corresponding data.

In our four-month window, June and July represent the good phase, August is the action phase, and September is the churn phase.

### Dataset and Data Dictionary

The dataset can be downloaded as needed. The accompanying data dictionary provides definitions for commonly used abbreviations.

### Data Preparation

Key steps in data preparation include:

- **Feature Derivation**: Creating new features based on business insights to differentiate effective models.
- **High-value Customer Filtering**: Identifying high-value customers as those whose recharge amounts are at or above the 70th percentile of average recharge amounts during the good phase.
- **Churn Tagging**: Classifying churners based on September's activity—those with no calls or internet usage are marked as churned (1), while others are marked as non-churned (0). Attributes related to September will be removed post-tagging.

### Modeling

We will develop models aimed at:

1. Predicting whether high-value customers will soon churn.
2. Identifying significant predictors of churn to understand why customers switch providers.

Given the large number of attributes, we will employ dimensionality reduction techniques like PCA before building predictive models. Due to low overall churn rates (5-10%), we will also implement strategies to address class imbalance.

Steps include:

- Preprocessing data (formatting columns, addressing missing values).
- Conducting exploratory analysis for insights.
- Feature derivation.
- Reducing variables with PCA.
- Training various models while tuning hyperparameters.
- Evaluating models with metrics that prioritize identifying churners over non-churners.

While one model may predict churn effectively, it might not reveal important features influencing decisions due to PCA's interpretability challenges. Therefore, we will create an additional model focused on identifying key predictors using logistic regression or tree-based methods while managing multi-collinearity when necessary.

After identifying important features, we will visually present them through plots or summary tables. Finally, we will recommend strategies for managing customer churn based on our findings.
