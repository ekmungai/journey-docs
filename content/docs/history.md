---
title: 'History'
date: 2018-11-28T15:14:39+10:00
weight: 11
---
```bash
journey history -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```

The history retrieves the metadata assocciated with the latest 10 (by default) migrations applied to the database. This information includes a description of the purpose of the migration, the author of the migration and the person who run it. This is useful for attribution and accountabilty. Adding a value to entries option `-e` allows you to decide how many records of migrations are to be retrieved.