---
title: Clientinfo.xml
permalink: /Clientinfo.xml/
---

*sclientinfo.xml* is a file that configures your modified Sakray client so that it may connect to rAthena Servers, for non-Sakray and Renewal clients this file is usually called *clientinfo.xml*.

Template
--------

    <?xml version="1.0" encoding="euc-kr" ?>
    <clientinfo>
        <desc>Ragnarok Client Information</desc>
        <servicetype>korea</servicetype>
        <servertype>sakray</servertype>
        <hideaccountlist />
        <passwordencrypt />
        <passwordencrypt2 />
        <extendedslot />
        <readfolder />
        <connection>
            <display>SERVER NAME HERE</display>
            <desc>Ragnarok Online</desc>
            <balloon>this is a tool tip</balloon>
            <address>SERVER IP HERE</address>
            <port>6900</port>
            <version>20</version>
            <langtype>1</langtype>
            <registrationweb>REGISTRATION URL HERE</registrationweb>
            <yellow>
                <admin>2000001</admin>
                <admin>2000002</admin>
                <admin>2000003</admin>
            </yellow>
            <loading>
                <image>loading00.jpg</image>
                <image>loading01.jpg</image>
                <image>loading02.jpg</image>
                <image>loading03.jpg</image>
                <image>loading04.jpg</image>
                <image>loading05.jpg</image>
                <image>loading06.jpg</image>
                <image>loading07.jpg</image>
                <image>loading08.jpg</image>
                <image>loading09.jpg</image>
                <image>loading10.jpg</image>
            </loading>
        </connection>
    </clientinfo>

Explanation
-----------

| Tag                  | Description                                                                                                                                                                                                                            |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <servicetype>        | Specifies the client service type (country). Affects client behavior for some features. See below for valid values. Should be set to **korea**, unless you know, what you want to achieve by using another value.                      |
| <servertype>         | Specifies the server type this client is intended for. Affects client behavior for some features. See below for valid values. Should be set to **sakray**, unless you know, what you want to achieve by using another value.           |
| <hideaccountlist />  | When present, disallows the client from showing Service Select screen and uses the first <connection> entry automatically.                                                                                                             |
| <passwordencrypt />  | When present, passwords are encrypted (method 1) before being sent to the server. Incompatible with **use_MD5_passwords** defined in .../conf/login_athena.conf.                                                                    |
| <passwordencrypt2 /> | When present, passwords are encrypted (method 2) before being sent to the server. When you use this with <passwordencrypt />, method 2 will be used. Incompatible with **use_MD5_passwords** defined in .../conf/login_athena.conf. |
| <extendedslot />     | When present, all character slots (usually 9) are available. Otherwise only 2-4 are enabled for use, others are displayed as 'Not available'.                                                                                          |
| <readfolder />       | When present, all files are first searched inside the /data/ folder, then inside the [GRF](/GRF "wikilink") archives. Otherwise files inside the /data/ folder are only accessed, when they were not found inside the GRF archives.    |
| <display>            | Displays the name of the server at the Service Select screen.                                                                                                                                                                          |
| <desc>               | Server description.                                                                                                                                                                                                                    |
| <balloon>            | This tag tells the game to display a tooltip when the cursor is over the server name on the server select screen.                                                                                                                      |
| <address>            | IP or DNS address of the server (for DNS, client needs the DNS hex).                                                                                                                                                                   |
| <port>               | Connection server port (default 6900).                                                                                                                                                                                                 |
| <version>            | Must be equal to **client_version_to_connect** defined in .../conf/login_athena.conf.                                                                                                                                              |
| <langtype>           | See table below.                                                                                                                                                                                                                       |
| <registrationweb>    | Web address to open when you click the Register button.                                                                                                                                                                                |
| <yellow>             | Characters with the following Account IDs will be seen in GM sprites and have Yellow name/chat (add the Account IDs of all your GMs here).                                                                                             |
| <aid>                | Use instead of <yellow> to also allow the right-click menu for your GMs.                                                                                                                                                               |
| <loading>            | Define each loading screen in the path .../data/texture/À¯ÀúÀÎÅÍÆäÀÌ½º/ (to use more than 10, client also needs Unlimited Loading Screens hex).                                                                                        |

**Note:** All [XML](/wikipedia:XML "wikilink") rules apply, so <tag /> options can also be written as <tag></tag>.

`+-----+------------------------+-------------------+`
`| int | enum SERVICETYPE       | "servicetype" tag |`
`+-----+------------------------+-------------------+`
`| 0   | SERVICETYPE_KOREA      | korea             |`
`| 1   | SERVICETYPE_AMERICA    | america           |`
`| 2   | SERVICETYPE_JAPAN      | japan             |`
`| 3   | SERVICETYPE_CHINA      | china             |`
`| 4   | SERVICETYPE_TAIWAN     | taiwan            |`
`| 5   | SERVICETYPE_THAI       | thai              |`
`| 6   | SERVICETYPE_INDONESIA  | indonesia         |`
`| 7   | SERVICETYPE_PHILIPPINE | philippine        |`
`| 8   | SERVICETYPE_MALAYSIA   | malaysia          |`
`| 9   | SERVICETYPE_SINGAPORE  | singapore         |`
`| 10  | SERVICETYPE_GERMANY    | germany           |`
`| 11  | SERVICETYPE_INDIA      | india             |`
`| 12  | SERVICETYPE_BRAZIL     | brazil            |`
`| 13  | SERVICETYPE_AUSTRALIA  | australia         |`
`| 14  | SERVICETYPE_RUSSIA     | russia            |`
`| 15  | SERVICETYPE_VIETNAM    | vietnam           |`
`| 17  | SERVICETYPE_CHILE      | chile             |`
`| 18  | SERVICETYPE_FRANCE     | france            |`
`| 19  | SERVICETYPE_UAE        | uae               |`
`+-----+------------------------+-------------------+`

`+-----+------------------------+-------------------+`
`| int | enum ?                 | "servertype" tag  |`
`+-----+------------------------+-------------------+`
`| 0   | ?                      | primary           |`
`| 1   | ?                      | sakray            |`
`| 2   | ?                      | local             |`
`| 5   | ?                      | pk                |`
`+-----+------------------------+-------------------+`

[Category:Client Configuration](/Category:Client_Configuration "wikilink")