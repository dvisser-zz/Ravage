### TODO

Items listed here should be changed one at a time, and the line marked done, this
file and the changed files committed together. After a session of N changes the
PDF should be updated and pushed. The PDF should not be updated with each and
every change as there is no benefit and a binary repository size drawback.

 - Change all values using capital K for kilo to lower case k for kilo
 - DONE, Add no connection symbol to unconnected pin of RTC
 - Reverse direction designators of PK4 and PK5 in VR interfaces sheet, regression in recent work

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

 - Add second independently fused 5V out to connector pin out if enough pins
 - MAX99XX decoupling cap arrangement design required
 - Power supply page - requires design, discuss http://forum.diyefi.org/viewtopic.php?f=58&t=1478
 - Switch to new connector type - Dan
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
 4.  RS232 communications @ 5e51d8a0c3d99bf64ca3599f3e954b67b4b253e9
 5.  RPM conditioned inputs @ NO pending testing
 6.  Core analogue inputs @ NO pending value selection
 7.  Extra analogue inputs @ NO pending value selection
 8.  Digital and wake up inputs @ NO pending testing and part selection
 9.  Knock sensor inputs @ 55f59ffe663e9ac85e15489c5aa0e3c054d4e89e
 10. Igniter output drivers @ NO pending testing
 11. Injector output drivers @ 0526a1bb8adf934c94060e8f6c12ad40b406c916
 12. GP low side drivers @ 442e732dc18f5674576314bf57ca98bb4ed757f9
 13. 3-wire ISCV drivers @ 15cc869f0e39f8fb0abcd6d57b411e65066c510a
 14. SD card slot @ NO pending multiple changes
 15. Connector pin out @ NO pending connector change

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
 15. Connector pin out

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
