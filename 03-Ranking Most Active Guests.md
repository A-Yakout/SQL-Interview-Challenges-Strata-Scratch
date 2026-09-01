# Ranking Most Active Guests

**Difficulty:** 🟡 Medium
**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10159-ranking-most-active-guests?code_type=1)

---

## ❓ Problem Statement
Identify the most engaged guests by ranking them according to their overall messaging activity. 
The most active guest, meaning the one who has exchanged the most messages with hosts, should have the highest rank.
If two or more guests have the same number of messages, they should have the same rank. Importantly, the ranking shouldn't skip any numbers, 
even if many guests share the same rank. 
Present your results in a clear format, showing the rank, guest identifier, and total number of messages for each guest, ordered from the most to least active.

---
## 🧠 My Approach (Business Logic)
1- Wrote CTE to get the total messages for each guest.

2- From this CTE used 'DENSE_RANK()' to get the rank of the guests with the ability to have multiple guests with the same rank, and without skipping .

---

## 💻 SQL Solution

```sql
WITH cte AS (
SELECT 
    id_guest,
    SUM(n_messages) as sum_n_messages
FROM airbnb_contacts
GROUP BY id_guest
)

select 
    DENSE_RANK() OVER(ORDER BY sum_n_messages DESC) AS ranking,
    id_guest,
    sum_n_messages
from cte;
