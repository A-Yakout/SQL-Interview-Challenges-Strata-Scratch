# Find all possible varieties which occur in either of the winemag datasets


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10025-find-all-possible-varieties-which-occur-in-either-of-the-winemag-datasets)

---

## ❓ Problem Statement
Find all possible varieties which occur in either of the winemag datasets.
Output unique variety values only.
Sort records based on the variety in ascending order.

---

## 💻 SQL Solution

```sql

SELECT 
    DISTINCT variety
FROM winemag_p1 
UNION
SELECT 
    DISTINCT variety
FROM winemag_p2
ORDER BY variety 
