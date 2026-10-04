# Thumbs-Up Rate by Model Version


**Difficulty:** 🟢 Easy


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10597-thumbs-up-rate-by-model-version)

---

## ❓ Problem Statement
The Applied Product team wants to compare how well users receive each model version. 
Calculate, for each model version, the percentage of rated responses that received a thumbs-up. 
Responses that were never rated are not counted, and model versions with no rated responses should not appear.

Feedback can be sent more than once for the same response, so count each response only once.

Output the model version and its thumbs-up percentage.

---

## 💻 SQL Solution

```sql

select 
    model_version,
    100 * COUNT(DISTINCT CASE WHEN feedback = 'thumbs_up' THEN response_id END) / COUNT(DISTINCT response_id) AS thumbs_up_pct
from ai_response_feedback
WHERE feedback IS NOT NULL
GROUP BY model_version
