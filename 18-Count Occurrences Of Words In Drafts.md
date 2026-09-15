# Count Occurrences Of Words In Drafts


**Difficulty:** 🟡 Medium


**Link:** [View Problem on Strata Scratch](https://platform.stratascratch.com/coding/9817-find-the-number-of-times-each-word-appears-in-drafts?code_type=1)

---

## ❓ Problem Statement
Find the number of times each word appears in the contents column across all rows in the google_file_store dataset.
Output two columns: word and occurrences.

---

## 💻 SQL Solution

```sql

SELECT
    word,
    COUNT(word) as occurrences
FROM ( 
select 
    filename,
    translate(lower(STRING_TO_TABLE(contents,' ')), '.,', '') as word
from google_file_store
) t
GROUP BY word
ORDER BY occurrences DESC
