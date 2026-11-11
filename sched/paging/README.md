# paging

## Overview
Implements legacy on-demand virtual memory page fault handling (`CONFIG_LEGACY_PAGING`) and the kernel page-fill worker thread (`pgfill`) that allocates physical pages and loads page contents from backing storage.

## Interface
- `paging.h:SIGPAGING` - Signal number (`SIGWORK`) used to wake the page-fill worker thread.
- `paging.h:g_pgworker` (`pg_worker.c:g_pgworker`) - Process ID (`pid_t`) of the `pgfill` kernel worker thread.
- `paging.h:g_pftcb` (`pg_worker.c:g_pftcb`) - Pointer to the TCB currently undergoing a page fill.
- `paging.h:pg_worker` (`pg_worker.c:pg_worker`) - Main entry point for the `pgfill` kernel thread.
- `pg_miss.c:pg_miss` - Page fault handler called from architecture exception code to block the faulting task and signal `pg_worker.c:g_pgworker`.

## Invariants
- Neither the idle task nor `pg_worker.c:g_pgworker` may cause a page fault (`DEBUGASSERT(g_pgworker != ftcb->pid)` and `DEBUGASSERT(!is_idle_task(ftcb))` in `pg_miss.c:pg_miss`).
- All interrupt/exception handlers, the idle thread, and `pg_worker.c:pg_worker` must reside in locked memory so they never fault.
- `pg_worker.c:pg_worker` executes with local interrupts disabled (`up_irq_save`) except while sleeping in `nxsched_usleep`.

## Side Effects
- Moves the faulting task from `g_readytorun` to `g_waitingforfill` in state `TSTATE_WAIT_PAGEFILL`, boosts `pg_worker.c:g_pgworker` priority via `nxsched_set_priority` (`CONFIG_PAGING_DEFPRIO`), switches CPU context via `up_switch_context`, and signals `SIGPAGING` via `nxsig_kill` in `pg_miss.c:pg_miss`.
- Allocates physical pages via `up_allocpage`, initiates synchronous or asynchronous page fills via `up_fillpage`, arms fill timeout watchdog `pg_worker.c:g_pgwdog` (`CONFIG_PAGING_TIMEOUT_TICKS`), unblocks completed tasks onto `g_readytorun`, and panics (`PANIC()`) on unrecoverable page allocation/fill failures in `pg_worker.c:pg_startfill` and `pg_worker.c:pg_callback`.

## Verification
- Run: `make test`
