# Workers With The Highest Salaries


**Difficulty:** 🟡 Medium

**Topic:** Window Function

**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10353-workers-with-the-highest-salaries?code_type=1)

---

## ❓ Problem Statement
A company wants to review compensation only for workers who have an official job title on record, 
since pay can't be properly benchmarked against a role that isn't documented.
Find the job titles of the workers with the highest salary among those who have a matching record in the title table. 
If multiple workers share the highest salary, include all of their job titles.

Output the job title(s), sorted alphabetically.

---
## 🧠 My Approach (Business Logic)
1- Used 'RANK()' to get the rank of salaries among all departments .

2- In the outer query we get highest salaries with rank equals to one .

---

## 💻 SQL Solution

```sql

SELECT 
    worker_title as best_paid_title
FROM(
SELECT
    worker_id,
    worker_title,
    salary,
    RANK() OVER(ORDER BY salary desc) as rnk
FROM worker w
RIGHT JOIN title t
ON w.worker_id = t.worker_ref_id
) t 
WHERE rnk = 1
