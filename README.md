# DataAnalytics-Assessment

This repository contains my SQL solutions for a Data Analyst proficiency assessment. The evaluation is based on solving real-world business problems using SQL across multiple database tables.

---

## Questions & Explanations

### **Q1. High-Value Customers with Multiple Products**
**Objective:** Identify customers who have at least one funded savings plan **AND** one funded investment plan, ordered by total deposits.

**Approach:**
- Join `users_customuser`, `savings_savingsaccount`, and `plans_plan`.
- Filter `savings_savingsaccount` where `confirmed_amount > 0` and `is_regular_savings = 1`.
- Filter `plans_plan` where `confirmed_amount > 0` and `is_a_fund = 1`.
- Group by customer and count each plan type.
- Sum total deposits and order by it descending.

---

### **Q2. Transaction Frequency Analysis**
**Objective:** Analyze transaction frequency and segment customers as "High", "Medium", or "Low" frequency users.

**Approach:**
- Count the number of transactions per customer.
- Determine the number of months covered in the data.
- Divide transactions by month to get average monthly frequency.
- Use a `CASE` statement to assign frequency category.
- Aggregate by category.

---

### **Q3. Account Inactivity Alert**
**Objective:** Find active accounts (savings or investment) with **no transactions** in the past **365 days**.

**Approach:**
- Use `last_transaction_date` from both `savings_savingsaccount` and `plans_plan`.
- Compare `last_transaction_date` to `CURRENT_DATE` or a fixed reference date.
- Calculate `inactivity_days` as the difference.
- Filter where `inactivity_days > 365`.

---
 
### **Q4. Customer Lifetime Value (CLV) Estimation**
**Objective:** Estimate CLV for each customer using a simplified formula:

CLV = (total_transactions / tenure_months) * 12 * avg_profit_per_transaction

**Approach:**
- Calculate tenure using the difference between `signup_date` and `CURRENT_DATE` in months.
- Sum up transaction values for each customer (converted from kobo).
- Compute average profit per transaction as 0.1% of transaction value.
- Plug into the CLV formula and order by highest CLV.

---

## Challenges & Resolutions

- **Kobo Conversion**: All monetary values were in kobo and required conversion to naira by dividing by 100.
- **Date Calculations**: Standardized date logic using SQL functions like `DATEDIFF()` or `TIMESTAMPDIFF()` (depending on SQL dialect).
- **Handling Joins**: Carefully managed LEFT/INNER joins to ensure completeness without duplication.
- **Frequency Categorization**: Ensured accuracy in monthly breakdowns using either a fixed period or dynamic month counts.

---

## How to Use

1. Clone this repo.
2. Open the `.sql` files in your preferred SQL editor.
3. Modify or run the queries against the provided database schema.

---

## Contact

**Onyejaka Kasarachi Sixtus**  
Email: [kasarachionyejaka@gmail.com](mailto:kasarachionyejaka@gmail.com)  
