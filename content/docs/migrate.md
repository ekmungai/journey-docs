---
title: 'Migrate'
date: 2018-11-28T15:14:39+10:00
weight: 8
---

###### Single Step Migration
```
journey migrate -p "path\to\versions\{versionNumber}.sql" -d sqlite -c "Data Source=journal.db"
```

This command will migrate the database forward by one step. Repetition of each operation will walk up the version ladder until the latest migration available. Adding the verbose mode flag `-v` allows you to view the queries of each migration as they are executed, which is useful for debugging.

###### Multi Step Migration
To migrate to a specific version that might be several steps ahead of the current one, modify the command with the target `-t` option and provide a integer value of the version to migrate to.
```
journey migrate -p "path\to\versions" -d sqlite -c "Data Source=journal.db" -t 2
```
The tool will calculate the migrations required to run through to reach the target version, and apply them in turn up to it. As each migration is encapsulated in its own transaction, every step on the route to the target will be applied atomically until a step fails or all steps are applied.  

###### Dry Run Migration
For assurance that the migration can be safely reversed without an adverse effect on the data in the database, you might want to rollback the changes applied immediately afterwords. This is facilitated by the dry run mode `r` flag. Regardless of how many steps the migration runs through, these will be rolled back in reverse order returning the database to the starting version before the migration.
```
journey migrate -p "path\to\versions" -d sqlite -c "Data Source=journal.db" -r
```
Dry run mode can be combined with the target migration option to incrementally ensure that each of the migrations from the first to the last can be reversed safely.