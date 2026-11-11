# timer

## Overview
Implements per-process POSIX interval timers (`timer_create`, `timer_settime`, `timer_delete`, `timer_gettime`, `timer_getoverrun`) and BSD interval timers (`setitimer`, `getitimer`) backed by kernel watchdog timers and signal notifications.

## Interface
- `timer.h:g_freetimers` (`timer_initialize.c:g_freetimers`) - Singly linked free list (`sq_queue_t`) of preallocated `struct posix_timer_s` instances (`CONFIG_PREALLOC_TIMERS`).
- `timer.h:g_alloctimers` (`timer_initialize.c:g_alloctimers`) - Singly linked list (`sq_queue_t`) of active allocated POSIX timers.
- `timer.h:g_locktimers` (`timer_initialize.c:g_locktimers`) - Spinlock (`spinlock_t`) serializing access to the timer lists and timer state.
- `timer.h:timer_initialize` (`timer_initialize.c:timer_initialize`) - Initializes `timer_initialize.c:g_freetimers` and `timer_initialize.c:g_alloctimers` during OS boot.
- `timer.h:timer_deleteall` (`timer_initialize.c:timer_deleteall`) - Deletes all POSIX timers owned by an exiting task (`pid`).
- `timer.h:timer_release` (`timer_release.c:timer_release`) - Decrements a timer's reference count (`timer->pt_crefs`) and frees or recycles it when the count reaches zero.
- `timer.h:timer_gethandle` (`timer_initialize.c:timer_gethandle`) - Validates a `timer_t` handle and verifies that the caller belongs to the owning task group.
- `timer_create.c:timer_create` - Creates a per-process POSIX timer for `CLOCK_REALTIME`, `CLOCK_MONOTONIC`, or `CLOCK_BOOTTIME`.
- `timer_delete.c:timer_delete` - Disarms and deletes a POSIX timer.
- `timer_settime.c:timer_settime` - Arms, rearms, or disarms a POSIX timer for relative or absolute (`TIMER_ABSTIME`) expiration and optional periodic reload.
- `timer_gettime.c:timer_gettime` - Returns the remaining time until expiration and reload interval of a POSIX timer.
- `timer_getoverrun.c:timer_getoverrun` - Returns the signal overrun count (`timer->pt_overrun`) for the most recent timer expiration.
- `timer_setitimer.c:setitimer` / `timer_getitimer.c:getitimer` - Sets and queries the task group's BSD interval timer (`ITIMER_REAL`, `ITIMER_VIRTUAL`, `ITIMER_PROF`) stored in `group->itimer`.

## Invariants
- Accesses to `timer_initialize.c:g_alloctimers` and `timer_initialize.c:g_freetimers` are protected by `timer_initialize.c:g_locktimers` (`spin_lock_irqsave` / `spin_unlock_irqrestore`).
- `timer_initialize.c:timer_gethandle` enforces task-group ownership (`owner->group == this_task()->group`) whenever called outside interrupt context.
- `timer->pt_crefs` reference counting prevents a timer structure from being freed while `timer_settime.c:timer_timeout` is actively delivering its notification.
- At most one signal per timer is queued in `timer->pt_act` at any time; expirations occurring while `timer->pt_act.sa_user != NULL` increment `timer->pt_overrun` up to `DELAYTIMER_MAX`.

## Side Effects
- Allocates and frees `struct posix_timer_s` objects from `timer_initialize.c:g_freetimers` or the kernel heap (`kmm_malloc`, `kmm_free`) in `timer_create.c:timer_allocate` and `timer_release.c:timer_release`.
- Starts and cancels kernel watchdog timers (`wd_start_abstick`, `wd_cancel`) in `timer_settime.c:timer_settime`, `timer_settime.c:timer_timeout`, and `timer_release.c:timer_release`.
- Queues `SI_TIMER` signal notifications (`nxsig_notification_source`) and cancels pending signal work (`nxsig_cancel_notification`) on timer expiration and deletion.
- Updates thread-local `errno` (`set_errno`) on invalid arguments or resource exhaustion.

## Verification
- Run: `make test`
