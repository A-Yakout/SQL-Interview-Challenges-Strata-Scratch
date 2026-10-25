# Monthly Percentage Difference


**Difficulty:** 🔴 Hard


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10319-monthly-percentage-difference)

---

## ❓ Problem Statement
Given a table of purchases by date, calculate the month-over-month percentage change in revenue. 
The output should include the year-month date (YYYY-MM) and percentage change,
rounded to the 2nd decimal point, and sorted from the beginning of the year to the end of the year.
The percentage change column will be populated from the 2nd month forward and can be calculated as ((this month's revenue - last month's revenue) / last month's revenue)*100.

---

## 💻 SQL Solution

```sql

WITH cte AS (
SELECT 
    DATE_TRUNC('month',created_at) AS year_month,
    SUM(value) as revenue,
    LAG(SUM(value)) OVER(ORDER BY DATE_TRUNC('month',created_at)) as last_mnth
FROM sf_transactions
GROUP BY DATE_TRUNC('month',created_at)
)
SELECT 
    year_month,
    ROUND((revenue - last_mnth) / last_mnth*100,2) as revenue_diff_pct
FROM cte
