# Finding Updated Records

**Difficulty:** 🟢 Easy
**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10299-finding-updated-records?code_type=1)

---

## ❓ Problem Statement
We have a table with employees and their salaries; however, some of the records are old and contain outdated salary information. Since there is no timestamp, assume salary is non-decreasing over time.
You can consider the current salary for an employee is the largest salary value among their records.
If multiple records share the same maximum salary, return any one of them. Output their id, first name, last name, department ID, and current salary. 
Order your list by employee ID in ascending order.
---

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
