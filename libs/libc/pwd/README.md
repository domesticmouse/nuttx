# Password & Shadow Database (`libs/libc/pwd`)

## Overview
Implements POSIX user password database (`<pwd.h>`), shadow password (`<shadow.h>`), and login name lookup APIs, supporting both `/etc/passwd` file parsing (`CONFIG_LIBC_PASSWD_FILE`) and a built-in default `root` account fallback.

## Interface
- `lib_pwd.h:ROOT_NAME`, `lib_pwd.h:ROOT_UID`, `lib_pwd.h:ROOT_GID`, `lib_pwd.h:ROOT_GEOCS`, `lib_pwd.h:ROOT_DIR`, `lib_pwd.h:ROOT_SHELL`, `lib_pwd.h:ROOT_PASSWD`, `lib_pwd.h:ROOT_PWDP` - Default root user account constants.
- `lib_pwd.h:g_passwd`, `lib_pwd.h:g_passwd_buffer`, `lib_pwd.h:g_spwd`, `lib_pwd_globals.c:g_passwd`, `lib_pwd_globals.c:g_spwd` - Shared static buffers used by non-reentrant password and shadow lookup functions.
- `lib_find_pwdfile.c:pwd_findby_name`, `lib_find_pwdfile.c:pwd_findby_uid`, `lib_find_pwdfile.c:pwd_findby_index` - Internal `/etc/passwd` (`CONFIG_LIBC_PASSWD_FILEPATH`) line parsers matching by username, UID, or record index.
- `lib_getlogin.c:getlogin`, `lib_getlogin.c:getlogin_r` - Retrieves the login name associated with the calling process's real user ID (`getuid()`).
- `lib_getpwbuf.c:getpwbuf`, `lib_getpwbufr.c:getpwbuf_r` - Populates a `struct passwd` record and string buffer from explicit `(uid, gid, name, gecos, dir, shell, passwd)` fields.
- `lib_getpwent.c:setpwent`, `lib_getpwent.c:endpwent`, `lib_getpwent.c:getpwent`, `lib_getpwent.c:getpwent_r` - Iterates sequentially through user database entries.
- `lib_getpwnam.c:getpwnam`, `lib_getpwnamr.c:getpwnam_r` - Looks up a `struct passwd` record by username.
- `lib_getpwuid.c:getpwuid`, `lib_getpwuidr.c:getpwuid_r` - Looks up a `struct passwd` record by `uid_t`.
- `lib_getspnam.c:getspnam`, `lib_getspnamr.c:getspnam_r` - Retrieves shadow password (`struct spwd`) records by username.

## Invariants
- `lib_getpwbufr.c:getpwbuf_r`, `lib_getlogin.c:getlogin_r`, and `lib_find_pwdfile.c:pwd_foreach` validate that the caller-supplied buffer (`buflen` / `bufsize`) can hold all null-terminated strings, returning `ERANGE` (or `-ERANGE`) and setting `*result = NULL` if insufficient.
- `lib_find_pwdfile.c:pwd_foreach` asserts `DEBUGASSERT(errcode > 0)` when `fopen` fails on `CONFIG_LIBC_PASSWD_FILEPATH`.

## Side Effects
- `lib_find_pwdfile.c:pwd_foreach` opens, reads, and closes the password file on the filesystem (`CONFIG_LIBC_PASSWD_FILEPATH`) via `fopen`/`fgets`/`fclose`.
- `lib_getlogin.c:getlogin`, `lib_getpwbuf.c:getpwbuf`, `lib_getpwent.c:getpwent`, `lib_getpwnam.c:getpwnam`, `lib_getpwuid.c:getpwuid`, and `lib_getspnam.c:getspnam` overwrite process-global state (`g_passwd`, `g_passwd_buffer`, `g_spwd`, or static `g_logname`/`g_ idx`) and set `errno` on failure.

## Verification
- Run: `make test`
