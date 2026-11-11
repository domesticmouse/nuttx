# POSIX Standard Symbolic Constants & System Wrappers (`libs/libc/unistd`)

## Overview
Implements POSIX `<unistd.h>`, `<getopt.h>`, `<sys/statvfs.h>`, `<sys/resource.h>`, `<sys/times.h>`, `<utime.h>`, and `<crypt.h>` user-space system call wrappers, process/session/user identity management, `exec*` and `fork`/`vfork`/`daemon` process creation, working directory management (`chdir`, `getcwd`), file locking (`flock`, `lockf`), command-line option parsing (`getopt`, `getopt_long`, `getopt_long_only`), and system configuration queries (`sysconf`, `pathconf`, `confstr`).

## Interface
- `lib_access.c:access`, `lib_access.c:faccessat`, `lib_chdir.c:chdir`, `lib_fchdir.c:fchdir`, `lib_getcwd.c:getcwd`, `lib_getcwd.c:get_current_dir_name`, `lib_restoredir.c:lib_restoredir` - File accessibility checks and working directory queries/updates (`PWD` environment variable).
- `lib_fchownat.c:fchownat`, `lib_linkat.c:linkat`, `lib_symlinkat.c:symlinkat`, `lib_readlinkat.c:readlinkat`, `lib_unlinkat.c:unlinkat`, `lib_truncate.c:truncate`, `lib_fdatasync.c:fdatasync`, `lib_posix_fallocate.c:posix_fallocate`, `lib_copy_file_range.c:copy_file_range`, `lib_statvfs.c:statvfs`, `lib_fstatvfs.c:fstatvfs`, `lib_utime.c:utime`, `lib_utimes.c:utimes`, `lib_utimes.c:futimesat`, `lib_futimes.c:futimes`, `lib_lutimes.c:lutimes`, `lib_flock.c:flock`, `lib_lockf.c:lockf`, `lib_pipe.c:pipe` - File system, link, timestamp, space allocation, file locking, and pipe wrappers.
- `lib_execl.c:execl`, `lib_execl.c:execlp`, `lib_execle.c:execle`, `lib_execv.c:execv`, `lib_execvp.c:execvp`, `lib_execvp.c:execvpe`, `lib_fork.c:fork`, `lib_fork.c:vfork`, `lib_daemon.c:daemon`, `lib_dpopen.c:dpopen`, `lib_dpopen.c:dpclose`, `lib_wait.c:wait3`, `lib_wait.c:wait4` - Process execution, forking (with `pthread_atfork` callbacks), daemonization, bidirectional pipe spawning, and child waiting.
- `lib_getuid.c:getuid`, `lib_geteuid.c:geteuid`, `lib_setuid.c:setuid`, `lib_seteuid.c:seteuid`, `lib_setreuid.c:setreuid`, `lib_getresuid.c:getresuid`, `lib_setresuid.c:setresuid`, `lib_getgid.c:getgid`, `lib_getegid.c:getegid`, `lib_setgid.c:setgid`, `lib_setegid.c:setegid`, `lib_setregid.c:setregid`, `lib_getresgid.c:getresgid`, `lib_setresgid.c:setresgid`, `lib_getgroups.c:getgroups`, `lib_setgroups.c:setgroups`, `lib_issetugid.c:issetugid` - User and group identity queries and modifications.
- `lib_getpgid.c:getpgid`, `lib_getpgrp.c:getpgrp`, `lib_setpgid.c:setpgid`, `lib_setpgrp.c:setpgrp`, `lib_getsid.c:getsid`, `lib_setsid.c:setsid`, `lib_getpriority.c:getpriority`, `lib_setpriority.c:setpriority`, `lib_nice.c:nice` - Process group, session, and scheduling priority wrappers.
- `lib_alarm.c:alarm`, `lib_sleep.c:sleep`, `lib_usleep.c:usleep`, `lib_times.c:times`, `lib_getrusage.c:getrusage`, `lib_ulimit.c:ulimit` - Timers (`SIGALRM`), sleep wrappers (`nanosleep`), and resource usage queries.
- `unistd.h:getoptvars`, `unistd.h:getopt_common`, `lib_getopt.c:getopt`, `lib_getopt_long.c:getopt_long`, `lib_getopt_longonly.c:getopt_long_only`, `lib_getopt_common.c:getopt_common`, `lib_getoptvars.c:getoptvars`, `lib_getoptargp.c:getoptargp`, `lib_getopterrp.c:getopterrp`, `lib_getoptindp.c:getoptindp`, `lib_getoptoptp.c:getoptoptp` - Thread-safe command-line short and long option parsing backed by TLS `struct getopt_s`.
- `lib_sysconf.c:sysconf`, `lib_pathconf.c:pathconf`, `lib_pathconf.c:fpathconf`, `lib_confstr.c:confstr`, `lib_getpagesize.c:getpagesize`, `lib_getdtablesize.c:getdtablesize`, `lib_gethostname.c:gethostname`, `lib_sethostname.c:sethostname`, `lib_getentropy.c:getentropy`, `lib_getpass.c:getpass`, `lib_getusershell.c:getusershell`, `lib_getusershell.c:setusershell`, `lib_getusershell.c:endusershell`, `lib_crypt.c:crypt`, `lib_crypt_r.c:crypt_r`, `lib_swab.c:swab` - System configuration, hostname, entropy, password prompt, crypto hashing (`/dev/crypto`), and byte swapping utilities.

## Invariants
- `lib_truncate.c:truncate` asserts `DEBUGASSERT(path != NULL && length >= 0)`.
- `lib_swab.c:swab` asserts `DEBUGASSERT(src != NULL && dest != NULL)`.
- `lib_getoptvars.c:getoptvars` stores `optarg`, `opterr`, `optind`, and `optopt` per-thread in TLS (`tls_get_info()->tl_getopt`) when `!CONFIG_BUILD_KERNEL`.

## Side Effects
- Invokes VFS, process, signal, and timer system calls, updates process environment variables (`setenv("PWD", ...)` in `chdir`/`fchdir`/`lib_restoredir`), interacts with `/dev/crypto` in `crypt_r`, and sets `errno` on errors.

## Verification
- Run: `make test`
