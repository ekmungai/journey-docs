---
title: 'Ideology'
date: 2018-11-28T15:14:39+10:00
weight: 3
---
There are already so many database migration tools built on sorts of plaforms and targeting all kinds of scenarios, so why create yet one more? Journey was concieved to address one major concern, that is the idea that migrations are always forward looking. Many of the tools mentioned above being designed with this concept in mind offer very limited flexibility in terms of the following scenarios.

###### Code/Database Version Coupling
In most cases, database migration files are checked into source control together with the code of the application using the database. In such a setup, all migration files that are deployed with code are executed up to the most recent one that is missing from the database's history tracking mechanism. 

While this works for most workflows, it creates a tight coupling between the database version and the version of the code being deployed. Consider a scenario where database version 1 migration is ready and checked into version control so that features dependent on it can be worked on by other teams. If one team finishes their feature first and checks in their code to source control, then another team starts building a completely different feature that depends on say version 2 of the database, they would be prohibited from checking version 2 of the database into source control until when the code for it is also ready, since doing so would apply that version to the database directly. This means that yet another team that could be working on a feature based on version 2 or higher of the database is essentially blocked until the second team is ready since they have no access to the version 2 of the database.

If the code in source control could be deployed but specify that only version 1 of the database should be applied, an arbitrary number of migrations could live in version control, without the danger of their being executed before the code that depends on them is ready. In this way, each feature can be shipped in tandem with the exact version of the database it depends on (as a configuration value perhaps).

###### Ehanced Developer Experience
The true power of Journey lies in the capabilities it provides to developers during development. Apart from guiding the developer on how to write consistent error free migrations and aslo validating that these are syntactically sound, Journey allows them to easily migrate up or down the version ladder to whichever version is most relevant to the code they are currently working on, while at the same time keeping the entire migration journey availble as it is checked into version control.

One very useful application of this capability is refactoring, during which the effects of later changes to the database can be elimitaed or at least easily identified during the refactor preventing surprises in the future.

###### In Built Atomicity
With each version file requiring both a migration and a rollback section, there is an established convension that changes to the database are to made to be exactly reversible. The script validation combined with the dry run migration mode offers a lvel of protection against irreciverable damage against production database systems as the effects of each migration can be thoroughly investigated during development before being applied.  