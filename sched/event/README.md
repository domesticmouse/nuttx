# event

## Overview
Implements kernel bitmask event group synchronization primitives (`nxevent_t`, `CONFIG_SCHED_EVENTS`), supporting wait-any and wait-all semantics, optional auto-clear on wake, tick-based timeouts, and interrupt-safe posting and clearing.

## Interface
- `event.h:nxevent_wait_irq` (`event_waitirq.c:nxevent_wait_irq`) - Interrupt/timeout handler that terminates a blocked task's event wait with a specified error code (`ECANCELED`, `EINTR`, `ETIMEDOUT`).
- `event_init.c:nxevent_init` - Initializes an `nxevent_t` waitlist and sets its initial event bitmask.
- `event_destroy.c:nxevent_destroy` - Destroys an initialized `nxevent_t` waitlist.
- `event_post.c:nxevent_post` - Sets or overwrites event bits according to `nxevent_flags_t` (`NXEVENT_POST_SET`) and wakes any waiting tasks whose wait conditions are satisfied.
- `event_wait.c:nxevent_tickwait` - Waits for any or all specified bits in `events` (`NXEVENT_WAIT_ALL`, `NXEVENT_WAIT_NOCLEAR`) with a tick timeout (`delay`).
- `event_wait.c:nxevent_wait` - Waits indefinitely for specified event bits (`nxevent_tickwait` with `UINT32_MAX`).
- `event_wait.c:nxevent_trywait` - Polls for specified event bits without blocking (`nxevent_tickwait` with `0`).
- `event_clear.c:nxevent_clear` - Atomically clears the bits specified by `mask` in `event->events` and returns the remaining bits.
- `event_getmask.c:nxevent_getmask` - Atomically reads and returns the current `event->events` bitmask.
- `event_reset.c:nxevent_reset` - Resets `event->events` to a new mask while waking any currently blocked tasks with `-ECANCELED`.

## Invariants
- `event_wait.c:nxevent_tickwait` must not be called from interrupt context or by the idle task (`DEBUGASSERT(event != NULL && up_interrupt_context() == false)` and `DEBUGASSERT(!is_idle_task(rtcb))`), and requires `rtcb->waitobj == NULL` prior to blocking.
- All accesses to `event->events` and `EVENT_WAITLIST(event)` are serialized within `enter_critical_section()`.

## Side Effects
- Moves blocking tasks from `g_readytorun` to `EVENT_WAITLIST(event)` in state `TSTATE_WAIT_EVENT`, arms `rtcb->waitdog` via `wd_start`, and switches CPU context via `up_switch_context` in `event_wait.c:nxevent_tickwait`.
- Cancels `tcb->waitdog`, unblocks waiting tasks onto `g_readytorun`, clears matched bits in `event->events` (unless `NXEVENT_WAIT_NOCLEAR` is set), and triggers context switches via `up_switch_context` in `event_post.c:nxevent_post`, `event_reset.c:nxevent_reset`, and `event_waitirq.c:nxevent_wait_irq`.

## Verification
- Run: `make test`
