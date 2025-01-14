---
title: "Antenna Report"
date: 2021-03-30T12:31:35+02:00
images: ["antenna-rule.png"]
featured_image: "antenna-rule.png"
---

Antenna rules are part of the [DRC](/terminology/drc).

![antenna rule](/antenna-rule.png)

When the ASIC is being built up layer by layer, we have the gates of the MOSFETS built first. Then we use the metal layers to connect them into bigger blocks.
Between layers, the [wafer](/terminology/wafer) is often flattened. This process can induce enough electrical charge to destroy the connected gate.

After OpenLANE finishes, we have an antenna report in this file: ./reports/routing/41-antenna.rpt (number may change with OpenLane config)

The antenna report is a long collection of smaller reports like this:

      _1438_  (sky130_fd_sc_hd__clkbuf_1)  A
    [1]  met2:
      PAR:   36.40  Ratio:    0.00       (Area)
      PAR:  182.35  Ratio: 3134.60       (S.Area)
      CAR:  115.98  Ratio:    0.00       (C.Area)
      CAR:  582.45  Ratio:    0.00       (C.S.Area)

    [1]  met1:
      PAR:   79.50  Ratio:    0.00       (Area)
      PAR:  400.02*  Ratio:  400.00       (S.Area)
      CAR:   79.58  Ratio:    0.00       (C.Area)
      CAR:  400.10  Ratio:    0.00       (C.S.Area)

    [1]  li1:
      PAR:    0.07  Ratio:    0.00       (Area)
      PAR:    0.09  Ratio:   75.00       (S.Area)
      CAR:    0.07  Ratio:    0.00       (C.Area)
      CAR:    0.09  Ratio:    0.00       (C.S.Area)

    [1]  M1M2_PR:
      PAR:    0.34  Ratio:    6.00       (Area)
      CAR:    0.49  Ratio:    0.00       (C.Area)

    [1]  L1M1_PR_MR:
      PAR:    0.15  Ratio:    3.00       (Area)
      CAR:    0.15  Ratio:    0.00       (C.Area)


We have the name of the net, in this case '_1438_'. 

Then 5 subsections related to the layers of the chips that each have a PAR or CAR value on the left and a ratio on the right.
PAR and CAR refer to Partial or Cumulative Antenna Ratio. 

From [this reference on page 375](https://www.ispd.cc/contests/18/lefdefref.pdf):

* A PAR tells you if any single metallization step is likely to inflict damage to a gate.
* A CAR adds the damages on successive layers together to accumulate them as the layers are built up.

If the value exceeds the ratio then it's a violation. This is shown by an asterix (grep '\*' 41-antenna.rpt to find all the violations). 

So in the report above we can see we have an antenna violation on met1 as the PAR value of 400.02 exceeds the ratio of 400.

## Ignoring antenna violations

On the skywater slack, Tim Edwards recently spoke about this:

> The general principle here is that antenna violations will give you a yield hit---that's something to worry about on a production run because it will affect profit margins.  But for a test chip on an MPW run, you could in principle have a yield loss as high as 10% and never notice it.  So then it comes down mostly to personal choice.  If the antenna violation is in a circuit that you think people will re-use as-is on other projects, then it would be in your best interest to knock the antenna violations down to zero.  But it is most likely that the antenna violations occur in (1) a synthesized block which would most likely be resynthesized if re-used in another project, or (2) a top level layout which would necessarily be re-done for another project.  That's the thinking behind my guidance.

And:

> Most violations are not worth fixing unless they exceed the ratio by 2x

OpenLANE automatically inserts antenna diode cells to protect nets.

One way to try to reduce antenna violations is to try increasing the number of iterations that OpenLANE will try to reduce antenna violations.

    GLB_RT_MAX_DIODE_INS_ITERS (default is 2, only active if insertion strategy is 3)

You can also try a different insertion strategy. This configuration variable is called:

    DIODE_INSERTION_STRATEGY (default is 3)

You can find the definition here in the [OpenLANE docs](https://openlane-docs.readthedocs.io/en/rtd-develop/configuration/README.html).

## OpenLANE summary tool

The [OpenLANE summary tools](/post/openlane_output_files) can list antenna violations with the --antenna flag

