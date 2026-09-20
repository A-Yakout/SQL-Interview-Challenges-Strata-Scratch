# Departments With 5 Employees

**Difficulty:** 🟢 Easy

**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9911-departments-with-5-employees)

---

## ❓ Problem Statement

Find departments with at more than or equal 5 employees.

---

---

## 💻 SQL Solution

```sql

SELECT 
    department
FROM employee
GROUP BY department
HAVING COUNT(*) >= 5
