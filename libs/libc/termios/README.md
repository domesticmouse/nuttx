# Terminal I/O Control (`libs/libc/termios`)

## Overview
Implements POSIX `<termios.h>` terminal control, line discipline configuration, baud rate accessors, raw mode setup, and terminal device query functions backed by `ioctl` operations.

## Interface
- `lib_tcgetattr.c:tcgetattr`, `lib_tcsetattr.c:tcsetattr` - Get (`TCGETS`) and set (`TCSETS`) `struct termios` attributes for terminal descriptor `fd`.
- `lib_cfmakeraw.c:cfmakeraw` - Configures a `struct termios` structure for raw (non-canonical, un-echoed, 8-bit, no-parity) terminal I/O.
- `lib_cfspeed.c:cfsetspeed`, `lib_cfspeed.c:cfgetspeed`, `lib_cfspeed.c:cfsetispeed`, `lib_cfspeed.c:cfsetospeed`, `lib_cfspeed.c:cfgetispeed`, `lib_cfspeed.c:cfgetospeed` - Get and set terminal baud rates in `termiosp->c_speed`, translating between symbolic `B*` constants (`CBAUD`, `BOTHER`) and numeric baud values.
- `lib_tcdrain.c:tcdrain`, `lib_tcflow.c:tcflow`, `lib_tcflush.c:tcflush`, `lib_tcsendbreak.c:tcsendbreak` - Drain output (`TCDRAIN`, cancellation point), control XON/XOFF flow (`TCXONC`), flush input/output queues (`TCFLSH`), and transmit break conditions (`TCSBRK`/`TCSBRKP`).
- `lib_tcgetpgrp.c:tcgetpgrp`, `lib_tcsetpgrp.c:tcsetpgrp`, `lib_tcgetsid.c:tcgetsid` - Query or set the foreground process group ID (`TIOCGPGRP`, `TIOCSPGRP`) or session leader ID (`TIOCGSID`) of a controlling terminal.
- `lib_isatty.c:isatty`, `lib_ttyname.c:ttyname`, `lib_ttynamer.c:ttyname_r` - Test whether `fd` refers to a terminal (`TCGETS`) and retrieve its device path (`FIOC_FILEPATH`).

## Invariants
- `lib_cfmakeraw.c:cfmakeraw` and `lib_cfspeed.c:cfsetspeed` / `lib_cfspeed.c:cfgetspeed` assert `DEBUGASSERT(termiosp)`.
- `lib_tcgetattr.c:tcgetattr` and `lib_tcsetattr.c:tcsetattr` return `-1` with `errno = ENOTTY` when `fd` is not a terminal device (`errno == ENOTSUP` translated to `ENOTTY`).

## Side Effects
- Performs terminal driver `ioctl` calls (`TCGETS`, `TCSETS`, `TCDRAIN`, `TCXONC`, `TCFLSH`, `TCSBRK`, `TIOCGPGRP`, `TIOCSPGRP`, `TIOCGSID`, `FIOC_FILEPATH`) and updates `errno` on failure.
- `lib_ttyname.c:ttyname` writes to a static `NAME_MAX`-sized path buffer.

## Verification
- Run: `make test`
