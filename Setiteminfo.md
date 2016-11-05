---
title: Setiteminfo
permalink: /Setiteminfo/
---

Syntax
------

-   **setiteminfo**(<item id>,<type>,<value>)

Description
-----------

This function will set some value of an item. Returns the new value on success, or -1 on fail (item_id not found or invalid type).

Valid types are:

<table>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Buy Price</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Sell Price</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Item Type</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>maxchance (Max drop chance of this item e.g. 1 = 0.01% , etc..</p>
<p><code>if = 0, then monsters don't drop it at all (rare or a quest item)</code><br />
<code>if = 10000, then this item is sold in NPC shops only</code></p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>sex</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>equip</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>weight (each 10 is 1 weight)</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>atk</p></td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>def</p></td>
</tr>
<tr class="even">
<td><p>9</p></td>
<td><p>range</p></td>
</tr>
<tr class="odd">
<td><p>10</p></td>
<td><p>slot</p></td>
</tr>
<tr class="even">
<td><p>11</p></td>
<td><p>look</p></td>
</tr>
<tr class="odd">
<td><p>12</p></td>
<td><p>elv</p></td>
</tr>
<tr class="even">
<td><p>13</p></td>
<td><p>wlv</p></td>
</tr>
<tr class="odd">
<td><p>14</p></td>
<td><p>view id</p></td>
</tr>
</tbody>
</table>

Examples
--------

**`setiteminfo`**` 7049,6,9990; // Stone now weighs 999.0`

See Also
--------

-

[Category:Script Command](/Category:Script_Command "wikilink")