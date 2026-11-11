# NuttX Timers, RTC, PWM & Watchdog Subsystem (`include/nuttx/timers`)

## Overview
Provides the upper-half and lower-half driver interfaces and arithmetic helpers for periodic hardware timers (`timer.h`), one-shot timers (`oneshot.h`), real-time clocks (`rtc.h`), Precision Time Protocol clocks (`ptp_clock.h`), watchdog timers (`watchdog.h`), Pulse Width Modulation (`pwm.h`), input capture (`capture.h`), pulse counters (`pulsecount.h`), DShot digital ESC control (`dshot.h`), tickless architecture bridges (`arch_timer.h`, `arch_alarm.h`, `arch_rtc.h`), 64-bit clock-counter conversion (`clkcnt.h`), and external RTC/clock-generator ICs.

## Interface
- `timer.h:timer_lowerhalf_s`, `timer.h:timer_ops_s`, `timer.h:timer_status_s`, `timer.h:timer_notify_s`, `timer.h:timer_register`, `timer.h:timer_unregister`, `timer.h:timer_setcallback`, `timer.h:TCIOC_START`, `timer.h:TCIOC_STOP`, `timer.h:TCIOC_SETTIMEOUT` - Periodic hardware timer upper/lower-half interface and `TCIOC_*` ioctls.
- `oneshot.h:oneshot_lowerhalf_s`, `oneshot.h:oneshot_operations_s`, `oneshot.h:oneshot_initialize`, `oneshot.h:oneshot_register`, `oneshot.h:ONESHOT_START`, `oneshot.h:ONESHOT_CANCEL`, `oneshot.h:OSIOC_START` - High-resolution one-shot timer driver operations and `clkcnt_t` tick/nanosecond conversion wrappers.
- `rtc.h:rtc_ops_s`, `rtc.h:rtc_lowerhalf_s`, `rtc.h:rtc_time`, `rtc.h:rtc_setalarm_s`, `rtc.h:rtc_setperiodic_s`, `rtc.h:rtc_initialize`, `rtc.h:RTC_RD_TIME`, `rtc.h:RTC_SET_TIME`, `rtc.h:RTC_SET_ALARM`, `rpmsg_rtc.h:rpmsg_rtc_initialize` - Real-Time Clock upper/lower-half driver and `RTC_*` ioctls.
- `watchdog.h:watchdog_lowerhalf_s`, `watchdog.h:watchdog_ops_s`, `watchdog.h:watchdog_status_s`, `watchdog.h:watchdog_register`, `watchdog.h:watchdog_unregister`, `watchdog.h:watchdog_notifier_chain_register`, `watchdog.h:WDIOC_START`, `watchdog.h:WDIOC_KEEPALIVE`, `watchdog.h:WDIOC_SETTIMEOUT` - Hardware watchdog timer upper/lower-half interface and auto-monitor keepalive controls.
- `pwm.h:pwm_lowerhalf_s`, `pwm.h:pwm_ops_s`, `pwm.h:pwm_info_s`, `pwm.h:pwm_chan_s`, `pwm.h:pwm_register`, `pwm.h:PWMIOC_SETCHARACTERISTICS`, `pwm.h:PWMIOC_START`, `pwm.h:PWMIOC_STOP` - Single- and multi-channel PWM output driver interface.
- `capture.h:cap_lowerhalf_s`, `capture.h:cap_ops_s`, `capture.h:cap_register`, `capture.h:CAPIOC_DUTYCYCLE`, `capture.h:CAPIOC_FREQUENCY`, `pulsecount.h:pulsecount_lowerhalf_s`, `pulsecount.h:pulsecount_register`, `dshot.h:dshot_lowerhalf_s`, `dshot.h:dshot_register` - Input PWM capture, pulse counter, and DShot motor ESC interfaces.
- `ptp_clock.h:ptp_lowerhalf_s`, `ptp_clock.h:ptp_ops_s`, `ptp_clock.h:ptp_clock_register`, `ptp_clock.h:ptp_clock_unregister`, `ptp_clock_dummy.h:ptp_clock_dummy_initialize` - IEEE 1588 PTP hardware clock character driver interface.
- `clkcnt.h:clkcnt_t`, `clkcnt.h:clkcnt_best_multshift`, `clkcnt.h:clkcnt_delta_time2cnt`, `clkcnt.h:clkcnt_delta_cnt2time_invdiv`, `arch_timer.h:up_timer_set_lowerhalf`, `arch_alarm.h:up_alarm_set_lowerhalf`, `arch_rtc.h:up_rtc_set_lowerhalf` - 64-bit fixed-point counter conversion utilities and system clock lower-half bindings.
- External RTC/Timer ICs: `ds3231.h:dsxxxx_rtc_initialize`, `mcp794xx.h:mcp794xx_rtc_initialize`, `pcf8563.h:pcf8563_rtc_initialize`, `pcf85263.h:pcf85263_rtc_initialize`, `rx8010.h:rx8010_rtc_initialize`, `pl031.h:pl031_initialize`, `goldfish_timer.h:goldfish_timer_initialize`, `cs2100-cp.h:cs2100_enable`, `timer_wdog.h:timer_wdog_initialize`, `watchdog_wdog.h:watchdog_wdog_initialize`.

## Invariants
- In `oneshot.h:oneshot_lowerhalf_s`, lower-half drivers using the `clk_count` interface (`ONESHOT_INITIALIZE_CNT`) must initialize the frequency conversion parameters via `oneshot_count_init` before any `ONESHOT_START` or `ONESHOT_CURRENT` macro is invoked.
- When `CONFIG_PWM_MULTICHAN` is enabled in `pwm.h:pwm_info_s`, the `channels` array must be terminated either by filling all `CONFIG_PWM_NCHANNELS` entries or by setting `channel = -1` on the first unused slot.

## Side Effects
- Registering drivers via `timer.h:timer_register`, `rtc.h:rtc_initialize`, `watchdog.h:watchdog_register`, `pwm.h:pwm_register`, `capture.h:cap_register`, or `ptp_clock.h:ptp_clock_register` creates `/dev/timer*`, `/dev/rtc*`, `/dev/watchdog*`, `/dev/pwm*`, `/dev/capture*`, and `/dev/ptp*` nodes.
- Binding a lower-half timer via `arch_timer.h:up_timer_set_lowerhalf`, `arch_alarm.h:up_alarm_set_lowerhalf`, or `arch_rtc.h:up_rtc_set_lowerhalf` drives the kernel's system tick/tickless scheduler wakeup interrupts.

## Verification
- Run: `make test`
