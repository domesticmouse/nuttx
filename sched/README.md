# sched

## Overview
The `sched` directory contains the NuttX operating system kernel core, encompassing OS bootstrap (`init`), the priority-driven and SMP task scheduler (`sched`), task and POSIX thread lifecycle management (`task`, `pthread`, `group`, `tls`), process address environment switching (`addrenv`), on-demand paging (`paging`), interrupt handling and critical sections (`irq`), timekeeping and timer facilities (`clock`, `wdog`, `hrtimer`, `timer`), inter-task synchronization and IPC primitives (`semaphore`, `event`, `mqueue`, `signal`), kernel work queues (`wqueue`), loadable kernel modules (`module`), function instrumentation (`instrument`), and crash/assertion diagnostics (`misc`).

## Subdirectories & Boundaries
- addrenv: [./addrenv/README.md](./addrenv/README.md) - Process address environment (`struct addrenv_s`) lifecycle, reference counting, MMU context switching, fork duplication, and kernel user-pointer access validation.
- clock: [./clock/README.md](./clock/README.md) - System timekeeping (`CLOCK_REALTIME`, `CLOCK_MONOTONIC`, `CLOCK_BOOTTIME`), tick counters, RTC synchronization, clock slewing, performance counters, busy-wait delays, and clock-change notifiers.
- event: [./event/README.md](./event/README.md) - Kernel bitmask event group synchronization primitives (`nxevent_t`, `CONFIG_SCHED_EVENTS`).
- group: [./group/README.md](./group/README.md) - Task group (`struct task_group_s`) lifecycle, member and child status tracking, user/group credentials, resource limits, file table inheritance, group signal delivery, and group heap allocation.
- hrtimer: [./hrtimer/README.md](./hrtimer/README.md) - Nanosecond-resolution high-resolution kernel timer subsystem (`CONFIG_HRTIMER`) backed by a red-black tree or sorted list.
- init: [./init/README.md](./init/README.md) - NuttX OS bootstrap (`nx_start`, `nx_bringup`, `nx_smp_start`), global scheduler task list tables, and per-CPU idle task initialization.
- instrument: [./instrument/README.md](./instrument/README.md) - Kernel function-call instrumentation hooks and per-task stack depth recording (`CONFIG_SCHED_STACK_RECORD`).
- irq: [./irq/README.md](./irq/README.md) - Interrupt vector table (`g_irqvector`), ISR dispatch, shared IRQ chains (`CONFIG_IRQCHAIN`), threaded/workqueue interrupts, UP/SMP critical sections, and `/proc/irqs`.
- misc: [./misc/README.md](./misc/README.md) - Kernel assertion and panic handling (`_assert`), ELF core dump generation (`CONFIG_COREDUMP`), mutex deadlock detection (`CONFIG_ARCH_DEADLOCKDUMP`), and panic/reboot notifier chains.
- module: [./module/README.md](./module/README.md) - Dynamically loadable kernel ELF module management (`insmod`, `rmmod`, `modhandle`, `modsym`) and `/proc/modules` reporting.
- mqueue: [./mqueue/README.md](./mqueue/README.md) - POSIX named message queues (`mq_*`, `nxmq_*`) and System V IPC message queues (`msgget`, `msgsnd`, `msgrcv`, `msgctl`).
- paging: [./paging/README.md](./paging/README.md) - Legacy on-demand virtual memory page fault handling (`pg_miss`) and the `pgfill` kernel worker thread (`CONFIG_LEGACY_PAGING`).
- pthread: [./pthread/README.md](./pthread/README.md) - Kernel-side POSIX thread creation, join/detach coordination, cancellation, robust mutex recovery, scheduling/affinity control, and thread signal operations.
- sched: [./sched/README.md](./sched/README.md) - Core priority-driven scheduler, ready/blocked task queues, preemption locking, FIFO/RR/sporadic policies, tick/tickless timer processing, SMP cross-CPU calls, `waitpid`, CPU load, critical monitor, and stack checking.
- semaphore: [./semaphore/README.md](./semaphore/README.md) - Kernel counting semaphores, mutexes (`NXSEM_IS_MUTEX`), read-write semaphores (`rw_semaphore_t`), priority inheritance, priority protection, and task termination recovery.
- signal: [./signal/README.md](./signal/README.md) - POSIX and real-time signal actions, masks, queuing, delivery, `sigevent` notifications, and signal-aware wait/sleep/poll primitives.
- task: [./task/README.md](./task/README.md) - User task and kernel thread creation, `posix_spawn`/`task_spawn`, `fork`/`vfork`, `execve`, cancellation, termination/exit, recovery, restart, reparenting, and `prctl`.
- timer: [./timer/README.md](./timer/README.md) - Per-process POSIX interval timers (`timer_create`, `timer_settime`, `timer_delete`) and BSD interval timers (`setitimer`, `getitimer`).
- tls: [./tls/README.md](./tls/README.md) - Thread Local Storage (`struct tls_info_s`) stack frame allocation/duplication and per-group `struct task_info_s` initialization.
- wdog: [./wdog/README.md](./wdog/README.md) - Kernel tick-resolution watchdog timers (`struct wdog_s`, `wd_start_abstick`, `wd_cancel`, `wd_timer`).
- wqueue: [./wqueue/README.md](./wqueue/README.md) - Kernel `HPWORK`, `LPWORK`, and dynamic work queues (`work_queue`, `work_cancel`, `work_cancel_sync`), priority inheritance, and work completion notifications.
