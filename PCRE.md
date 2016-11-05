---
title: PCRE
permalink: /PCRE/
---

What is PCRE
------------

PCRE (Perl Compatible Regular Expressions) is a library that can make you npc trigger with some expresions said by the players. If you say "Hello" you can make the npc say "Hi, how are you?" or something like that. You first need to define the patterns wich will trigger the labels of the npc. Read the documentation of:

-   [activatepset](/activatepset "wikilink")
-   [deactivatepset](/deactivatepset "wikilink")
-   [defpattern](/defpattern "wikilink")
-   [deletepset](/deletepset "wikilink")

or look into npc/custom/eliza.txt to see how it works.

### PCRE in Windows

If you are using Windows (VC++) you DON'T NEED TO DO ANYTHING, it comes by default enabled.

### PCRE in Linux

Perl-compatible regular expression is a library package. PCRE doesn't have it's own native API, but is more like a set of "wrapper" functions that are based on the POSIX API are also supplied in the library libpcreposix. According to your distribution, you can install PCRE package using the following commands:

For Debian based systems:

`apt-get update`
`apt-get install libpcre3 libpcre3-dev`

For Red Hat based systems:

`yum install pcre`
`yum install pcre-devel`

Then you are ready to recompile your SVN.

Go to your server folder: NOTE: Replace "trunk" with your server path.

`cd trunk`

Configure it with PCRE enabled:

`./configure --with-pcre`

If you get some error, probably you installed PCRE-devel package in a non-standard folder. You will need to check where is installed the pcre-devel and set:

`./configure --with-pcre=/PATH/TO/YOUR/PCRE/INSTALATION/FOLDER/`

If you don't get any errors, you are done and your can now compile your sql/txt with PCRE without problems.

For SQL servers:

`make clean`
`make sql`

For TxT servers:

`make clean`
`make txt`

It's done, now you recompiled your server with PCRE support enabled!

[Category:Installation](/Category:Installation "wikilink")