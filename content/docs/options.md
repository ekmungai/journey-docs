---
title: 'Options'
date: 2018-11-28T15:14:39+10:00
weight: 13
---
##### Options
The following options are available:

| Option | Name | Description | Required |
|:- | :---------------------- | :------------ | :------------ |
| -d | Database Type           | One of the [supported databasses](../requirements/index.md#Supported Databases), in lowercase. Defaults to sqlite | Yes |
| -c | Connection String       | The database connection string | Yes |
| -p | Versions Directory Path | The path to the location of the migration files | Yes |
| -s | Schema                  | The schema to apply the migrations to | No |
| -q | Quiet Mode              | Run queries without prompting. Defaults to false | No |
| -t | Target Version          | The version to migrate/rollback/update the database to | No |
| -e | History Entries         | The number of descriptions of applied migration to retrieve from the database. Defaults to 10 | No |
| -v | Verbose Mode            | Print out migration queries as they are executed. Defaults to false | No |
| -r | Dry Run Mode            | Rollback migrations immediately after applying them. Defaults to false | No |
