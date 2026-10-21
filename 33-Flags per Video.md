# Flags per Video


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/2102-flags-per-video)

---

## ❓ Problem Statement
For each video, find how many unique users flagged it. 
A unique user can be identified using the combination of their first name and last name. 
Do not consider rows in which there is no flag ID.

---

## 💻 SQL Solution

```sql

select
video_id,
COUNT(DISTINCT CONCAT(COALESCE(user_firstname,''),' ',COALESCE(user_lastname,''))) as num_unique_users
from user_flags
WHERE flag_id IS NOT NULL
GROUP BY video_id;
