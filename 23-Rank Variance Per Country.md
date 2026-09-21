# Rank Variance Per Country


**Difficulty:** 🔴 Hard


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/2007-rank-variance-per-country)

---

## ❓ Problem Statement
Compare the total number of comments made by users in each country during December 2019 and January 2020.
For each month, rank countries by their total number of comments in descending order.
Countries with the same total should share the same rank, and the next rank should increase by one (without skipping numbers).

Return the names of the countries whose rank improved from December to January (that is, their rank number became smaller).

---

## 💻 SQL Solution

```sql

WITH dec AS (
SELECT 
    country,
    SUM(number_of_comments) AS total,
    DENSE_RANK() OVER(ORDER BY SUM(number_of_comments) DESC) AS rnk
FROM fb_comments_count c
JOIN fb_active_users u
ON c.user_id = u.user_id
WHERE
EXTRACT(YEAR FROM created_at) = 2019 
  AND
EXTRACT(MONTH FROM created_at) = 12
GROUP BY u.country
), jan AS (
SELECT 
    country,
    SUM(number_of_comments) AS total,
    DENSE_RANK() OVER(ORDER BY SUM(number_of_comments) DESC) AS rnk
FROM fb_comments_count c
JOIN fb_active_users u
ON c.user_id = u.user_id
WHERE
EXTRACT(YEAR FROM created_at) = 2020
AND
EXTRACT(MONTH FROM created_at) = 1
GROUP BY u.country
)
SELECT
    j.country
FROM dec d 
JOIN jan j 
ON d.country = j.country
WHERE j.rnk < d.rnk
