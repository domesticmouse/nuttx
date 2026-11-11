# Group Database Operations (`libs/libc/grp`)

## Overview
Implements POSIX `<grp.h>` group database lookup, iteration, and supplementary group initialization (`getgrnam`, `getgrnam_r`, `getgrgid`, `getgrgid_r`, `getgrent`, `setgrent`, `endgrent`, `getgrouplist`, `initgroups`), backed either by `/etc/group` (`CONFIG_LIBC_GROUP_FILE`) or a static root group fallback.

## Interface
- `[lib_getgrnam.c:getgrnam]`, `[lib_getgrnamr.c:getgrnam_r]` - Looks up a group database entry by group name.
- `[lib_getgrgid.c:getgrgid]`, `[lib_getgrgidr.c:getgrgid_r]` - Looks up a group database entry by group ID (`gid_t`).
- `[lib_getgrent.c:setgrent]`, `[lib_getgrent.c:endgrent]`, `[lib_getgrent.c:getgrent]` - Rewinds, closes, and sequentially reads entries from the group database.
- `[lib_getgrouplist.c:getgrouplist]` - Populates `groups` with all group IDs to which `user` belongs, always including `group`.
- `[lib_initgroups.c:initgroups]` - Initializes the calling process's supplementary group access list for `user` via `getgrouplist()` and `setgroups()`.
- `[lib_getgrbuf.c:getgrbuf]`, `[lib_getgrbufr.c:getgrbuf_r]` - Internal helpers formatting a raw group record into `struct group` and caller buffer space.
- `[lib_find_grpfile.c:grp_findby_name]`, `[lib_find_grpfile.c:grp_findby_gid]`, `[lib_find_grpfile.c:grp_findby_index]`, `[lib_find_grpfile.c:grp_findby_user]` - Internal `/etc/group` file parser and search routines (`CONFIG_LIBC_GROUP_FILE`).
- `[lib_grp_globals.c:g_group]`, `[lib_grp_globals.c:g_group_buffer]` - Shared static buffer and `struct group` storage used by non-reentrant group functions.

## Invariants
- Non-reentrant functions (`[lib_getgrent.c:getgrent]`, `[lib_getgrgid.c:getgrgid]`, `[lib_getgrnam.c:getgrnam]`, `[lib_getgrbuf.c:getgrbuf]`) return pointers to static storage (`[lib_grp_globals.c:g_group]`, `[lib_grp_globals.c:g_group_buffer]`) that may be overwritten by subsequent calls.
- When `CONFIG_LIBC_GROUP_FILE` is disabled, lookups only match `ROOT_NAME` (`"root"`) with `ROOT_GID` (`0`) (`[lib_getgrnamr.c:getgrnam_r]`, `[lib_getgrgidr.c:getgrgid_r]`).

## Side Effects
- Opens, reads, and closes `CONFIG_LIBC_GROUP_FILEPATH` (`/etc/group`) via `fopen()`, `fgets()`, and `fclose()` when `CONFIG_LIBC_GROUP_FILE` is enabled (`[lib_find_grpfile.c:grp_findby_name]`).
- Allocates and frees dynamic buffers via `lib_malloc()`, `lib_realloc()`, and `lib_free()` (`[lib_getgrbuf.c:getgrbuf]`, `[lib_find_grpfile.c:grp_findby_user]`, `[lib_initgroups.c:initgroups]`).
- `[lib_initgroups.c:initgroups]` mutates the process's supplementary group list via `setgroups()`.

## Verification
- Run: `make test`
