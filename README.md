# nRF52840-Dongle_hex
Mecrisp-Stellaris Forth 2.4.7 RA hex file specialized for nRF52840-Dongle.

Redirects UART Rx and Tx to pins P0.29 and P0.31 respectively on the dongle.  Also 
includes the radio REPL code.

Note: at present, no USB support, so the current choices of access to the REPL on it are
either 1.  The radio REPL, which I include in the hex file, or 2. Serial access over
the above two pins.
