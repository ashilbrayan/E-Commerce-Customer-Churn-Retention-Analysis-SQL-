# E-Commerce Customer Churn Analysis | MySQL

An end-to-end MySQL analytics project focused on understanding customer churn patterns in an e-commerce business. The project covers data cleaning, standardization, feature engineering, and extensive exploratory analysis to uncover key drivers of customer attrition and support data-backed retention strategies.

---

## 📌 Project Overview

E-commerce businesses face significant revenue risk from customer churn. This project analyzes historical transactional and behavioral data to identify patterns related to:

- Customer tenure and engagement
- Preferred payment modes and devices
- Satisfaction scores and complaint behavior
- Purchase frequency, cashback, and order value trends
- Geographic and demographic factors influencing churn

The goal is to generate actionable insights that help the business design targeted retention initiatives.

---

## 🛠️ Tech Stack

- **Database**: MySQL 8.0+
- **Language**: SQL (DDL + DML + Analytical Queries)
- **Key Techniques**:
  - Data cleaning & imputation (mean / mode)
  - Outlier handling
  - Value standardization
  - Feature engineering (new derived columns)
  - Multi-condition filtering, aggregations, and grouping
  - Conditional logic & categorization
  - Joins with a secondary returns table

---

## 📂 Project Structure---

E-Commerce-Customer-Churn-Retention-Analysis-SQL/ ├── ecommerce_churn_analysis.sql    
# Complete SQL script (cleaning + analysis) ├── sql_query_output.png             
# Sample query output screenshot └── README.md


## 🧹 Data Cleaning & Preparation

### Missing Value Imputation
- **Mean imputation** (rounded to nearest integer where required):  
  `WarehouseToHome`, `HourSpendOnApp`, `OrderAmountHikeFromlastYear`, `DaySinceLastOrder`
- **Mode imputation**:  
  `Tenure`, `CouponUsed`, `OrderCount`

### Outlier Handling
- Removed rows where `WarehouseToHome > 100`

### Value Standardization
- `PreferredLoginDevice`: Replaced “Phone” → “Mobile Phone”
- `PreferedOrderCat`: Replaced “Mobile” → “Mobile Phone”
- `PreferredPaymentMode`:  
  - “COD” → “Cash on Delivery”  
  - “CC” → “Credit Card”

### Column Transformations
- Renamed:
  - `PreferedOrderCat` → `PreferredOrderCat`
  - `HourSpendOnApp` → `HoursSpentOnApp`
- Created new columns:
  - `ComplaintReceived` → “Yes” if `Complain = 1`, else “No”
  - `ChurnStatus` → “Churned” if `Churn = 1`, else “Active”
- Dropped original columns: `Churn`, `Complain`

---

## 📊 Key Analytical Insights Covered

The project answers the following business questions:

1. Count of Churned vs Active customers
2. Average tenure and total cashback of churned customers
3. Percentage of churned customers who raised complaints
4. City tier with highest churn among Laptop & Accessory buyers
5. Most preferred payment mode among active customers
6. Total order amount hike for single customers preferring mobile phones
7. Average devices registered by UPI users
8. City tier with the highest overall customer base
9. Gender that used the highest number of coupons
10. Customer count and max hours spent on app by preferred order category
11. Total order count for credit-card users with maximum satisfaction score
12. Average satisfaction score of customers who complained
13. Preferred order category of customers who used more than 5 coupons
14. Top 3 preferred order categories by average cashback
15. Preferred payment modes of customers with ~10 months tenure and >500 orders
16. Churn status breakdown by warehouse-to-home distance categories  
    (Very Close ≤5km | Close ≤10km | Moderate ≤15km | Far >15km)
17. Order details of married customers in City Tier-1 whose order count exceeds the overall average

### Additional Analysis
- Created `customer_returns` table and joined it with churned + complained customers to analyze return behavior.

---

## 🚀 How to Run

1. Create a database (example: `ecomm`).
2. Import the original dataset into a table.
3. Execute the SQL script step-by-step or as a complete workflow.
4. Review the results of each analytical query.

```sql
CREATE DATABASE IF NOT EXISTS ecomm;
USE ecomm;







