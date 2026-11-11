# Signal Set & Handler Utilities (`libs/libc/signal`)

## Overview
Implements POSIX and System V user-space signal set manipulation functions (`sigemptyset`, `sigfillset`, `sigaddset`, `sigdelset`, `sigismember`, bitwise set combinations), signal disposition helpers (`signal`, `sigset`, `sighold`, `sigrelse`, `sigignore`, `siginterrupt`), process/group signaling (`raise`, `killpg`), waiting (`sigwait`, `sigpause`), and signal message printing (`psignal`, `psiginfo`).

## Interface
- `sig_emptyset.c:sigemptyset`, `sig_fillset.c:sigfillset`, `sig_addset.c:sigaddset`, `sig_delset.c:sigdelset`, `sig_ismember.c:sigismember`, `sig_isemptyset.c:sigisemptyset` - Initialize, modify, and query `sigset_t` bitmasks across `_SIGSET_NELEM` words.
- `sig_andset.c:sigandset`, `sig_orset.c:sigorset`, `sig_nandset.c:nxsig_nandset`, `sig_xorset.c:nxsig_xorset` - Bitwise AND, OR, NAND, and XOR operations across two `sigset_t` structures.
- `sig_signal.c:signal`, `sig_set.c:sigset`, `sig_hold.c:sighold`, `sig_relse.c:sigrelse`, `sig_ignore.c:sigignore`, `sig_interrupt.c:siginterrupt`, `sig_pause.c:sigpause` - Configure signal handlers (`sigaction`) and process signal masks (`sigprocmask`), or suspend until a signal arrives (`sigsuspend`).
- `sig_raise.c:raise`, `sig_killpg.c:killpg` - Send a signal to the calling thread/task (`_THREAD_KILL` / `kill`) or process group.
- `sig_wait.c:sigwait` - Synchronously waits for any signal in `set` via `sigtimedwait` and writes its number to `*sig`.
- `sig_altstack.c:sigaltstack` - Stub returning `-ENOSYS` (`errno = ENOSYS`) for alternate signal stack configuration.
- `sig_psignal.c:psignal`, `sig_psignal.c:psiginfo` - Prints a signal description string (`strsignal`) and optional prefix message to `stderr` or `syslog`.

## Invariants
- `sig_addset.c:sigaddset`, `sig_delset.c:sigdelset`, and `sig_ismember.c:sigismember` validate signal numbers with `GOOD_SIGNO(signo)`, returning `-1` with `errno = EINVAL` for out-of-range signals.
- `sig_wait.c:sigwait` asserts `DEBUGASSERT(set != NULL && sig != NULL)` and returns a positive `errno` value directly rather than `-1`.

## Side Effects
- `sig_signal.c:signal`, `sig_set.c:sigset`, `sig_hold.c:sighold`, `sig_relse.c:sigrelse`, `sig_ignore.c:sigignore`, and `sig_interrupt.c:siginterrupt` invoke kernel `sigaction` and/or `sigprocmask` system calls to mutate process signal handlers and blocked signal masks.
- `sig_raise.c:raise` and `sig_killpg.c:killpg` deliver signals to the current thread or target process group.
- `sig_psignal.c:psignal` writes formatted output to `stderr` (`fprintf`) or `syslog(LOG_INFO, ...)`.

## Verification
- Run: `make test`
