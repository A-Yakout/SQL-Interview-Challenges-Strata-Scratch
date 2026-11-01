# Department Workforce Analysis


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/2170-department-workforce-analysis)

---

## ❓ Problem Statement
The workforce planning team is analyzing department growth since the company's expansion, focusing on teams that have grown substantially.


For each department with 5 or more employees hired after 2020, return the name, headcount, total payroll, and average salary.

---

## 💻 SQL Solution

```sql

SELECT
    department,
    COUNT(id) as headcount,
    SUM(salary) as total_payroll,
    AVG(salary) as avg_salary
from techcorp_workforce
WHERE EXTRACT(YEAR FROM joining_date) >= 2020
GROUP BY department
HAVING COUNT(id) > 5
