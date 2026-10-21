# Number of Shipments Per Month


**Difficulty:** 🟢 Easy


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/2056-number-of-shipments-per-month)

---

## ❓ Problem Statement
Write a query that will calculate the number of shipments per month. 
The unique key for one shipment is a combination of shipment_id and sub_id. 
Output the year_month in format YYYY-MM and the number of shipments in that month.

---

## 💻 SQL Solution

```sql

SELECT 
    -- DATE_TRUNC('month',shipment_date) AS year_month,
    -- Result: 2021-09-01 ❌
    TO_CHAR(shipment_date,'YYYY-MM') AS year_month,
    -- Result: 2021-09 ✅
    COUNT(CONCAT(shipment_id,sub_id)) AS count
FROM amazon_shipment
GROUP BY TO_CHAR(shipment_date,'YYYY-MM')
