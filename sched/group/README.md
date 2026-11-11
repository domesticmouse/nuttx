# group

## Overview
Manages task groups (`struct task_group_s`), which represent the shared process-level container across a main task and its pthreads, including member lists, child exit status tracking (`struct child_status_s`), user/group credentials (`uid`, `gid`, supplementary groups), resource limits (`RLIMIT_STACK`, `RLIMIT_NOFILE`), file descriptor inheritance, group-wide signal delivery, and privilege-aware group heap allocation.

## Interface
- `group.h:task_initialize` (`group_childstatus.c:task_initialize`, `CONFIG_SCHED_CHILD_STATUS`) - Initializes the preallocated `struct child_status_s` pool (`group_childstatus.c:g_child_pool`).
- `group.h:group_allocate` / `group.h:group_initialize` (`group_create.c`) - Allocates and initializes a task group container (or binds `group_create.c:g_kthread_group` for kernel threads) and registers the main task as its initial member.
- `group.h:group_bind` / `group.h:group_join` (`group_join.c`, `!CONFIG_DISABLE_PTHREAD`) - Binds a newly created pthread TCB to its parent's task group and adds it to `group->tg_members`.
- `group.h:group_leave` / `group.h:group_drop` (`group_leave.c`) - Removes an exiting thread from `group->tg_members`, releases group resources (`group_leave.c:group_release`) when the last non-kernel member exits, and frees the `struct task_group_s` container once all `waitpid` waiters finish.
- `group.h:group_add_waiter` / `group.h:group_del_waiter` (`group_waiter.c`) - Tracks active `waitpid` waiters (`group->tg_nwaiters`) to defer freeing a deleted group.
- `group.h:group_foreachchild` (`group_foreachchild.c:group_foreachchild`, `HAVE_GROUP_MEMBERS`) - Iterates over all member threads in `group->tg_members`.
- `group.h:group_kill_children` (`group_killchildren.c:group_kill_children`, `HAVE_GROUP_MEMBERS`) - Terminates all sibling threads in the group except the calling thread during task exit or restart.
- `group.h:group_suspend_children` (`group_suspendchildren.c:group_suspend_children`) / `group.h:group_continue` (`group_continue.c:group_continue`) - Suspends or resumes all member threads in a task group (`SIGSTOP`/`SIGTSTP`/`SIGCONT`).
- `group.h:group_signal` (`group_signal.c:group_signal`) - Dispatches a process-directed signal to a single waiting or unmasked thread within the task group.
- `group.h:group_alloc_child` / `group.h:group_free_child` / `group.h:group_add_child` / `group.h:group_exit_child` / `group.h:group_find_child` / `group.h:group_remove_child` / `group.h:group_remove_children` / `group.h:group_has_child` (`group_childstatus.c`) - Manages parent/child exit status structures (`group->tg_children`).
- `group.h:group_setupidlefiles` (`group_setupidlefiles.c:group_setupidlefiles`) / `group.h:group_setuptaskfiles` (`group_setuptaskfiles.c:group_setuptaskfiles`) - Opens initial `stdin`/`stdout`/`stderr` descriptors on the idle task and clones or applies spawn file actions to child task file descriptor lists (`group->tg_fdlist`).
- `group_malloc.c:group_malloc` / `group_zalloc.c:group_zalloc` / `group_realloc.c:group_realloc` / `group_free.c:group_free` (`CONFIG_MM_KERNEL_HEAP`) - Allocates and frees memory from either the kernel heap (`kmm_*`) or user heap (`kumm_*`) based on `GROUP_FLAG_PRIVILEGED`.
- `group.h:group_init_rlimit` / `group_rlimit.c:getrlimit` / `group_rlimit.c:setrlimit` - Initializes, queries, and updates per-group resource limits (`RLIMIT_STACK`, `RLIMIT_NOFILE`).
- `group_getuid.c:getuid` / `group_geteuid.c:geteuid` / `group_getgid.c:getgid` / `group_getegid.c:getegid` / `group_getresuid.c:getresuid` / `group_getresgid.c:getresgid` / `group_getgroups.c:getgroups` / `group_issetugid.c:issetugid` / `group_setuid.c:setuid` / `group_seteuid.c:seteuid` / `group_setreuid.c:setreuid` / `group_setresuid.c:setresuid` / `group_setgid.c:setgid` / `group_setegid.c:setegid` / `group_setregid.c:setregid` / `group_setresgid.c:setresgid` / `group_setgroups.c:setgroups` - Queries and modifies task group real, effective, saved, and supplementary user/group IDs.
- `group_umask.c:umask` / `group_umask.c:getumask` - Sets and reads the task group file mode creation mask (`group->tg_umask`).

## Invariants
- All kernel threads (`TCB_FLAG_TTYPE_KERNEL`) share the single static `group_create.c:g_kthread_group`, which must never be passed to `group_leave.c:group_release` (`bool release = !(tcb->flags & TCB_FLAG_TTYPE_KERNEL)`).
- `group->tg_members` and `group->tg_children` list mutations are serialized by `group->tg_lock` (`spin_lock_irqsave`), and `group_childstatus.c:g_child_pool` is serialized by `group_childstatus.c:g_child_pool_lock`.
- Non-root task groups (`group->tg_euid != 0` / `group->tg_egid != 0`) may only transition UIDs/GIDs to existing real, effective, or saved IDs, cannot call `group_setgroups.c:setgroups` (`EPERM`), and cannot raise hard resource limits (`rlp->rlim_max > limit->rlim_max` in `group_rlimit.c:setrlimit`).
- `group_signal.c:group_signal` delivers a process-directed signal to at most one waiting or unblocked member thread in the group (except `SIGCHLD`, which wakes all waiting threads).

## Side Effects
- Allocates and frees `struct task_group_s`, `struct child_status_s`, chroot paths (`fs_heap_strdup`, `fs_heap_free`), and group heap objects (`kmm_*`, `kumm_*`).
- Closes open file descriptors (`fdlist_free`), unloads shared libraries and binaries (`libelf_removeall`, `binfmt_exit`), destroys memory mappings (`mm_map_destroy`), releases pending signals (`nxsig_release`) and pthreads (`pthread_release`), and destroys `group->tg_mutex` when the last member leaves in `group_leave.c:group_release`.
- Opens `/dev/console` or `/dev/null` onto file descriptors `0`, `1`, and `2` in `group_setupidlefiles.c:group_setupidlefiles`, and copies file tables (`fdlist_copy`, `spawn_file_actions`) in `group_setuptaskfiles.c:group_setuptaskfiles`.

## Verification
- Run: `make test`
