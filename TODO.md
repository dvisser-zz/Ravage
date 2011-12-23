### TODO

Items listed here should be changed one at a time, and the line marked done, this
file and the changed files committed together. After a session of N changes the
PDF should be updated and pushed. The PDF should not be updated with each and
every change as there is no benefit and a binary repository size drawback.

 - DONE Change "ISCV INV OUT" to "ISCV INV." same for non-inverted.
 - DONE Change all instances of injecter and igniter to ignitor and injector (e >> o) and remove the # from in front of each number
 - DONE in same commit as above line, Change the short versions "INJ1" to Injector 1" and "IGN1" to "Ignitor 1" between the connector sheet and the driver sheets
 - DONE Change wording "optional: fit these if using PORTB to drive injectors and remove the 100K and 1K resistors from PORTT." to "Note: Fit these if using PORTB to drive injectors and remove the 1K resistor from PORTT."
 - DONE Swap SD card slot to this push-pull part: http://au.element14.com/jsp/displayProduct.jsp?sku=1764377&action=view&CMP=GRHS-1000466
 - DONE Swap clock chip on knock page to identical crystal part number to main MCU, but with 1M resistor in parallel http://forum.diyefi.org/viewtopic.php?p=20799#p20799
 - DONE Set values of the four knock input resistors to those discussed http://forum.diyefi.org/viewtopic.php?p=20799#p20799
 - DONE Remove absolute file paths from all sheets, in one commit
 - DONE Add cost effective soic8 RTC I2C chip to lower left of cpu sheet
 - DONE Add 2 x cpu ground, 2 x switched 5v, 1 x always on 5v, 1 x raw 12v to the spare port headers
 - Increase value of ignition drive series limit resistors to 200ohm to keep power dissipation reasonable in extreme use cases
 - Fix RX/TX pin labels in green page box on bus on CPU page
 - Move RXEF040 polyfuse from ext MAP to power supply sheet where it is more obvious
 - Increase 47pF to 0.1uF on MAP/AAP same as everywhere else to make BOM simpler
 - Remove (5.6V) zener protection from CPU 5V rail, Fred's mistake
 - Change ground connection from RS232 jack to default not connected with two adjacent pads that can be jumpered only if desired, to avoid ground loops
 - Fix reversed polarity on RS232 2.5mm jack for LC-1, see this for info from Preston http://forum.diyefi.org/viewtopic.php?f=58&t=1477

### SD card sheet changes

Discuss all SD card sheet changes before doing anything, skype, IRC and forum: http://forum.diyefi.org/viewtopic.php?f=58&t=1479

 - Add cross to NC pins on SD card sheet
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

### PDF Sheet Ordering

All sheets except for the CPU/navigation sheet will be A4 size. The CPU sheet
needs to be larger to fit the minimum required items on it. The sheet ordering
should be kept consistent on every commit. Preferred ordering is as follows.

 1.  CPU, decoupling, clock, PLL, config, BDM, load/run SW, CEL, other sheets
 2.  Power supplies
 3.  USB communications
 4.  RS232 auxiliary communications
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

### Pre-Layout Lock Down

As each sheet becomes a perfect representation of what we want to see in RavAGE
it will get locked. That is to say, no further changes to that sheet's source
.SchDoc file will be allowed without agreement between all key players.

Locked sheets will be listed here as they are finalised:

 - Injector output drivers SHA: 579debcee21d78963c464d22f276e9007f06890d
 - GP low side drivers SHA: 34ec877048cf25f6aa3182fc51247ac7178a53ac
 - 3-wire ISCV drivers SHA: 145077c2c545e9f36c01ac72a6633bf734ca3d17

### Space Constraints

Due to the target board size and the level of things included so far, some
items could get cut when layout starts and we start getting a feel for
realistic limitations. The current plan is a 2-layer board with all features
that are currently in the schematics. I will list the possible changes below.

 - Change from 2-layer to 4-layer. Benefits more compact, better noise resistance. Drawbacks, more expensive, mildly less hackable.
 - Remove SD card slot and 3.3V power supply components
 - Remove RS232 interface for LC-1 and other products
 - Remove knock sensing interface circuit
 - Drop always-on support in favour of a simpler key switched design
 - No built in BDM header included, program via bed of nails or edge connector
 - Less spare and GP and diagnostic drivers and protection circuits
 - Less injector and ignition drivers, 4 minimum each, optimally 6 ignition, 8 injection
