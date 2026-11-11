# tls

## Overview
Manages per-thread Thread Local Storage (`struct tls_info_s`) stack frame allocation and duplication as well as per-group task info (`struct task_info_s`) initialization and teardown, including standard I/O stream lists, `pthread_atfork` handlers, dynamic module handles, and environment cleanup.

## Interface
- `tls.h:tls_info_size` - Returns the architecture-aligned size of `struct tls_info_s`.
- `tls.h:task_init_info` (`task_initinfo.c:task_init_info`) - Allocates and initializes a task group's `struct task_info_s` (`group->tg_info`), mutexes, and stdio stream list.
- `tls.h:task_uninit_info` (`task_uninitinfo.c:task_uninit_info`) - Releases a task group's `struct task_info_s`, registered `pthread_atfork` entries, `dlopen` module handles, environment variables, and stdio file buffers.
- `tls.h:tls_init_info` (`tls_initinfo.c:tls_init_info`) - Carves a `struct tls_info_s` frame from the bottom of a newly created thread's stack and links it to `tcb->group->tg_info`.
- `tls.h:tls_dup_info` (`tls_dupinfo.c:tls_dup_info`) - Carves a `struct tls_info_s` frame for a child thread and duplicates the parent thread's TLS data and cleanup stack.

## Invariants
- `tls_initinfo.c:tls_init_info` and `tls_dupinfo.c:tls_dup_info` require `up_stack_frame(tcb, tls_info_size())` to return the exact base of the allocated stack (`DEBUGASSERT(info == tcb->stack_alloc_ptr)`).
- Under `CONFIG_BUILD_KERNEL`, `task_uninitinfo.c:task_uninit_info` only traverses and frees user-allocated lists when `(group->tg_flags & GROUP_FLAG_PRIVILEGED) != 0`; unprivileged user-space allocations are reclaimed automatically when the address environment is destroyed.

## Side Effects
- Carves TLS frames from task stacks via `up_stack_frame` and initializes architecture TLS registers/pointers via `up_tls_initialize` in `tls_initinfo.c:tls_init_info` and `tls_dupinfo.c:tls_dup_info`.
- Allocates and frees group heap memory (`group_zalloc`, `group_free`), initializes and destroys recursive mutexes (`nxrmutex_init`, `nxrmutex_destroy`), and releases task environment strings (`env_release`) in `task_initinfo.c:task_init_info` and `task_uninitinfo.c:task_uninit_info`.

## Verification
- Run: `make test`
