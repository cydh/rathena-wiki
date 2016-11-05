---
title: Ipbanlist
permalink: /Ipbanlist/
---

The \`ipbanlist\` table is used in SQL servers to permanently ban a specific IP or a range of IPs.

@jailfor/@jail
--------------

To jail a character for a specified time, use the command:

`@jailfor `<time>` `<char name>

To permanently jail a character, use the command:

`@jail `<char name>

@ban
----

To ban a character (and their entire account) for a specified time, use the command:

`@ban `<time>` `<char name>

When they try to login, they will receive this message:

`You are prohibited to log in until YYYY-MM-DD HH:MM:SS`

@block
------

To permanently block a character (and their entire account), use the command:

`@block `<char name>

When they try to login, they will receive this message:

`Account ID blocked by the Game Master Team.`

ipbanlist
---------

The \`ipbanlist\` table is used in SQL servers to permanently ban a specific IP or a range of IPs.

### rAthena SQL

------------------------------------------------------------------------

1.  Connect to your MySQL database and go to the \`ipbanlist\` table
2.  Add in the info:
    -   **list** = 58.69.24.\* (the IP address or range)
    -   **btime** = 2008-01-16 00:00:00 (the time of Ban, optional)
    -   **rtime** = 2050-01-01 00:00:00 (when the Ban expires) <font color="#FF0000">\*NOTE:</font> this must be greater than the current date-time! If you leave it at 0000, the ban will immediatly expire
    -   **reason** = (optional)

3.  click Save.
4.  for IP bans in SQL, the changes take effect immediatly, no restart/reload needed

`` INSERT INTO `ipbanlist` VALUES ( '127.0.0.1', NOW(), NOW() + INTERVAL 1 YEAR, 'Fun XD' ); ``

ban IP '127.0.0.1' for 1 year.

`` INSERT INTO `ipbanlist` VALUES ( '58.69.*.*', NOW(), NOW() + INTERVAL 3 MONTH, 'Fun XD' ); ``

ban IPs that start with '58.69.\*.\*' for 3 months.

To unban the IP just execute this

`` DELETE from `ipbanlist` WHERE `list`='58.69.*.*' ``

[Category:Configuration](/Category:Configuration "wikilink")