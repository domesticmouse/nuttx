# POSIX Spawn Attributes & File Actions (`libs/libc/spawn`)

## Overview
Implements POSIX `<spawn.h>` spawn attribute (`posix_spawnattr_t`) and file action (`posix_spawn_file_actions_t`) initialization, configuration, inspection, debug dumping, and destruction routines used by `posix_spawn` and `posix_spawnp`.

## Interface
- `lib_psa_init.c:posix_spawnattr_init`, `lib_psa_destroy.c:posix_spawnattr_destroy` - Initialize `posix_spawnattr_t` from the caller's current scheduling parameters/signal mask and destroy it.
- `lib_psa_getflags.c:posix_spawnattr_getflags`, `lib_psa_setflags.c:posix_spawnattr_setflags` - Get or set spawn attribute flags (`POSIX_SPAWN_RESETIDS`, `POSIX_SPAWN_SETPGROUP`, `POSIX_SPAWN_SETSCHEDPARAM`, `POSIX_SPAWN_SETSCHEDULER`, `POSIX_SPAWN_SETSIGDEF`, `POSIX_SPAWN_SETSIGMASK`).
- `lib_psa_getschedparam.c:posix_spawnattr_getschedparam`, `lib_psa_setschedparam.c:posix_spawnattr_setschedparam`, `lib_psa_getpriority.c:posix_spawnattr_getpriority`, `lib_psa_setpriority.c:posix_spawnattr_setpriority` - Get or set child task scheduling priority and sporadic scheduling parameters (`CONFIG_SCHED_SPORADIC`).
- `lib_psa_getschedpolicy.c:posix_spawnattr_getschedpolicy`, `lib_psa_setschedpolicy.c:posix_spawnattr_setschedpolicy` - Get or set child scheduling policy (`SCHED_OTHER`, `SCHED_FIFO`, `SCHED_RR`, `SCHED_SPORADIC`).
- `lib_psa_getsigmask.c:posix_spawnattr_getsigmask`, `lib_psa_setsigmask.c:posix_spawnattr_setsigmask` - Get or set the child signal mask (`sigset_t`).
- `lib_psa_getstackaddr.c:posix_spawnattr_getstackaddr`, `lib_psa_setstackaddr.c:posix_spawnattr_setstackaddr`, `lib_psa_getstacksize.c:posix_spawnattr_getstacksize`, `lib_psa_setstacksize.c:posix_spawnattr_setstacksize` - Get or set child stack address and stack size (`CONFIG_POSIX_SPAWN_DEFAULT_STACKSIZE`).
- `lib_psa_dump.c:posix_spawnattr_dump`, `lib_psfa_dump.c:posix_spawn_file_actions_dump` - Output debug trace dumps of spawn attributes and queued file actions via `_err`.
- `lib_psfa_init.c:posix_spawn_file_actions_init`, `lib_psfa_destroy.c:posix_spawn_file_actions_destroy` - Initialize and free a `posix_spawn_file_actions_t` linked list.
- `lib_psfa_addaction.c:add_file_action`, `lib_psfa_addclose.c:posix_spawn_file_actions_addclose`, `lib_psfa_adddup2.c:posix_spawn_file_actions_adddup2`, `lib_psfa_addopen.c:posix_spawn_file_actions_addopen` - Allocate and append close, dup2, or open file action entries (`struct spawn_general_file_action_s`) to a `posix_spawn_file_actions_t` list.

## Invariants
- All `posix_spawnattr_*` and `posix_spawn_file_actions_*` functions assert non-`NULL` structure pointers via `DEBUGASSERT` and return positive `errno` codes (`0` on success, `ENOMEM` on allocation failure) without modifying `errno`.
- `lib_psfa_addclose.c:posix_spawn_file_actions_addclose`, `lib_psfa_adddup2.c:posix_spawn_file_actions_adddup2`, and `lib_psfa_addopen.c:posix_spawn_file_actions_addopen` require non-negative file descriptors (`fd >= 0`).

## Side Effects
- `lib_psfa_addclose.c:posix_spawn_file_actions_addclose`, `lib_psfa_adddup2.c:posix_spawn_file_actions_adddup2`, and `lib_psfa_addopen.c:posix_spawn_file_actions_addopen` allocate action nodes on the heap via `lib_zalloc` / `lib_malloc`, freed by `lib_psfa_destroy.c:posix_spawn_file_actions_destroy` via `lib_free`.
- `lib_psa_init.c:posix_spawnattr_init` queries the calling task's scheduling parameters (`sched_getparam`, `sched_getscheduler`) and signal mask (`sigprocmask`).

## Verification
- Run: `make test`
