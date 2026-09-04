# Finding Purchases

**Difficulty:** 🟡 Medium

**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10553-finding-purchases?code_type=1)

---

## ❓ Problem Statement
Identify returning active users by finding users who made a repeat purchase within 7 days or less of their previous transaction,
excluding same-day purchases. Output a list of these user_id.

---
## 🧠 My Approach (Business Logic)
1- Wrote CTE to get the current purchase and the next purchase for each user .

2- In the outer query filtered the rows by getting the next purchase which done within 7 days after the first purchase .

---

## 💻 SQL Solution

```sql
WITH cte AS (
SELECT 
    user_id,
    created_at as current_purchase,
    LEAD(created_at,1) OVER(PARTITION BY user_id ORDER BY created_at) nxt_purchase,
    ROW_NUMBER() OVER(PARTITION BY user_id ORDER BY created_at) as rank
from amazon_transactions
)

SELECT
DISTINCT user_id
FROM cte
WHERE 
(nxt_purchase::date - current_purchase::date) BETWEEN 1 AND 7
