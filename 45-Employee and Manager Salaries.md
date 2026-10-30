# Employee and Manager Salaries


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9894-employee-and-manager-salaries)

---

## ❓ Problem Statement
Find employees who are earning more than their managers. Output the employee's first name along with the corresponding salary.

---

## 💻 SQL Solution

```sql

SELECT
    empl.first_name,
    empl.salary
FROM employee empl
JOIN employee mgr
ON empl.manager_id = mgr.id
WHERE empl.salary > mgr.salary
