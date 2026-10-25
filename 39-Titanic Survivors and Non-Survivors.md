# Titanic Survivors and Non-Survivors


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9881-make-a-report-showing-the-number-of-survivors-and-non-survivors-by-passenger-class)

---

## ❓ Problem Statement
Make a report showing the number of survivors and non-survivors by passenger class. 
Classes are categorized based on the pclass value as:

•	First class: pclass = 1
•	Second class: pclass = 2
•	Third class: pclass = 3


Output one row per survival status, with a column for the number of passengers in each class.

---

## 💻 SQL Solution

```sql

SELECT 
    survived,
    SUM(CASE WHEN pclass = 1 THEN 1 ELSE 0 END) AS first_class,
    SUM(CASE WHEN pclass = 2 THEN 1 ELSE 0 END) AS second_class,
    SUM(CASE WHEN pclass = 3 THEN 1 ELSE 0 END) AS third_class
FROM titanic
GROUP BY survived;

/*
select 
    survived,
    SUM(CASE WHEN pclass = 1 AND survived = 1 THEN pclass WHEN pclass = 1 AND survived = 0 THEN 1 END) AS first_class,
    SUM(CASE WHEN pclass = 2 AND survived = 1 THEN 1 WHEN pclass = 2 AND survived = 0 THEN 1 END) AS second_class,
    SUM(CASE WHEN pclass = 3 AND survived = 1 THEN 1 WHEN pclass = 3 AND survived = 0 THEN 1 END) AS third_class
from titanic
GROUP BY survived
*/
