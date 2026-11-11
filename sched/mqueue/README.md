# mqueue

## Overview
Implements POSIX named message queues (`struct mqueue_inode_s`) and System V IPC message queues (`struct msgq_s`), including preallocated and dynamic message buffer pools, prioritized message queuing, timed send/receive blocking, signal/thread event notification (`mq_notify`), and task termination recovery.

## Interface
- `mqueue.h:g_msgfree` / `mqueue.h:g_msgfreeirq` / `mqueue.h:g_msgfreelock` (`mq_initialize.c`) - Global free lists of preallocated POSIX message buffers (`CONFIG_PREALLOC_MQ_MSGS`, `CONFIG_PREALLOC_MQ_IRQ_MSGS`) and protecting spinlock.
- `mqueue.h:nxmq_initialize` (`mq_initialize.c:nxmq_initialize`) - Initializes the preallocated POSIX and System V message pools (`mq_initialize.c:g_msgpool`) at boot.
- `mqueue.h:nxmq_free_msg` (`mq_msgfree.c:nxmq_free_msg`) - Returns a POSIX message buffer (`MQ_ALLOC_FIXED`, `MQ_ALLOC_IRQ`) to its free list or frees it (`MQ_ALLOC_DYN`) via `kmm_free`.
- `mqueue.h:nxmq_wait_irq` (`mq_waitirq.c:nxmq_wait_irq`) - Interrupt/timeout handler that aborts a blocked task's `TSTATE_WAIT_MQNOTEMPTY` or `TSTATE_WAIT_MQNOTFULL` wait.
- `mqueue.h:nxmq_wait_receive` / `mqueue.h:nxmq_notify_receive` (`mq_rcvinternal.c`) - Internal blocking receive loop and post-receive `waitfornotfull` waiter wake-up.
- `mqueue.h:nxmq_wait_send` / `mqueue.h:nxmq_notify_send` (`mq_sndinternal.c`) - Internal blocking send loop, `SI_MESGQ` notification dispatch, and post-send `waitfornotempty` waiter wake-up.
- `mqueue.h:nxmq_recover` (`mq_recover.c:nxmq_recover`) - Decrements `nwaitnotempty` or `nwaitnotfull` when a blocked task is deleted or canceled.
- `mq_msgqalloc.c:nxmq_alloc_msgq` / `mq_msgqfree.c:nxmq_free_msgq` - Allocates and frees POSIX message queue inode structures (`struct mqueue_inode_s`) and drains queued messages.
- `mq_send.c:mq_send` / `mq_send.c:mq_timedsend` / `mq_send.c:nxmq_send` / `mq_send.c:nxmq_timedsend` / `mq_send.c:file_mq_send` / `mq_send.c:file_mq_timedsend` / `mq_send.c:file_mq_ticksend` - Sends a prioritized message to a POSIX message queue.
- `mq_receive.c:mq_receive` / `mq_receive.c:mq_timedreceive` / `mq_receive.c:nxmq_receive` / `mq_receive.c:nxmq_timedreceive` / `mq_receive.c:file_mq_receive` / `mq_receive.c:file_mq_timedreceive` / `mq_receive.c:file_mq_tickreceive` - Receives the oldest highest-priority message from a POSIX message queue.
- `mq_getattr.c:mq_getattr` / `mq_getattr.c:file_mq_getattr` / `mq_setattr.c:mq_setattr` / `mq_setattr.c:file_mq_setattr` - Queries and updates POSIX message queue attributes (`O_NONBLOCK`).
- `mq_notify.c:mq_notify` - Registers or detaches a one-shot `struct sigevent` notification for empty-to-non-empty queue transitions.
- `msg.h:g_msgfreelist` / `msg.h:g_msgpoolwait` (`msginternal.c`) - System V message buffer free list and pool exhaustion wait queue.
- `msg.h:nxmsg_alloc` / `msg.h:nxmsg_free` / `msg.h:nxmsg_wakeup_senders` / `msg.h:nxmsg_wakeup_receivers` / `msg.h:nxmsg_wakeup_pool` / `msg.h:nxmsg_lookup` / `msg.h:nxmsg_findkey` (`msginternal.c`) - Internal System V message queue table (`msginternal.c:g_msgqs`) management and waiter wake-up helpers.
- `msgget.c:msgget` / `msgsnd.c:msgsnd` / `msgrcv.c:msgrcv` / `msgctl.c:msgctl` - System V IPC message queue creation, send, typed receive, and control (`IPC_STAT`, `IPC_SET`, `IPC_RMID`) interfaces.

## Invariants
- POSIX message lists (`msgq->msglist`) are maintained in descending priority order (`prio <= MQ_PRIO_MAX`) with FIFO ordering within each priority level (`mq_send.c:nxmq_add_queue`).
- Interrupt handlers may never block on a full or empty queue (`up_interrupt_context()` returns `-EAGAIN` in `mq_send.c`, `mq_receive.c`, and `msgsnd.c`) and only allocate from `mqueue.h:g_msgfree` or `mqueue.h:g_msgfreeirq`.
- Only one task may register an `mq_notify.c:mq_notify` notification on a queue at a time (`msgq->ntpid`), and the registration is automatically cleared upon firing in `mq_sndinternal.c:nxmq_notify_send`.
- Removing a System V queue via `msgctl(IPC_RMID)` (`msginternal.c:nxmsg_free`) clears its `g_msgqs` slot before waking blocked tasks with `EIDRM`.

## Side Effects
- Allocates and frees message buffers and queue descriptors from static pools (`mq_initialize.c:g_msgpool`) or the kernel heap (`kmm_malloc`, `kmm_zalloc`, `kmm_realloc`, `kmm_free`).
- Blocks tasks in `TSTATE_WAIT_MQNOTEMPTY` or `TSTATE_WAIT_MQNOTFULL`, arms/cancels `rtcb->waitdog`, and switches CPU context via `up_switch_context`.
- Dispatches poll events (`nxmq_pollnotify` with `POLLIN`/`POLLOUT`), delivers `SI_MESGQ` signal notifications (`nxsig_notification`), and sets `errno` on failure.

## Verification
- Run: `make test`
