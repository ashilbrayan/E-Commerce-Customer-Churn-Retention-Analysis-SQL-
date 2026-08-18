---

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

1. Create a database (e.g., `ecomm`).
2. Import the original dataset into a table (commonly named `customer_churn` or similar).
3. Execute the SQL script step-by-step or as a complete workflow.
4. Review the results of each analytical query.

```sql
-- Example: Create database
CREATE DATABASE IF NOT EXISTS ecomm;
USE ecomm;