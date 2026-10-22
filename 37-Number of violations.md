# Number of violations


**Difficulty:** 🟢 Easy


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9728-inspections-that-resulted-in-violations)

---

## ❓ Problem Statement
You are given a dataset of health inspections that includes details about violations. 
Each row represents an inspection, and if an inspection resulted in a violation, the violation_id column will contain a value.

Count the total number of violations that occurred at 'Roxanne Cafe' for each year, based on the inspection date. 
Output the year and the corresponding number of violations in ascending order of the year.

---

## 💻 SQL Solution

```sql

select 
    EXTRACT(YEAR FROM inspection_date) as inspection_year,
    COUNT(violation_id) as n_violations
from sf_restaurant_health_violations
WHERE business_name LIKE 'Roxanne Cafe'
GROUP BY inspection_year
