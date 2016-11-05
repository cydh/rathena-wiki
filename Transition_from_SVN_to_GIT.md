---
title: Transition from SVN to GIT
permalink: /Transition_from_SVN_to_GIT/
---

Transitioning from SVN to GIT
=============================

While switching your server to GIT may sound like a daunting task, it's relatively simple and straightforward, even for servers with heavy modifications. **We strongly encourage you to do so, since our primary efforts will now be directed towards our repository on GitHub.** Simply follow the steps listed below, depending on your OS:

Windows Instructions
--------------------

For this process, we'll be using [msysgit](https://code.google.com/p/msysgit/downloads/list?can=2) and [TortoiseGit](https://code.google.com/p/tortoisegit/wiki/Download?tm=2). Download and install both (in that order) if you don't have them already.

### In TortoiseGit, right-click and select "Git Clone..." where you want to create your new repository

[<File:ULa1u8a.jpg>](/File:ULa1u8a.jpg "wikilink")

### Enter rAthena's GitHub URL and hit "OK"

[`https://github.com/rathena/rathena`](https://github.com/rathena/rathena)

[<File:czNpAgf.jpg>](/File:czNpAgf.jpg "wikilink")

### Cloning may take a minute or two. Hit "Close" after it finishes

[<File:dgF5HRl.jpg>](/File:dgF5HRl.jpg "wikilink")

### Update your SVN repository using TortoiseSVN's "SVN Update"

[<File:9HNDSej.jpg>](/File:9HNDSej.jpg "wikilink")

### Hit "OK" after it finishes. Resolve any conflicts now (read more below)

[<File:5ww9HK7.jpg>](/File:5ww9HK7.jpg "wikilink")

### Copy all files in your SVN directory, excluding the .svn folder itself

[<File:gNTwT7B.jpg>](/File:gNTwT7B.jpg "wikilink")

### In your new GIT directory, paste the files you just copied

[<File:QDXu3Rq.jpg>](/File:QDXu3Rq.jpg "wikilink")

### When prompted, opt to merge all folders and replace all files

[<File:N9psegA.jpg>](/File:N9psegA.jpg "wikilink") [<File:iOeYCNr.jpg>](/File:iOeYCNr.jpg "wikilink")

### In TortoiseGit, right-click and select "Stash Save" to store all your changes

[<File:tVyxmsw.jpg>](/File:tVyxmsw.jpg "wikilink")

### Create a name that you'll recognize later, like "Update to Latest"

[<File:0YPzXbf.jpg>](/File:0YPzXbf.jpg "wikilink")

That's it, you're finished. When you want to update your GIT repository, follow these steps:

### Right-click and select "Pull..." to merge all new changes

[<File:JSjpp8l.jpg>](/File:JSjpp8l.jpg "wikilink") [<File:Fna1kfs.jpg>](/File:Fna1kfs.jpg "wikilink")

### Right-click and select "Stash Pop" to restore your custom changes

[<File:GwvsyxR.jpg>](/File:GwvsyxR.jpg "wikilink") [<File:sg3BF4Z.jpg>](/File:sg3BF4Z.jpg "wikilink")

Linux Instructions
------------------

### Clone the GIT repository

`git clone `[`https://github.com/rathena/rathena.git`](https://github.com/rathena/rathena.git)

This creates the new directory named "rathena" and will be the new server location, but can be changed is desired.

### Update SVN Repo to latest

`svn co http://svn.code.sf.net/p/rathena/svn/trunk/`

You can solve conflicts later, but it's best to do it now and make sure you can compile, and even test the server, before continuing.

### Copy the files over

`cp -rf trunk/* rathena/`

Recursive tag to copy all sub-directories and files, forced so you don't have to manually accept overwriting each file.

### Configure and compile new GIT server location

`./configure && make clean sql`

If there are any specific functions you enable when configuring, modify this command.

### Shut down old server and start-up new one

If you have any server auto-restart scripts, you can either edit the cronjob to point to a new location, or rename directories:

`mv trunk trunk-bak && mv rathena trunk`

### You can now pull GIT changes by typing

`git pull`

Notes about GIT
---------------

These commands assume you have changed directory to new GIT directory.   When doing a pull, you may receive a message saying:

`Please, commit your changes or stash them before you can merge.`
`Aborting`

  In order to pull changes into your local repository, you have a couple options.  The one which will be most used by our users is going to be to stash the changes and recall these changes after a pull.  If you're just starting using GIT, then you'll need to configure a name and email before doing a stash.  

`git config --global user.email "you@example.com"`
`git config --global user.name "Your Name"`

  Now, stash local changes:  

`git stash save "Update to Latest"`

"Update to Latest" can be anything, it's just a note.   Do the pull - Followed by a 'pop' to replace your code:  

`git pull`
`git stash pop`

  No conflicts?  You're good to complete your update!  Otherwise, keep reading...

Conflicts
---------

It's possible that you'll run into conflicts along the way, with messages such as:  

`CONFLICT (content): Merge conflict in src/map/atcommand.c`

  When you see these messages, a conflict in merging your code occurred.  Much like resolving code conflicts in SVN, these conflicts create points within the files which show your code compared to the code pulled from the remote repo.  To fix them, open your files and find the conflict locations denoted by:  

`<<<<<<<: Indicates the start of the lines that had a merge conflict.`
`=======: Indicates the break point used for comparison. Breaks up changes that user has committed (above) to changes coming from merge (below) to visually see the differences.`
`>>>>>>>: Indicates the end of the lines that had a merge conflict.`

  Then you can choose which piece of code you wish to keep.  After all shown conflicts are corrected, you can continue your normal update process.  

References
----------

-   [Setting your email in git](https://help.github.com/articles/setting-your-email-in-git)
-   [How do I resolve git saying "Commit your changes or stash them before you can merge"?](http://stackoverflow.com/questions/15745045/how-do-i-resolve-git-saying-commit-your-changes-or-stash-them-before-you-can-me)
-   [CONFLICT (content): Merge conflict in](http://stackoverflow.com/questions/11091969/conflict-content-merge-conflict-in)

*Credits to [Akinari](http://rathena.org/board/user/9210-akinari/) for writing a good part of this guide. Credits to [Euphy](http://rathena.org/board/user/4938-euphy/) to putting it together on [the forums](http://rathena.org/board/topic/87120-transitioning-from-svn-to-git/)*