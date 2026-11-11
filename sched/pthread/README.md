# pthread

## Overview
Implements kernel-side POSIX thread (`pthread`) management, including thread creation and stack/TLS setup, join and detach coordination (`group->tg_joinqueue`), thread cancellation and exit hooks, robust mutex inconsistency recovery, scheduling parameter and SMP affinity control, and thread-directed signal masking and queuing.

## Interface
- `pthread_create.c:g_default_pthread_attr` - Default `pthread_attr_t` initializer (`PTHREAD_ATTR_INITIALIZER`).
- `pthread_create.c:nx_pthread_create` - Allocates and initializes a `TCB_FLAG_TTYPE_PTHREAD` TCB, joins the parent task group and address environment, allocates or attaches a thread stack and TLS frame, configures scheduling policy (`SCHED_FIFO`, `SCHED_RR`, `SCHED_SPORADIC`), and activates the thread.
- `pthread_exit.c:nx_pthread_exit` - Masks signals, completes pending join handshakes (`pthread_completejoin.c:pthread_completejoin`), runs exit hooks (`nxtask_exithook`), and terminates the calling pthread via `up_exit`.
- `pthread_join.c:pthread_join` - Blocks the caller on `rtcb->join_sem` until a target joinable thread in the same task group terminates and retrieves its `exit_value`.
- `pthread_detach.c:pthread_detach` - Marks a running pthread as detached (`TCB_FLAG_DETACHED`) or frees its retained `struct task_join_s` record if already exited.
- `pthread_cancel.c:pthread_cancel` - Requests deferred or asynchronous cancellation of a target pthread (`PTHREAD_CANCELED`).
- `pthread.h:pthread_completejoin` / `pthread.h:pthread_destroyjoin` (`pthread_completejoin.c`) - Wakes waiting joiners on `tcb->join_queue` or records `exit_value` in `group->tg_joinqueue`, and destroys consumed `struct task_join_s` records.
- `pthread.h:pthread_findjoininfo` (`pthread_findjoininfo.c:pthread_findjoininfo`) - Finds or allocates a retained `struct task_join_s` entry on `group->tg_joinqueue`.
- `pthread.h:pthread_release` (`pthread_release.c:pthread_release`) - Frees all remaining `struct task_join_s` entries in `group->tg_joinqueue` when a task group exits.
- `pthread.h:pthread_mutex_inconsistent` (`pthread_mutexinconsistent.c:pthread_mutex_inconsistent`, `!CONFIG_PTHREAD_MUTEX_UNSAFE`) - Marks robust user mutexes listed on `tls->tl_mhead` as `_PTHREAD_MFLAGS_INCONSISTENT` and wakes waiters via `nxmutex_reset`/`nxrmutex_reset`.
- `pthread_getschedparam.c:pthread_getschedparam` / `pthread_setschedparam.c:pthread_setschedparam` / `pthread_setschedprio.c:pthread_setschedprio` - Queries and updates a pthread's scheduling policy and priority.
- `pthread_getaffinity.c:pthread_getaffinity_np` / `pthread_setaffinity.c:pthread_setaffinity_np` (`CONFIG_SMP`) - Queries and updates a pthread's CPU affinity mask.
- `pthread_sigmask.c:pthread_sigmask` - Modifies the calling thread's signal mask (`SIG_BLOCK`, `SIG_UNBLOCK`, `SIG_SETMASK`), stripping `SIGKILL` and `SIGSTOP`.
- `pthread_sigqueue.c:pthread_sigqueue` - Queues a real-time signal (`SI_QUEUE`) with a `union sigval` payload to a specific thread (`nxsig_dispatch`).

## Invariants
- `pthread_join.c:pthread_join` and `pthread_detach.c:pthread_detach` require the target thread to belong to the caller's task group (`tcb->group == rtcb->group`), not be detached (`(tcb->flags & TCB_FLAG_DETACHED) == 0`), and not be the calling thread itself (`tcb != rtcb`, returning `EDEADLK`).
- All accesses to `group->tg_joinqueue` and `tcb->join_queue` are serialized by the task group's recursive mutex `group->tg_mutex`.
- `pthread_cancel.c:pthread_cancel`, `pthread_setschedparam.c:pthread_setschedparam`, `pthread_setschedprio.c:pthread_setschedprio`, and `pthread_setaffinity.c:pthread_setaffinity_np` enforce same-group control permissions via `nxsched_may_control` (`EPERM`) and reject `IDLE_PROCESS_ID` (`ESRCH`).
- In kernel/protected builds (`!CONFIG_BUILD_FLAT`), `pthread_mutexinconsistent.c:pthread_mutex_accessible` validates user virtual addresses and backing page mappings (`up_addrenv_find_page` / `umm_heapmember`) before dereferencing `tls->tl_mhead` so an exiting faulted thread cannot fault again.

## Side Effects
- Allocates and frees TCBs (`TCB_FLAG_FREE_TCB`), thread stacks (`up_create_stack`, `up_use_stack`, `up_addrenv_kstackalloc`), and join structures (`kmm_zalloc`, `kmm_free`).
- Joins and leaves task groups and address environments (`group_bind`, `group_join`, `addrenv_join`), pops TLS cleanup handlers (`tls_cleanup_popall`), and activates/terminates threads (`nxtask_activate`, `nxtask_terminate`, `up_exit`).
- Blocks and wakes joining threads via `rtcb->join_sem` (`nxsem_wait_uninterruptible`, `nxsem_post`) and dispatches thread-targeted signals (`nxsig_dispatch`, `nxsig_procmask`).

## Verification
- Run: `make test`
