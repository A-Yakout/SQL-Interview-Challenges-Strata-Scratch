# Consecutive Days


**Difficulty:** 🔴 Hard


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/2054-consecutive-days?code_type=1)

---

## ❓ Problem Statement
Find all the users who were active for 3 consecutive days or more.

---

## 💻 SQL Solution

```sql

SELECT
    user_id
FROM(
SELECT
    user_id,
    record_date,
    LEAD(record_date) OVER(PARTITION BY user_id ORDER BY record_date) AS nxt_one,
    LEAD(record_date,2) OVER(PARTITION BY user_id ORDER BY record_date) AS nxt_two
FROM sf_events
) t 
WHERE (nxt_one::date - record_date::date) = 1 
AND (nxt_two::date - nxt_one::date) = 1
