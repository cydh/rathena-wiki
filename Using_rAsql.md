---
title: Using rAsql
permalink: /Using_rAsql/
---

**rAsql** is "an easy to use one-click installer for a local SQL testing environment on Windows." <sup>[\[2\]](http://rathena.org/board/user/441-sirius-white/)</sup> It automatically starts a MySQL instance by creating a virtual drive on the computer and also provides a management tool in the form of [HeidiSQL](http://www.heidisql.com/). rAsql is based on [Uniform Mini Server](https://sourceforge.net/projects/miniserver/).

**Do note that rAsql is meant for local testing of rAthena only and should not be used for hosting a public server.**

History
-------

TXT save engine offered a way for users to test scripts and other things with basically zero set-up required. After the fork from [eAthena](/eAthena "wikilink"), Users were asked to vote as to what should be done about the TXT support. It has been decided that support for TXT would be dropped <sup>[\[1\]](http://rathena.org/board/topic/53926-removal-of-txt-support/)</sup>. **rAsql** was created by [Yommy](http://rathena.org/board/user/251-yommy/) to serve as a replacement for TXT, which was officially dropped in revision 15503.

Downloading rAsql
-----------------

rAsql can be obtained from the rAthena GitHub repository:

<https://github.com/rathena/rAsql>

Setting up rAsql
----------------

rAsql is preconfigured and doesn't require any additional setup, except initial database import. It can be done with any SQL client, preferably with bundled HeidiSQL.

By default rAsql listens on the same port as regular MySQL server, ie. 3306, and accepts connections only from localhost. There is one SQL user `ragnarok` (password: `ragnarok`) and one user database `ragnarok`.

### Initial database import in HeidiSQL

-   Running `mysql_start.bat` will start the MySQL instance and open HeidiSQL.

[center](/File:rasql_run.png "wikilink")

-   Click *Open*. This will connect you to the MySQL server. Select your `ragnarok` database.

[center](/File:rasql_open.jpg "wikilink")

-   Select *Import* -&gt; *Load SQL File...* (or press Ctrl+O). Navigate to *sql-files* inside your rAthena folder and open *main.sql*.

[center](/File:Rasql_insert_start.png "wikilink")

-   Press F9 to run the script.

[center](/File:rasql_insert_finish.png "wikilink")

Controlling rAsql
-----------------

### Starting

To start rAsql run `mysql_start.bat`.

### Stopping

To stop rAsql run `mysql_stop.bat`.

### Password Change

To change the default password for the user `ragnarok` you will need to:

-   Click *Tools* -&gt; *User Manager*
-   Input the new password for both `ragnarok@localhost` and `ragnarok@127.0.0.1`
-   Open `mysql_close.bat` in notepad and change the password on the line:

`udrive\bin\mysqladmin.exe --port=3306 --user=ragnarok --password=`**`ragnarok`**` shutdown`

[Category:Installation](/Category:Installation "wikilink")