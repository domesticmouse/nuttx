# instrument

## Overview
Provides kernel function-call instrumentation initialization and per-task stack usage and call-depth tracking (`CONFIG_SCHED_STACK_RECORD`).

## Interface
- `instrument.h:instrument_initialize` (`instrument.c:instrument_initialize`) - Registers configured kernel instrumentation hooks during early OS startup.
- `stack_monitor.c:g_stack_monitor` (`CONFIG_SCHED_STACK_RECORD`) - Global `struct instrument_s` descriptor registering `stack_monitor.c:stack_monitor_enter` and `stack_monitor.c:stack_monitor_leave` callbacks.

## Invariants
- `stack_monitor.c:stack_monitor_enter` and `stack_monitor.c:stack_monitor_leave` must be compiled with `noinstrument_function` and `nooptimiziation_function` to prevent recursive instrumentation traps.
- Stack recording callbacks ignore calls before `OSINIT_OS_READY()`, when `this_task()` is `NULL`, or when the current stack pointer falls outside `[tcb->stack_base_ptr, tcb->stack_base_ptr + tcb->adj_stack_size)`.

## Side Effects
- Registers `stack_monitor.c:g_stack_monitor` with the global instrumentation list via `instrument_register` in `instrument.c:instrument_initialize`.
- Updates `tcb->stackrecord_sp`, `tcb->stackrecord_pc`, `tcb->level`, `tcb->caller_deepest`, `tcb->level_deepest`, `tcb->sp_deepest`, and `tcb->stackrecord_pc_deepest` on every instrumented function entry and exit in `stack_monitor.c:stack_monitor_enter` and `stack_monitor.c:stack_monitor_leave`.

## Verification
- Run: `make test`
