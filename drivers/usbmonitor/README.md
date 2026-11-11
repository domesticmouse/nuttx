# USB Monitor Daemon (`drivers/usbmonitor`)

## Overview
Implements a background kernel daemon (`usbmonitor.c`) that periodically enumerates and dumps buffered USB device (`usbtrace_enumerate`) and USB host (`usbhost_trdump`) trace records to the system log.

## Interface
- `[usbmonitor.c:usbmonitor_start]` - Configures USB device/host trace ID bitmasks and spawns the `"USB Monitor"` kernel thread (`kthread_create`).
- `[usbmonitor.c:usbmonitor_stop]` - Requests termination of the running USB monitor daemon and resets its state.

## Invariants
- `[usbmonitor.c:usbmonitor_start]` is idempotent when `g_usbmonitor.started` is already true, returning `OK` without spawning duplicate threads.

## Side Effects
- `[usbmonitor.c:usbmonitor_start]` mutates global state `g_usbmonitor`, enables USB trace filtering via `usbtrace_enable`, and creates a background kernel thread running at `CONFIG_USBMONITOR_PRIORITY`.
- Periodically drains trace buffers (`usbtrace_enumerate`, `usbhost_trdump`) and outputs formatted diagnostic lines via `syslog`.

## Verification
- Run: `make test`
