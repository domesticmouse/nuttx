# POSIX Semaphores (`libs/libc/semaphore`)

## Overview
Provides user-space POSIX unnamed and named semaphore initialization, destruction, acquisition (`wait`/`trywait`/`timedwait`/`clockwait`), release (`post`), and priority-inheritance/priority-ceiling protocol configuration, including fast-path atomic compare-and-exchange operations in flat builds (`CONFIG_BUILD_FLAT`).

## Interface
- `sem_init.c:sem_init`, `sem_init.c:nxsem_init` - Initializes an unnamed `sem_t` with an initial count and default protocol/maxvalue.
- `sem_destroy.c:sem_destroy` - Destroys an unnamed semaphore.
- `sem_open.c:sem_open`, `sem_close.c:sem_close`, `sem_unlink.c:sem_unlink` - Opens, closes, and unlinks named semaphores (`CONFIG_FS_NAMED_SEMAPHORES`).
- `sem_wait.c:sem_wait`, `sem_wait.c:nxsem_wait`, `sem_wait.c:nxsem_wait_uninterruptible`, `sem_wait.c:nxsem_clockwait_uninterruptible` - Decrements (locks) a semaphore, blocking until available or interrupted/canceled (`CONFIG_CANCELLATION_POINTS`).
- `sem_trywait.c:sem_trywait`, `sem_trywait.c:nxsem_trywait` - Non-blocking semaphore decrement returning `-EAGAIN` (or setting `errno = EAGAIN`) if unavailable.
- `sem_timedwait.c:sem_timedwait`, `sem_clockwait.c:sem_clockwait` - Decrements a semaphore with an absolute timeout on `CLOCK_REALTIME` or a caller-specified `clockid_t`.
- `sem_post.c:sem_post`, `sem_post.c:nxsem_post` - Increments (unlocks) a semaphore and wakes waiting threads if needed.
- `sem_getvalue.c:sem_getvalue`, `sem_getvalue.c:nxsem_get_value` - Reads the current semaphore counter into `*sval`.
- `sem_getprotocol.c:sem_getprotocol`, `sem_setprotocol.c:sem_setprotocol`, `sem_setprotocol.c:nxsem_set_protocol` - Gets or sets the semaphore protocol (`SEM_PRIO_NONE`, `SEM_PRIO_INHERIT`, `SEM_PRIO_PROTECT`, `SEM_TYPE_MUTEX`).
- `sem_getprioceiling.c:nxsem_getprioceiling`, `sem_setprioceiling.c:nxsem_setprioceiling`, `sem_setmaxvalue.c:nxsem_setmaxvalue` - Gets/sets priority ceiling (`CONFIG_PRIORITY_PROTECT`) and maximum allowed semaphore count (`CONFIG_CUSTOM_SEMAPHORE_MAXVALUE`).

## Invariants
- `sem_init.c:nxsem_init` requires `sem != NULL` and `0 <= value <= SEM_VALUE_MAX`, returning `-EINVAL` otherwise.
- `sem_wait.c:nxsem_wait` and `sem_trywait.c:nxsem_trywait` assert `DEBUGASSERT(!OSINIT_IDLELOOP() || !sched_idletask() || up_interrupt_context())` in flat builds so the idle task never blocks on a semaphore.
- Fast-path user-space atomic `atomic_cmpxchg` in `sem_wait.c`, `sem_trywait.c`, and `sem_post.c` is only used when `SEM_PRIO_INHERIT` and `SEM_PRIO_PROTECT` are not active on the semaphore.

## Side Effects
- Mutates `sem->semcount`, `sem->flags`, and `sem->maxvalue` (atomically or via kernel system calls `nxsem_*`) and sets thread `errno` on POSIX wrapper failure.
- `sem_wait.c:sem_wait`, `sem_timedwait.c:sem_timedwait`, and `sem_clockwait.c:sem_clockwait` act as POSIX cancellation points (`enter_cancellation_point`/`leave_cancellation_point`).

## Verification
- Run: `make test`
