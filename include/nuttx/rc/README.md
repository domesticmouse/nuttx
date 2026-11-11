# NuttX Remote Control (LIRC) Subsystem (`include/nuttx/rc`)

## Overview
Defines the Linux Infrared Remote Control (`LIRC`) compatible upper-half and lower-half character driver interface and dummy test driver for receiving and transmitting raw IR pulses, spaces, and decoded scancodes in NuttX.

## Interface
- `lirc_dev.h:lirc_lowerhalf_s`, `lirc_dev.h:lirc_ops_s`, `lirc_dev.h:lirc_driver_type_e`, `lirc_dev.h:lirc_raw_event_s` - LIRC lower-half device descriptor, driver type enumeration (`LIRC_DRIVER_IR_RAW`, `LIRC_DRIVER_SCANCODE`), and hardware operations vtable (`tx_ir`, `tx_scancode`, `s_tx_mask`, `s_tx_carrier`, `s_rx_carrier_range`).
- `lirc_dev.h:lirc_register`, `lirc_dev.h:lirc_unregister` - Registration and unregistration functions binding a lower-half IR driver to `/dev/lircN`.
- `lirc_dev.h:lirc_sample_event`, `lirc_dev.h:lirc_raw_event`, `lirc_dev.h:lirc_scancode_event` - Event push helpers called by lower-half drivers (typically from interrupt context) to report received IR pulses or scancodes to the upper-half circular buffer.
- `dummy.h:rc_dummy_initialize` - Initialization entry point for the simulated dummy remote control driver.

## Invariants
- A `lirc_dev.h:lirc_lowerhalf_s` driver configured as `LIRC_DRIVER_SCANCODE` must push events via `lirc_dev.h:lirc_scancode_event`, whereas `LIRC_DRIVER_IR_RAW` drivers push pulse/space durations via `lirc_dev.h:lirc_raw_event` or `lirc_dev.h:lirc_sample_event`.

## Side Effects
- `lirc_dev.h:lirc_register` allocates an upper-half event buffer and registers `/dev/lircN` in the VFS.
- `lirc_dev.h:lirc_raw_event` and `lirc_dev.h:lirc_scancode_event` append event records to the upper-half FIFO and wake threads blocked on `read()` or `poll()`.

## Verification
- Run: `make test`
