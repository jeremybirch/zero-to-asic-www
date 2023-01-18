---
title: "Floorplan"
date: 2020-11-13T18:20:59+01:00
images: ["floorplan.png"]
featured_image: "floorplan.png"
---

The floorplanning stage is where [OpenLane](/terminology/openlane) decides how big an area we need to fit everything in.
All the required [standard cells](/terminology/standardcell) are placed in the bottom left corner, ready for the [place and route](/terminology/place_and_route) stage.

![floorplan](/floorplan.png)

All the little rectangles in the centre are called tap cells. They make sure the [MOSFETs](/terminology/mosfet) work correctly by connecting the [P doped](/terminology/doping) [substrate](/terminology/wafer) to ground and the N-wells (that insulate the P-type MOSFETS) to power.

The slightly bigger rectangles at the edges are decoupling capacitors. After the [routing](/terminology/place_and_route) is finished, any spare space is filled up with decoupling capacitors. The job of these capacitors is to make sure that all the cells get a nice smooth power supply.

In larger designs, floorplanning decides where various blocks of the design will be positioned, including the pad ring, and what space will be allocated for power structures and top-level routing that join the blocks together. This is often an iterative process, trying to minimize the size of the whole chip, reduce wiring delays between blocks, and achieve a routable result. For a given process technology, the main things that control cost of a given chip are the size of the chip, the yield of that chip (which also depends on the size) and the cost of testing the functionality. So floorplanning serves a vital role in controlling cost as well as achieving performance.
