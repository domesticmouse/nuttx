# GDB Remote Serial Protocol Stub (`libs/libc/gdbstub`)

## Overview
Implements the GDB Remote Serial Protocol (RSP) target stub (`<nuttx/gdbstub.h>`) in `libc`. Supports packet framing and checksum verification, target memory and register read/write, thread enumeration and context queries, `qRcmd` monitor command execution (`backtrace`, `Complete`), console output encoding, and SMP-aware hardware breakpoint and watchpoint management.

## Interface
- `[lib_gdbstub.c:gdb_state_init]` - Allocates and initializes a `struct gdb_state_s` session bound to `send`, `recv`, and `monitor` callbacks.
- `[lib_gdbstub.c:gdb_state_uninit]` - Frees a `struct gdb_state_s` session allocated by `gdb_state_init`.
- `[lib_gdbstub.c:gdb_process]` - Main RSP command loop processing incoming GDB packets (`g`, `G`, `p`, `P`, `m`, `M`, `X`, `c`, `s`, `Z`, `z`, `q`, `v`, `T`, `H`, `?`) and dispatching stop reasons.
- `[lib_gdbstub.c:gdb_console_message]` - Encodes a human-readable message into a hex-formatted GDB `'O'` console output packet and transmits it.
- `[lib_gdbstub.c:gdb_debugpoint_add]` - Installs a software/hardware breakpoint or watchpoint across all CPUs (`CONFIG_SMP`) via `up_debugpoint_add`.
- `[lib_gdbstub.c:gdb_debugpoint_remove]` - Removes a previously installed breakpoint or watchpoint across all CPUs via `up_debugpoint_remove`.

## Invariants
- When `CONFIG_BOARD_MEMORY_RANGE` is enabled, all memory read/write requests in `[lib_gdbstub.c:gdb_process]` are checked against `g_memory_region` permissions before accessing target addresses.
- Incoming GDB packets must match their two-digit hex checksum or are rejected with a `'-'` NAK response (`[lib_gdbstub.c:gdb_process]`).

## Side Effects
- `[lib_gdbstub.c:gdb_state_init]` and `[lib_gdbstub.c:gdb_state_uninit]` allocate and free heap memory via `lib_zalloc()` and `lib_free()`.
- `[lib_gdbstub.c:gdb_process]` reads and writes target memory and CPU/TCB register state (`up_getusrsp`, `tcb->xcp.regs`), and performs synchronous packet I/O via `state->send` and `state->recv`.
- `[lib_gdbstub.c:gdb_debugpoint_add]` and `[lib_gdbstub.c:gdb_debugpoint_remove]` program hardware debug registers via `up_debugpoint_add()` / `up_debugpoint_remove()` and issue cross-CPU calls via `nxsched_smp_call_async()` when `CONFIG_SMP` is active.

## Verification
- Run: `make test`
