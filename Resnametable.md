---
title: Resnametable
permalink: /Resnametable/
---

The **resource name table** or resnametable, is responsible for creating pathname aliases for client-side files, regardless of whether inside or outside a [GRF](/GRF "wikilink") archive. The server can also read this file when [using GRFs for map data](/:Category:Configuration#Overriding_map-cache "wikilink"), as well. It is stored in `data\resnametable.txt`, typically inside the archive.

Usage
-----

This file is used whenever a resource (file) is required to be known under different name, while maintaining the same data, mostly used for duplicating maps, but available for any kind of file. It is preferred to use this mechanism, as it avoids the need to copy files physically, thus saves space and improves system's cache performance. The path, to which pathnames relate to, appears to depend on the pathname's file extension, see [table below](/#Known_Base_Paths "wikilink").

Format
------

In use is a single-line 2-column [token text table](/Token_Text_Table "wikilink") format, whose 1st column holds the alias pathname and the 2nd column contains the pathname of the actual file.

`alias pathname#real pathname#`

Example
-------

`nguild_pay.rsw#payg_cas01.rsw#`
`nguild_pay.gat#payg_cas01.gat#`
`nguild_pay.gnd#payg_cas01.gnd#`
`유저인터페이스\map\nguild_pay.bmp#유저인터페이스\map\payg_cas01.bmp#`

This virtually copies the map payg_cas01 to nguild_pay.

Known Base Paths
----------------

| Extension | Path            |
|-----------|-----------------|
| bmp       | data\\texture\\ |
| gat       | data\\          |
| gnd       | data\\          |
| rsw       | data\\          |

[Category:Client Configuration](/Category:Client_Configuration "wikilink")