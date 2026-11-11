# Thread-Local and Task-Local Storage (`libs/libc/tls`)

## Overview
Implements thread-local storage (`struct tls_info_s`) and task-local storage (`struct task_info_s`) lookup, key allocation, per-thread/per-task value access, destructor invocation on thread/task exit, and thread cancellation cleanup handler stacks (`pthread_cleanup_push`/`pop`).

## Interface
- `tls_getinfo.c:tls_get_info` - Returns the current thread's `struct tls_info_s *` pointer (computed from the aligned stack pointer via `TLS_INFO(up_getsp())` when `CONFIG_TLS_ALIGNED` is set, or via `up_tls_info()`).
- `tls_destruct.c:tls_destruct` - Executes registered per-thread TLS destructors (`tl_dtor`) in reverse index order on thread exit (`CONFIG_TLS_NELEM`).
- `tls_cleanup.c:tls_cleanup_push`, `tls_cleanup.c:tls_cleanup_pop`, `tls_cleanup.c:tls_cleanup_popall` - Push, pop, and drain cancellation cleanup callbacks (`tls->tl_stack`, `tls->tl_tos`) when `CONFIG_TLS_NCLEANUP > 0`.
- `task_getinfo.c:task_get_info` - Returns the current task group's `struct task_info_s *` pointer (`tls_get_info()->tl_task`).
- `task_tls.c:task_tls_get_value`, `task_tls.c:task_tls_set_value` - Get and set task-wide TLS slot values (`ta_telem[tlsindex]`) under `CONFIG_TLS_TASK_NELEM`.
- `task_tls_destruct.c:task_tls_alloc`, `task_tls_destruct.c:task_tls_destruct` - Allocate a global task TLS key with optional destructor (`tls_dtor_t`) and run all registered task TLS destructors on task exit.

## Invariants
- `tls_cleanup.c:tls_cleanup_push` asserts `DEBUGASSERT(tls != NULL)` and `DEBUGASSERT(tls->tl_tos < CONFIG_TLS_NCLEANUP)`.
- `tls_destruct.c:tls_destruct` and `task_tls_destruct.c:task_tls_destruct` clear the slot value (`tl_elem[elem] = 0` / `ta_telem[elem] = 0`) before invoking the destructor callback.

## Side Effects
- Mutates thread-local (`struct tls_info_s`) and task-group (`struct task_info_s`) storage arrays, cleanup stacks, and global destructor tables (`g_tls_dtor`, `g_tlsset`), and invokes user-registered destructor and cleanup callbacks.

## Verification
- Run: `make test`
