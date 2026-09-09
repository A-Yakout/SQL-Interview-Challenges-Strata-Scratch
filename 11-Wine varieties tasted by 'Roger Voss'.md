# Wine varieties tasted by 'Roger Voss'


**Difficulty:** 🟢 Easy


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10024-wine-varieties-tasted-by-roger-voss?code_type=1)

---

## ❓ Problem Statement
Find wine varieties tasted by 'Roger Voss' and with a value in the 'region_1' column of the dataset.
Output unique variety names only.

---

## 💻 SQL Solution

```sql

SELECT 
    DISTINCT variety
FROM winemag_p2
WHERE taster_name = 'Roger Voss' AND region_1 IS NOT NULL
