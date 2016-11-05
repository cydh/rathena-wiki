---
title: Restoring SQL
permalink: /Restoring_SQL/
---

Restoring a Backup
==================

Issue this command from a Unix terminal:

Single Database:

       mysql -u root -p (databasename) < database_name.sql

Multiple Databases in one dump to a Single Database:

       mysql -u root - p --one-database (databasename) < all_databases.sql