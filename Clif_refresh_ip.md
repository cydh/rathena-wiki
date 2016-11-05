---
title: Clif refresh ip
permalink: /Clif_refresh_ip/
---

Syntax
------

`uint32 `**`clif_refresh_ip`**`(void);`

Parameters
----------

-   **N/A**

Description
-----------

Refreshes map_server ip, returns the new ip if the ip changed, otherwise it returns 0.

Example
-------

`void chrif_update_ip(int fd)`
`{`
` uint32 new_ip;`
` WFIFOHEAD(fd,6);`
` new_ip = host2ip(char_ip_str);`
` if (new_ip && new_ip != char_ip)`
`  char_ip = new_ip; //Update char_ip`
` `**`new_ip` `=` `clif_refresh_ip();`**
` if (!new_ip) return; //No change`
` WFIFOW(fd,0) = 0x2736;`
` WFIFOL(fd,2) = htonl(new_ip);`
` WFIFOSET(fd,6);`
`}`

From

[Category:Source_Functions](/Category:Source_Functions "wikilink")