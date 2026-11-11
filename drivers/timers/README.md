# Timers, RTC, PWM, Watchdog, and Capture Drivers (`drivers/timers`)

## Overview
Provides upper-half character drivers, architecture timer bridges, and peripheral lower-half drivers for general-purpose hardware timers (`timer.c`, `arch_timer.c`, `timer_wdog.c`, `goldfish_timer.c`), oneshot timers (`oneshot.c`), real-time clocks (`rtc.c`, `arch_rtc.c`, `rpmsg_rtc.c`, `pl031.c`, `ds3231.c`, `mcp794xx.c`, `pcf85263.c`, `pcf8563.c`, `rx8010.c`), watchdog timers (`watchdog.c`, `watchdog_wdog.c`), pulse-width modulation (`pwm.c`), input capture (`capture.c`, `fake_capture.c`), pulse counters (`pulsecount.c`), DShot ESC motor control (`dshot.c`), IEEE 1588 PTP hardware clocks (`ptp_clock.c`, `ptp_clock_dummy.c`), and clock multiplier ICs (`cs2100-cp.c`).

## Interface
- `[timer.c:timer_register]`, `[timer.c:timer_unregister]`, `[timer.c:timer_setcallback]`, `[timer_wdog.c:timer_wdog_initialize]`, `[goldfish_timer.c:goldfish_timer_initialize]` - Upper-half hardware timer character driver (`/dev/timerN`) and software/Goldfish lower-half implementations.
- `[oneshot.c:oneshot_register]` - Upper-half oneshot timer character driver (`/dev/oneshotN`).
- `[arch_alarm.c:up_alarm_set_lowerhalf]`, `[arch_timer.c:up_timer_set_lowerhalf]`, `[arch_rtc.c:up_rtc_set_lowerhalf]`, `[arch_alarm.c:up_perf_init]`, `[arch_alarm.c:up_perf_convert]` - Binds oneshot, timer, or RTC lower-half drivers to the NuttX system clock (`up_timer_*`) and performance counter (`up_perf_*`) APIs.
- `[rtc.c:rtc_initialize]`, `[rpmsg_rtc.c:rpmsg_rtc_initialize]`, `[rpmsg_rtc.c:rpmsg_rtc_server_initialize]`, `[pl031.c:pl031_initialize]`, `[ds3231.c:dsxxxx_rtc_initialize]`, `[mcp794xx.c:mcp794xx_rtc_initialize]`, `[pcf85263.c:pcf85263_rtc_initialize]`, `[pcf8563.c:pcf8563_rtc_initialize]`, `[rx8010.c:rx8010_rtc_initialize]` - Upper-half `/dev/rtcN` character driver and RPMSG, ARM PL031, and I2C RTC lower-half drivers.
- `[watchdog.c:watchdog_register]`, `[watchdog.c:watchdog_unregister]`, `[watchdog.c:watchdog_notifier_chain_register]`, `[watchdog.c:watchdog_notifier_chain_unregister]`, `[watchdog.c:watchdog_automonitor_timeout]`, `[watchdog_wdog.c:watchdog_wdog_initialize]` - Upper-half watchdog timer driver (`/dev/watchdogN`) with optional auto-monitor keepalive and panic notifier chains.
- `[pwm.c:pwm_register]`, `[capture.c:cap_register]`, `[capture.c:cap_register_multiple]`, `[fake_capture.c:fake_capture_initialize]`, `[pulsecount.c:pulsecount_register]`, `[pulsecount.c:pulsecount_expired]`, `[dshot.c:dshot_register]` - Upper-half drivers for PWM generation, duty/frequency input capture, pulse counting, and DShot digital ESC signaling.
- `[ptp_clock.c:ptp_clock_register]`, `[ptp_clock.c:ptp_clock_unregister]`, `[ptp_clock.c:ptp_clockid_to_filep]`, `[ptp_clock_dummy.c:ptp_clock_dummy_initialize]` - POSIX PTP hardware clock driver (`/dev/ptpN`).
- `[cs2100-cp.c:cs2100_enable]`, `[cs2100-cp.c:cs2100_disable]`, `[cs2100-cp.c:cs2100_dump]` - Cirrus Logic CS2100-CP fractional-N clock multiplier I2C configuration driver.

## Invariants
- `[arch_alarm.c:up_perf_init]` and `[arch_timer.c:up_perf_init]` assert `DEBUGASSERT(CONFIG_BOARD_LOOPSPERMSEC != 0)` when fallback delay constants are used.
- Upper-half registration routines (`[timer.c:timer_register]`, `[watchdog.c:watchdog_register]`, `[pwm.c:pwm_register]`, `[capture.c:cap_register]`, `[pulsecount.c:pulsecount_register]`, `[dshot.c:dshot_register]`, `[rtc.c:rtc_initialize]`, `[ptp_clock.c:ptp_clock_register]`) assert non-null `lower` and `lower->ops` pointers (`setup`/`shutdown`).
- `[rtc.c:rtc_initialize]` asserts alarm IDs satisfy `0 <= alarmid < CONFIG_RTC_NALARMS`.
- `[cs2100-cp.c:cs2100_enable]` asserts `DEBUGASSERT(config->i2c->ops && config->i2c->ops->transfer)`.

## Side Effects
- Registers character devices (`/dev/timer*`, `/dev/oneshot*`, `/dev/rtc*`, `/dev/watchdog*`, `/dev/pwm*`, `/dev/capture*`, `/dev/dshot*`, `/dev/ptp*`) via `register_driver`.
- Programs hardware timer/RTC/PWM/watchdog registers via MMIO or I2C (`I2C_TRANSFER`), attaches hardware interrupts, and delivers POSIX signals (`nxsig_notification`) to registered user tasks on timer/alarm expiration.
- `[rpmsg_rtc.c:rpmsg_rtc_initialize]` synchronizes system time across processor cores over RPMSG endpoints.

## Verification
- Run: `make test`
