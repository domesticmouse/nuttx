# Time, Calendar & Timezone Conversions (`libs/libc/time`)

## Overview
Implements ISO C and POSIX `<time.h>` and `<sys/time.h>` clock queries (`time`, `gettimeofday`, `settimeofday`, `timespec_get`, `gethrtime`), sleep (`nanosleep`), Gregorian/Julian calendar math, UTC/local broken-down time conversions (`gmtime`, `localtime`, `mktime`, `timegm`, `tzset` with IANA TZif zoneinfo parsing under `CONFIG_LIBC_LOCALTIME`), and string formatting/parsing (`asctime`, `ctime`, `strftime`, `strptime`).

## Interface
- `lib_time.c:time`, `lib_gettimeofday.c:gettimeofday`, `lib_settimeofday.c:settimeofday`, `lib_timespec_get.c:timespec_get`, `lib_gethrtime.c:gethrtime`, `lib_difftime.c:difftime`, `lib_nanosleep.c:nanosleep` - System clock queries, updates (`clock_gettime`/`clock_settime`), high-resolution monotonic time, elapsed time difference, and high-resolution sleep (`clock_nanosleep`).
- `lib_isleapyear.c:clock_isleapyear`, `lib_daysbeforemonth.c:clock_daysbeforemonth`, `lib_dayofweek.c:clock_dayoftheweek`, `lib_calendar2utc.c:clock_calendar2utc` - Internal and kernel-shared calendar utility functions.
- `lib_gmtime.c:gmtime`, `lib_gmtimer.c:gmtime_r`, `lib_gmtime.c:localtime`, `lib_gmtimer.c:localtime_r`, `lib_localtime.c:localtime`, `lib_localtime.c:localtime_r`, `lib_localtime.c:mktime`, `lib_localtime.c:tzset`, `lib_tzset.c:tzset`, `lib_timegm.c:timegm`, `lib_timegm.c:mktime` - Convert between `time_t` epoch seconds and `struct tm` in UTC or local timezones.
- `lib_asctime.c:asctime`, `lib_asctimer.c:asctime_r`, `lib_ctime.c:ctime`, `lib_ctimer.c:ctime_r`, `lib_strftime.c:strftime`, `lib_strptime.c:strptime` - Format `struct tm` / `time_t` into strings and parse date/time strings into `struct tm`.

## Invariants
- `lib_timespec_get.c:timespec_get` requires `b == TIME_UTC` (returning `0` otherwise).
- `lib_localtime.c` serializes access to shared timezone state (`lclmem`, `gmtmem`, `tzname`) using `g_lcl_lock` (`nxmutex_lock`/`nxmutex_unlock`) when `CONFIG_LIBC_LOCALTIME` is enabled.

## Side Effects
- `lib_settimeofday.c:settimeofday` updates the system real-time clock via `clock_settime(CLOCK_REALTIME, ...)`.
- `lib_localtime.c:tzset` reads the `TZ` environment variable (`getenv`), opens and reads TZif files under `CONFIG_LIBC_TZDIR` (`open`/`read`/`close`), and mutates global `tzname`, `timezone`, and `daylight` variables.
- `lib_gmtime.c:gmtime`, `lib_asctime.c:asctime`, and `lib_ctime.c:ctime` overwrite module-static buffers.

## Verification
- Run: `make test`
