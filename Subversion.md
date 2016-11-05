---
title: Subversion
permalink: /Subversion/
---

Preface
-------

This article will cover the **Subversion** details related to rAthena. **Subversion** is a version control system that allows multiple users to contribute to the development of rAthena, if permitted. It is also the most efficient method to downloading the source code of rAthena.

About Subversion
----------------

As mentioned above **Subversion** is a version control system that allows users to download the latest source code. It uses the structure of trunk and branch to declare the development code and the stable code. A **trunk** is referred to as the development code that needs to be tested and validated for bugs. A **branch** is typically used for developing larger features or as alternative development path, without breaking current trunk code. Exception to this is **stable**, which is considered stable subset of trunk.

### Checkout

When you **checkout** a piece of code, it is downloaded, along with all history, properties and files, onto your machine so you can make local changes or use it in a production environment.

### Commit

When you **commit** a piece of code, you are uploading your changes back to the server and increasing the revision number of the SVN by 1. The increase in revision number by 1 is done no matter how many changes are made per commit. Each commit includes the author's name, what they changed and when they changed it, which can be viewed and referenced later.

Only members of the [rAthena development team](/Staff "wikilink") can commit code straight to the rAthena SVN.

### Update

When you **update** your SVN, you are taking your local copy of the SVN that was previously **checked out** and applying the latest updates from the server to it. In this operation, many files are changed, but some are added, deleted or moved. When you update your copy of the SVN, a lot of conflicts can happen, so keep an eye out of those.

### Making changes

When you make a change to your copy of the SVN on Windows, a number of different icons will appear in the directory of the SVN. Below is a brief explanation of what each of these icons mean:

|                                                                                                |                                                                                                                                                                                       |
|------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Modified SVN tag](/Image:SVN_red.jpg "wikilink")                                              | Changes have been made from the original downloaded script this indicates what scripts you have modified.                                                                             |
| [Conflict SVN tag](/Image:SVN_yellow.jpg "wikilink")                                           | Conflicts with original script you need to search for the &lt;&lt;&lt;&lt;&lt;<mine> and &gt;&gt;&gt;&gt;&gt;&gt;&gt;<mine> to see what parts are conflicting and change accordingly. |
| [Unmodified SVN tag](/Image:SVN_green.jpg "wikilink")                                          | No changes with original script have been made.                                                                                                                                       |
| [Generated SVN tag](/Image:SVN_-.jpg "wikilink") or [New SVN tag](/Image:SVN_q.jpg "wikilink") | Files you added yourself that weren't in the original repository.                                                                                                                     |

### Obtain/Install Subversion

Please see the [:Category:Installation](/:Category:Installation "wikilink") appropriate category for installation of Subversion on your operating system of choice and how to utilize it.

rA Subversion Details
---------------------

You can find the root or index of the rAthena source code at the following link: . This link can be used if you need to view a single file and don't want to dig up your "copy" of the source code.

### rAthena Trunk

**rAthena Trunk** is used as the *testing* or otherwise development code. It has all of the latest features, but is not guaranteed to be bug or problem free.

You can checkout the trunk branch from the following link:

### rAthena Developer Branches

Each developer that contributes to the rAthena Project is welcome to their own folder on the SVN, where they may make their own branch. A lot of times, this separate branch is a testing bed for a new feature. You should never assume that any branch that is not trunk or not stable is usable. Often times, it is not.

Using .diff/.patch files
------------------------

Often times, developers and contributors will release their work with a .diff or .patch file. these files are designed specifically to be applied to an SVN revision and 'patched' in.

In Windows, you can apply a diff or patch file by placing the diff file into the SVN directory, right clicking the diff or patch file, navigating to the Subversion menu and clicking 'Apply Patch'.

If the revision numbers are different, or the code is different in anyway, the patch will likely fail with the error message that the revision numbers do not match. The diff file will include some important symbols and numbers to help you apply them manually.

`/path/to/file [Revision 233]`
`@@ +241,4 -241,4 @@`
`+ This line will be added at the line number or position indicated above.`
`- This line will be removed at the line number or position indicated above.`

So in the file, we're to remove line 241 and replace it with the line that has the '+' next to it.

[Category:Basics](/Category:Basics "wikilink")