# Find all posts which were reacted to with a heart

**Difficulty:** 🟢 Easy
**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10087-find-all-posts-which-were-reacted-to-with-a-heart?code_type=1)

---

## ❓ Problem Statement
Find all posts which were reacted to with a heart. For such posts output all columns from facebook_posts table.
---

---

## 💻 SQL Solution

```sql
select distinct
    r.post_id,
    r.poster,
    p.post_text,
    post_keywords,
    post_date
from facebook_reactions r
JOIN facebook_posts p
ON r.post_id = p.post_id
WHERE reaction = 'heart'
