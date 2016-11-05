---
title: XAMPP Installation
permalink: /XAMPP_Installation/
---

What is 'XAMPP'
===============

'XAMPP' is an open source and free program that takes apache, mysql, perl and PHP and packages them into one easy installer. This can be handy if your server is serving your Control Panel and MySQL server on the same machine as [rAthena](/rAthena "wikilink").

Getting and Installing XAMPP
============================

XAMPP is located on their website. You can download it for Windows, Mac OSX and \*nix. Their website is located here: [<http://www.apachefriends.org/en/xampp.html> <http://www.apachefriends.org/en/xampp.html>](/http://www.apachefriends.org/en/xampp.html_http://www.apachefriends.org/en/xampp.html "wikilink")

Installing on Windows
---------------------

Click either Zip or Exe. After clicking one, you will have to choose a mirror. Choose one of the Mirrors and click Download. \*Note\* The Zip and Exe are the same! You don't need to download them both.

When you have finished the downloading and updating, extract the files to somewhere accessible, the root of your Local Disk should do just fine. Once extracted, navigate inside the folder and run setup_xampp.bat. A window should appear similar to the one below.

[Image:Openingsetup3tk.png](/Image:Openingsetup3tk.png "wikilink")

When the windows says 'Press any key to close the window...' XAMPP is installed, and you can press the spacebar to close the window. Now, navigate to your xampp_control.exe file and run the exe. You should get a popup for the XAMPP control center similar to the one below:

[Image:Controlpanel9mg.png](/Image:Controlpanel9mg.png "wikilink")

Go ahead and start the Apache and MySQL servers by clicking the buttons outlined in red.

We should verify the security of our XAMPP installation. Navigate your web browser to <http://127.0.0.1> (or the IP of your server) and choose a language at the page that comes up. You should then get a warning about security. Click the link in the image below that's highlighted in red to fix these security problems.

[Image:Nextlink5cb.png](/Image:Nextlink5cb.png "wikilink")

You should then come upon a page that you can set your MySQL root password. You should set this to something that is hard to guess. You should also give yourself a username and password and 'make safe your .htaccess directory' in the box below and you can close out of the web browser.

[Image:Security9am.png](/Image:Security9am.png "wikilink")

After you're done, your phpmyadmin is setup and will accept root and your established root password at <http://127.0.0.1/phpmyadmin>. You can now login and finish [Configuring](/:Category:Configuration "wikilink") and [Compiling](/Compiling "wikilink") your server.

[Category:Installation](/Category:Installation "wikilink")