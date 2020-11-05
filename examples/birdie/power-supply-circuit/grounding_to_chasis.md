
context:
- typically in automotive applications, you only run positives and you "ground" through the chasis - as the negative of the battery is connected to the chasis
- in offgrid solutions, you have negatives for your full circuit already. so the question is - should you still ground to the chasis?
  - the implied question here is - should you connect the negative of your offgrid solution to the negative of your vehicle battery?
- note that the chasis is not ever truely grounded. you have 4 big insullators separating the chassis and the ground

seeing both to do so and not to do so still

--

> This is about 120 volt ac. If your 120ac is connected to the pedestal. Your chassis is not connected to the green wire. Your toaster oven cord has a short to the chassis. The breaker will not trip. The chassis will be hot to earth, and you will complete the circuit when you stand on damp ground and touch the skin of the vehicle. The chassis should always be connected to the green wire when getting power from the pedestal. And yes, 120 volts can kill you.

[1](https://www.cheaprvliving.com/forums/showthread.php?tid=26822)
--

[1](https://www.cheaprvliving.com/forums/showthread.php?tid=26822)
  - no explanation for it yet
  - tons of people asking why
  - some people mentioning that it caused problems in the circuit


---

> Thanks for all the replies.

> I called and talked to the people at blue sea and they suggested exactly what Midwest Drifter laid out.
> 1. connect all the green (ground wires) to the panels ground (safety ground) buss bar.
> 2. connect the green wires from the safety ground buss bar to the inverter (my Magnum inverter has a pass through and an internal transfer switch).
> 3. connect the two panel safety buss bars together (I'm running a main and sub panel)
> 4. Do not ground the AC system to the chassis.

> Run GFCI:
> 1. All internal 120 amp outlets are GFCI protected
> 2. My 30 amp shore power plug in has GFCI protection as well

> I'm also running a ELCI main and sub panels for additional protection.

> I think the only thing outstanding is whether you ground the DC system to the chassis or just back to the negative pole on the battery pack. I'm currently grounding to the chassis.

https://sprinter-source.com/forums/index.php?threads/58574/


---


> The manual says this...

> The inverter/charger should always be connected to a permanent, grounded wiring system. The idea is to connect the metallic chassis of the various enclosures together to have them at the same voltage potential, which reduces the possibility for electric shock. For the majority of installations, the inverter chassis and the negative battery conductor are connected to the system’s ground bond via a safetygrounding conductor (bare wire or green insulated wire) at only one point in the system. Per the NEC, the size for the grounding conductor is usually based on the size of the overcurrent device used in the DC system. Refer to Table 1 to select the appropriate DC ground wire based on the overcurrent device used for your inverter model.

> If the inverter is in a vehicle, DO NOT connect the battery negative (-) cable to the vehicle’s safety ground. Only connect to the inverter’s negative battery terminal. If there are any non-factory installed appliances onboard the vehicle, DO NOT ground them at safety ground. Only ground them at the negative bus of the DC load center (as applicable).

https://forum.solar-electric.com/discussion/350524/to-ground-or-not-to-ground-to-chassis


---

MPPT SOlare charge controller manual says, on page 5, section 3.2:
> The USA National Electric Cod (NEC) requires the use of an external ground fault protection device (GFPD). These MPPT chargers do not have internal ground fault protection. The system electrical negative should be bonded through a GFPD to earth ground at one (and only one) location.

---

to read: https://www.rvtravel.com/rv-electricity-the-abcs-of-campground-power-and-grounding-part-2/
