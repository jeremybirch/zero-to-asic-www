---
title: "Padring"
date: 2020-11-13T16:09:29+01:00
images: ["raven.png"]
featured_image: "raven.png"
---

We need to make sure we can package the [IC](/terminology/ic) after the [wafer](/terminology/wafer) has been diced into individual [dies](/terminology/die).

A common way of packaging ICs is to connect them to a [leadframe](/terminology/die#leadframe) by bonding tiny wires between the leads of the leadframe and the pads on the die.

The big bond pads around the outside of the IC often include [ESD protection diodes](https://en.wikipedia.org/wiki/Electrostatic_discharge), Input/Output drivers and so on.

This picture shows _raven_, an IC from Efabless. You can see around the edge there are the big bond pads and the power and ground lines. This structure is called a padring.

The ring around the outside of the die (dark blue) serves two purposes: it carries power supplies to the pads, and it forms part of the 'seal ring'. This is a stacked structure on all layers around the edge of the die and is designed to try to prevent contamination (including moisture) from being able to seep into the die, particularly through the micro-cracks that are created by sawing up the wafer to separate the die. Further cracks may be introduced by the bonding process which mechanically smears the end of the bondwire (often a highly oure wire of gold, aluminium or copper) onto the pad in order to form a bond. For both of these reasons, circuitry is normally kept away from these areas of damage. Becuase of the bonding process, and the width of the wires and machinery involved, the pad pitch is typically at least 25um. 

The circuitry attached to a pad might be a special buffer to convert external voltage levels to internal ones, large output driver transistors to drive much larger external currents than are present inside the device, and protection structures to prevent external effects (such as ESD discharges and extreme voltages) from destroying the chip. All of these are quite large compared with standard cell circuitry.

For more complex designs, such as modern microprocessors and memories that have hundreds or thousands of pins, other bonding techniques are used to avoid the chip being made bigger due to having a single line of pads all the way round the edge (which is called 'bondpad limited'). For these larger designs, ball bonding or similar techniques are used which spread the bonding points across the area of the die rather than just being at the edge, and use small balls of metal to directly connect the pads to the package without the use of a bondwire.

![raven](/raven.png)

The padring used in the [Google shuttle is included in Caravel](/terminology/shuttle#caravel).
