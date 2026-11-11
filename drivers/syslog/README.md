# System Logging (Syslog) Subsystem (`drivers/syslog`)

## Overview
Implements the NuttX system logging (`syslog`) infrastructure, including formatted log generation (`vsyslog.c`, `vsyslog_rfc5424.c`), multi-channel dispatch (`syslog_channel.c`, `syslog_write.c`, `syslog_flush.c`), interrupt-context ring buffering (`syslog_intbuffer.c`), early boot raw stream logging (`syslog_early.c`), `/dev/syslog` and `/dev/ramlog` character drivers (`syslog_chardev.c`, `ramlog.c`), file/device/console/stream output channels (`syslog_device.c`, `syslog_devchannel.c`, `syslog_filechannel.c`, `syslog_consolechannel.c`, `syslog_console.c`, `syslog_stream.c`), and cross-core RPMSG syslog transport (`syslog_rpmsg.c`, `syslog_rpmsg_server.c`).

## Interface
- `[syslog_initialize.c:syslog_initialize]` - Initializes configured syslog channels during OS boot Phases.
- `[syslog_channel.c:syslog_channel_register]`, `[syslog_channel.c:syslog_channel_unregister]` - Dynamically attaches or removes a `syslog_channel_t` backend from the active channel array.
- `[syslog_write.c:syslog_write]`, `[syslog_write.c:syslog_write_foreach]`, `[syslog_write.c:syslog_write_priority]`, `[syslog_flush.c:syslog_flush]` - Writes unformatted buffers or flushes pending data across all registered syslog channels.
- `[vsyslog.c:nx_vsyslog]`, `[vsyslog_rfc5424.c:nx_vsyslog]`, `[syslog_early.c:early_syslog]`, `[syslog_early.c:early_vsyslog]` - Formats log messages (standard or RFC 5424) with optional timestamps, CPU IDs, process names, and priority prefixes.
- `[syslog_intbuffer.c:syslog_add_intbuffer]`, `[syslog_intbuffer.c:syslog_flush_intbuffer]` - Captures syslog output emitted from interrupt handlers into `g_syslog_intbuffer` and flushes it from thread context.
- `[syslog_chardev.c:syslog_register]`, `[syslog_console.c:syslog_console_init]` - Registers `/dev/syslog` and `/dev/console` character devices backed by syslog.
- `[ramlog.c:ramlog_register]`, `[ramlog.c:ramlog_syslog_register]`, `[ramlog.c:ramlog_putc]`, `[ramlog.c:ramlog_write]` - Circular RAM buffer logger and character device (`/dev/ramlog` / `/dev/kmsg`).
- `[syslog_device.c:syslog_dev_uninitialize]`, `[syslog_stream.c:syslog_stream_uninit]` - Tears down character-device or `lib_outstream_s`-backed syslog channels.
- `[syslog_rpmsg.c:syslog_rpmsg_init_early]`, `[syslog_rpmsg.c:syslog_rpmsg_init]`, `[syslog_rpmsg.c:syslog_rpmsg_putc]`, `[syslog_rpmsg.c:syslog_rpmsg_write]`, `[syslog_rpmsg.c:syslog_rpmsg_flush]`, `[syslog_rpmsg_server.c:syslog_rpmsg_server_init]` - Client and server drivers for forwarding syslog streams across cores via RPMSG.

## Invariants
- `[syslog_channel.c:syslog_channel_register]` and `[syslog_channel.c:syslog_channel_unregister]` require `DEBUGASSERT(channel != NULL)` and a valid `channel->sc_ops`.
- `[ramlog.c:ramlog_register]` asserts `DEBUGASSERT(!up_interrupt_context())` and `DEBUGASSERT(devpath && buffer && buflen > sizeof(struct ramlog_header_s))`.
- `[syslog_device.c:syslog_dev_initialize]` asserts `syslog_dev->sl_state == SYSLOG_UNINITIALIZED || syslog_dev->sl_state == SYSLOG_REOPEN`.
- `[syslog_rpmsg.c:syslog_rpmsg_init_early]` requires the ring buffer size to be a power of two (`DEBUGASSERT((size & (size - 1)) == 0)`).

## Side Effects
- Registers `/dev/syslog`, `/dev/console`, or `/dev/ramlog` character devices via `register_driver` and opens underlying log files or character devices in the VFS (`file_open`).
- `[syslog_intbuffer.c:syslog_add_intbuffer]` acquires a no-trace IRQ spinlock (`spin_lock_irqsave_notrace`) when appending characters to the interrupt ring buffer.
- `[syslog_rpmsg.c:syslog_rpmsg_write]` schedules delayed work-queue items (`work_queue`) and transmits `SYSLOG_RPMSG_TRANSFER` messages over RPMSG endpoints.

## Verification
- Run: `make test`
