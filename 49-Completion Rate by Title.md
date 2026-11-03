# Completion Rate by Title


**Difficulty:** 🟢 Easy


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10803-completion-rate-by-title)

---

## ❓ Problem Statement
The Product Analytics team at a streaming service wants to know which titles viewers actually finish.
For each title with at least 100 viewing sessions, calculate the completion rate: the percentage of its sessions that were completed.
Count every session toward the total, including sessions with zero or missing watch time. 
Round the rate to 1 decimal place.

Output the title name and the completion rate.

---

## 💻 SQL Solution

```sql

SELECT
title_name,
ROUND(SUM(CASE WHEN completed = 1 THEN 100.0 ELSE 0 END) / COUNT(s.title_id),1) AS completion_pct
FROM stream_titles t
JOIN stream_sessions s
ON t.title_id = s.title_id
GROUP BY title_name
HAVING COUNT(session_id) >=100
ORDER BY completion_pct DESC
