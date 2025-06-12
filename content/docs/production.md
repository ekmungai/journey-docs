---
title: 'Production'
date: 2018-11-28T15:14:39+10:00
weight: 5
---

#### Journey .Net Library 

###### File Based Update
The basic use of the Journey .Net library in production is to execute the Update command during the startup of a .Net Core application. This will migrate/rollback the database to the highest version available in the versions directory.

```bash
# initialize the library
var journey = new JourneyFacade(databaseType, connectionString, versionsDirectory);
# initialize migrations (in quiet mode) in case its the first time
await journey.init(true);
# sync the database
await journey.Update();

```
###### Targeted Update
The Journey library can be used not only to keep the database automatically in sync with deployment of the code running on top of it, but also offers fine grained tuning of which version of the database should be run against each individual deployment. The latter allows for the independent deployment of the code and the database accross enviromnents which speeds up development of both. To update the database to a specific (available) version, regardless of the contents of the versions of directory, simply provide the target version to the update function. 

```bash
await journey.Update(versionNumber);
```