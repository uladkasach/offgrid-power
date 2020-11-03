### Question: why do metal conductors have resistance?
- > Within a metal conductor, even though there are free electrons, there is still resistance to current flow. This can be described by simple models, but apparently only quantum electron theories accurately deal with the behavior of metals under extreme conditions such as very low temperatures. Replacing the idea of electrons as particles with electrons as waves solves the problems of the simpler models. You can picture these electron waves oscillating through the metal lattice (which can also be pictured as a wave-like structure) - the interference of the lattice structure with the electrons causes resistance. This resistance is caused mainly by two things. One is impurities in the metal, which cause irregularities in the periodicity of the lattice. The other is the disturbance or "vibration" of the lattice caused by heat. Since some heat is always present (except at absolute zero) there is always some resistance from this source which prevents the electrons from sailing through.
   - https://education.jlab.org/qa/current_02.html

- "Electron theory of resistance"
  - http://www.schoolphysics.co.uk/age16-19/Electricity%20and%20magnetism/Current%20electricity/text/Resistance_/index.html

  - The resistance of any conducting material depends on the following factors:
    - the material itself (actually how many free electrons there are per metre cubed)
    - its length
    - its cross-sectional area
    - its temperature

  - Resistance (R) = V/I =2Lm /e2tnA
    - I = nAve
    - E = V/L
      - Ee = Ve/L = F
      - Ve/mL
      - v' = Vet /Lm
      - Vet = v

### Question: why does current cause heat in wires?
  - > Near room temperatures, metals have resistance. The primary cause of this resistance is the thermal motion of ions. [1](https://electronics.stackexchange.com/a/78678/59733)

### Question: why does resistance * current cause heat?

### Question: why does increasing radius of wire decrease resistance?
  - there are more electrons available, per length, to carry the current
    - > The larger the cross-sectional area of the conductor, the more electrons per unit length are available to carry the current. As a result, the resistance is lower in larger cross-section conductors. [1](https://electronics.stackexchange.com/a/78678/59733)

    - Question about this explanation though
      - why do the number of free electrons result in a decrease of resistance?
        - i though resistance was due to electrons bouncing and hitting random immobile atoms
        - there should be a proportional increase of immobile atoms && electrons
        - so shouldn't the rate of randomly hitting immobile atoms still be the same?
          - assuming motion is random, and the percentage of electrons -to- immobile atoms is the same => it should be the same
        - IS IT BECAUSE ELECTRONS HAVE TO MOVE LESS QUICKLY TO HAVE THE SAME OVERALL CURRENT? -> LESS COLLISIONS OVERALL? SINCE MORE ELECTRONS MOVING SLOWLY? -vs- LESS ELECTRONS MOVING QUICKLY? (!)(!) [answer]
          - see "electron theory of resistance": Resistance (R) = V/I =2Lm /e2tnA
          - Answer = speed of electrons depends on current + number of electrons + area!
            - J = n * v [https://physics.stackexchange.com/a/386098/42618]
              - i.e., current depends on number of electrons + speed
                - -> increase speed -> increase friction
                - -> increase electrons -> decrease speed -> decrease friction
            - I = n*A*v*e [https://physics.stackexchange.com/a/527894/42618]
              - area also affects, so when increase cross-sectional area of conductor, increasing both number of free electrons and area

    - i.e.,:
      - the thicker the wire -> the more free electrons -> the slower the electrons have to go -> the less they bump around
        - is free electron speed variable under current? or is it a constant?
        - it is variable! (electron drift velocity = fn (current, number of electrons))

  - [solution]: so, the reason that increasing the radius decreases the resistance is because:
    - there are more electrons now carrying that current -> so their average "electron drift velocity" decreases, which means the rate of collisions decreases -> which means less energy lost to heating up atoms



### Question: why does increasing length of a wire increase resistance?
  > The number of scattering events encountered by an electron passing through a material is proportional to the length of the conductor. The longer the conductor, therefore, the higher the resistance. [1](https://electronics.stackexchange.com/a/78678/59733)





R=ρL/A = ρL/(pi*r^2) [1](https://www.physicsclassroom.com/class/circuits/Lesson-3/Resistance)


### explanation attempt

Resistance comes from the random collisions that electrons have with immobile atoms on their way along the circuit [source-verify;double-check].

The resistance of a cylindrical conductor to electric current is a function of the length of the conductor (i.e., how far electrons have to push) and the diameter of the cross section of the conductor (i.e., how many other electrons there are to push forward).

The voltage drop in a circuit is a function of the current flowing through it (i.e., how fast electrons are pushing around) and the resistance of the circuit (i.e., how much useless pushing they have to do to get from point a to point b).


### analogy attempt

Electrical current can be thought of as an endless, tightly packed, traffic jam of little electrons in a tunnel with obstacles in the way. Electrons actually move through the circuit _really_ slowly, because they have to shove and bounce around their environment - bouncing mostly in random directions - but generally against the direction of the applied electric field. The only things that move in their environment are other electrons, so to get to where they want to go - they have to shove the other electrons forward and avoid the obstacles (i.e., immobile atoms).

When they push atoms, they cause heat.

When they push electrons, they move forward.

The more electrons are available to be pushed (wider cross-section), the less fast each electron has to be pushed (decrease in resistance).

The farther the electrons have to push (longer length), the more electrons collide with immobile atoms (increase in resistance).

