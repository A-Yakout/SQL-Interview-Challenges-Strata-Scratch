# Highest Salary In Department


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9897-highest-salary-in-department)

---

## ❓ Problem Statement
A business wants to identify its highest-paid employee in each department for compensation benchmarking and review. 
Find the employee with the highest salary in each department.

Output the department name, the employee's first name and their salary.
If multiple employees share the highest salary in a department, return all of them.

---

## 💻 SQL Solution

```sql

SELECT
department,
first_name,
salary
FROM(
SELECT 
    department,
    first_name,
    salary,
    RANK() OVER(PARTITION BY department ORDER BY salary DESC) rnk
FROM employee
)t 
WHERE rnk = 1
