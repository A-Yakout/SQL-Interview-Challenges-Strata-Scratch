# Salary Less Than Twice The Average


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/2110-salary-less-than-twice-the-average)

---

## ❓ Problem Statement
Write a query to get the list of managers whose salary is less than twice the average salary of employees reporting to them.
For these managers, output their ID, salary and the average salary of employees reporting to them.

---

## 💻 SQL Solution

```sql

-- First: Getting the informations of the employees and salary average of each manager team
WITH team AS (
SELECT
    h.manager_empl_id,
    AVG(e.salary) AS avg_employee_salary
FROM map_employee_hierarchy h
LEFT JOIN dim_employee e
ON h.empl_id = e.empl_id
GROUP BY h.manager_empl_id
)
-- Second: Getting the information of the manager with his salary 
-- Filtering the managers who get less than twice the employee average salary
SELECT
    t.manager_empl_id,
    mgr.salary as manager_salary,
    avg_employee_salary
FROM team t
LEFT JOIN dim_employee mgr
ON mgr.empl_id = t.manager_empl_id
WHERE mgr.salary < 2*avg_employee_salary
