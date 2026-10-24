# Processed Ticket Rate By Type


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9781-find-the-rate-of-processed-tickets-for-each-type)

---

## ❓ Problem Statement
Find the processed rate of tickets for each type. 
The processed rate is defined as the number of processed tickets divided by the total number of tickets for that type.

Round this result to two decimal places.

---

## 💻 SQL Solution

```sql

select 
    type,
    ROUND(SUM(CASE WHEN processed = TRUE THEN 1.0 ELSE 0 end) / COUNT(*),2) AS processed_rate
from facebook_complaints
GROUP BY type
