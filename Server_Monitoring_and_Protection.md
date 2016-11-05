---
title: Server Monitoring and Protection
permalink: /Server_Monitoring_and_Protection/
---

Following tips are intended to point out important tasks while running your server, to avoid 3rd-party disturbances, including but not limited to hacking, cheating and service outage.

Setup a firewall
----------------

This is one way in protecting your system from unwanted attacks. But just placing the firewall is just lame. So, to use some ports for eA, allow ports 6900,6121 and 5121(The default) or the ports you use for rAthena to accept incoming connections, since this is a server. Close unneeded ports for security reasons. Configure your firewall as you please. And always update it so that you get the latest protection from hackers.

Monitor your rAthena server for unusual activity
------------------------------------------------

Monitoring the server will help you on figuring out if you are already being hacked. If you see something unusual and can't figure it out immediately, check it in-game. Then try to figure out what's happening. If you still can't find it out immediately, shutdown the server for a while. Then turn it on again. If that happens again, recheck again. Repeat the process to find out who or what's hacking you.

Check your scripts for possible malicious code
----------------------------------------------

A lot of *clone* type sites mimicking rAthena have sprung up over time, offering support and scripts. However, sometimes, these scripts or other things that they offer, are embedded with unwanted **SQL queries** or **atcommands**. The creator will wait for you to install it and then they will use it to gain access to things normally they could not.

A good way to check (if you're using Windows) is to navigate to your folder where all your scripts are located. It is a good idea to keep scripts that you've either obtained or created separate from the ones that come from the emulator, as 99% of the standard scripts included in the rAthena SVN are safe from possible exploits.

Open up your search bar. Now look for the area that allows you to search "for files containing...". Inside that bar, search for "query_sql" & "atcommand".

Then search!

A list will then pop up. Some things will show up and that's okay. Some scripts would be very hard to script, or would not simply work without the SQL or the atcommand. However, the key is go over and to make sure that each script that uses SQL or the atcommand is safe and isn't something else that someone left there to exploit later on.

Constantly monitor your server's save data
------------------------------------------

Your SQL DB's of your server, if you are using SQL, or the files in the /save/ folder in your server folder, if you are using TXT. This is an alternative for checking what/who is hacking you. Constantly check for unusual inputs in an account. This helps especially when the hacker tried to duplicate Zeny or something like that.

Record server logs
------------------

Recording the logs may help in resolving the problem. I know some Server Managers that saves all the logs of the server. IP's are recorded in the logs. So, if you see that an IP just done an unusual thing, check it. If this is confirmed and had made something really bad, ban the IP.

Update your OS
--------------

Updating is a good way to protect your system. The updates usually contains security fixes, which is helpful in protecting the system. If the updates for your operating system are released at fixed intervals (e.g. Windows), consider adjusting your weekly maintenance times to do both during the downtime; maintaining the server and updating of your operating system.