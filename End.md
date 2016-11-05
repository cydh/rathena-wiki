---
title: End
permalink: /End/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [end](/end "wikilink");

Description
-----------

This command will stop the execution for this particular script. It is the normal way to end a script which does not use [mes](/mes "wikilink"), otherwise use [close](/close "wikilink").

Examples
--------

       if(BaseLevel <= 10) {
          npctalk "Look at that you are still a n00b";
          end;
       }
       if(BaseLevel <= 20) {
          npctalk "Look at that you are getting better, but still a n00b";
          end;
       }
       if(BaseLevel <= 30) {
          npctalk "Look at that you are getting there, you are almost 2nd profession now right???";
          end;
       }
       if(BaseLevel <= 40) {
          npctalk "Look at that you are almost 2nd profession";
          end;
       }

Notes
-----

Without the use of 'end' it would travel through all the if's until the end of the script. If you were Level 10 or less, you would see all the speech lines, the use of 'end' stops this, and ends the script.