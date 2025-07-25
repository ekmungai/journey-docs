---
title: 'Update'
date: 2018-11-28T15:14:39+10:00
weight: 10
---
Particularly useful when using the .Net library, the update command migrates the database up or down to a desired version.

###### File Based Update
```
journey update -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db"
```
In this mode, the tool will migrate upto the highest available version number in the versions directory if the current database version is lower, or down to it in case it's lower. In this way, the tool resembles most currently available migration solutions with the additional capability of automaticall rolling back from a higher database version without needing a new new reversing migration. 

###### Targeted Update
```
journey update -p "path\to\versions-dir" -d sqlite -c "Data Source=journal.db" -t 3
```
When a target is specified, the database will be migrated up or rolled back down to the target, regardless of contents of the versions directory. This is particularly useful if database changes have outpaced changes in the code in different environements, such that the changes should be applied in say a staging environment while QA is verifying the feature in the code which has not been released in production yet. By setting the target to the version compatible with the production code, all migration files can still be checked into version control without fear of their being automatically applied in an environment not prepared for newer versions of the database. 