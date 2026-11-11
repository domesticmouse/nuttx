# Built-in Application Registry Queries (`libs/libc/builtin`)

## Overview
Provides lookup and metadata query helpers for compile-time registered NuttX built-in applications stored in the global `g_builtins` table (`CONFIG_BUILTIN`). Supports querying built-in entry descriptors by index, checking availability by name, and retrieving application names, file modes, UIDs, and GIDs.

## Interface
- `[lib_builtin_forindex.c:builtin_for_index]` - Returns a `FAR const struct builtin_s *` descriptor for `index` if `index < g_builtin_count`, or `NULL` otherwise.
- `[lib_builtin_getname.c:builtin_getname]` - Returns the registered string name of the built-in application at `index`, or `NULL` if out of range.
- `[lib_builtin_isavail.c:builtin_isavail]` - Searches the built-in registry for `appname` and returns its table index or `-ENOENT` if not found.
- `[lib_builtin_getmode.c:builtin_getmode]` - Returns the permission mode (`mode`) of the built-in application at `index` under `CONFIG_SCHED_USER_IDENTITY`.
- `[lib_builtin_getuid.c:builtin_getuid]` - Returns the owner `uid` of the built-in application at `index` under `CONFIG_SCHED_USER_IDENTITY`.
- `[lib_builtin_getgid.c:builtin_getgid]` - Returns the group `gid` of the built-in application at `index` under `CONFIG_SCHED_USER_IDENTITY`.

## Invariants
- `index` must be strictly less than `g_builtin_count` (`[lib_builtin_forindex.c:builtin_for_index]`) and have a non-NULL `name` field (`[lib_builtin_getname.c:builtin_getname]`) to be treated as a valid built-in entry.
- Out-of-range indices passed to `[lib_builtin_getmode.c:builtin_getmode]`, `[lib_builtin_getuid.c:builtin_getuid]`, or `[lib_builtin_getgid.c:builtin_getgid]` safely return `0`.

## Side Effects
- Reads the global `g_builtins` array and `g_builtin_count` counter (`[lib_builtin_forindex.c:builtin_for_index]`).

## Verification
- Run: `make test`
