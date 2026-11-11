# NuttX System Logging Subsystem (`include/nuttx/syslog`)

## Overview
Defines the NuttX system logging (`syslog`) channel architecture (`syslog.h`), circular RAM-backed log driver (`ramlog.h`), `/dev/console` syslog binding (`syslog_console.h`), and cross-processor RPMsg syslog forwarding (`syslog_rpmsg.h`).

## Interface
- `syslog.h:syslog_channel_s`, `syslog.h:syslog_channel_t`, `syslog.h:syslog_channel_ops_s`, `syslog.h:syslog_ratelimit_s`, `syslog.h:syslog_channel_info_s` - Syslog channel descriptor, output callback table (`sc_putc`, `sc_force`, `sc_flush`, `sc_write`, `sc_write_force`, `sc_close`), and rate-limiting state.
- `syslog.h:syslog_channel_register`, `syslog.h:syslog_channel_unregister`, `syslog.h:syslog_initialize`, `syslog.h:syslog_file_channel`, `syslog.h:syslog_stream_channel`, `syslog.h:syslog_write`, `syslog.h:syslog_write_priority`, `syslog.h:syslog_flush`, `syslog.h:nx_vsyslog`, `syslog.h:early_syslog`, `syslog.h:early_vsyslog` - Channel registration, file/stream channel attachment, formatting, and flush APIs.
- `syslog.h:SYSLOGIOC_GETCHANNELS`, `syslog.h:SYSLOGIOC_SETFILTER`, `syslog.h:SYSLOGIOC_SETRATELIMIT`, `syslog.h:SYSLOGIOC_GETRATELIMIT` - `/dev/log` control ioctl commands.
- `ramlog.h:ramlog_register`, `ramlog.h:ramlog_syslog_register`, `ramlog.h:ramlog_putc`, `ramlog.h:ramlog_write` - In-memory circular buffer character driver and syslog backend.
- `syslog_console.h:syslog_console_init` - Console syslog device initialization.
- `syslog_rpmsg.h:syslog_rpmsg_init_early`, `syslog_rpmsg.h:syslog_rpmsg_init`, `syslog_rpmsg.h:syslog_rpmsg_server_init`, `syslog_rpmsg.h:syslog_rpmsg_putc`, `syslog_rpmsg.h:syslog_rpmsg_write`, `syslog_rpmsg.h:syslog_rpmsg_flush` - Client and server RPMsg syslog transport.

## Invariants
- Every `syslog.h:syslog_channel_ops_s` implementation must support both normal task-context output (`sc_putc` / `sc_write`) and interrupt/panic-safe output (`sc_force` / `sc_write_force`) when `sc_write_force` or `sc_force` is invoked during interrupt handling or assertions.
- `syslog_rpmsg.h:syslog_rpmsg_init_early` must be provided a pre-allocated static buffer to capture early boot logs before the RPMsg transport is established by `syslog_rpmsg.h:syslog_rpmsg_init`.

## Side Effects
- `syslog.h:syslog_channel_register` and `syslog.h:syslog_channel_unregister` mutate the global `g_syslog_channel` array of active output sinks.
- `syslog.h:syslog_file_channel` opens and binds a VFS file or character device as a persistent syslog output sink.

## Verification
- Run: `make test`
