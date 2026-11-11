# SEGGER RTT and SystemView Drivers (`drivers/segger`)

## Overview
Provides NuttX integration drivers for SEGGER Real-Time Transfer (RTT) and SEGGER SystemView. Implements scheduler instrumentation note drivers (`note_rtt.c` and `note_sysview.c`), polling-based UART serial devices over RTT channels (`serial_rtt.c`), C library input/output stream wrappers (`stream_rtt.c`), and a syslog output channel (`syslog_rtt.c`).

## Interface
- `[note_rtt.c:notertt_register]`, `[note_rtt.c:g_notertt]` - Initializes an RTT output stream on `CONFIG_NOTE_RTT_CHANNEL` and registers the `rtt` scheduler instrumentation note driver.
- `[note_sysview.c:note_sysview_initialize]`, `[note_sysview.c:note_sysview_get_interrupt_id]` - Initializes SEGGER SystemView with `perf_getfreq()`, starts SystemView recording, and registers the `sysview` scheduler note driver (`g_note_sysview_driver`).
- `[segger.c:g_segger_lock]`, `[segger.c:g_segger_offset]` - Global recursive spinlock (`rspinlock_t`) and uncached address offset definitions for RTT buffer synchronization.
- `[serial_rtt.c:serial_rtt_initialize]` - Configures RTT up/down buffers and registers `/dev/ttyR0`..`/dev/ttyR2` (and `/dev/console` if configured) with the upper-half UART driver.
- `[stream_rtt.c:lib_rttoutstream_open]`, `[stream_rtt.c:lib_rttoutstream_close]`, `[stream_rtt.c:lib_rttinstream_open]`, `[stream_rtt.c:lib_rttinstream_close]` - Opens and closes `lib_outstream_s` and `lib_instream_s` wrappers backed by RTT channels.
- `[syslog_rtt.c:syslog_rtt_putc]`, `[syslog_rtt.c:syslog_rtt_write]` - Syslog channel character and buffer output callbacks targeting `CONFIG_SYSLOG_RTT_CHANNEL`.
- Subdirectories:
  - [./config/README.md](./config/README.md) - SEGGER RTT and SystemView configuration headers and locking/timestamp macros.

## Invariants
- `[note_sysview.c:note_sysview_initialize]` requires the hardware performance counter frequency `perf_getfreq()` to be non-zero; otherwise it logs an error and triggers `PANIC()`.
- `[stream_rtt.c:lib_rttoutstream_open]` and `[stream_rtt.c:lib_rttinstream_open]` assert via `DEBUGASSERT(stream->buffer)` that heap allocation succeeds when opening non-zero RTT channels (`channel != 0`), and `rttstream_getc`/`rttstream_gets` assert `DEBUGASSERT(stream)`.

## Side Effects
- `[serial_rtt.c:serial_rtt_initialize]` registers character devices (`/dev/ttyR0`..`/dev/ttyR2`, `/dev/console`) via `uart_register` and starts periodic watchdog timers (`wd_start`) on attach to poll RTT buffers.
- `[stream_rtt.c:lib_rttoutstream_open]` and `[stream_rtt.c:lib_rttinstream_open]` allocate channel buffers from the kernel heap (`kmm_malloc`) and reconfigure SEGGER RTT control block descriptors (`SEGGER_RTT_ConfigUpBuffer`, `SEGGER_RTT_ConfigDownBuffer`).
- `[note_sysview.c:note_sysview_initialize]` and `[note_rtt.c:notertt_register]` register global scheduler instrumentation hooks via `note_driver_register` and transmit trace packets over shared memory RTT buffers.

## Verification
- Run: `make test`
