# wqueue

## Overview
Implements kernel-mode high-priority (`HPWORK`), low-priority (`LPWORK`), and dynamically created work queues (`CONFIG_SCHED_WORKQUEUE`), supporting delayed/periodic work scheduling, synchronous and asynchronous cancellation, priority inheritance, and work queue event notifications.

## Interface
- `wqueue.h:g_hpwork` (`kwork_thread.c:g_hpwork`, `CONFIG_SCHED_HPWORK`) - Global high-priority kernel work queue descriptor (`struct hp_wqueue_s`).
- `wqueue.h:g_lpwork` (`kwork_thread.c:g_lpwork`, `CONFIG_SCHED_LPWORK`) - Global low-priority kernel work queue descriptor (`struct lp_wqueue_s`).
- `wqueue.h:work_qid2wq` - Maps a queue ID (`HPWORK`, `LPWORK`) to its `struct kwork_wqueue_s *` instance.
- `wqueue.h:work_insert_pending` / `wqueue.h:work_remove` - Inserts or removes a `struct work_s` item in `wqueue->pending` ordered by expiration tick `work->qtime`.
- `wqueue.h:work_timer_expired` (`kwork_thread.c:work_timer_expired`) - Watchdog callback that dispatches expired work items and wakes worker threads.
- `wqueue.h:work_timer_reset` - Reprograms or cancels `wqueue->timer` to match the head of `wqueue->pending`.
- `wqueue.h:work_start_highpri` (`kwork_thread.c:work_start_highpri`, `CONFIG_SCHED_HPWORK`) - Initializes and spawns the `HPWORK` kernel worker thread pool.
- `wqueue.h:work_start_lowpri` (`kwork_thread.c:work_start_lowpri`, `CONFIG_SCHED_LPWORK`) - Initializes and spawns the `LPWORK` kernel worker thread pool.
- `kwork_queue.c:work_queue` / `kwork_queue.c:work_queue_wq` - Schedules a work item to run after `delay` ticks from the current system tick.
- `kwork_queue.c:work_queue_next` / `kwork_queue.c:work_queue_next_wq` - Re-schedules a periodic work item relative to its previous expiration tick `work->qtime`.
- `kwork_cancel.c:work_cancel` / `kwork_cancel.c:work_cancel_wq` - Asynchronously cancels a queued work item.
- `kwork_cancel.c:work_cancel_sync` / `kwork_cancel.c:work_cancel_sync_wq` - Cancels a work item and blocks until any in-flight execution on a worker thread completes.
- `kwork_thread.c:work_queue_create` / `kwork_thread.c:work_queue_free` - Dynamically creates and destroys custom kernel work queues and their worker threads.
- `kwork_thread.c:work_queue_dispatch` / `kwork_thread.c:work_queue_in_queue` / `kwork_thread.c:work_queue_priority` / `kwork_thread.c:work_queue_priority_wq` / `kwork_thread.c:work_queue_setpriority` / `kwork_thread.c:work_queue_setpriority_wq` - Queries and controls work queue execution state and thread priorities.
- `kwork_inherit.c:lpwork_boostpriority` / `kwork_inherit.c:lpwork_restorepriority` (`CONFIG_PRIORITY_INHERITANCE`) - Boosts and restores `LPWORK` worker thread priorities to prevent priority inversion.
- `kwork_notifier.c:work_notifier_setup` / `kwork_notifier.c:work_notifier_teardown` / `kwork_notifier.c:work_notifier_signal` (`CONFIG_WQUEUE_NOTIFIER`) - Registers, removes, and triggers event notification callbacks on work queues.

## Invariants
- `wqueue->pending` is maintained in ascending order of `work->qtime` (`clock_compare`) under `wqueue->lock` (`spin_lock_irqsave` / `spin_unlock_irqrestore`).
- `wq_get_worker(wq)` relies on `struct kworker_s` elements being allocated contiguously immediately following `struct kwork_wqueue_s`.
- `kwork_thread.c:work_queue_free` rejects static queues (`qid == HPWORK || qid == LPWORK`) with `-EINVAL` and rejects self-destruction from one of the queue's own worker threads with `-EDEADLK`.
- `kwork_cancel.c:work_qcancel` skips waiting on `worker->wait` if the calling thread is the worker currently executing `work`.

## Side Effects
- Spawns and terminates kernel worker threads (`kthread_create_with_stack`, `nxsem_post` with `wqueue->exit = true`) in `kwork_thread.c:work_queue_create` and `kwork_thread.c:work_queue_free`.
- Arms and cancels watchdog timers (`wd_start_abstick`, `wd_cancel`), posts and waits on semaphores (`wqueue->sem`, `worker->wait`), and adjusts worker thread priorities (`nxsched_set_priority`).
- Allocates and frees work queue and notifier structures on the kernel heap (`kmm_zalloc`, `kmm_malloc`, `kmm_free`).

## Verification
- Run: `make test`
