# Errata to Pocket65 v1 rev A
Hardware bugs found first prototype assembly
## Wrong USB battery charger footprint
USB charger module footprint is wrong, especially the pads for battery connection. These pads overlap power output pads.
### Solution
USB charger module needs to be mounted with some separation from the computer PCB. 1-pin goldpin headers with standard 0.1'' standoff placed in each corner do an excellent job. Then the battery connection can be connected too using a wire (e.g. left-over leads of a THT resistor).
## Top/bottom PCB collision
Top PCB button leads on the bottom side collide with various elements on the bottom PCB - capacitors, integrated circuits in sockets etc.
### Solution
Trim all button leads, so they don't poke out from the bottom of top PCB.
## Expansion connector sticks out too much
During the design phase it was supposed to be male connector, later changed to female connector, which does not need any stick-out.
### Solution
None needed, but should be fixed in future revisions.

