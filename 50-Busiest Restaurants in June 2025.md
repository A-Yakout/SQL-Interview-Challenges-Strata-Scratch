# Busiest Restaurants in June 2025


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10789-busiest-restaurants-in-june-2025)

---

## ❓ Problem Statement
The Merchant team at a food delivery marketplace wants to spotlight its busiest restaurants in the June 2025 partner newsletter. 
Find the top 5 restaurants by number of delivered orders placed in June 2025.
Count only orders that were delivered, and assign each order to the month in which it was placed. 
If restaurants tie at the cutoff, include all tied restaurants, so the result can contain more than 5 rows.

Output the restaurant ID, restaurant name, and number of delivered orders.

---

## 💻 SQL Solution

```sql

WITH deliverd_cnt AS (
SELECT 
    o.restaurant_id,
    name,
    SUM(CASE WHEN status = 'delivered' THEN 1 ELSE 0 END) AS delivered_orders,
    DENSE_RANK() OVER(ORDER BY SUM(CASE WHEN status = 'delivered' THEN 1 ELSE 0 END) DESC) AS rnk
FROM fooddelivery_restaurants r
JOIN fooddelivery_orders o 
ON r.restaurant_id = o.restaurant_id
WHERE EXTRACT(MONTH FROM placed_at) = 6
GROUP BY 
    o.restaurant_id,
    name
)
SELECT 
    restaurant_id,
    name,
    delivered_orders
FROM deliverd_cnt
WHERE rnk <= 5
