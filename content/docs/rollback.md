---
title: 'Rollback'
date: 2018-11-28T15:14:39+10:00
weight: 9
---
###### Single Step Rollback
```
journey rollback -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```

This command will rollback the database backward by one step. Repetition of each operation will walk down the version ladder until all migrations, including the initializing migration that adds the versions table are undone. Adding the verbose mode flag `-v` allows you to view the queries of each rollback as they are executed, which is useful for debugging.

###### Multi Step Rollback
To rollback to a specific version that might be several steps behind of the current one, modify the command with the target `-t` option and provide a integer value of the version to rollback to.
```
journey rollback -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db" -t 2
```
The tool will calculate the rollbacks required to run through to reach the target version, and apply them in turn down to it. As each rollback is encapsulated in its own transaction, every step on the route to the target will be applied atomically until a step fails or all steps are applied.  