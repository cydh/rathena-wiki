---
title: Server Time Configuration Linux
permalink: /Server_Time_Configuration_Linux/
---

We'll get straight to the point. The information below will help you configure your **Server Time** according to different parts of the world. You will be prompted to select several time zone options. For this example, we'll be using Pacific Time.

Launch : **tzselect** in cli (command line interface)

    Please identify a location so that time zone rules can be set correctly.
      Please select a continent or ocean.
       1) Africa
       2) Americas
       3) Antarctica
       4) Arctic Ocean
       5) Asia
       6) Atlantic Ocean
       7) Australia
       8) Europe
       9) Indian Ocean
      10) Pacific Ocean
      11) none - I want to specify the time zone using the Posix TZ format.
      #?

Enter your desired region:

    2

      Please select a country.
       1) Anguilla           27) Honduras
       2) Antigua & Barbuda      28) Jamaica
       3) Argentina          29) Martinique
       4) Aruba          30) Mexico
       5) Bahamas            31) Montserrat
       6) Barbados           32) Netherlands Antilles
       7) Belize             33) Nicaragua
       8) Bolivia            34) Panama
       9) Brazil             35) Paraguay
      10) Canada             36) Peru
      11) Cayman Islands         37) Puerto Rico
      12) Chile          38) St Barthelemy
      13) Colombia           39) St Kitts & Nevis
      14) Costa Rica             40) St Lucia
      15) Cuba           41) St Martin (French part)
      16) Dominica           42) St Pierre & Miquelon
      17) Dominican Republic         43) St Vincent
      18) Ecuador            44) Suriname
      19) El Salvador            45) Trinidad & Tobago
      20) French Guiana      46) Turks & Caicos Is
      21) Greenland          47) United States
      22) Grenada            48) Uruguay
      23) Guadeloupe             49) Venezuela
      24) Guatemala          50) Virgin Islands (UK)
      25) Guyana             51) Virgin Islands (US)
      26) Haiti
      #?

Select a country:

    47

      Please select one of the following time zone regions.
       1) Eastern Time
       2) Eastern Time - Michigan - most locations
       3) Eastern Time - Kentucky - Louisville area
       4) Eastern Time - Kentucky - Wayne County
       5) Eastern Time - Indiana - most locations
       6) Eastern Time - Indiana - Daviess, Dubois, Knox & Martin Counties
       7) Eastern Time - Indiana - Starke County
       8) Eastern Time - Indiana - Pulaski County
       9) Eastern Time - Indiana - Crawford County
      10) Eastern Time - Indiana - Switzerland County
      11) Central Time
      12) Central Time - Indiana - Perry County
      13) Central Time - Indiana - Pike County
      14) Central Time - Michigan - Dickinson, Gogebic, Iron & Menominee Counties
      15) Central Time - North Dakota - Oliver County
      16) Central Time - North Dakota - Morton County (except Mandan area)
      17) Mountain Time
      18) Mountain Time - south Idaho & east Oregon
      19) Mountain Time - Navajo
      20) Mountain Standard Time - Arizona
      21) Pacific Time
      22) Alaska Time
      23) Alaska Time - Alaska panhandle
      24) Alaska Time - Alaska panhandle neck
      25) Alaska Time - west Alaska
      26) Aleutian Islands
      27) Hawaii
    #?

Select a time zone:

    21

      The following information has been given:

        United States
        Pacific Time

      Therefore TZ='America/Los_Angeles' will be used.
      Local time is now:    Fri Feb 27 10:08:21 PST 2009.
      Universal Time is now:    Fri Feb 27 18:08:21 UTC 2009.
      Is the above information OK
      1) Yes
      2) No
      #?

Confirm your choice:

    1

      You can make this change permanent for yourself by appending the line
        TZ='America/Los_Angeles'; export TZ
      to the file '.profile' in your home directory; then log out and log in again.

      Here is that TZ value again, this time on standard output so that you
      can use the /usr/bin/tzselect command in shell scripts:
      America/Los_Angeles