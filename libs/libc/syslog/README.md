# System Logging (`libs/libc/syslog`)

## Overview
Implements POSIX `<syslog.h>` logging configuration (`openlog`, `closelog`, `setlogmask`) and message formatting (`syslog`, `vsyslog`), supporting standard syslog channel output (`nx_vsyslog`), instrumentation note output (`sched_note_vprintf` under `CONFIG_SYSLOG_TO_SCHED_NOTE`), and no-op stubbing (`CONFIG_SYSLOG_NONE`).

## Interface
- `lib_openlog.c:openlog`, `lib_openlog.c:closelog` - Configure or reset logging identity, options (`LOG_PERROR`, `LOG_PID`), and facility (`g_syslog_option`, `g_syslog_ident`).
- `lib_setlogmask.c:setlogmask`, `syslog.h:g_syslog_mask` - Atomically updates the process/system syslog priority bitmask (`g_syslog_mask`, initialized to `CONFIG_SYSLOG_DEFAULT_MASK`) and returns the previous mask.
- `lib_syslog.c:syslog`, `lib_syslog.c:vsyslog` - Checks `LOG_MASK(LOG_PRI(priority)) & g_syslog_mask`, optionally duplicates output to `stderr` when `LOG_PERROR` is active, and forwards to `nx_vsyslog`.
- `lib_syslog_note.c:syslog`, `lib_syslog_note.c:vsyslog` - Routes syslog messages to the scheduler instrumentation trace buffer via `sched_note_vprintf` (`CONFIG_SYSLOG_TO_SCHED_NOTE`).
- `lib_syslog_none.c:syslog`, `lib_syslog_none.c:vsyslog` - No-op syslog stubs when `CONFIG_SYSLOG_NONE` is enabled.

## Invariants
- `lib_syslog.c:vsyslog` and `lib_syslog_note.c:vsyslog` drop any message whose priority bit (`LOG_MASK(LOG_PRI(priority))`) is cleared in `g_syslog_mask`.

## Side Effects
- `lib_openlog.c:openlog`, `lib_openlog.c:closelog`, and `lib_setlogmask.c:setlogmask` mutate global state (`g_syslog_mask`, `g_syslog_option`, `g_syslog_ident`).
- `lib_syslog.c:vsyslog` writes formatted log data to kernel syslog channels via `nx_vsyslog` and optionally to `STDERR_FILENO` via `lib_rawoutstream`.

## Verification
- Run: `make test`
