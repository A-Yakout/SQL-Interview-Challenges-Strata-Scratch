# Second Highest Salary


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9892-second-highest-salary)

---

## ❓ Problem Statement
Find the second highest salary of employees.


---

## 💻 SQL Solution

```sql

SELECT
    salary
FROM(
SELECT
    id,
    salary,
    ROW_NUMBER() OVER(ORDER BY salary DESC) as rnk
FROM employee
) t 
WHERE rnk = 2
