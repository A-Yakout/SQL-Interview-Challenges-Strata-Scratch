# Top Cool Votes


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10060-top-cool-votes)

---

## ❓ Problem Statement
Find the review_text that received the highest number of  cool votes.
Output the business name along with the review text with the highest number of cool votes.

---

## 💻 SQL Solution

```sql

SELECT
    business_name,
    review_text
FROM(
select 
    business_name,
    cool,
    review_text,
    RANK() OVER(ORDER BY cool DESC) rnk
from yelp_reviews
)t 
WHERE rnk = 1
