# sched

## Overview
The `sched` component implements the core NuttX priority-driven scheduler and task state machine. It manages ready-to-run, assigned, pending, and blocked task queues (`nxsched_add_readytorun`, `nxsched_remove_readytorun`, `nxsched_add_blocked`, `nxsched_remove_blocked`, `nxsched_merge_pending`), preemption locking (`sched_lock`, `sched_unlock`, `sched_lockcount`), priority and policy control (`SCHED_FIFO`, `SCHED_RR`, `SCHED_SPORADIC`), periodic tick and tickless timer evaluation (`nxsched_process_timer`, `nxsched_reassess_timer`), task sleeping and suspension (`nxsched_ticksleep`, `nxsched_suspend`), SMP CPU affinity and cross-CPU function execution (`nxsched_select_cpu`, `nxsched_smp_call*`), child process waiting (`waitpid`, `wait`, `waitid`), CPU load estimation (`clock_cpuload`), critical section/preemption runtime monitoring (`sched_critmonitor.c`), stack overflow checking (`nxsched_checkstackoverflow`), and system/thread introspection (`sysinfo`, `profil`, `sched_backtrace`, `nxsched_get_stackinfo`, `nxsched_get_stateinfo`).

## Interface
- `sched.h:nxsched_add_prioritized` - Inserts a TCB into a prioritized task list in descending `sched_priority` order.
- `sched.h:nxsched_deliver_task` - Enqueues a task on a target CPU's `g_delivertasks` queue and sends an SMP scheduling IPI (`CONFIG_SMP`).
- `sched.h:nxsched_select_cpu` - Selects the lowest-priority target CPU permitted by an affinity mask (`CONFIG_SMP`).
- `sched.h:this_task` - Returns the currently executing TCB on the local CPU (`g_running_tasks[this_cpu()]` or `g_readytorun.head`).
- `sched_addreadytorun.c:nxsched_add_readytorun` - Places a TCB onto the ready-to-run, assigned, or pending task list and returns `true` if the head of the active run queue changed.
- `sched_addreadytorun.c:nxsched_switch_running` - Switches the running task on `cpu` to the highest-priority runnable task when preemption is unlocked (`CONFIG_SMP`).
- `sched_removereadytorun.c:nxsched_remove_readytorun` / `sched_removereadytorun.c:nxsched_remove_self` - Removes a TCB from its active run queue and activates the next runnable task.
- `sched_addblocked.c:nxsched_add_blocked` / `sched_removeblocked.c:nxsched_remove_blocked` - Adds or removes a TCB from a kernel wait list (`g_tasklisttable[task_state]`) or `tcb->waitobj` queue.
- `sched_mergepending.c:nxsched_merge_pending` - Merges `g_pendingtasks` into `g_readytorun` or `g_assignedtasks` when the scheduler lock is released.
- `sched_process_delivered.c:nxsched_process_delivered` - Moves tasks delivered via `g_delivertasks[cpu]` into the target CPU's runnable queues (`CONFIG_SMP`).
- `sched_setpriority.c:nxsched_set_priority` / `sched_reprioritize.c:nxsched_reprioritize` / `sched_reprioritizertr.c:nxsched_reprioritize_rtr` - Updates task effective/base priorities and repositions tasks within ready-to-run, pending, or blocked prioritized queues.
- `sched_lock.c:sched_lock` / `sched_unlock.c:sched_unlock` / `sched_lockcount.c:sched_lockcount` - Increments, decrements, or queries the calling task's preemption lock counter (`rtcb->lockcount`).
- `sched_getparam.c:nxsched_get_param` / `sched_getparam.c:sched_getparam` / `sched_setparam.c:nxsched_set_param` / `sched_setparam.c:sched_setparam` - Gets or sets scheduling parameters (`struct sched_param`), including sporadic server budget parameters.
- `sched_getscheduler.c:nxsched_get_scheduler` / `sched_getscheduler.c:sched_getscheduler` / `sched_setscheduler.c:nxsched_set_scheduler` / `sched_setscheduler.c:sched_setscheduler` - Queries or configures a task's scheduling policy (`SCHED_FIFO`, `SCHED_RR`, `SCHED_SPORADIC`, `SCHED_OTHER`) and priority.
- `sched_yield.c:sched_yield` - Yields the CPU to equal- or higher-priority runnable tasks.
- `sched_rrgetinterval.c:sched_rr_get_interval` / `sched_roundrobin.c:nxsched_process_roundrobin` / `sched_roundrobin.c:nxsched_suspend_roundrobin` / `sched_roundrobin.c:nxsched_resume_roundrobin` - Queries the `CONFIG_RR_INTERVAL` quantum and manages per-task round-robin timeslice accounting.
- `sched_sporadic.c:nxsched_validate_sporadic` / `sched_sporadic.c:nxsched_initialize_sporadic` / `sched_sporadic.c:nxsched_start_sporadic` / `sched_sporadic.c:nxsched_stop_sporadic` / `sched_sporadic.c:nxsched_reset_sporadic` / `sched_sporadic.c:nxsched_resume_sporadic` / `sched_sporadic.c:nxsched_suspend_sporadic` / `sched_sporadic.c:nxsched_process_sporadic` / `sched_sporadic.c:nxsched_sporadic_lowpriority` - Implements `CONFIG_SCHED_SPORADIC` replenishment and budget-exhaustion timers.
- `sched_processtick.c:nxsched_process_timer` - Processes periodic system timer ticks, updating scheduler ticks, CPU load, timeslices, and watchdog expirations.
- `sched_processtickless.c:nxsched_reassess_timer` / `sched_processtickless.c:nxsched_timer_start` / `sched_processtickless.c:nxsched_get_next_expired` - Evaluates elapsed intervals and reprograms hardware timers in `CONFIG_SCHED_TICKLESS` mode.
- `sched_sleep.c:nxsched_ticksleep` / `sched_sleep.c:nxsched_abstick_sleep` / `sched_sleep.c:nxsched_wakeup` / `sched_sleep.c:nxsched_usleep` / `sched_sleep.c:nxsched_msleep` / `sched_sleep.c:nxsched_sleep` / `sched_sleep.c:nxsched_nanosleep` - Blocks a task in `TSTATE_WAIT_SIG` for a relative or absolute tick duration without signal interruption (`TCB_FLAG_NONCANCELABLE`).
- `sched_suspend.c:nxsched_suspend` - Transitions a task into `TSTATE_TASK_STOPPED` (`g_stoppedtasks`), recovering held mutexes if blocked on a semaphore.
- `sched_switchcontext.c:nxsched_switch_context` - Records scheduler instrumentation notes, critical monitor hooks, and address environment switches across a context switch.
- `sched_getaffinity.c:nxsched_get_affinity` / `sched_getaffinity.c:sched_getaffinity` / `sched_setaffinity.c:nxsched_set_affinity` / `sched_setaffinity.c:sched_setaffinity` / `sched_getcpu.c:sched_getcpu` - Queries or modifies per-task SMP CPU affinity masks (`tcb->affinity`) and reports the caller's CPU ID (`CONFIG_SMP`).
- `sched_smp.c:nxsched_smp_call_init` / `sched_smp.c:nxsched_smp_call_handler` / `sched_smp.c:nxsched_smp_call_single` / `sched_smp.c:nxsched_smp_call` / `sched_smp.c:nxsched_smp_call_single_async` / `sched_smp.c:nxsched_smp_call_async` - Executes synchronous or asynchronous callbacks across target CPUs via SMP inter-processor interrupts (`CONFIG_SMP`).
- `sched_waitpid.c:nxsched_waitpid` / `sched_waitpid.c:waitpid` / `sched_wait.c:wait` / `sched_waitid.c:waitid` - Waits for child task state changes (`CONFIG_SCHED_WAITPID`).
- `sched_gettcb.c:nxsched_get_tcb` / `sched_verifytcb.c:nxsched_verify_tcb` / `sched_releasetcb.c:nxsched_releasepid` / `sched_releasetcb.c:nxsched_release_tcb` / `sched_self.c:nxsched_self` / `sched_idletask.c:sched_idletask` / `sched_foreach.c:nxsched_foreach` - Looks up TCBs in `g_pidhash`, validates TCB pointers, releases PIDs and TCB resources, queries the current/idle task state, and iterates over active TCBs.
- `sched_getfiles.c:nxsched_get_fdlist_from_tcb` / `sched_getfiles.c:nxsched_get_fdlist` / `sched_get_tls.c:nxsched_get_tls` / `sched_get_tls.c:nxsched_get_stackargs` / `sched_get_stackinfo.c:nxsched_get_stackinfo` / `sched_get_stateinfo.c:nxsched_get_stateinfo` / `sched_maycontrol.c:nxsched_may_control` - Retrieves task file descriptor tables, TLS blocks, stack arguments, stack geometry, human-readable state strings, and permission checks.
- `nxsched_checkstackoverflow.c:nxsched_checkstackoverflow` - Checks stack coloration against `CONFIG_STACK_OVERFLOW_CHECK` watermarks and asserts on overflow.
- `sched_critmonitor.c:nxsched_critmon_preemption` / `sched_critmonitor.c:nxsched_critmon_csection` / `sched_critmonitor.c:nxsched_critmon_busywait` / `sched_critmonitor.c:nxsched_switch_critmon` / `sched_critmonitor.c:nxsched_update_critmon` - Tracks per-thread and global maximum preemption-off, critical-section, busy-wait, and run times (`CONFIG_SCHED_CRITMONITOR`).
- `sched_cpuload.c:g_cpuload_total` / `sched_cpuload.c:nxsched_process_taskload_ticks` / `sched_cpuload.c:nxsched_process_cpuload_ticks` / `sched_cpuload.c:clock_cpuload` / `sched_cpuload.c:cpuload_init` / `sched_cpuload_oneshot.c:nxsched_oneshot_extclk` / `sched_cpuload_period.c:nxsched_period_extclk` - Accumulates per-task tick counts and decays historical load averages (`CONFIG_SCHED_CPULOAD_*`).
- `sched_backtrace.c:sched_backtrace` / `sched_profil.c:profil` / `sched_sysinfo.c:sysinfo` / `sched_dumponexit.c:nxsched_dumponexit` - Captures task call stacks (`CONFIG_SCHED_BACKTRACE`), PC histogram profiling (`CONFIG_SCHED_LPWORK`), system uptime/memory/task statistics, and exit state dumps (`CONFIG_SCHED_DUMP_ON_EXIT`).

