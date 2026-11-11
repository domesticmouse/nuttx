# Scheduler Instrumentation Note Drivers (`drivers/note`)

## Overview
Implements the kernel scheduler instrumentation (`sched_note`) dispatcher, filter control (`/dev/notectl`), and pluggable trace sink drivers including circular RAM buffer (`/dev/note`), syslog (`notelog`), VFS/stream output (`notestream`), UDP network streaming (`notenet`), crash snapshot (`notesnap`), and cross-core RPMSG forwarding (`noterpmsg`).

## Interface
- `[note_driver.c:note_driver_register]`, `[note_driver.c:sched_note_add]`, `[note_driver.c:sched_note_start]`, `[note_driver.c:sched_note_stop]`, `[note_driver.c:sched_note_suspend]`, `[note_driver.c:sched_note_resume]`, `[note_driver.c:sched_note_irqhandler]`, `[note_driver.c:sched_note_syscall_enter]`, `[note_driver.c:sched_note_syscall_leave]`, `[note_driver.c:sched_note_event_ip]`, `[note_driver.c:sched_note_vprintf_ip]`, `[note_driver.c:sched_note_filter_mode]`, `[note_driver.c:note_get_taskname]` - Core instrumentation hooks, filter configuration APIs, and note driver registration.
- `[note_initialize.c:note_early_initialize]`, `[note_initialize.c:note_initialize]` - Early boot and post-VFS initialization of configured note drivers.
- `[noteram_driver.c:noteram_register]`, `[noteram_driver.c:noteram_initialize]` - Circular in-memory trace buffer driver (`/dev/note`, `[noteram_driver.c:struct noteram_driver_s]`).
- `[notectl_driver.c:notectl_register]` - Instrumentation filter control character device (`/dev/notectl`).
- `[notestream_driver.c:notefile_register]`, `[notenet_driver.c:notenet_init]`, `[notesnap_driver.c:notesnap_register]`, `[notesnap_driver.c:notesnap_dump]`, `[noterpmsg_driver.c:noterpmsg_init]`, `[noterpmsg_server.c:noterpmsg_server_init]` - Stream, UDP network, snapshot, and RPMSG client/server trace sinks.

## Invariants
- Number of registered note channels must not exceed `CONFIG_DRIVERS_NOTE_MAX` (`[note_driver.c:CONFIG_DRIVERS_NOTE_MAX]`).
- Trace buffer and task-name cache updates inside instrumentation hooks must use non-traced spinlocks (`[note_driver.c:spin_lock_irqsave_notrace]`, `[noteram_driver.c:spin_lock_irqsave_notrace]`) to prevent recursive instrumentation deadlocks.

## Side Effects
- Registers `/dev/note` and `/dev/notectl` character devices (`[noteram_driver.c:register_driver]`, `[notectl_driver.c:register_driver]`), transmits trace packets over UDP sockets (`notenet_driver.c`) or RPMSG endpoints (`[noterpmsg_driver.c:rpmsg_create_ept]`), and registers panic notifiers for crash dumps.

## Verification
- Run: `make test`
