# init

## Overview
Implements the NuttX operating system bootstrap sequence, global scheduler task list tables, per-CPU idle task and group initialization, SMP secondary core startup, system worker thread creation, and initial application bring-up.

## Interface
- `init.h:nx_start` (`nx_start.c:nx_start`) - Primary kernel initialization entry point and CPU0 idle loop; does not return.
- `init.h:nx_bringup` (`nx_bringup.c:nx_bringup`) - Starts system kernel threads, mounts initial filesystems, initializes board drivers, and spawns the initial application task.
- `init.h:nx_smp_start` (`nx_smpstart.c:nx_smp_start`, `CONFIG_SMP`) - Starts all secondary CPUs (`1 .. CONFIG_SMP_NCPUS - 1`) during OS bring-up.
- `init.h:nx_idle_trampoline` (`nx_smpstart.c:nx_idle_trampoline`, `CONFIG_SMP`) - Entry trampoline and idle loop for secondary CPUs; does not return.
- `nx_start.c:g_readytorun` - Global or per-CPU (`CONFIG_SMP`) queue of ready-to-run tasks.
- `nx_start.c:g_assignedtasks` (`CONFIG_SMP`) - Per-CPU queues of tasks pinned to a specific CPU.
- `nx_start.c:g_delivertasks` (`CONFIG_SMP`) - Per-CPU slots for cross-CPU task delivery.
- `nx_start.c:g_running_tasks` - Per-CPU pointers to the currently executing TCB.
- `nx_start.c:g_pendingtasks` - Queue of ready-to-run tasks deferred while scheduling is locked.
- `nx_start.c:g_waitingforsignal` - Queue of tasks blocked waiting for a signal.
- `nx_start.c:g_waitingforfill` (`CONFIG_LEGACY_PAGING`) - Queue of tasks blocked waiting for a page fill.
- `nx_start.c:g_stoppedtasks` (`CONFIG_SIG_SIGSTOP_ACTION`) - Queue of tasks stopped by `SIGSTOP` or `SIGTSTP`.
- `nx_start.c:g_inactivetasks` - Queue of initialized but unactivated tasks.
- `nx_start.c:g_lastpid` - Last assigned process/thread ID counter.
- `nx_start.c:g_pidhash` - Dynamically sized PID-to-TCB lookup hash table.
- `nx_start.c:g_npidhash` - Current capacity of `nx_start.c:g_pidhash`.
- `nx_start.c:g_tasklisttable` - Lookup table mapping `tstate_t` task states to their corresponding scheduler queues and list attributes.
- `nx_start.c:g_nx_initstate` - Global OS initialization state (`enum nx_initstate_e`).
- `nx_start.c:g_idletcb` - Per-CPU array of idle task TCBs (`struct tcb_s`).

## Invariants
- `nx_start.c:g_nx_initstate` advances monotonically through `OSINIT_BOOT`, `OSINIT_TASKLISTS`, `OSINIT_MEMORY`, `OSINIT_HARDWARE`, `OSINIT_OSREADY`, and `OSINIT_IDLELOOP` during startup.
- Secondary CPUs in `nx_smpstart.c:nx_idle_trampoline` spin until `OSINIT_IDLELOOP()` becomes true before entering `up_idle()`.
- Each CPU's idle TCB in `nx_start.c:g_idletcb` is assigned `pid == cpu`, `sched_priority == 0`, and `TCB_FLAG_TTYPE_KERNEL` (plus `TCB_FLAG_CPU_LOCKED` when `CONFIG_SMP` is enabled).

## Side Effects
- Initializes kernel memory managers, PID hash tables, filesystems, interrupt vectors, clocks, POSIX timers, signals, semaphores, message queues, networking, binary loaders, instrumentation, and architecture hardware in `nx_start.c:nx_start`.
- Boots secondary CPUs via `up_cpu_start` and initializes per-CPU idle tasks (`nx_smpstart.c:Idle_Task`) in `nx_smpstart.c:nx_smp_start`.
- Spawns the `pgfill` worker (`nx_bringup.c:nx_pgworker`), high/low-priority kernel work queues and user work queue (`nx_bringup.c:nx_workqueues`), mounts `/etc` ROMFS (`nx_bringup.c:nx_romfsetc`), invokes `board_early_initialize`/`board_late_initialize`, and spawns the initial system task (`nx_bringup.c:nx_create_initthread`) in `nx_bringup.c:nx_bringup`.

## Verification
- Run: `make test`
