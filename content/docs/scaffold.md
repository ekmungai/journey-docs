---
title: 'Scaffold'
date: 2018-11-28T15:14:39+10:00
weight: 6
heading: 'Commands'
---

```
journey scaffold -p "path\to\versions" -d sqlite -c "Data Source=journal.db"
```
Scaffolding is the process of preparing a blank migration file in preparation for the next version. The command will create a file with the next version number as the file number and the follwing content:

```
-- ------------------------------------------------------------------
-- | Migration file formatting rules.                               |
-- | 1. There must be one and only one migration and one and only   |
-- |    one rollback section.                                       |
-- | 2. Only change the section between transaction blocks.         | 
-- | 3. Each migration and rollback must have only one transaction. |                                       |
-- ******************************************************************

-- start migration

BEGIN;

-- SCAFFOLDING: Enter your migration queries here ..

INSERT INTO versions (
    version,
    description,
    run_by,
    author)
VALUES (1, '', '', '');

END;

-- end migration

-- start rollback

BEGIN;

-- SCAFFOLDING: Enter your rollback queries here ..

DELETE FROM versions WHERE version = 1;

END;

-- end rollback
```
As the instructions direct, the queries for effecting the desired changes to the datavase should be entered to replace the commented `SCAFFOLDING` sections of the template file. Metadata relating to the migration should be filled in to the query inserting into the versions table, providing historical information of changes performed pn the database. 

###### Initial Setup
If the tool has never been used against the database before, the following prompted will be displayed requesting confirmation to run the queries required to setup the versions table.
`Migrations have not been initialized. Would you like to do so now? [Y/n]`
The prompt can be disabled by running the application in quiet mode using the `-q` flag. This is will run the initialization queries automatically before proceeding with the entered command.