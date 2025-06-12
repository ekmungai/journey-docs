---
title: 'Validate'
date: 2018-11-28T15:14:39+10:00
weight: 7
---
```
journey validate -p "path\to\versions\{versionNumber}.sql" -d sqlite -c "Data Source=journal.db"
```
Calling validate on a migration file ensures that:
1. All Transaction blocks are properly opened and closed.
2. All sections are properly opened and closed.
3. Both the `migration` and `rollback` sections are present in the file.

While this is not a full proof method to protect against database corruption and dataloss due to harmful queries in the migrations, its a first line of defense that ensure that at least the syntax of the queries is not the cause of a problem. By enforcing that all migrations also have a rollback section, some assurance is provided that the database can always be restored to an earlier state. 