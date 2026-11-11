# wdog

## Overview
Provides kernel tick-resolution watchdog timers (`struct wdog_s`), maintaining an expiration-sorted active timer queue, tickless hardware timer reprogramming, and interrupt-context callback dispatch.

## Interface
- `wdog.h:g_wdactivelist` (`wd_initialize.c:g_wdactivelist`) - Doubly linked list (`struct list_node`) of active watchdog timers sorted by expiration tick.
- `wdog.h:g_wdtimer` (`wd_initialize.c:g_wdtimer`, `CONFIG_SCHED_TICKLESS`) - High-resolution timer (`hrtimer_t`) backing tickless watchdog expirations when `CONFIG_HRTIMER` is enabled.
- `wdog.h:g_wdtimernested` (`CONFIG_SCHED_TICKLESS`) - Flag indicating whether a watchdog callback is currently executing.
- `wdog.h:g_wdexpired` (`CONFIG_SCHED_TICKLESS`) - Expiration tick of the currently firing watchdog callback.
- `wdog.h:wd_timer` (`wd_start.c:wd_timer`) - Processes expired watchdog timers at the given system tick count and dispatches their callbacks.
- `wdog.h:wd_timer_start` (`CONFIG_SCHED_TICKLESS`) - Reprograms the underlying hardware timer or hrtimer for the next watchdog expiration.
- `wdog.h:wd_timer_cancel` (`CONFIG_SCHED_TICKLESS`) - Cancels the underlying tickless timer when the watchdog queue becomes empty.
- `wdog.h:wd_get_next_expire` (`CONFIG_SCHED_TICKLESS`) - Returns the remaining ticks until the head of `wd_initialize.c:g_wdactivelist` expires.
- `wd_start.c:wd_start_abstick` - Arms a watchdog timer (`struct wdog_s`) to fire at an absolute tick count (`wd_start`, `wd_start_abstime`, and `wd_start_realtime` wrap this function).
- `wd_cancel.c:wd_cancel` - Disarms an active watchdog timer and removes it from `wd_initialize.c:g_wdactivelist`.
- `wd_gettime.c:wd_gettime` - Returns the remaining ticks before an active watchdog timer expires, or `0` if inactive/expired.

## Invariants
- `wd_initialize.c:g_wdactivelist` is maintained in ascending order of `wdog->expired` using signed tick comparisons (`clock_compare`) inside `enter_critical_section()`.
- Watchdog callbacks execute in interrupt context with `wdog->func` cleared to `NULL` before invocation (`wd_start.c:wd_expiration`) so timers can safely re-arm themselves.

## Side Effects
- Inserts and removes nodes in `wd_initialize.c:g_wdactivelist` and reprograms tickless hardware timers (`wdog.h:wd_timer_start`, `wdog.h:wd_timer_cancel`) in `wd_start.c:wd_start_abstick`, `wd_cancel.c:wd_cancel`, and `wd_start.c:wd_timer`.
- Restores PIC base registers (`up_setpicbase`), emits scheduler trace notes (`sched_note_wdog`), and triggers `CRITMONITOR_PANIC` if a callback exceeds `CONFIG_SCHED_CRITMONITOR_MAXTIME_WDOG` in `wd_start.c:wd_expiration`.

## Verification
- Run: `make test`
