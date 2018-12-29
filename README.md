# nRF52840-Dongle_hex
Mecrisp-Stellaris Forth 2.4.7 RA hex file specialized for nRF52840-Dongle (https://www.nordicsemi.com/Software-and-Tools/Development-Kits/nRF52840-Dongle)

Redirects UART Rx and Tx to pins P0.29 and P0.31 respectively on the dongle. I selected
those particular pins because they appear to be unburdened and they are easy to 
access on the dongle pinout.  

To power the dongle, either power it with 5v over the USB connector, or else provide 3.3v to the VDD_OUT pin.  Despite its name, the Nordic schematic (see copy included here in this repository) shows that the VDD_OUT pin is connected directly to VDD on the chip.

Note: at present the hex file here provides no USB support, so the current choices of access to the REPL 
on the dongle are either 1.  The wireless REPL (https://github.com/rabbithat/nRF52_wireless_Forth_REPL), 
which I include in the hex file, or 2. serial access over the above two pins.  If you prefer to use different 
pins, you can very easily select the ones you want using the FORTH code (https://github.com/rabbithat/nRF52_change_UART_pins) 
already included in the hex file.

-----------------------------------------------------------------------
Installing the HEX file onto the Dongle:

In theory it could be uploaded to a new Dongle over the USB connector 
using the Nordic software tools.  However, I installed it using an 
nRF52840-DK instead.  To install it using a DK, make the following  
temporary connections using Dupont jumper wires while the DK is
unplugged and powered off:

VDD on the DK connects to VDD_OUT on the dongle.

VTG on the DK connects to VDD on the DK.

GND on the DK connects to GND on the dongle.

GND_DETECT on the DK connects to GND on the DK.

SWDIO on the DK connects to SWDIO on the dongle.

SWDCLK on the DK connects to SWDCLK on the dongle.

Then plug in the DK to your computer using its USB
connector.  Doing so will power both the DK and the dongle.
A JLINK virtual drive will appear on your computer's 
directory.  Simply drag and drop the HEX file from this
repository onto the JLINK virtual drive and wait a short 
while for the programming to finish.  Afterward, unplug
the USB connection to your computer and then remove the
temporary dupont wire connections.  Your dongle is now
programmed and ready to use.  That's all there is to it!
To power the dongle you may simply plug it into any USB
port.  If you have installed Version 2, you can talk to 
the REPL wirelessly and/or you may talk to it over a 
serial connection to pins P0.29 (Rx) and P0.31 (Tx).


-----------------------------------------------------------------------
Revision History:
-----------------------------------------------------------------------

Version 2 includes the following definition:

: init #29 makeNewUartRxPin #31 makeNewUartTxPin remote ;

so that the dongle will immediately activate the wireless REPL after powering up.

---------------------------------------------------------------------------

Version 1 includes the following definition:

: init #29 makeNewUartRxPin #31 makeNewUartTxPin ;

This makes pin P0.29 is the Serial Rx pin, and pin P0.31 is the Serial Tx pin.
By default it does not start the wireless REPL, but you may do so at
any time by typing 'remote' into the REPL.
