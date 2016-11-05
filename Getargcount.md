---
title: Getargcount
permalink: /Getargcount/
---

Syntax
------

-   [getargcount](/getargcount "wikilink")()

Description
-----------

To be used inside functions/callsub labels, returns quantity of arguments provided

Examples
--------

In **callsub**:

    mapname,x,y,z<TAB>script<TAB>SampleCallSub<TAB>123,{
          mes "The number of arguments in the callsub is: "+callsub(SAMPLE_CS,1,2,3,4,5,6);
    close;

    SAMPLE_CS:
        return getargcount();
    end;
    }

    //This should return the message:
    //The number of arguments in the callfunc is 6

In **callfunc**:

    mapname,x,y,z<TAB>script<TAB>SampleCallSub<TAB>123,{
          mes "The number of arguments in the callfunc is: "+callfunc(SAMPLE_CS,1,2,3,4,5);
    close;

    }
    function<TAB>script<TAB>funcName<TAB>{
         return getargcount();
    }

    //This should return the message:
    //The number of arguments in the callfunc is 5

[Category:Script Command](/Category:Script_Command "wikilink")