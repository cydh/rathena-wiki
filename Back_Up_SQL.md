---
title: Back Up SQL
permalink: /Back_Up_SQL/
---

### Creating A Backup

Issue this command from a Unix terminal:

For single database:

       mysqldump -u (username) -p database_name > database_name.sql

For multiple database: (one output)

       mysqldump -u (username) -p --databases database_name_1 database_name_2 > 2_databases.sql

All databases:

       mysqldump -u root -p --all-databases > all_databases.sql