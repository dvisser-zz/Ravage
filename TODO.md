### TODO

Items listed here should be changed one at a time, and the line marked done, this
file and the changed files committed together. After a session of N changes the
PDF should be updated and pushed. The PDF should not be updated with each and
every change as there is no benefit and a binary repository size drawback.

 - DONE, Remove CPU pins that aren't connected from the bus and add NC X symbol to them for easy identification of unused pins, commit PDF after this change before others.
 - DONE, Move Spare IO headers to single header on sheet immediately before connector sheet (15), commit PDF after this change before others.
 - DONE, Move ADC ground to just come from CPU/Refernce ground, not be it's own and have 2 small pins called "Sensor Ground" near all of the inputs, commit PDF after this change before others.
 - Reorder the connector pin out from most sensitive to most noisy by way of these changes:
   - 5v tps physically adjacent to tps in
   - 5v aux physically adjacent to ext map in
   - Ignitor drives adjacent to inputs
   - Fuel pump relay drive adjacent to ignitor drives
   - Spare DINs next to spare ADCs
   - Rename 12V switched to 12V BRV/Wakeup and move to a small pin with the other inputs
 - Change the connector pin out in the following way as discussed on forum:
   - Add extra big pin to injector ground scheme, one on 1,3,5, the other on 2,4,6
   - Add extra big pin to ACC ground scheme, spread the pins across them similar to injector ground
   - Move one knock input to a dedicated connector and the other two pads/header for DIY addition
 - All connector changes above in a single commit except the ADC ground rework which should be in one commit WITH PDF update before the other items are done so that it can be separately checked, total 4 PDF commits and four schematic sheet commits, interlaced.
   - DONE, Update all VNB10N07 MOSFET's to VND14NV04-E MOSFET's due to space limitations and the fact that they are newer components.
   - Add more decoupling to MAX9926 IC's as per datasheet recommendations.

### SD card sheet changes

Discuss all SD card sheet changes before doing anything, skype, IRC and forum: http://forum.diyefi.org/viewtopic.php?f=58&t=1479

 - Improve layout of SD card sheet - Preston wants to do this
 - Move 3.3V regulator to 12V input such that sharp current changes don't affect our analogue stuff
 - Use regulator with enable input and parallel with analogue enable on 5V setup
 - Reduce post reg capacitor to 47uF tantalum
 - Add 200uF capacitor(s) to input of 3.3V reg
 - Change 1.0uF to 0.1uF ceramics on both sides of 3.3V reg
 - Move all 3.3V power supply caps to power supply sheet

All pages that are changed must be rechecked and enter another cycle of fix and
then check or be confirmed good and then locked down.

### Still To Add/Do

Known issues which don't have a solution 100% nailed down yet.

 - MAX99XX decoupling cap arrangement design required
 - Power supply page - requires design, discuss http://forum.diyefi.org/viewtopic.php?f=58&t=1478
 - Finalise VR interface LEDs - Dan
 - Select digital input resistor values - Can't, needs diode part selection
 - Finalise selection of wakeup pin - Fred
 - Verify that TC427COA can drive 100mA continuous - Dan
 - Double check that opto will work with unchanged SM - Fred
 - Tune the ADC input filters - Fred + consultation
 - PLL cap that is not sensitive to mechanical noise - Maybe
 - All pages, as the last step, check that power and ground connections are consistent and correct - Fred

And perhaps more.

### Pre-Layout Lock Down

As each sheet becomes a perfect representation of what we want to see in RavAGE
it will get locked. That is to say, no further changes to that sheet's source
.SchDoc file will be allowed without agreement between all key players.

Locked sheets will be listed here as they are finalised:

 1.  CPU and buses, etc @ NO pending cosmetic changes and movements
 2.  Power supplies @ NO pending discussion and design
 3.  USB communications @ NO pending testing
 4.  RS232 communications @ 499fc0af7bf7de4701e36266eb26f4519f6fdbed
 5.  RPM conditioned inputs @ NO pending testing
 6.  Core analogue inputs @ NO pending value selection
 7.  Extra analogue inputs @ NO pending value selection
 8.  Digital and wake up inputs @ NO pending testing and part selection
 9.  Knock sensor inputs @ 4c290ffce1c0d5e6a108e121f6de7f48d35dc9bd
 10. Igniter output drivers @ NO pending testing
 11. Injector output drivers @ 4c290ffce1c0d5e6a108e121f6de7f48d35dc9bd
 12. GP low side drivers @ 4c290ffce1c0d5e6a108e121f6de7f48d35dc9bd
 13. 3-wire ISCV drivers @ 7f8c11123221a048d2e89803336e2ae40265c135
 14. SD card slot @ NO pending multiple changes
 15. Spare IO Header @ NO pending initial design
 16. Connector pin out @ NO pending pin assignment

### PDF Sheet Ordering

All sheets except for the CPU/navigation sheet will be A4 size. The CPU sheet
needs to be larger to fit the minimum required items on it. The sheet ordering
should be kept consistent on every commit. Preferred ordering is as follows.

 1.  CPU, decoupling, etc
 2.  Power supplies
 3.  USB communications
 4.  RS232 communications
 5.  RPM conditioned inputs
 6.  Core analogue inputs
 7.  Extra analogue inputs
 8.  Digital and wake up inputs
 9.  Knock sensor inputs
 10. Igniter output drivers
 11. Injector output drivers
 12. GP low side drivers
 13. 3-wire ISCV drivers
 14. SD card slot
 15. Spare IO Header
 16. Connector pin out

### Space Constraints

Due to the target board size and the level of things included so far, some
items could get cut when layout starts and we start getting a feel for
realistic limitations. The current plan is a 2-layer board with all features
that are currently in the schematics. I will list the possible changes below.

 - Change from 2-layer to 4-layer. Benefits more compact, better noise resistance. Drawbacks, more expensive, mildly less hackable.
 - Remove SD card slot and 3.3V power supply components
 - Remove RS232 interface for LC-1 and other products
 - Remove knock sensing interface circuit
 - Drop always-on support and RTC in favour of a simpler key switched design
 - No built in BDM header included, program via bed of nails or edge connector
 - Less spare and GP and diagnostic drivers and protection circuits
 - Less injector and ignition drivers, 4 minimum each, optimally 6 ignition, 8 injection
