This adds functionality for APD ESC `status` bitfield telemetry in the AP_Periph project.

AP_Periph on the skyways-plane4.2.0 branch does not support either the MatekL431 CAN node, nor does it support APD ESC telemetry whatsoever.  So we need to use a more recent version of AP_Periph.

Further, even the up-to-date version of AP_Periph does not support the APD ESC `status` bitfield.  This fork implements a change which gets the `status` int via UART, and packs it into the `error_count` field in the `esc status` dronecan message.

Beyond this, it's on the flight controller side.
