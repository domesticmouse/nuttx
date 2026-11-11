# User-Space Work Queue (`libs/libc/wqueue`)

## Overview
Implements the NuttX user-space work queue (`USRWORK`) subsystem (`CONFIG_LIBC_USRWORK`), providing delayed and immediate work scheduling (`work_queue`), work cancellation (`work_cancel`), and dynamic multi-threaded user work queue creation (`work_queue_create`) using POSIX threads (`pthread_t`) and semaphores (`sem_t`).

## Interface
- `wqueue.h:struct usr_wqueue_s`, `wqueue.h:struct usr_worker_s`, `wqueue.h:g_usrwork` - Internal user-space work queue control structure (holding `dq_queue_t q`, `sem_t lock`, `sem_t wake`, and `struct usr_worker_s worker[]`) and the default `USRWORK` queue instance.
- `work_usrthread.c:work_usrstart`, `work_usrthread.c:work_queue_create`, `work_usrthread.c:work_queue_free`, `work_usrthread.c:work_queue_priority`, `work_usrthread.c:work_queue_priority_wq` - Starts the default `USRWORK` worker thread (`CONFIG_LIBC_USRWORKPRIORITY`, `CONFIG_LIBC_USRWORKSTACKSIZE`), dynamically creates/destroys custom user work queues (`struct kwork_wqueue_s *`), and queries worker thread priority.
- `work_queue.c:work_queue`, `work_queue.c:work_queue_wq`, `work_queue.c:work_queue_next`, `work_queue.c:work_queue_next_wq` - Schedules a `struct work_s` item on `USRWORK` (or `handle`) to execute `worker(arg)` after `delay` system clock ticks, keeping the doubly-linked queue ordered by expiration tick (`qtime`).
- `work_cancel.c:work_cancel`, `work_cancel.c:work_cancel_wq`, `work_cancel.c:work_cancel_sync`, `work_cancel.c:work_cancel_sync_wq` - Removes a pending `struct work_s` item from a user work queue (optionally waiting via `sem_wait` if the work is currently executing on another thread in `work_cancel_sync_wq`).

## Invariants
- Access to `wqueue->q` is serialized by `wqueue->lock` (`nxsem_wait_uninterruptible` / `nxsem_post`), and entries in `wqueue->q` are maintained in non-decreasing `work->qtime` order so the head always represents the earliest deadline.
- In flat builds (`!CONFIG_BUILD_PROTECTED && !CONFIG_BUILD_KERNEL`), `work_queue` and `work_cancel` only handle `qid == USRWORK` when called from user-space; other queue IDs return `-EINVAL`.

## Side Effects
- Spawns and joins POSIX worker threads (`pthread_create`, `pthread_join`, `pthread_kill`), acquires/posts semaphores (`nxsem_wait_uninterruptible`, `nxsem_clockwait_uninterruptible`, `nxsem_post`), allocates/frees queue structures (`lib_zalloc`, `lib_free`), and invokes scheduled `worker_t` callbacks asynchronously.

## Verification
- Run: `make test`
