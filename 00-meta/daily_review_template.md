---
title: Daily Review {{date:YYYY-MM-DD}}
date: {{date:YYYY-MM-DD}}
---

## 今日解いた
- [ ] 

## 再訪 (期限到来)
```dataview
TABLE rating, status, revisit
FROM "problems"
WHERE revisit and date(revisit) <= date(today)
SORT revisit ASC
```

## 未解決 / upsolve
```dataview
TABLE rating, tries
FROM "problems"
WHERE status = "upsolve"
SORT rating ASC
```

## タグ別件数 (例: number-theory)
```dataview
TABLE length(rows) AS count
GROUP BY contains(tags, "number-theory")
```