### TODO

Items listed here should be changed one at a time, and the line marked done, this
file and the changed files committed together. After a session of N changes the
PDF should be updated and pushed. The PDF should not be updated with each and
every change as there is no benefit and a binary repository size drawback.

 - DONE, Change TC4427ACOA to TC4427VOA and add a note allow builders to derate to TC4427EOA, or use the previous chip in 125C, if they choose.
 - DONE, Fix totally wrong PLL circuit! :-o How did we all miss that? :-/
 - DONE, Put the crystal circuit and left hand decoupling caps back the way they were before but flip it left to right such that the two wires are hard on the left just like they are hard on the right at the moment.This will allow the wires running down on the far left and make rooom to extend the CPU power caps to be a bit wider, higher, clearer and equal in size to each other, but i the earlier style. Sorry for being unclear and wasting your time! :-(
 - DONE, Change "FUEL PUMP RELAY" to "FP RELAY" on connector sheet
 - DONE, Make Sensor Ground traces follow same right angle path as other traces and have the ground symbol out to the left just past the other labels
 - Make connector pin out match this diagram: http://stuff.fredcooke.com/RavagePinOutAttempt2.png while still maintaining the left/right split and right angle traces.
 - DONE, Specify tight tolerance resistors for setting adjustable Vreg
 - Add notes to notes file about VR input resistors and caps being 200V and preferably 500mW
 - Add notes to notes file about VR 5k Shunt resistor being high wattage
 - Add notes to notes file about 470ohm adc current limit resistors being 250mW
 - Add notes to notes file about 200ohm ignition current limit resistors being 2W
 - Ground tabs of regulators in power supply sheet
 - Increase 22uF cap on output of LM2941S Reg to 47uF
 - Lower value of pull up on input to regulator from 33k to 20k: 6/20000 = 0.0003 - allows it to function at our lowest voltage of 6V
 - Add ferrite bead to 5V USB input before caps to prevent USB power noise corrupting comms, something like this: http://nz.element14.com/murata/blm18pg300sn1d/ferrite-bead-0603-case-30ohm/dp/1515741RL
 - Add LEDs to 5V switched, BRV/key power, and FTDI pin CBUS3
 - Change tx/rx LED resistors to 1k to reduce brightness
 - Expose CBUS2 and CBUS4 of FT232 to pads for DIY use

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
 - Finalise VR interface LEDs - Dan http://forum.diyefi.org/viewtopic.php?f=58&t=1510
 - Select digital input resistor values - Can't, needs diode part selection
 - Finalise selection of wakeup pin - Fred
 - Verify that TC427COA can drive 100mA continuous - Dan http://forum.diyefi.org/viewtopic.php?f=9&t=1188
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
 12. GP low side drivers @ 0e0ec7b1f4f0095ec0caf7929a33b819e120481e
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
