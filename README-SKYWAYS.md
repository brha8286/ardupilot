This fork is intended to provide a more up-to-date version of AP_Periph than what is currently available on skyways-plane4.2.0.

APD ESC telemetry is output via UART. The UART signal is received on the Skyways V3 aircraft with a Mateksys L431 CAN node on an optoisolator companion board, which interprets the UART messages and outputs dronecan. Neither the APD ESC nor the MatekL431 board are supported in AP_Periph on 4.2.0. As such, we need to use a later version of AP (specifically, with AP_Periph 1.6) to make use of APD ESC telemetry, which is what this is forked from.

Further, even with the MatekL431+APD ESC functinality in AP_Periph, the ESC status bitfield (included in ESC UART telem) is not supported. This fork includes a change implementing the status bitfield on the CAN node side. There is no field in the dronecan ESC status packet for "status", which is silly. So this gets the status flag from the UART message, and packs it into the error count message.

Beyond this, it's on the flight controller side to do something with this modified dronecan message.
