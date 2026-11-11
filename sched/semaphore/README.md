# semaphore

## Overview
Implements kernel counting semaphores, mutexes (`NXSEM_IS_MUTEX`), and read-write semaphores (`rw_semaphore_t`), supporting priority inheritance (`CONFIG_PRIORITY_INHERITANCE`), priority ceiling protection (`CONFIG_PRIORITY_PROTECT`), tick/clock-based timed waits, and task termination recovery.

## Interface
- `semaphore.h:nxsem_initialize` (`sem_initialize.c:nxsem_initialize`, `CONFIG_PRIORITY_INHERITANCE`) - Initializes the preallocated semaphore holder pool (`sem_holder.c:nxsem_initialize_holders`) during OS startup.
- `semaphore.h:nxsem_wait_irq` (`sem_waitirq.c:nxsem_wait_irq`) - Interrupt/timeout handler that aborts a blocked task's semaphore wait with `EINTR`, `ETIMEDOUT`, or `ECANCELED`.
- `semaphore.h:nxsem_timeout` (`sem_timeout.c:nxsem_timeout`) - Watchdog callback that terminates an expired timed semaphore wait with `ETIMEDOUT`.
- `semaphore.h:nxsem_recover` (`sem_recover.c:nxsem_recover`) - Releases pending semaphore waits and held semaphore references (`sem_holder.c:nxsem_release_all`) when a task is deleted or canceled.
- `semaphore.h:nxsem_initialize_holders` / `semaphore.h:nxsem_destroyholder` / `semaphore.h:nxsem_add_holder` / `semaphore.h:nxsem_add_holder_tcb` / `semaphore.h:nxsem_boost_priority` / `semaphore.h:nxsem_release_holder` / `semaphore.h:nxsem_restore_baseprio` / `semaphore.h:nxsem_canceled` / `semaphore.h:nxsem_release_all` (`sem_holder.c`, `CONFIG_PRIORITY_INHERITANCE`) - Tracks semaphore holders and dynamically boosts/restores holder thread priorities.
- `semaphore.h:nxsem_protect_wait` / `semaphore.h:nxsem_protect_post` (`sem_protect.c`, `CONFIG_PRIORITY_PROTECT`) - Enforces `SEM_PRIO_PROTECT` priority ceiling protocol on semaphore lock and unlock.
- `sem_destroy.c:nxsem_destroy` - Resets an unnamed semaphore or mutex and releases its holder structures.
- `sem_wait.c:nxsem_wait_slow` - Slow-path blocking acquisition for counting semaphores and mutexes.
- `sem_trywait.c:nxsem_trywait_slow` - Slow-path non-blocking acquisition attempt returning `-EAGAIN` if unavailable.
- `sem_post.c:nxsem_post_slow` - Slow-path release for counting semaphores and mutexes, waking the highest-priority blocked waiter.
- `sem_tickwait.c:nxsem_tickwait` / `sem_tickwait.c:nxsem_tickwait_uninterruptible` - Acquires a semaphore with a relative tick timeout (`delay`).
- `sem_timedwait.c:nxsem_timedwait` / `sem_timedwait.c:nxsem_timedwait_uninterruptible` - Acquires a semaphore with an absolute `CLOCK_REALTIME` timeout.
- `sem_clockwait.c:nxsem_clockwait` - Acquires a semaphore with an absolute timeout against a specified `clockid_t`.
- `sem_reset.c:nxsem_reset` - Resets a counting semaphore's count or a mutex's state while waking blocked waiters as needed.
- `sem_setprotocol.c:nxsem_set_protocol` (`CONFIG_PRIORITY_INHERITANCE`) - Configures `SEM_PRIO_NONE`, `SEM_PRIO_INHERIT`, or `SEM_PRIO_PROTECT` on a semaphore.
- `sem_rw.c:init_rwsem` / `sem_rw.c:destroy_rwsem` / `sem_rw.c:down_read` / `sem_rw.c:down_read_trylock` / `sem_rw.c:up_read` / `sem_rw.c:down_write` / `sem_rw.c:down_write_trylock` / `sem_rw.c:up_write` / `sem_rw.c:downgrade_write` - Initializes, destroys, locks, unlocks, and downgrades read-write semaphores (`rw_semaphore_t`).

## Invariants
- A mutex (`NXSEM_IS_MUTEX(sem)`) cannot be posted from interrupt context (`DEBUGASSERT(!up_interrupt_context())` in `sem_post.c:nxsem_post_slow`), cannot be locked recursively by the same thread (`sem_wait.c:nxsem_wait_slow`), and is never interrupted by `EINTR` or `ECANCELED` (`sem_wait.c:nxsem_wait_slow`, `sem_waitirq.c:nxsem_wait_irq`).
- The idle task may never block in `sem_wait.c:nxsem_wait_slow` (`DEBUGASSERT(!is_idle_task(rtcb))`), and a blocking task must have `rtcb->waitobj == NULL` prior to waiting.
- Under `CONFIG_PRIORITY_PROTECT`, `sem_protect.c:nxsem_protect_wait` rejects lock attempts with `-EINVAL` if `rtcb->sched_priority > sem->ceiling`.
- `sem_rw.c:destroy_rwsem` requires no active readers, writers, or waiters (`DEBUGASSERT(rwsem->waiter == 0 && rwsem->reader == 0 && rwsem->writer == 0 && rwsem->holder == RWSEM_NO_HOLDER)`).

## Side Effects
- Atomically updates `NXSEM_COUNT(sem)` or `NXSEM_MHOLDER(sem)`, moves tasks between `g_readytorun` and prioritized waitlists `SEM_WAITLIST(sem)` in state `TSTATE_WAIT_SEM`, and switches CPU context via `up_switch_context`.
- Boosts and restores holder task priorities via `nxsched_set_priority` in `sem_holder.c:nxsem_boostholderprio`, `sem_holder.c:nxsem_restore_priority`, and `sem_protect.c:nxsem_protect_post`, and panics (`PANIC()`) if `sem_holder.c:g_freeholders` is exhausted (`CONFIG_SEM_PREALLOCHOLDERS > 0`).
- Maps and unmaps user-space semaphores into kernel virtual memory (`kmm_map_user`, `kmm_unmap`, `CONFIG_MM_KMAP`) and arms/cancels per-TCB watchdog timers (`rtcb->waitdog`).

## Verification
- Run: `make test`
