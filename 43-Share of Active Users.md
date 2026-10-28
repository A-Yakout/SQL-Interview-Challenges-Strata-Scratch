# Share of Active Users


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/2005-share-of-active-users)

---

## ❓ Problem Statement
Calculate the percentage of users who are both from the US and have an 'open' status, as indicated in the fb_active_users table.

---

## 💻 SQL Solution

```sql

SELECT
    SUM(CASE WHEN country = 'USA' AND status = 'open' THEN 100.0 ELSE 0 END) / COUNT(*) AS us_active_share
FROM fb_active_users;
