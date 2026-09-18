# Customer Churn Prevention System

Self-directed portfolio project analyzing a public bank customer dataset (10,000 records) to practice segmentation analysis, DAX, and dashboard storytelling in Power BI.

# Overview

Bank customer churn is a well-known analytics case study. I used this dataset to build an end-to-end analysis: from raw data to a segmented, interactive Power BI dashboard, with the goal of identifying which customer groups are most likely to churn and why.

Dataset: 10,000 customer records — demographics, account details, product usage, churn flag (Exited: 1 = churned, 0 = retained) Baseline churn rate: 20.4% (2,037 of 10,000 customers)

# Objectives
- Identify which customer segments churn at the highest rate
- Understand which attributes correlate with churn (geography, age, product count, activity status, credit score, balance, tenure)
- Build an interactive Power BI dashboard to explore these patterns
- Practice translating raw findings into clear, prioritized recommendations
# Approach

**1.** Data preparation Validated data quality (no missing values, no duplicates), then used Power Query to engineer segmentation columns: age groups, balance bands, credit score segments, product category, and activity status.

**2.** Segmentation analysis Broke down churn rate across 7 dimensions:

|**Segment**  	|                  **Finding**                                                    |
|---------------|---------------------------------------------------------------------------------|
|Geography      |Germany churns at 32.4% vs. ~16-17% in France/Spain                              |
|Age	          |      40–50 age group has the highest churn (56%)                                 |
|Product count  |   	Single-product customers churn at 27.7% vs. 10.3% for multi-product customers |
|Activity status|   	Inactive members churn at 26.9% vs. 14.3% for active members                  |
|Credit score	  |   Lowest band (400–600) churns at 29.8%                                           |
|Balance	Churned|    customers carry a higher average balance (€91,810) than retained customers (€72,745) |
|Tenure          | New customers (0–2 years) churn more (23.5%) than mid-tenure customers                 |

**3.** Dashboard build Built a 4-page interactive Power BI dashboard: Executive Summary, Customer Segmentation, Financial Impact modeling, and Risk Analysis, with drill-through, cross-filtering, and a custom risk-scoring DAX measure combining geography, age, product count, and activity signals.

**Sample DAX measures:**

dax
Churn Rate = DIVIDE([Churned Customers], [Total Customers], 0) * 100

Customer Risk Score =
VAR GeoScore = IF(Geography = "Germany", 30, 10)
VAR AgeScore = IF(Age >= 40 && Age < 60, 25, 10)
VAR ProductScore = IF(NumOfProducts = 1, 20, 5)
VAR ActivityScore = IF(IsActiveMember = 0, 25, 5)
RETURN GeoScore + AgeScore + ProductScore + ActivityScore

**4.** Hypothetical impact modeling To practice connecting analysis to business value, I modeled what a targeted retention strategy could look like if applied in a real setting — e.g., reducing churn from 20.4% to ~16-17% by prioritizing the highest-risk segments (Germany, age 40–50, single-product, inactive members). These are illustrative estimates based on the dataset, not delivered business outcomes.

# Key takeaways
- Inactivity and single-product ownership were the strongest behavioral churn indicators in this dataset
- Germany's churn rate stood out sharply from other markets, worth flagging as a segment-specific issue in a real business context
- Multi-dimensional segmentation surfaces patterns that a single "overall churn rate" number hides
# Tools

Power BI Desktop · DAX · Power Query · Excel


Status: Self-directed practice project · Dataset: public/anonymized bank churn dataset (10,000 records)