## Invariants
- Prioritized task queues (`g_readytorun`, `g_pendingtasks`, and prioritized wait lists) are maintained in descending `sched_priority` order (`sched.h:nxsched_add_prioritized`); each CPU's idle task (`sched_priority == 0`, `is_idle_task(tcb)`) remains permanently at the tail of its run queue and is never blocked or removed.
- All mutations to global scheduler task lists and `g_pidhash` must execute inside `enter_critical_section()`.
- When preemption is locked on a CPU (`nxsched_islocked_tcb(rtcb)` / `rtcb->lockcount > 0`), higher-priority runnable tasks are deferred in `g_pendingtasks` (UP) or `g_readytorun` (SMP) until `sched_unlock.c:sched_unlock` decrements `rtcb->lockcount` to zero and calls `sched_mergepending.c:nxsched_merge_pending`.
- Tasks with `TCB_FLAG_CPU_LOCKED` cannot have their CPU affinity modified (`sched_setaffinity.c:nxsched_set_affinity` returns `-EINVAL`).
- Synchronous cross-CPU calls (`sched_smp.c:nxsched_smp_call` with `wait == true`) must not be invoked from interrupt context (`DEBUGASSERT(!up_interrupt_context())`).

## Side Effects
- Mutates global task state queues (`g_readytorun`, `g_assignedtasks`, `g_delivertasks`, `g_running_tasks`, `g_pendingtasks`, `g_waitingforsignal`, `g_stoppedtasks`, `g_inactivetasks`) and `g_pidhash`.
- Performs architecture context switches (`up_switch_context`, `up_update_task`), switches MMU address environments (`addrenv_switch`), and sends SMP inter-processor interrupts (`up_send_smp_sched`, `up_send_smp_call`).
- Arms and cancels hardware tickless timers (`up_timer_start`, `up_alarm_start`) and kernel watchdog timers (`wd_start_abstick`, `wd_cancel`, `wd_timer`).
- Frees TCBs, stacks (`up_release_stack`), group bindings (`group_leave`), timers (`timer_Cancel` / `wd_cancel`), and address environments (`addrenv_drop`) in `sched_releasetcb.c:nxsched_release_tcb`.
- Triggers kernel assertions or panics on stack overflow (`nxsched_checkstackoverflow.c:nxsched_checkstackoverflow`) or critical monitor timeout violations (`CRITMONITOR_PANIC` in `sched_critmonitor.c`).

## Verification
- Run: `make test`
