# Hour Of Highest Gas Expense


**Difficulty:** 🟢 Easy


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10005-hour-of-highest-gas-expense?code_type=1)

---

## ❓ Problem Statement
Find the hour of the single ride with the highest gasoline cost.
Assume only one ride has this maximum, so exactly one hour qualifies.

---

## 💻 SQL Solution

```sql

SELECT
    hour
FROM(
SELECT
    hour,
    gasoline_cost,
    RANK() OVER(ORDER BY gasoline_cost DESC) rnk
FROM lyft_rides
)t 
WHERE rnk = 1
