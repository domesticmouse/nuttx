# NuttX SEGGER RTT & SystemView Integration (`include/nuttx/segger`)

## Overview
Provides integration interfaces for SEGGER Real Time Transfer (`RTT`) and SEGGER SystemView (`sysview`), exposing stream wrappers, syslog channels, virtual serial consoles, and `sched_note` instrumentation backends over debug probe memory buffers.

## Interface
- `rtt.h:lib_rttoutstream_s`, `rtt.h:lib_rttinstream_s`, `rtt.h:lib_rttoutstream_open`, `rtt.h:lib_rttoutstream_close`, `rtt.h:lib_rttinstream_open`, `rtt.h:lib_rttinstream_close` - `lib_outstream_s` and `lib_instream_s` stream adapters over SEGGER RTT channels.
- `rtt.h:syslog_rtt_putc`, `rtt.h:syslog_rtt_write`, `rtt.h:serial_rtt_initialize` - Syslog output callbacks and `/dev/ttyR*` serial driver initialization over RTT channels.
- `note_rtt.h:notertt_register` - Registration entry point for the RTT-backed scheduler instrumentation (`sched_note`) driver.
- `sysview.h:note_sysview_initialize` - Initialization function for the SEGGER SystemView instrumentation note backend.

## Invariants
- RTT channel indices passed to `rtt.h:lib_rttoutstream_open`, `rtt.h:lib_rttinstream_open`, or `rtt.h:serial_rtt_initialize` must be less than the configured `SEGGER_RTT_MAX_NUM_UP_BUFFERS` / `SEGGER_RTT_MAX_NUM_DOWN_BUFFERS`.

## Side Effects
- Writing via `rtt.h:syslog_rtt_write` or `sysview.h:note_sysview_initialize` mutates the in-RAM SEGGER RTT control block (`_SEGGER_RTT`) polled by an attached J-Link debug probe.
- `rtt.h:serial_rtt_initialize` allocates circular buffers, starts a polling timer if needed, and registers `/dev/ttyR*` character devices.

## Verification
- Run: `make test`
