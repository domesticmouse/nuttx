# Environment Variable Management (`libs/libc/environ`)

## Overview
Implements standard C and POSIX environment variable management (`getenv`, `setenv`, `putenv`, `unsetenv`, `clearenv`, `secure_getenv`, `environ`) and task-group environment lifecycle helpers (`env_dup`, `env_release`, `env_foreach`, `env_sanitize_secure`) when `CONFIG_DISABLE_ENVIRON` is not set.

## Interface
- `[env_getenv.c:getenv]` - Searches the calling task group's environment array for `name` and returns a pointer to its value string.
- `[env_secureexec.c:secure_getenv]` - Returns `getenv(name)` unless the current task group is marked secure-execution (`ta_secure_exec`), in which case it returns `NULL`.
- `[env_secureexec.c:env_sanitize_secure]` - Strips security-sensitive variables (`LD_LIBRARY_PATH`, `LD_PRELOAD`, `PATH`, `TMPDIR`, `TZ`) during `setuid`/`setgid` execution.
- `[env_setenv.c:setenv]` - Adds or updates `name=value` in the task group's environment, allocating storage for the formatted string.
- `[env_putenv.c:putenv]` - Inserts or replaces a `"name=value"` string directly into the environment pointer array without copying the string payload.
- `[env_unsetenv.c:unsetenv]` - Removes `name` from the environment without freeing the underlying string buffer.
- `[env_clearenv.c:clearenv]` - Clears the environment pointer table (`ta_environ`) while retaining allocated string blocks until task exit.
- `[env_getenvironptr.c:get_environ_ptr]` - Returns the address of the calling task group's `char **environ` array.
- `[env_dup.c:env_dup]` - Duplicates the parent task group's environment array and variable strings for a newly spawned task group.
- `[env_release.c:env_release]` - Frees the environment pointer array (`ta_environ`) and all string allocations tracked in `ta_envmem` on task group teardown.
- `[env_foreach.c:env_foreach]` - Iterates over all `"name=value"` entries in a task group's environment, invoking callback `cb`.
- `[env_alloc.c:env_alloc]`, `[env_alloc.c:env_free]`, `[env_alloc.c:env_reserve]`, `[env_findvar.c:env_findvar]`, `[env_removevar.c:env_removevar]` - Internal environment memory management and table lookup helpers.

## Invariants
- Environment functions require a valid task-group TLS info structure (`tls_get_info()->tl_task != NULL`) and must not be called from interrupt handlers or the idle task (`[env_getenv.c:getenv]`, `[env_setenv.c:setenv]`).
- Variable strings allocated by `[env_alloc.c:env_alloc]` are retained on `info->ta_envmem` until `[env_release.c:env_release]` so pointers returned by `[env_getenv.c:getenv]` remain valid across subsequent `setenv`/`unsetenv`/`clearenv` calls (`[env_unsetenv.c:unsetenv]`, `[env_clearenv.c:clearenv]`).
- `[env_putenv.c:putenv]` stores the caller-provided `char *string` directly into `ta_environ` without copying.

## Side Effects
- Acquires and releases the task-group recursive mutex `info->ta_lock` via `nxrmutex_lock()` and `nxrmutex_unlock()` (`[env_getenv.c:getenv]`, `[env_setenv.c:setenv]`, `[env_putenv.c:putenv]`, `[env_unsetenv.c:unsetenv]`, `[env_clearenv.c:clearenv]`).
- Allocates, reallocates, and frees heap memory (`lib_malloc`, `lib_realloc`, `lib_free` or `kumm_malloc`/`kumm_free`) for `ta_environ` and `ta_envmem` nodes (`[env_alloc.c:env_alloc]`, `[env_release.c:env_release]`).
- Sets thread `errno` (`EINVAL`, `ENOMEM`, `ENOENT`) on error.

## Verification
- Run: `make test`
