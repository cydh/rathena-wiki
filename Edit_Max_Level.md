---
title: Edit Max Level
permalink: /Edit_Max_Level/
---

One of the most common issues during server configurations is setting the max base and job levels. The process involves a 2-part editing--the source code and the configuration files.

Editing The Source Code
-----------------------

### \\src\\map\\map.h

------------------------------------------------------------------------

Open ***\\src\\map\\map.h*** and look for this line of code:

`#define MAX_LEVEL `***`160`***

Change ***160*** to your desired maximum value, i.e.

`#define MAX_LEVEL `***`1000`***

Compiling The Server
--------------------

After editing the source code, you must recompile your binaries for the changes to take effect.

See [Compiling](/Compiling "wikilink").

Editing The Configuration and Database Files
--------------------------------------------

### \\conf\\battle\\client.conf

------------------------------------------------------------------------

Open ***\\conf\\battle\\client.conf*** and look for this line of code:

`max_lv: `***`99`***

and

`aura_lv: `***`99`***

Modify these to your desire values. But take note of the maximum values had in your source. Any value exceeding the supported values will be automatically reverted to **99**.

### \\db\\(pre-)re\\job_exp.txt

------------------------------------------------------------------------

sets the final maximum values for the base and job levels. The included file supports up to base level 1000.

Each entry under job_exp.txt is in the format

`Max Level,Class list,Type (0 - Base Exp / 1 - Job Exp),Exp 1,2,3,...`
`Example: //Base - Normal and Baby Jobs`
`         99,0:1:2:3:4:5:6:7:8:9:10:11:12:13:14:15:... = 99 Base level for Normal Jobs and baby Jobs`

Edit the Max Level values to your desired values. You can also set the maximum Job level under this file. Each entry is labeled accordingly.

[Category:Configuration](/Category:Configuration "wikilink") [Category:Source Snippets](/Category:Source_Snippets "wikilink")