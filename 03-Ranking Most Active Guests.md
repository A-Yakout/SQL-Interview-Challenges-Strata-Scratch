# Ranking Most Active Guests

**Difficulty:** 🟡 Medium
**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10159-ranking-most-active-guests?code_type=1)

---

## ❓ Problem Statement
Identify the most engaged guests by ranking them according to their overall messaging activity. 
The most active guest, meaning the one who has exchanged the most messages with hosts, should have the highest rank.
If two or more guests have the same number of messages, they should have the same rank. Importantly, the ranking shouldn't skip any numbers, 
even if many guests share the same rank. 
Present your results in a clear format, showing the rank, guest identifier, and total number of messages for each guest, ordered from the most to least active.

---
## 🧠 My Approach (Business Logic)
1- Wrote CTE to get the total messages for each guest.

2- From this CTE used 'DENSE_RANK()' to get the rank of the guests with the ability to have multiple guests with the same rank, and without skipping .

---

## 💻 SQL Solution

```sql
WITH rnk_salaries AS (
select 
    id,
    first_name,
    last_name,
    department_id,
    salary,
    ROW_NUMBER() OVER(PARTITION BY id ORDER BY salary DESC) as rnk
from ms_employee_salary
)
SELECT
    id,
    first_name,
    last_name,
    department_id,
    salary
FROM rnk_salaries 
WHERE rnk = 1
