# April Admin Employees


**Difficulty:** 🟢 Easy
**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9845-find-the-number-of-employees-working-in-the-admin-department)

---

## ❓ Problem Statement
Find the number of employees working in the Admin department that joined in April or later, in any year.

---

---

## 💻 SQL Solution

```sql
SELECT
COUNT(worker_id) as n_admins 
FROM worker 
WHERE department LIKE 'Admin'
AND EXTRACT(month FROM joining_date) >= 4
