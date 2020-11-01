# Why balance cells

Balancing is critical to get full access to your battery capacity. think of it as a bucket with sides of different height. the total capacity of that bucket is only as high as the shortest side, because any excess will spill over. [link-to-site-with-bucket-analogy]

Additionally, an unbalanced pack of cells can result in one of the cells in the pack discharging / overcharging beyond its limits. However, a good BMS should be monitoring each cell of a battery pack individually, and should never allow any of the cells to go beyond its limits - so really the only limitation of an unbalanced battery pack, built correctly with a good BMS, is capacity.

There are two scenarios that lead to unbalanced batteries:
1. continual balance:
  - for correcting cell drift over time, with usage, due to internal resistance differences
  - most good BMS account for this
  - you can do this with a manual tool as well
  - balancing only requires small currents, less than 0.5 amps
    - (orion jr 2 is at 150mA [https://www.orionbms.com/manuals/pdf/jr2_operational_manual.pdf])
2. initial balance:
  - for initial construction of a battery, where cells are not guaranteed to be balanced
  - this must be done manually - and may require large changes in state of charge of batteries
  - must be done when initially constructing a battery

# How to balance cells

### Case 1: balancing cells that have drifted

We wont go into too much detail here, since for the most part - you'll have either a good BMS or a dedicated balancing tool that will do this for you. These tools are primarily intended for cell drift applications - where the cells are pretty close to being balanced already and have just slightly drifted, and as such require small state-of-charge adjustments to rebalanced them (i.e., apply small currents, typically less than 0.5 amps).

There are two types of balancing that cell balancers can do
- Active: (redistributing charge between cells)
- Passive: (discharging)

Most balancing tools will take the passive approach because it is simpler and costs less.

### Case 2: balancing cells during initial construction

When building a new battery pack from cells, you'll need to spend some time to balance these cells after you get them.

Prerequisites:
- in order to optimally balance a battery pack, you must be working with matched cells
  - if you have cells of different capacity (due to age or chemistry), you will never be able to get full capacity of the larger cells
  - if you have cells of different internal resistances (due to age or chemistry), cells will drift out of balance over time

Considerations: (these considerations about LiFePo4 cells dictate the nuances with which we interact with them)
- LiFePo4 cells have _very_ small internal resistance
  - LiFePo4 cells have internal resistances typically between 0.1mΩ-0.3mΩ
  - therefore, small voltage differences can cause _very_ high currents to go between cells when connected in parallel (e.g., 0.2V -> 1000 Amps)
- LiFePo4 cells have _very_ small voltage-difference / state-of-charge-difference
  - LiFePo4 have a very big plateau in voltage -vs- state-of-charge
  - therefore, voltage is not a good way to determine state of charge unless, you are at top or bottom [knees](definitions.md)

Goal:
- get cells to same state of charge

The level of precision with which you need to balance LiFePo4 cells depends on how you intend to connect them:
- LiFePo4 cells _will_ self balance in parallel
  - which means as long as you can connect them safely - they'll self balance and you dont need to worry
- LiFePo4 cells _will not_ self balance in series
  - which means that you and your tools will need to balance them with precision
  - for initial balancing, you'll want to get it as close as possible so that your BMS can take it from there (since BMS balance at low currents)


#### Safely connecting LiFePo4 cells in parallel

When you connect LiFePo4 cells in parallel, they will balance each other over time. The smaller the voltage difference, the longer it will take them to balance, due to Ohms Law: V = I * R.

##### The Concern

LiFePo4 cells have a very low internal resistance [consideration-1]. This is both good and bad.
- Good because small voltage differences will still result in relatively fast balancing
- Bad because larger voltage differences will cause too much current to flow between the cells.

Quick table of stats for typical LiFePo4 cell internal resistance of 0.1mΩ per cell:
- 0.2 V difference => 1000 Amps (effectively a short circuit)
- 0.02 V difference => 100 Amps
- 0.002 V difference => 10 Amps (undetectable by standard multimeter)
- 0.0002 V difference => 1 Amps (undetectable by standard multimeter)

This table is calculated using Ohms law
  - I = V * R
  - I = (V2 - V1) / (R1 + R2)
  - I = (Voltage Difference) / (Total Resistance)
  - I = (Voltage Difference) / (0.2mΩ)

The concern is that, if your cells have too high of a difference in voltage, the current will destroy your cells. Therefore, you must make sure that the voltage difference of your cells will not surpass the max charging / discharging current your cells are rated for.

For 190 Ah cells:
  - rated for 0.5C charging -> 95 Amps
  - therefore, we want just under 0.02 V difference max
  - fortunately, 0.02 V difference is easily detected by a standard multimeter

Note: the table above assumes "worst case scenario" - where the batteries have the minimal rated internal impedance. Its in the correct order of magnitude of what you'll typically find. Most cells are rated between 0.1mΩ-0.3mΩ.

##### The Solution

As we saw above, we must make sure that the cells are within 0.02 V of eachother before connecting in parallel - otherwise we will effectively short-circuit the cells - too large of a current passing between the two.

If your cells are more than 0.02 V apart from eachother, you really only have two options:
- manually charge the lower voltage cell
- manually discharge the higher voltage cell

In an ideal world, you would also be able to place a resistor between the cells to limit current - but this is dependent on the voltage difference you want to cater to and it is very difficult to find resistors of suitable size:
- for example:
  - if you want to ensure no more than 70 Amps are flowing with up to a 0.2 V difference in charge, then you'll need a 3mΩ
    - I = V / R
      - we want to limit current to max 70 Amps
      - the max difference between cells we'll allow is 0.2V
      - => R = V / I = 0.2 / 70 = 0.00286 = 2.9 mΩ
  - you will be hard pressed to find a resistor less than 1 Ohm, so this is not really an option in most scenarios.
- therefore, this is not a practical solution for most situations

Fortunately, manually charging / discharging is the simple enough.

To charge, you can use a variable power supply to charge to the desired voltage. For example:
- variable power supply:
  - [link-to-example] https://www.amazon.com/gp/product/B07M9N73YQ/ref=ppx_yo_dt_b_asin_title_o07_s00?ie=UTF8&psc=1
  - [link-to-example-of-usage]
- LiPo cell charger:
  - [link-to-example]
  - [link-to-example-of-usage]

To discharge, you could use large resistors, dischargers, or load testers:
- resistors:
  - [link-to-example]
  - [link-to-example-of-usage] [link-to-example-of-usage-with-relays-to-switchoff]
- dischargers:
  - [link-to-example]
  - [link-to-example-of-usage]
- load testers:
  - [link-to-example] https://www.amazon.com/gp/product/B07F3NHHST/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1
  - [link-to-example-of-usage]

Even more fortunately, a basic multimeter has just enough precision to measure at the 0.01V order of magnitude.
- for example:
  - for a 190 Ah capacity battery, 0.5 C is the maximal continuos charge current recommended
    - i.e., no more than 95 Amps continuously flowing
    - therefore, no more than just under 0.02V difference between cells is allowed
      - I = 0.02 V / 0.2 mΩ = 0.02 V / 0.0002 Ω = 100 A
- to allow for extra caution in rounding, you may as well aim to get the voltages within 0.01 V
  - examples, considering excessively worst case "rounding" method:
    - 3.33 (3.33999) -vs- 3.31 (3.31000) => no good, that is effectively 0.03 V difference
    - 3.32 (3.32999) -vs- 3.31 (3.31000) => ok, that is under 0.02 V difference
    - 3.31 (3.31999) -vs- 3.31 (3.31000) => ok, that is under 0.01 V difference

##### Summary

To safely connect LiFePo4 cells in parallel, make sure that the voltage difference will cause a current smaller than the lowest C rating of the cells.

At 0.1mΩ internal cell resistance per cell, between two cells wired in parallel:
- 0.02 V difference => 100 Amps
- 0.01 V difference => 50 Amps

Typical max charge current for a LiFePo4 cell is 0.5 C, so:
- 200 Ah cell -> no more than 0.02 V difference to safely connect
- 100 Ah cell -> no more than 0.01 V difference to safely connect

#### Efficiently balancing LiFePo4 cells for series

When you connect LiFePo4 cells in series, they will not balance each other over time. What is worse, is that it is very difficult to detect the state of charge of LiFePo4 cells when considering voltage alone, due to their "voltage plateau".

Therefore, you must take active measures to specifically give an initial balance to the cells before combining them in series.

##### The Concern

LiFePo4 cells have a very flat "voltage plateau" for most of their states of charge [consideration-2]. This is both good and bad.
- Good because:
  - you will have a stable and predictable voltage for most of your depth of discharge.
  - you can safely connect cells in parallel for throughout most of their states of charge.
- Bad because
  - it is very difficult to determine the state of charge of the cell for most of the states of charge.
  - parallel-cells will self-balance very slowly, if at all, in large ranges of state-of-charge.

Quick table of stats for typical LiFePo4 cell of state-of-charge -vs- voltage:
- 90% SOC => ~3.35 V (~3.33 V under 0.25C load)
- 70% SOC => ~3.30 V (~3.30 V under 0.25C load)
- 55% SOC => ~3.30 V (~3.29 V under 0.25C load)
- 40% SOC => ~3.30 V (~3.28 V under 0.25C load)
- 30% SOC => ~3.25 V (~3.25 V under 0.25C load)
- 20% SOC => ~3.23 V (~3.23 V under 0.25c load)

To create a table like this, you must measure the state of charge of the battery by measuring the current drawn from a battery and integrating it over time to detect how much capacity has been used, of the total capacity measured in advance, and comparing it against the voltage. This table was sourced from the good folks at (solacity.com[8])[https://www.solacity.com/how-to-keep-lifepo4-lithium-ion-batteries-happy/].

What this means is that between 40% and 70% state of charge, there is less than 10mV of difference - with potentially zero difference in voltage at some points along the plateau.

This is concerning for two reasons:
- most multimeters can not detect less than 10mV precision
- batteries connected in parallel in this range may not ever balance
Therefore, you must make sure that when balancing the cells, you are balancing at either the top or bottom voltage-knee of the cells state of charge - where voltage changes more significantly with state-of-charge

Note: in the theoretical worst case scenario of the voltage-plateau, there is absolutely zero difference in voltage - which means that even with the extremely small internal resistance of the cells there would still be no balancing occurring when wired in parallel at these states-of-charge.

##### The Solution

As we saw above, the main problem in balancing is dealing with the voltage-plateau of LiFePo4 cells. There is really only one way to solve for this: balance outside of the voltage plateau.

The two ranges outside of the voltage-plateau are called the voltage "knees", since the rapid increase in change in voltage looks like a knee on both end when drawn on a graph. Balancing at the high voltage knee is called "top balancing", and balancing at the low voltage knees is called "bottom balancing".

Should you top balance or bottom balance?
- If you have matched cells and are not going beyond a 90% depth of discharge - it will make no difference to you.
  - matched cells means the cells have the same capacity, meaning as long as they are balanced on one side, they'll be very close on the other.
  - 90% depth of discharge, which you already should be below to maximize battery cycle life, means that even if the cells dont have the exact same capacity - you'll never notice.
- When you add in a good BMS, which you should already have, it makes even less difference to you.
  - your BMS will slowly balance your cells at the top when charging, to prevent capacity loss due to cell drift - caused over time due to internal resistance differences, so you'll effectively have your cells top balanced anyway.
  - your BMS will monitor each cell's voltage individually to protect it from both over charge or discharge, in worst case scenarios that it turns out the cells for some reason are not matched and do not have the same capacity

To assist with the next section, here is a quick table of voltage difference -vs- balancing current, for two LiFePo4 cells connected in parallel with worse case internal resistances of 0.3mΩ
- 0.01 V -> I = V / R = 0.01V / 0.6mΩ = 0.01V / 0.0006Ω = 16.67 Amps
- 0.005 V => ~8.3 Amps
- 0.001 V => ~1.6 Amps

Lets assume a high capacity scenario, which will take longer to balance than lower capacity scenarios, so will be more of a worse case scenario for most folks. Lets assume you have a 10kWh battery pack, consisting of 16 cells at 190 Ah each. All 16 cells in parallel result in a total capacity of 3040 Ah. This means that each %1 of state-of-charge consists of 30.4 Ah.

Bottom balancing:
- connect the cells in parallel, [after making sure its safe to do so](#safely-connecting-lifepo4-cells-in-parallel)
- discharge the cells to ~3.15 V
  - this is ~15% S.O.C
  - at this voltage, the cells balance faster than 16 amps per hour, sufficient for most use cases with batteries left overnight for balancing
    - at worst, the slope in this range is 0.05V per 5% S.O.C difference => 0.01V per 1% S.O.C difference
    - assuming you are aiming for at most a 1% SOC difference, that is a total of 0.01V at worst => ~16 Amps difference at slowest pace
    - this means that the absolute worst case, absolute slowest pace, you will balance at 0.5% state-of-charge per hour
    - which means that in 24 hours you can balance more than 12% state-of-charge in a 3040 Ah 16p, block of cells connected in parallel
- leave overnight for most configs
  - overnight, 10 hours, will be able to transfer atleast 160 Ah of charge (e.g,. 5% state-of-charge difference for a 3040Ah pack)

Top balancing
- connect the cells in parallel, [after making sure its safe to do so](#safely-connecting-lifepo4-cells-in-parallel)
- charge the cells to [TODO:pick-voltage-and-do-maths]
- leave overnight for most configs

After your cells are balanced, you're good to go - you may now disconnect them from the parallel configuration and wire them in series as desired.

##### Summary

To successfully balance your cells, in order to use maximum capacity when cells are connected in series, you must either top or bottom balance the cells. Both work, as long as your cells are matched. Leave overnight at top or bottom voltage, connected in parallel, for them to balance.





----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------

# References and Details

which is better, top or bottom?:
- [1] https://diysolarforum.com/threads/top-vs-bottom-balancing-and.2801/
- > this is a religious question
- >  I have read several places that LiFePo can "tolerate over voltage" better than other chemistries, but I have never heard LiFePO can tolerate under voltage. In fact, I have heard statements like "under-voltage will instantly kill LiFePo"
Given those two statements, I would think that bottom balancing is best for battery protection..... but that is a guess on my part.

we chose bottom balancing because:
- under-voltage will instantly kill LiFePo - so its better to know that all cells are at same low voltage, rather than at high voltage
- BMS will top balance for us at high voltage anyway, slowly
- it is faster, since cells are stored (and thus shipped) at 30% S.o.C and it can take a while to charge them

NOTE:
- even though cells can have the same voltages, they could still have different capacities


[2] https://www.mobile-solarpower.com/diy-lifepo4-solar-battery.html
> Bottom Balancing the Cells: This is REQUIRED when first building a LiFePO4 battery. And it is very easy to do. Slowly discharge the cells to 5-10%  capacity while watching the balance of the cells. When the battery is nearly depleted, balance the cells. Then charge it back up again.  Discharge again and watch the balance of the cells. If they are bottom balanced properly, they should be nearly the same voltage when nearly depleted. This will ensure that none of the cells will dip to too low of a voltage when the battery is discharged.
Bottom balancing is recommended for solar because you want your SOC to float around 50%.  If you have a small battery, mismatched/used cells, chargers that only charge to 14.5 volts (and cannot be edited), you should top balance. More on this at the bottom of the page (or watch this video).

> Step 2: Equalize the voltage of the cells. This will "balance" the cells so that they are the same voltage. Use this guide to determine how to equalize your cells:
>  - If you check the voltage and the cells are identical or within .05 volts of each other, you can skip equalization. Go to step 3.
>  - If the cells have a similar voltage, but they are a little bit different (within .2 volts of each other), you can safely parallel connect them to equalize the voltages.
>  - If the cells have a large voltage difference (more than .2 of a volt), you should not parallel connect, and instead discharge the higher voltage cell with a 25-50 watt, 2.7 ohm resistor. Just attach the leads of the resistor to the individual higher voltage cell, and wait till it is at a voltage that is closer to the other cells. When they are within .3 volts of each other, then you can connect them in parallel and allow them to equalize.
> And this is how you connect the battery cells in parallel. Be sure to allow them to equalize for a few hours to a day (if the guide above says its safe to do so):


Note: source [1] says that it will take forever for the cells to balance just by passive connection. but source [2] says to do just that. Which is correct?

--

[5]: http://liionbms.com/php/wp_parallel_balance.php
- good way to prebalance is to connect them all in parallel and wait
- best way to prebalance is to connect all in parallel and charge to 100

again, what is the risk of short-circuiting the batteries when connecting in parallel though? lifepo4 are low impedance - so what is the threshold of voltage delta

----------


[4] https://endless-sphere.com/forums/viewtopic.php?t=14840
> I thought you couldn't do that to low-impedance battery cells like LiFePO4 or NiCd or etc. The problem being, no two cells ever have EXACTLY the same voltage across their terminals. One cell might have 3.71V, while the next cell has 3.73V. If you put these two cells in parallel, you immediately get a current flow as the higher-voltage cell tries to charge the lower-voltage cell. Since the cells are very low impedance, the current can be quite large, and one cell can exhaust the other as it tries to charge it.
