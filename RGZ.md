---
title: RGZ
permalink: /RGZ/
---

An RGZ file is a proprietary compressed archive format used for [Ragnarok Online](/Ragnarok_Online "wikilink"), developed by [Gravity](http://en.wikipedia.org/wiki/Gravity_(company)). It is used for patching the local file system directory, the game client resides in. The archive mostly contains updated game executable or new background music files. The extension is always **.rgz** and might be an abbreviation for **ragnarok+gzip**.

File Format
-----------

The RGZ archive is a sequential concatenation of files and/or directories entries, compressed with [gzip](http://en.wikipedia.org/wiki/Gzip), much like [tar+gzip](http://en.wikipedia.org/wiki/Tar_(file_format)) archives are. Each entry inside the archive is defined by following structure:

| Field Offset | Field Size | Field                       |
|--------------|------------|-----------------------------|
| 0            | 1          | Entry type (case-sensitive) |
| 1            | 1          | File name field length      |
| 2            | ?          | File name (zero-terminated) |

The entry type specifies, what kind of data it represents. It can be **f** (file), **d** (directory) or **e** (end). The file name always denotes relative position of the file, inside the folder, the archive is patched to.

### File

A file entry can store any type of file, up to 2<sup>32</sup> - 1 Byte (4 [GiB](http://en.wikipedia.org/wiki/Gibibyte) - 1 Byte) in length. If the file is put into a sub-directory, the entire path is assumed to exist. A file entry always follows a directory entry, that creates the path in advance. The additional data in the file entry has the following structure:

| Field Offset | Field Size | Field                                                                     |
|--------------|------------|---------------------------------------------------------------------------|
| 0            | 4          | Data length ([little endian](http://en.wikipedia.org/wiki/Little_endian)) |
| 4            | ?          | Data                                                                      |

### Directory

Directory entries have no additional data, and create a single directory, not an entire path. That means if you want to create **dir1\\dir2** it requires two entries, one for **dir1** and the second for **dir2**.

### End

End entry is the last entry inside the archive, and makes the patcher stop parsing the archive. The file name for this entry is always **end**.

### Hex Workshop Definition File (ragnarok.hsl)

`/********************`
`* `
`* Ragnarok Resource files to view and edit`
`*`
`*/`
`#include "standard-types.hsl"`
`#pragma displayname("Ragnarok GZip") ;`
`#pragma fileextensions(".rgz") ;`
`#pragma byteorder(little_endian) `
`//#pragma maxarray(65536)`
`#pragma hide()`
`struct FILESTRUCT`
`{`
`   BYTE type;`
`   `
`   struct tagFILENAME`
`   {`
`       BYTE length;`
`       char string[length];`
`   };`
`   `
`   switch (type)`
`   {`
`       case 0x66:`
`           struct FILECONTENTS`
`           {`
`               DWORD length;`
`               blob  contents[length];`
`           };`
`           break;`
`       default:`
`       `
`           break;`
`   };`
`   `
`};`
`#pragma show()`
`struct files`
`{`
`   struct FILESTRUCT entries[256];`
`};`

Tools
-----

-   [RGZ pack/unpack ulility](http://eamirror.skamfroj.net/xdl/download.php?id=32)
-   [RGZ builder](http://sourceforge.net/projects/clientpatcher/files/)
-   [7-zip RGZ plugin](http://vanaheim.the-aria.com/rgz/)

See Also
--------

-   [GRF](/GRF "wikilink")

[Category:File Formats](/Category:File_Formats "wikilink")