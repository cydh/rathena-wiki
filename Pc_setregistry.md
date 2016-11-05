---
title: Pc setregistry
permalink: /Pc_setregistry/
---

Record a given value in sql (table global_reg_value) for the character.
-------------------------------------------------------------------------

`int pc_setregistry(struct map_session_data *sd, const char *reg, int val, int type)`

-   sd = player session
-   reg = str field in global_reg_value
-   val = value field in global_reg_value
-   type :
    -   1 account2 ???
    -   2 Variable will be recorded for account
    -   3 Variable will be recorded for char

Example
-------

`pc_setregistry(sd,"security",1,3)`

This will set security to 1 in sql database for charid related to session.

`pc_setregistry(sd,"security",1,2)`

This will set security to 1 in sql database for accountid related to session.