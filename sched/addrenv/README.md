# addrenv

## Overview
Manages process address environments (`struct addrenv_s`) for tasks and groups, including allocation, reference counting, context switching, fork duplication, temporary kernel selection/restoration, and kernel-build user-pointer access validation.

## Interface
- `addrenv.c:addrenv_switch` - Switches the active hardware address environment on the current CPU to match the target TCB (`tcb`).
- `addrenv.c:addrenv_allocate` - Allocates a zero-initialized `struct addrenv_s` with an initial reference count of 1.
- `addrenv.c:addrenv_attach` - Attaches a newly created `struct arch_addrenv_s` to a task before group initialization.
- `addrenv.c:addrenv_join` - Shares a parent task's address environment with a newly created child task.
- `addrenv.c:addrenv_fork` (`CONFIG_ARCH_HAVE_FORK`) - Duplicates a parent task's owned address environment and copies user-space memory regions into the child environment.
- `addrenv.c:addrenv_leave` - Detaches a task from its owned and active address environments upon task exit.
- `addrenv.c:addrenv_select` - Temporarily selects a target address environment on the calling task and CPU, saving the previous environment.
- `addrenv.c:addrenv_restore` - Restores a previously saved address environment after `addrenv.c:addrenv_select`.
- `addrenv.c:addrenv_take` - Increments the atomic reference count on `struct addrenv_s`.
- `addrenv.c:addrenv_give` - Decrements the atomic reference count on `struct addrenv_s` and returns the remaining count.
- `addrenv.c:addrenv_drop` - Releases a reference to `struct addrenv_s` and destroys the underlying architecture environment when the count reaches zero.
- `addrenv.c:uaccess_ok` (`CONFIG_BUILD_KERNEL`) - Validates that a user buffer range `[uaddr, uaddr + size)` lies entirely within user address space (`CONFIG_ARCH_TEXT_VBASE` to `ARCH_HEAP_VEND`).
- `addrenv.c:uaccess_check` (`CONFIG_BUILD_KERNEL`) - Checks whether a kernel thread is currently copying user memory via `TCB_FLAG_KERNEL_UACCESS`.
- `addrenv.c:uaccess_fault` (`CONFIG_BUILD_KERNEL`) - Terminates the calling task with `SIGSEGV` on an invalid user memory access.

## Invariants
- `addrenv.c:g_addrenv` per-CPU active address environment pointers are serialized by `addrenv.c:g_addrenv_lock` with local interrupts and preemption disabled (`spin_lock_irqsave_nopreempt`).
- `addrenv.c:addrenv_drop` must be invoked after releasing `addrenv.c:g_addrenv_lock` in `addrenv.c:addrenv_switch` to prevent deadlock with `LPWORK` critical sections.
- `addrenv.c:addrenv_fork` requires `ptcb->addrenv_own != NULL` (`DEBUGASSERT(oldenv != NULL)`).
- `addrenv.c:addrenv_select` must not be called from interrupt context.

## Side Effects
- Flushes D-Cache/invalidates I-Cache via `up_addrenv_coherent` and switches MMU page tables via `up_addrenv_select` in `addrenv.c:addrenv_switch`.
- Allocates and frees kernel heap memory (`kmm_zalloc`, `kmm_free`) and destroys architecture page tables (`up_addrenv_destroy`) directly or deferred on `LPWORK` (`addrenv.c:addrenv_destroy`) via `addrenv.c:addrenv_drop`.
- Terminates the current task via `_exit(SIGSEGV)` in `addrenv.c:uaccess_fault`.

## Verification
- Run: `make test`
