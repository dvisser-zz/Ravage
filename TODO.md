### TODO

Items listed here should be changed one at a time, and the line marked done, this
file and the changed files committed together. After a session of N changes the
PDF should be updated and pushed. The PDF should not be updated with each and
every change as there is no benefit and a binary repository size drawback.

 - DONE, Move RPM magic input from A4 to K4 and add the other channel to K5
 - DONE, Fit a Molex 500901-0801 micro SD card slot attached to SPI1
 - DONE, Change CPU RX to CPU RXD0 and CPU RX 2 to CPU RXD1, same for TX pins
 - DONE, Correct PDF page ordering and page number labeling per new guide added below
 - DONE, Add a 0.33 μF to 1.0 μF ceramic capacitor in parallel with a 0.01 μF ceramic capacitor on Vs of each MAP/AAP sensor
 - DONE, Add 15nF capacitors to the two ground monitoring analogue inputs
 - DONE, Move the spare digital inputs from A0 and A1 to J0 and J1 which have interrupt capability
 - DONE, Add (5.6V) zener protection of 5V rails from: http://forum.diyefi.org/viewtopic.php?f=58&t=1328
 - DONE, Add headers for spare IO, at least: SPI2 (H4-7), I2C0 (J6-7), CAN0 (M0-1)
 - DONE, Add headers for bonus IO, maybe: I2C1 (J4-5), CAN1 (M2-3), CAN2 (M4-M5), ports C and D if space
 - DONE, Protect LEDs from high reverse voltage with another diode 

All pages that are changed must be rechecked and enter another cycle of fix and
then check or be confirmed good and then locked down.

### Still To Review

These pages have not been checked and confirmed good or had fixes suggested.

 - Knock interface page
 - RS232 for LC-1 page
 - Power supply page

Once checked they should be moved to the TODO or to Lock Down.

### Still To Add/Do

Known issues which don't have a solution 100% nailed down yet.

 - Switch to new connector type - Dan
 - Finalise VR interface LEDs - Dan
 - Select digital input resistor values - Can't, needs diode part selection
 - Finalise selection of wakeup pin - Fred
 - Verify that TC427COA can drive 100mA continuous - Dan
 - Double check that opto will work with unchanged SM - Fred
 - Tune the ADC input filters - Fred + consultation
 - PLL cap that is not sensitive to mechanical noise - Maybe

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

 - CPU page, except net names/other sheet connections, and maybe PLL cap type

