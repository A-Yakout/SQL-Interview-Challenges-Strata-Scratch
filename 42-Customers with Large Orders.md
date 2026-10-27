# Customers with Large Orders


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/2172-customers-with-large-orders)

---

## ❓ Problem Statement
The marketing team wants to identify high-value customers for a premium loyalty program.
Find all customers who have placed at least one order over $100. 
Return customer ID and name. Consider all orders regardless of their payment or fulfillment status.

---

## 💻 SQL Solution

```sql

WITH cte AS(
SELECT
    c.customer_id,
    customer_name,
    amount
from online_store_customers c
LEFT JOIN online_store_orders o
ON c.customer_id = o.customer_id
)
SELECT 
    DISTINCT
    customer_id,
    customer_name
FROM cte
WHERE amount > 100
ORDER BY customer_id
