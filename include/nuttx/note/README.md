# NuttX Scheduler Instrumentation Note Drivers (`include/nuttx/note`)

## Overview
Defines kernel-to-driver interfaces, filtering structures, and character/stream driver registration prototypes for NuttX scheduler instrumentation (`sched_note`). This package bridges scheduler events (task switches, syscalls, IRQs, spinlocks, heap usage, and user trace dumps) to pluggable backends including RAM buffers, syslogs, snapshots, streams, and network sinks.

## Interface
- `note_driver.h:note_driver_s`, `note_driver.h:note_driver_ops_s`, `note_driver.h:note_filter_s` - Core note driver descriptor, instrumentation callback table (`add`, `start`, `stop`, `suspend`, `resume`, `syscall_enter`, `syscall_leave`, `irqhandler`, `heap`, `event`, `vprintf`), and per-driver filter masks.
- `note_driver.h:note_early_initialize`, `note_driver.h:note_initialize`, `note_driver.h:note_driver_register`, `note_driver.h:note_get_taskname` - Core initialization, registration, and PID-to-taskname lookup routines.
- `notectl_driver.h:notectl_register`, `notectl_driver.h:NOTECTL_GETMODE`, `notectl_driver.h:NOTECTL_SETMODE`, `notectl_driver.h:NOTECTL_GETSYSCALLFILTER`, `notectl_driver.h:NOTECTL_SETSYSCALLFILTER`, `notectl_driver.h:NOTECTL_GETIRQFILTER`, `notectl_driver.h:NOTECTL_SETIRQFILTER` - `/dev/notectl` ioctl commands and registration entry point for runtime trace filter configuration.
- `noteram_driver.h:noteram_initialize`, `noteram_driver.h:noteram_register`, `noteram_driver.h:NOTERAM_CLEAR`, `noteram_driver.h:NOTERAM_GETMODE`, `noteram_driver.h:NOTERAM_SETMODE`, `noteram_driver.h:NOTERAM_GETREADMODE`, `noteram_driver.h:NOTERAM_SETREADMODE` - In-memory circular note buffer driver registration and buffer control ioctls.
- `notelog_driver.h:g_notelog_driver` - Global syslog-backed note driver instance (`CONFIG_DRIVERS_NOTELOG`).
- `notenet_driver.h:notenet_init` - Network-backed note driver initialization.
- `notesnap_driver.h:notesnap_register`, `notesnap_driver.h:notesnap_dump`, `notesnap_driver.h:notesnap_dump_with_stream` - Snapshot instrumentation registration and crash/state dump routines.
- `notestream_driver.h:notestream_driver_s`, `notestream_driver.h:notefile_register` - Stream-based note driver structure and file-backed registration.

## Invariants
- `note_driver.h:note_early_initialize` must only register note drivers that do not depend on dynamic memory management (`mm`) or VFS readiness, whereas `note_driver.h:note_initialize` registers `/dev` nodes once the filesystem is available.
- Callbacks in `note_driver.h:note_driver_ops_s` are invoked directly from critical scheduler paths, interrupt handlers, and spinlock operations; implementations must not block or trigger recursive instrumentation notes.

## Side Effects
- Registering drivers via `note_driver.h:note_driver_register`, `notectl_driver.h:notectl_register`, `noteram_driver.h:noteram_register`, or `notestream_driver.h:notefile_register` mutates the kernel's active note driver list and creates character device nodes in `/dev`.
- Issuing `noteram_driver.h:NOTERAM_CLEAR` or `notectl_driver.h:NOTECTL_SETMODE` ioctls mutates in-memory trace buffers and global instrumentation filter masks.

## Verification
- Run: `make test`
