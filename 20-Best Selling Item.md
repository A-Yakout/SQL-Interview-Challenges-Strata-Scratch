# Best Selling Item


**Difficulty:** 🔴 Hard


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10172-best-selling-item)

---

## ❓ Problem Statement
Find the best-selling item for each month (no need to separate months by year). 
The best-selling item is determined by the highest total sales amount, calculated as: total_paid = unitprice * quantity.
A negative quantity indicates a return or cancellation (the invoice number begins with 'C'.
To calculate sales, ignore returns and cancellations. Output the month, description of the item, and the total amount paid.

---

## 💻 SQL Solution

```sql

WITH cte AS (
SELECT
    EXTRACT(MONTH from invoicedate) as month,
    description,
    SUM(unitprice * quantity) as total_paid,
    RANK() OVER(PARTITION BY (EXTRACT(MONTH from invoicedate)) ORDER BY SUM(unitprice * quantity) desc) as rnk
FROM online_retail
WHERE quantity > 0
GROUP BY (EXTRACT(MONTH from invoicedate)) ,description
)
SELECT 
    month,
    description,
    total_paid 
FROM cte
WHERE rnk = 1
ORDER BY month
