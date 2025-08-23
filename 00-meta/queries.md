```dataview
TABLE oj, contest, rating, status, revisit
FROM "problems/atcoder"
WHERE rating and rating >= 1200 and rating <= 1599
SORT rating ASC
```

```dataview
TABLE rating, tries, time_spent
FROM "problems"
WHERE status = "solved" and contains(tags, "graph")
SORT date DESC
LIMIT 30
```