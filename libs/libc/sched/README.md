# Scheduler, Task Startup & Cancellation (`libs/libc/sched`)

## Overview
Provides user-space scheduler priority/CPU-set queries, task/thread ID helpers, user-mode task entry trampolines, thread cancellation point management, stack backtrace/dump utilities, and CPU/performance clock queries.

## Interface
- `clock_getcpuclockid.c:clock_getcpuclockid` - Computes a CPU-time `clockid_t` for process `pid`.
- `clock_perf.c:perf_gettime` - Returns the current performance counter timestamp via `clock_systime_ticks` or hardware perf counter.
- `sched_backtrace.c:sched_backtrace`, `sched_backtrace.c:unwind_arch_adjustment` - Captures call stack return addresses for thread `tid` (using `_Unwind_Backtrace` fallback when `CONFIG_ARCH_HAVE_BACKTRACE` is disabled).
- `sched_cpucount.c:sched_cpucount` - Counts the number of enabled CPUs in a `cpu_set_t` bitmask (`CONFIG_SMP`).
- `sched_dumpstack.c:sched_dumpstack` - Formats and logs a stack backtrace for `tid` via `syslog(LOG_EMERG, ...)` (with symbol names when `CONFIG_ALLSYMS` is enabled).
- `sched_getprioritymax.c:sched_get_priority_max`, `sched_getprioritymin.c:sched_get_priority_min` - Return `SCHED_PRIORITY_MAX` and `SCHED_PRIORITY_MIN` for a scheduling policy (`SCHED_FIFO`, `SCHED_RR`, `SCHED_OTHER`, `SCHED_SPORADIC`).
- `task_cancelpt.c:enter_cancellation_point`, `task_cancelpt.c:leave_cancellation_point`, `task_cancelpt.c:check_cancellation_point` - Manage nested cancellation-point reference counts (`tl_cpcount`) and pending cancellation state (`TC_FLAG_CANCEL_PENDING`) in thread-local storage (`CONFIG_CANCELLATION_POINTS`).
- `task_getpid.c:getpid`, `task_gettid.c:gettid` - Return the caller's process ID (`_SCHED_GETPID()`) and thread ID (`_SCHED_GETTID()`).
- `task_setcancelstate.c:task_setcancelstate`, `task_setcanceltype.c:task_setcanceltype`, `task_testcancel.c:task_testcancel` - Configure per-thread cancellation state (`TASK_CANCEL_ENABLE`/`TASK_CANCEL_DISABLE`), cancellation type (`TASK_CANCEL_DEFERRED`/`TASK_CANCEL_ASYNCHRONOUS`), and explicit cancellation testing.
- `task_startup.c:nxtask_startup` - Default user-space task startup trampoline that invokes `exit(entrypt(argc, argv))` when `!CONFIG_BUILD_KERNEL`.

## Invariants
- `task_cancelpt.c:enter_cancellation_point` and `task_cancelpt.c:leave_cancellation_point` must be strictly paired; `enter_cancellation_point` asserts `DEBUGASSERT(tls->tl_cpcount < INT16_MAX)` and `leave_cancellation_point` asserts `DEBUGASSERT(tls->tl_cpcount > 0)`.
- `task_startup.c:nxtask_startup` asserts `DEBUGASSERT(entrypt)` and never returns to its caller.

## Side Effects
- `task_cancelpt.c:leave_cancellation_point`, `task_setcancelstate.c:task_setcancelstate`, `task_setcanceltype.c:task_setcanceltype`, and `task_testcancel.c:task_testcancel` mutate TLS flags (`tls->tl_cpstate`, `tls->tl_cpcount`) and may terminate the calling thread or task via `pthread_exit(PTHREAD_CANCELED)` or `_exit(EXIT_FAILURE)`.
- `sched_dumpstack.c:sched_dumpstack` emits emergency log messages via `syslog`.

## Verification
- Run: `make test`
