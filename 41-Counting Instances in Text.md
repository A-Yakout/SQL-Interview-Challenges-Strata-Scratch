# Counting Instances in Text


**Difficulty:** 🔴 Hard


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9814-counting-instances-in-text)

---

## ❓ Problem Statement
Find the number of times the exact words bull and bear appear in the contents column.
Count all occurrences, even if they appear multiple times within the same row. 
Matches should be case-insensitive and only count exact words, that is, exclude substrings like bullish or bearing.


Output the word (bull or bear) and the corresponding number of occurrences.

---

## 💻 SQL Solution

```sql


SELECT
    'bull' as word,
    COUNT(*) AS nentry
FROM google_file_store
WHERE contents LIKE 'bull %' OR contents LIKE '% bull %' OR contents LIKE '% bull'

UNION ALL

SELECT
    'bear' as word,
    COUNT(*) AS nentry
FROM google_file_store
WHERE contents LIKE 'bear %' OR contents LIKE '% bear %' OR contents LIKE '% bear'

/*
-- my code
select 
    'bull' as word,
    SUM(CASE WHEN contents LIKE '%bull %' THEN 1 ELSE 0 end) AS nentry
from google_file_store

UNION ALL

select 
    'bear' as word,
    SUM(CASE WHEN contents LIKE '%bear %' THEN 1 ELSE 0 end) AS nentry
from google_file_store


SELECT 
    'bull' AS word, 
    COUNT(matches) AS nentry
FROM google_file_store, REGEXP_MATCHES(contents, '\bbull\b', 'ig') AS matches

UNION ALL

SELECT 
    'bear' AS word, 
    COUNT(matches) AS nentry
FROM google_file_store, REGEXP_MATCHES(contents, '\bbear\b', 'ig') AS matches;


-- i : case insenstative
-- g : searching global (searching inside all the text)



*/
