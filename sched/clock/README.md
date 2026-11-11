# clock

## Overview
Implements the NuttX system clock and timekeeping subsystem (`CLOCK_REALTIME`, `CLOCK_MONOTONIC`, `CLOCK_BOOTTIME`), including tick counters, hardware RTC synchronization, NTP/BSD clock slewing (`adjtime`, `clock_adjtime`), high-resolution performance counters (`perf_gettime`), busy-wait delays, and clock-change notifier chains.

## Interface
- `clock.h:g_basetime` (`clock_initialize.c:g_basetime`) - Real-time epoch offset (`struct timespec`) corresponding to system boot (tick 0).
- `clock.h:g_basetime_lock` (`clock_initialize.c:g_basetime_lock`) - Spinlock (`spinlock_t`) protecting `clock_initialize.c:g_basetime`.
- `clock.h:clock_basetime` (`clock_initialize.c:clock_basetime`) - Initializes the initial `g_basetime` from RTC (`up_rtc_gettime`) or `CONFIG_START_YEAR`/`CONFIG_START_MONTH`/`CONFIG_START_DAY`.
- `clock.h:clock_initialize` (`clock_initialize.c:clock_initialize`) - Initializes hardware RTC (`up_rtc_initialize`), timekeeping, and system timer (`up_timer_initialize`).
- `clock.h:clock_update_sched_ticks` / `clock.h:clock_increase_sched_ticks` / `clock.h:clock_get_sched_ticks` (`clock_sched_ticks.c`) - Updates and reads the global scheduler tick counter (`clock_sched_ticks.c:g_system_ticks`).
- `clock_initialize.c:clock_synchronize` / `clock_initialize.c:clock_resynchronize` (`CONFIG_RTC`) - Synchronizes or resynchronizes system time with the external hardware RTC.
- `clock.c:clock` - Returns the current system tick count (`clock_systime_ticks`).
- `clock_gettime.c:nxclock_gettime` / `clock_gettime.c:clock_gettime` - Reads the current time for `CLOCK_REALTIME`, `CLOCK_MONOTONIC`, `CLOCK_BOOTTIME`, process/thread CPU-time clocks, or dynamic FD/PTP clocks.
- `clock_settime.c:clock_settime` - Sets `CLOCK_REALTIME` (or a dynamic PTP clock), updates the RTC, and triggers clock change notifications.
- `clock_getres.c:clock_getres` - Returns the nanosecond resolution of the specified `clockid_t`.
- `clock_adjtime.c:adjtime` (`clock_timekeeping.c:adjtime`) / `clock_adjtime.c:nxclock_adjtime` / `clock_adjtime.c:clock_adjtime` - Slews the system clock or adjusts hardware/PTP clock frequency.
- `clock_delay.c:up_mdelay` / `clock_delay.c:up_udelay` / `clock_delay.c:up_ndelay` - Performs calibrated busy-wait millisecond, microsecond, and nanosecond delays.
- `clock_notifier.c:register_clock_notifier` / `clock_notifier.c:unregister_clock_notifier` / `clock_notifier.c:clock_notifier_call_chain` - Manages and invokes the atomic notifier chain (`clock_notifier.c:g_clock_notifier_head`) on real-time clock changes.
- `clock_perf.c:perf_gettime` / `clock_perf.c:perf_convert` / `clock_perf.c:perf_getfreq` - Reads and converts hardware performance counter timestamps.
- `clock_realtime2absticks.c:clock_realtime2absticks` - Converts an absolute `CLOCK_REALTIME` `struct timespec` into an absolute system tick count.
- `clock_systime_ticks.c:clock_systime_ticks` / `clock_systime_timespec.c:clock_systime_timespec` - Returns elapsed system time since boot in ticks or `struct timespec`.
- `clock_timekeeping.h:clock_timekeeping_get_wall_time` / `clock_timekeeping.h:clock_timekeeping_set_wall_time` / `clock_timekeeping.h:clock_update_wall_time` / `clock_timekeeping.h:clock_inittimekeeping` (`clock_timekeeping.c`, `CONFIG_CLOCK_TIMEKEEPING`) - Cycle-counter-based continuous wall-time tracking and NTP slewing.

## Invariants
- `clock_sched_ticks.c:g_system_ticks` is protected by `clock_sched_ticks.c:g_system_tick_lock` (`write_seqlock_irqsave` / `read_seqbegin`) when 64-bit ticks are used on 32-bit architectures.
- `clock_initialize.c:g_basetime` is serialized by `clock_initialize.c:g_basetime_lock` (`spin_lock_irqsave` / `spin_unlock_irqrestore`), or by `clock_timekeeping.c:g_clock_lock` when `CONFIG_CLOCK_TIMEKEEPING` is enabled.
- `clock_initialize.c:clock_resynchronize` refuses to step system time backward when `curr_ts >= rtc_time`.

## Side Effects
- Initializes, reads, and updates hardware timers and RTCs (`up_timer_initialize`, `up_rtc_initialize`, `up_rtc_gettime`, `up_rtc_settime` directly or via `LPWORK` `clock_initialize.c:g_RTC_save_work`), and adjusts hardware clock rates (`up_adjtime`, `up_rtc_adjtime`).
- Issues PTP character driver `ioctl` commands (`PTP_CLOCK_GETTIME`, `PTP_CLOCK_SETTIME`, `PTP_CLOCK_ADJTIME`, `PTP_CLOCK_GETRES`) when `clock_id` encodes a file descriptor (`CLOCK_FD`).
- Broadcasts `CLOCK_REALTIME` updates to registered listeners via `clock_notifier.c:clock_notifier_call_chain` and sets `errno` on invalid clock IDs or timespecs.

## Verification
- Run: `make test`
