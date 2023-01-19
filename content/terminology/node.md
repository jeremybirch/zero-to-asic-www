---
title: "Node"
date: 2020-11-13T16:48:16+01:00
images: ["half-pitch.png"]
featured_image: "half-pitch.png"
description: "The node is nonsense"
---

The node (or process node) is used to designate the smallness of the manufacturing process used to create a chip.

The metrics for measuring integration density used to be metal half-pitch and gate length. For a while they were about the same number. This number became known as the node or process number.

The half-pitch refers to half the minimum center-to-center distance spacing (or pitch) between Metal 1 lines.

![half pitch](/half-pitch.png)

By 1990s these numbers became uncoupled, and the 130nm node actually has 70nm gates. 
By 2000, the node number "had by then absolutely no meaning" (Paolo Gargini. IEEE article by Samuel  K. Moore: [The node is nonsense](https://ieeexplore.ieee.org/document/9150552).)

It's still used as a marketing tool, but it doesn't really mean anything anymore.

This is because the whole industry effectively follows Moore's Law - which states that (on average) the transistor density and speed doubles every 3 years. In order to achieve a doubling of the number of transistors (which take up chip area, a two dimensional measure) we need to reduce the linear (one dimensional) size by 1/(square root of 2), or multiply by 0.707. So the steps in process node tend to go by an approximation of this : 500, 350 (not 353), 250 (not 247), 180 (not 177), 130 (not 127), 90 (not 92) and so on. The aim of these process steps is to achieve the doubling of performance and transistor density - this may not actually reduce the wiring pitch or transistor channel length by the same 0.707 factor.

Moore's Law allows everyone, from the designers to the fabs, the equipment manufacturers and the research engineers and physicists to know where they need to be and when, so that tasks that take several years to perform can be aimed at a commercially viable target. This is why the 'law' is really a self-fulfilling prophecy - it is not profitable to move at a slower pace (your competotion beat you to it) and it is very hard to move at a faster pace (none of the bits you need will be technically mature enough yet).

![node sizes](/node-table.png)

The table above shows how the gate length and metal half width measurements have become uncoupled from the node number. The table came from this interesting video about the latest and smallest process sizes.

{{< youtube 1kQUXpZpLXI >}}

Finally, this chart shows how even though the 130nm process is quite old, it and larger/older sizes still account for about 50% of all ASICs made by EuroPractice.

This is because a lot of analogue and mixed-signal devices use larger process nodes, both because the specialised processes for higher voltages and currents tend to be developed after the equivalent low voltage digital processes, and benefit from reusing old equipment, but also because analogue circuits actually work better on those nodes. Analogue circuits often use very large transistors to carry high currents, or tolerate large voltages, and require good device mathcing. This means that they don't really benefit from nodes aimed at producing ever smaller transistors that may have large variations between devices.


![process pie chart](/process-pie-chart.png)
