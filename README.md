# nRF52840-Dongle_hex
Mecrisp-Stellaris Forth 2.4.7 RA hex file specialized for nRF52840-Dongle.

Redirects UART Rx and Tx to pins P0.29 and P0.31 respectively on the dongle. I selected
those particular pins because they appear to be unburdened and they are easy to 
access on the dongle pinout.  

Note: at present the hex file here provides no USB support, so the current choices of access to the REPL 
on the dongle are either 1.  The wireless REPL (https://github.com/rabbithat/nRF52_wireless_Forth_REPL), 
which I include in the hex file, or 2. Serial access over the above two pins.  If you prefer to use different 
pins, you can select the ones you want using the FORTH code (https://github.com/rabbithat/nRF52_change_UART_pins) 
already included in the hex file.
