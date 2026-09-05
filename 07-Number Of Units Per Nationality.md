# Number Of Units Per Nationality


**Difficulty:** 🟡 Medium

**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10156-number-of-units-per-nationality?code_type=1)

---

## ❓ Problem Statement
Write a query that returns how many different apartment-type units (counted by distinct unit_id) are owned by people under 30, grouped by their nationality.
Sort the results by the number of apartments in descending order.

---
## 🧠 My Approach (Business Logic)
1- Wrote CTE to get hosts with age less than 30 .

2- In the outer query filtered the rows by getting only apartment-type units and counted by distinct unit_id then grouped by their nationality .

---

## 💻 SQL Solution

```sql

WITH cte AS (
SELECT 
    host_id,
    nationality,
    age
FROM airbnb_hosts h
WHERE age < 30
) 
SELECT
    nationality,
    COUNT(DISTINCT unit_id) as apartment_count
FROM cte c 
JOIN airbnb_units u 
ON c.host_id = u.host_id
WHERE unit_type = 'Apartment'
GROUP BY nationality
ORDER BY apartment_count DESC
