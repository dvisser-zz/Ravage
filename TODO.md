### TODO

Items listed here should be changed one at a time, and the line marked done, this
file and the changed files committed together. After a session of N changes the
PDF should be updated and pushed. The PDF should not be updated with each and
every change as there is no benefit and a binary repository size drawback.

 - DONE, Replace TC427COA IC used in ignitor drive schematic with the newer pin compatable TC4427ACOA IC. 
 - DONE, Fix reversed 1a port wires on VR sheet green box in MCU sheet
 - DONE, Make direction of all connector sheet ground off sheet symbols consistent
 - DONE, Connect knock input directly to CH1 input and put CH2 input on a single header pin for DIY connection
 - DONE, Add a note to the connector sheet stating that L pins and M pins are capable of higher current
 - Mirror crystal circuit left to right with the wires running down on the left and extend the CPU power caps to be a bit wider, higher, clearer and equal in size to each other
 - Extend the wires from PE 5,6,7 directly out without the steps
 - Remove the notes on capacitors and resistors from the PLL and Clock as these are standard values now
 - Combine the two grounds on the BDM header schematic
 - Split the sentence "Please refer to NOTES.md and ERRATA.md files for important design information." across two lines between 'Errata.md' and 'files' and surround with a dotted line. Current font size is OK.
 - Change "FUEL PUMP RELAY" to "FP RELAY" for net names, but leave "Fuel Pump Relay Driver" on the LSD sheeti
 - Change "LOAD/RUN" port label to just "LOAD" to respect the fact that the default state is doing a burnout, not loading code. (and allow it to not overlap the wire label next to it)
 - Change text in "Serial Monitor" box from "SM LOAD/RUN Jumper" to "Firmware Load Jumper"
 - Make the Extra analogue input green box be the same width as the others in that column
 - Make the second column of green boxes all the same width as each other, probably the same as RS232 or SD or USB currently is, use your discretion
 - Change text on VR sheet from "optional" (one of which is in the wrong place) to:

This resistor
for VR ONLY.

and

This resistor for
hall/opto ONLY.

 - Connector pin order changes:
  - Move Sensor Grounds close to: IAT,CHT,TPS,EGO,MAT,EXT MAP,SPARE ADC 1,SPARE ADC 2,+5V TPS,+5V AUX and extend both traces out past the other port symbols before joining
  - Move "+12V BRV/WAKEUP" between spare ADCs and spare DINs
  - Move spare LSD up closer to power/grounds
  - Move ISCV up closer to spare LSD
  - Move Injector outputs to right hand side of drawing
  - Move fuel pump relay drive to right hand side of drawing, it must be in the last 1-4 pin set, next to the ignitor drives.

### SD card sheet changes

Discuss all SD card sheet changes before doing anything, skype, IRC and forum: http://forum.diyefi.org/viewtopic.php?f=58&t=1479

 - Improve layout of SD card sheet - Preston wants to do this
 - Move 3.3V regulator to 12V input such that sharp current changes don't affect our analogue stuff
 - Use regulator with enable input and parallel with analogue enable on 5V setup
 - Reduce post reg capacitor to 47uF tantalum
 - Change 1.0uF to 0.1uF ceramics on both sides of 3.3V reg
 - Move all 3.3V power supply caps to power supply sheet

All pages that are changed must be rechecked and enter another cycle of fix and
then check or be confirmed good and then locked down.

### Still To Add/Do

Known issues which don't have a solution 100% nailed down yet.

 - Power supply page - requires design, discuss http://forum.diyefi.org/viewtopic.php?f=58&t=1478
 - Finalise VR interface LEDs - Dan
 - Select digital input resistor values - Can't, needs diode part selection
 - Finalise selection of wakeup pin - Fred
 - Verify that TC427COA can drive 100mA continuous - Dan
 - Double check that opto will work with unchanged SM - Fred
 - Tune the ADC input filters - Fred + consultation
 - PLL cap that is not sensitive to mechanical noise - Maybe
 - Annotate all components in the schematics
 - Add to and correct the NOTES.md file

And perhaps more.

### Connector pin ordering

At least four concerns guide the selection of pin to function mappings. By far
the most important of these is noise considerations. For this reason the layout
should maintain the following block ordering:

 1. RPM Inputs (hyper sensitive)
 2. Analogue Inputs (and 5V/Ground for them) (very sensitive)
 3. Digital Inputs (very sensitive)
 4. Ignition Outputs, low current (not sensitive, not noisy)
 5. Fuel pump relay drive (not sensitive, potential to be noisy)
 6. Spare LSD Outputs (not sensitive, usually noisy, when used)
 7. ISCV Outputs (not sensitive, usually noisy, when used)
 8. Injector Outputs (not sensitive, always noisy, when used)
 9. Power and Grouds (not sensitive, grounds always noisy)

The other three concerns are these:

 1. Intuitive User Order
 2. Fine grain routing
 3. Schematic Aesthetics

1 and 2 are of similar importance, and 3 should take a back seat to the others,
while still being kept in mind for ease of comprehension. As such the designers
are free to reorder pins of this sheet during the layout process to facilitate a
better, lower noise, simpler, cleaner, more compact, more comprehensible for the
user layout. Aside from the block ordering, the page should be kept with all
inputs and ignition drivers on the left and all high current and high noise
connections on the right. This sheet reordering does not need to follow the
usual process of agree, TODO, action, and can be done at the designers will.
Although this breaks with the process, it provides significant benefits in both
speed of development and quality of development. Thus it is worth doing this way.

The spare pins header sheet is subject to the same freedoms for layout reasons.

### Pre-Layout Lock Down

As each sheet becomes a perfect representation of what we want to see in RavAGE
it will get locked. That is to say, no further changes to that sheet's source
.SchDoc file will be allowed without agreement between all key players.

Locked sheets will be listed here as they are finalised:

 1.  CPU and buses, etc @ NO pending cosmetic changes and movements
 2.  Power supplies @ NO pending discussion and design
 3.  USB communications @ NO pending testing
 4.  RS232 communications @ 247e1f109145382aaa98ed5c90c7676b9f4068cd
 5.  RPM conditioned inputs @ NO pending testing
 6.  Core analogue inputs @ NO pending value selection
 7.  Extra analogue inputs @ NO pending value selection
 8.  Digital and wake up inputs @ NO pending testing and part selection
 9.  Knock sensor inputs @ NO pending input style change
 10. Igniter output drivers @ NO pending testing
 11. Injector output drivers @ 7ad534dc22ba7a4618d42d22ae2bb547ddda230f
 12. GP low side drivers @ 7ad534dc22ba7a4618d42d22ae2bb547ddda230f
 13. 3-wire ISCV drivers @ 7ad534dc22ba7a4618d42d22ae2bb547ddda230f
 14. SD card slot @ NO pending multiple changes
 15. Spare IO Header @ NO pending possible rearrangement
 16. Connector pin out @ NO pending pin rearrangement

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
