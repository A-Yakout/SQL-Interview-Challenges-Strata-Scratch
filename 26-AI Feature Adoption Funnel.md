# AI Feature Adoption Funnel


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/10583-ai-feature-adoption-funnel)

---

## ❓ Problem Statement
The Data Science and Analytics team wants to see how many users progress through each stage of an AI writing feature's adoption funnel: 
impression (saw the feature), first_use (tried it at least once), and repeat_use (used it more than once). Count the unique users at each stage.

Because of a tracking gap, some users have a repeat_use event but no first_use event; they must still count toward first_use.

---

## 💻 SQL Solution

```sql

SELECT
    'impression' as funnel_stage,
    COUNT(DISTINCT user_id) as unique_users
FROM ai_funnel_events
WHERE event_type = 'impression'

UNION ALL

SELECT
    'first_use' as funnel_stage,
    COUNT(DISTINCT user_id) as unique_users
FROM ai_funnel_events
WHERE event_type IN ('first_use','repeat_use')

UNION ALL

SELECT
    'repeat_use' as funnel_stage,
    COUNT(DISTINCT user_id) as unique_users
FROM ai_funnel_events
WHERE event_type = 'repeat_use'

/* My code trying to solve it


select 
    event_type as funnel_stage,
    COUNT(DISTINCT user_id) as unique_users
from ai_funnel_events
GROUP BY event_type

SELECT 
    user_id,
    event_type,
    RANK() OVER(PARTITION BY user_id ORDER BY event_type)
FROM ai_funnel_events

*/
