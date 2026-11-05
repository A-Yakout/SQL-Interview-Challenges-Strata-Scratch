# Income By Title and Gender


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10077-income-by-title-and-gender)

---

## ❓ Problem Statement
Find the average total compensation based on employee titles and gender. 
Total compensation is calculated by adding both the salary and bonus of each employee. 
However, not every employee receives a bonus so disregard employees without bonuses in your calculation. Employee can receive more than one bonus.
Output the employee title, gender (i.e., sex), along with the average total compensation.

---

## 💻 SQL Solution

```sql

WITH cte AS (
SELECT
    worker_ref_id,
    SUM(bonus) as total_bonus
FROM sf_bonus
GROUP BY worker_ref_id
), cte2 AS (
SELECT
    id,
    first_name,
    employee_title,
    sex,
    (salary + total_bonus) AS total_compensation,
    total_bonus
FROM sf_employee e
JOIN cte b -- Inner join to ignore employee without bonus as required
ON e.id = b.worker_ref_id
)
SELECT
    employee_title,
    sex,
    AVG(total_compensation) as avg_compensation
FROM cte2 
GROUP BY 
    employee_title,
    sex
