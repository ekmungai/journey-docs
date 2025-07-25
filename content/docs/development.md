---
title: 'Development'
date: 2018-11-28T15:14:39+10:00
weight: 4
heading: 'Usage'
---

#### Journey Command CLI
The most versatile use of Journey is through the Journey Command application that shines the most during development rather than in production. Invocations of the  application have the following structure:

```bash
journey [Command] [Option|Flag(s)] [OptionValue]
```
See [Command Reference]({{< relref "commands.md" >}}) and [Option Reference]({{< relref "options.md" >}}) for more details on all commands and options.

###### Scaffolding
```bash
journey scaffold -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```
To get things rolling, the first step is to obtain a scaffoding of the next version's migration file. This is done by running the [Scaffold]({{< relref "scaffold.md" >}}) command, which will provide a starting point for adding queries that will transition the database to the next version. 

###### Validation
```bash
journey validate -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```
After adding the queries that should change the database, the next step would be to run [Validate]({{< relref "validate.md" >}}) command, which ensure that the file conforms to expectations of the Journey migration tool. This reduces the risk of database corruption because of syntax errors in the migration script. Of course, if the queries themselves are harmful but syntatically correct, this command wont be of much help. This command will validate the latest version in the versions directory.

###### Migrating
```bash
journey migrate -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```
Once the migration file is prepared, its time to apply it by running the [Migrate]({{< relref "migrate.md" >}}) command. This will execute the queries contained in the `migration` section of the file against the database. This command will migrate the latest version in the versions directory.

###### Rollback
```bash
journey rolback -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```
In the event the changes were not ideal or what was expected, the database can be restored back to the state it was in before the migration by running the [Rollback]({{< relref "rollback.md" >}}) command. This executes the queries contained in the `rollback` section of the migration file against the database which, if prepared correctly should completely reverse the effects of the migration queries without any side effects. This command will rollback the latest version in the versions directory.

###### Update
```bash
journey update -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```
To sync the database to the highest version in the versions directory, you can run the [Update]({{< relref "update.md" >}}) command. This is the most common use case in a non-development environment such as when using the .Net library version of Journey. 

###### History
```bash
journey history -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```
To get a description of the migrations that have been applied to the database up to the current version, you would run the [History]({{< relref "history.md" >}}) command which returns the descriptions, authors an run time of all migrations that have been run against the database up to the latest version. This command will return the descriptions of the 10 latest migrations.
