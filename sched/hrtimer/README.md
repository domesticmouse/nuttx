# hrtimer

## Overview
Implements the nanosecond-resolution kernel timer subsystem (`CONFIG_HRTIMER`), using either an intrusive red-black tree (`CONFIG_HRTIMER_TREE`) or sorted doubly linked list with SMP seqlock synchronization and synchronous/asynchronous cancellation.

## Interface
- `hrtimer.h:g_hrtimer_lock` (`hrtimer_initialize.c:g_hrtimer_lock`) - Seqlock (`seqcount_t`) protecting the global hrtimer queue.
- `hrtimer.h:g_hrtimer_guard` (`hrtimer_initialize.c:g_hrtimer_guard`) - Permanent sentinel timer node (`hrtimer_t`) at the tail of the hrtimer queue.
- `hrtimer.h:g_hrtimer_tree` (`CONFIG_HRTIMER_TREE`) - Red-black tree container (`struct hrtimer_tree_s`) of active timers.
- `hrtimer.h:g_hrtimer_head` (`CONFIG_HRTIMER_TREE`) - Cached pointer to the earliest-expiring node in `hrtimer.h:g_hrtimer_tree`.
- `hrtimer.h:g_hrtimer_list` (`!CONFIG_HRTIMER_TREE`) - Sorted doubly linked list (`struct list_node`) of active timers.
- `hrtimer.h:g_hrtimer_running` (`CONFIG_SMP`) - Per-CPU array tracking the currently executing hrtimer callback and cancellation bit.
- `hrtimer.h:hrtimer_lock` / `hrtimer.h:hrtimer_unlock` - Acquires and releases the hrtimer write seqlock with local interrupts saved.
- `hrtimer.h:hrtimer_reprogram` - Reprograms the architecture oneshot timer/alarm to the earliest expiration time in the queue.
- `hrtimer.h:hrtimer_process` - Interrupt-context expiration handler that dequeues expired timers, invokes their callbacks, and re-inserts periodic timers.
- `hrtimer_start.c:hrtimer_start_absolute` - Starts or restarts a high-resolution timer for an absolute nanosecond timestamp (`hrtimer_start` wraps this for relative delays).
- `hrtimer_cancel.c:hrtimer_cancel` - Asynchronously cancels a pending or running high-resolution timer.
- `hrtimer_cancel.c:hrtimer_cancel_sync` - Cancels a high-resolution timer and waits until any concurrently running callback completes.
- `hrtimer_gettime.c:hrtimer_gettime` - Returns the remaining nanoseconds until an hrtimer expires.

## Invariants
- All hrtimer queue mutations must hold `hrtimer.h:hrtimer_lock` (`write_seqlock_irqsave` on `CONFIG_SMP`, `up_irq_save` on UP).
- `hrtimer_initialize.c:g_hrtimer_guard` is never removed from the queue, guaranteeing `hrtimer_get_first()` is always non-NULL and simplifying signed 64-bit expiration comparisons (`clock_compare64`).
- `hrtimer.h:hrtimer_process` must be invoked from interrupt context (`DEBUGASSERT(up_interrupt_context())`) and requires periodic callback return values not to exceed `HRTIMER_MAX_DELAY`.
- `hrtimer_t` pointers must be at least 2-byte aligned (`DEBUGASSERT(((uintptr_t)hrtimer & 1u) == 0)`) so bit 0 of `hrtimer.h:g_hrtimer_running` can encode concurrent cancellation (`hrtimer.h:hrtimer_cancel_running`).

## Side Effects
- Reprograms architecture oneshot hardware timers via `up_alarm_start` (`CONFIG_ALARM_ARCH`) or `up_timer_start` (`CONFIG_TIMER_ARCH`) in `hrtimer.h:hrtimer_reprogram`.
- Executes user-supplied `hrtimer->func` callbacks in interrupt context outside `hrtimer.h:hrtimer_lock` in `hrtimer.h:hrtimer_process`.
- Sleeps (`nxsched_usleep`) in task context or spins in interrupt/critical context while waiting for an active callback to finish during `hrtimer_cancel.c:hrtimer_cancel_sync`.

## Verification
- Run: `make test`
