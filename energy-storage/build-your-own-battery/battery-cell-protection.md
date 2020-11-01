
# fundamental considerations

- over charging (each cell)
- over discharging (each cell)
- too hot (each cell)
- too cold (each cell)

notice that these considerations apply to _each cell_, not the overall battery.

therefore, to properly protect a battery pack - one must monitor and protect _each cell_


# additional considerations

- [bms:monitoring]: a good bms _must_ monitor each individual cell voltage
  - [3]:
    - > individual cell level monitoring, of per-cell voltage, is necessary in a good pack design.
    - > A good BMS (battery management system) will cut off charging well before any damage can be done to an individual cell.
    - >  Pack voltage alone tells you nothing about an individual cell going off early, only what the overall pack voltage is.

- [bms:balance]: if cells are not balanced in battery (both before put together and through usage, due to drift), you can damage the battery
  - [3]:
    - > In my experience, with properly matched LFP cells, these high charging voltages are simply unnecessary for fractional C / house bank use. Charging these cells to more than 14.0V, when they are properly matched, is really not necessary and only leads you closer into the danger zone, especially, if the cells were to drift or become out of balance.
      - NOTE:
        - charging to high voltage is unnecessary for fractional C / house bank usage
        - and is dangerous, if not monitoring cell voltage
        - and is dangerous, if not properly balanced
    - > Over discharging and over charging an unbalanced pack is where many LFP cells are destroyed. One minute the bank is delivering or accepting massive amounts of current and the next minute a cell has gone under voltage or over voltage and a cell hockey sticks or falls off the cliff before the other cells do.


- [charging]:
  - no float charging for lifepo4!
  - [3]
    - > They EXPECT you to charge to 14.6V/14.4V and then then STOP CHARGING.
    - > The reality is this is not at all how any commercially available marine chargers work.
    - > “Charge to 14.6V” is not the same as “Charge to 14.6V and then let it remain charging at 14.6V for FOUR HOURS”
