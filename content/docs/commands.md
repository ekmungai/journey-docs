---
title: 'Commands'
date: 2018-11-28T15:14:39+10:00
weight: 12
heading: 'References'
---
##### Commands
The following commands are available:

| Command | Description |
| :------------- | :------------ |
| scaffold       | Prepare the template for the migration file for the next version of the database |
| validate       | Verify the correctness of the structure of the migration file for the specified version |
| migrate        | Apply any pending migrations. Proceeds one step at a time, unless a target is specified |
| rollback       | Reverse the latest migration. Proceeds one step at a time, unless a target is specified |
| update         | Migrate or Rollback the database to the highest version in the versions directory, or to a target if one is specified |
| history        | Display the last migration entries as up to the given entries |