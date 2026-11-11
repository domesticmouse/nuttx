# libgcc

## Overview
Provides GCC runtime support for GCOV code coverage collection/dumping (`gcov.c`) and `gmon`/`gprof` execution profiling (`profile.c`) in NuttX. Manages linked lists of `struct gcov_info` objects emitted by GCC instrumentation and call-graph arc/histogram tables updated by `mcount_internal` and `profil`.

## Interface
- `gcov.c:__gcov_init`, `gcov.c:__gcov_merge_add`, `gcov.c:__gcov_exit`, `gcov.c:__gcov_execve`, `gcov.c:__gcov_execl`, `gcov.c:__gcov_execv`, `gcov.c:__gcov_execle`, `gcov.c:__gcov_fork`, `gcov.c:__gcov_dump`, `gcov.c:__gcov_reset`, `gcov.c:__gcov_unload`, `gcov.c:__gcov_info_start`, `gcov.c:__gcov_info_end`
- `profile.c:moncontrol`, `profile.c:monstartup`, `profile.c:_mcleanup`, `profile.c:mcount_internal`

## Invariants
- Access to the global `gcov.c:__gcov_info_start` singly-linked list (`struct gcov_info`) must be serialized using the recursive mutex `gcov.c:g_gcov_lock`.
- `profile.c:monstartup` must not allocate memory if the OS is not ready (`!OSINIT_OS_READY()`), if called from an interrupt context (`up_interrupt_context()`), or if `g_monparam.tos` is already initialized.
- Updates to `profile.c:g_monparam` (`tos`, `froms`, `kcount`, `running`) are synchronized via `spin_lock_irqsave` and `spin_unlock_irqrestore` on `g_monparam.lock`, and profiling functions are marked `noinstrument_function` to prevent recursive `mcount_internal` invocation.

## Side Effects
- `gcov.c:__gcov_init` initializes `GCOV_PREFIX_STRIP` and `GCOV_PREFIX` environment variables via `setenv`, optionally registers a reboot notifier via `register_reboot_notifier` (`CONFIG_COVERAGE_GCOV_DUMP_REBOOT`), and prepends `info` to `__gcov_info_start`.
- `gcov.c:__gcov_dump` allocates temporary buffers (`lib_malloc`, `lib_get_tempbuffer`), creates directories (`mkdir`), opens and writes `.gcda` or single-stream hex dump files (`_NX_OPEN`, `_NX_WRITE`, `_NX_CLOSE`), and logs status via `syslog`.
- `gcov.c:__gcov_reset` zeroes all active function counter arrays in `__gcov_info_start`, and `gcov.c:__gcov_unload` unlinks `gcov_info` nodes within an unloaded address range.
- `profile.c:moncontrol`, `profile.c:monstartup`, and `profile.c:_mcleanup` allocate and free kernel heap memory (`kmm_zalloc`, `kmm_free`), start/stop PC sampling via `profil`, and write `gmon.out` profiling data to the filesystem (`file_open`, `file_write`, `file_close`).

## Verification
- Run: `make test`
