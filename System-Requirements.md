
Basic Requirements
------------------

[rAthena](/rAthena "wikilink") works off of the [client-server model](/wikipedia:Client–server_model "wikilink"). The player, usually using a [hexed](/Hexing "wikilink") kRO [RE](/Renewal "wikilink") client, first connects to the [Login Server](/Login_Server "wikilink"). When the client enters their login information, it is given the list of available char-servers, which the player chooses from. After the server has been chosen, the client connects to the selected [Character Server](/Character_Server "wikilink"), which displays the characters on that player's account. After selecting a character, the client is directed to the [Map Server](/Map_Server "wikilink"), which maintains maps and the character positions on the server and relays this information to the client.

rAthena is designed to run on a machine that is designated as a Server, either Dedicated or VPS. It can run on a workstation, but using that workstation for other tasks (including playing on the same machine that is running the server) will reduce performance.

Hardware Requirements
---------------------

rAthena requires the following resources from the machine in order to function without problems or the common "Lag":

-   1.5 GHz or faster CPU, either Intel or AMD is acceptable. Some members have reported that they have gotten rAthena to run on other processors.
-   512 MB of RAM, MINIMUM. The map server in an idle state consumes about 150-200MB of RAM, depending on how many maps and [NPCs](/NPC "wikilink") are loaded.
-   A video card powerful enough to run the Operating System of your choice. rAthena is a console based software, which means that all that is required to run it is a console or command access.
-   Fast internet or network connection. This is very hard to predict. A lot of questions arise that ask 'how much bandwidth does rAthena need?'. There is no answer to that. It is all depending on how many characters are connected, from where, and what they do while connected to the server.
-   250MB of Hard Drive space or better, up-to 1GB depending on how big the database may get.

Software Requirements
---------------------

rAthena, depending on what you plan to do with it and what platform you run it on, will require, at a minimum, the following:

-   GCC compatible compiler
-   zlib
-   MySQL server and libraries
-   Subversion (if using self-compiled packages)

Supported Operating Systems
---------------------------

The following operating systems have been tested and are known to work:

### [Linux](/wikipedia:Linux "wikilink")

-   Debian Based: [Debian](http://www.debian.org/), [Knoppix](http://www.knoppix.net/), [Ubuntu Server & Desktop](http://www.ubuntu.com/)
-   RPM Based: [CentOS](http://www.centos.org/), [Fedora Core](http://fedoraproject.org/), [Mandriva](http://www2.mandriva.com/), [Red Hat Linux](http://www.redhat.com/rhel/), [SUSE Linux](http://www.novell.com/linux/)
-   Slackware Based: [Slackware](http://www.slackware.com/)

### [Unix](/wikipedia:Unix "wikilink")

-   BSD Based: [FreeBSD](http://www.freebsd.org/), [OpenBSD](http://www.openbsd.org/)

### [Windows](/wikipedia:Microsoft_Windows "wikilink")

-   [Server Versions](/wikipedia:Windows_Server "wikilink"): Windows Server 2000, Windows Server 2003, Windows Server 2008, Windows Server 2008 R2
-   Home Versions: Windows 98, Windows ME, Windows 2000, Windows XP, Windows Vista, Windows 7

64-bit operating systems of all those listed will take some time and effort to get working.

[Category:Basics](/Category:Basics "wikilink")