# Total Cost Of Orders


**Difficulty:** 🟢 Easy

**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10183-total-cost-of-orders?code_type=1)

---

## ❓ Problem Statement
Find the total cost of each customer's orders. Output customer's id, first name, and the total order cost. Order records by customer's first name alphabetically.

---

## 💻 SQL Solution

```sql
SELECT 
    c.id,
    first_name,
    SUM(total_order_cost) as sum
FROM customers c
INNER JOIN orders o 
ON c.id = o.cust_id
GROUP BY c.id,
    first_name
ORDER BY first_name
