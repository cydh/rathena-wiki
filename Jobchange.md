---
title: Jobchange
permalink: /Jobchange/
---

Syntax
------

-   **jobchange** <job number>{,<upper flag>};

Description
-----------

This command will change the job class of the invoking character. It does work using the job IDs, but you can also use job names. The full list of job names and the IDs they correspond to can be found in .

This command will also set a permanent character-based variable 'jobchange_level' which will contain the job level at the time right before changing jobs, which can be checked for later in scripts.

**NOTE:** 'upper flag' can alternatively be used to specify the type of job one changes to.

Upper Values
------------

| Value         | Description                    |
|---------------|--------------------------------|
| -1 or not set | Preserves the current job type |
| 0             | Normal/Standard Classes        |
| 1             | High/Advanced Classes          |
| 2             | Baby Classes                   |

Examples
--------

`   // This would change your player into a Swordman`
`   `**`jobchange`**` 1;`
`   `
`   // This would change your player into a Swordman High`
`   `**`jobchange`**` 4002; `
`   `
`   // This would change your player into a Swordman`
`   `**`jobchange`**` Job_Swordman; `
`   `
`   // This would change your player into a Swordman High`
`   `**`jobchange`**` Job_Swordman_High; `
`   `
`   // This would change the character to a high swordsman. `
`   `**`jobchange`**` Job_Swordman,1;`

[Category:Script_Command](/Category:Script_Command "wikilink")