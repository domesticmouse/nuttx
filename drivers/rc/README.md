# Remote Control (LIRC) Drivers (`drivers/rc`)

## Overview
Implements the Linux Infrared Remote Control (LIRC) compatible character driver framework (`/dev/lircN`) for receiving and transmitting raw IR pulses, spaces, and decoded scancodes, along with a dummy RC test driver.

## Interface
- `[lirc_dev.c:lirc_register]`, `[lirc_dev.c:lirc_unregister]` - Registers and unregisters a `/dev/lirc<minor>` character device bound to a `struct lirc_lowerhalf_s` driver (`[lirc_dev.c:struct lirc_upperhalf_s]`).
- `[lirc_dev.c:lirc_raw_event]`, `[lirc_dev.c:lirc_sample_event]`, `[lirc_dev.c:lirc_scancode_event]` - Pushes incoming infrared pulse/space timing samples or scancodes from lower-half ISR/work contexts into open file handle circular buffers (`[lirc_dev.c:struct lirc_fh_s]`).
- `[dummy.c:rc_dummy_initialize]` - Initializes the simulated periodic infrared remote control lower-half driver (`[dummy.c:struct dummy_dev_s]`).

## Invariants
- Open file handle lists (`upper->fh`) and circular buffer writes from interrupt context are protected by critical sections (`[lirc_dev.c:enter_critical_section]`) and upper-half mutexes (`[lirc_dev.c:nxmutex_lock]`).
- Write payload sizes in `[lirc_dev.c:lirc_write]` must be aligned to `sizeof(unsigned int)` in pulse mode or `sizeof(struct lirc_scancode)` in scancode mode.

## Side Effects
- Registers `/dev/lircN` character devices (`register_driver`), allocates per-client `circbuf_s` ring buffers, wakes blocked readers/pollers (`nxsem_post`, `poll_notify`), and transmits IR signals via lower-half `tx_ir`/`tx_scancode` callbacks.

## Verification
- Run: `make test`
