# VFS Inode Tree and File Descriptor Table Management

## Overview
Manages the in-memory VFS pseudo-filesystem inode hierarchy (search, reservation, reference counting, permissions, and path resolution) as well as per-task-group file descriptor tables (`struct fdlist`) and open file instances (`struct file`).

## Interface
- `inode.h:g_root_inode`, `inode.h:inode_initialize`, `inode.h:inode_root_reserve` - Root pseudo-filesystem inode and subsystem initialization.
- `inode.h:inode_lock`, `inode.h:inode_unlock`, `inode.h:inode_rlock`, `inode.h:inode_runlock` - Exclusive write and shared read locking for the in-memory inode tree.
- `inode.h:inode_search_setup`, `inode.h:inode_search`, `inode.h:inode_search_release`, `inode.h:inode_find`, `inode.h:inode_nextname`, `inode.h:inode_getpath` - Path canonicalization, symlink resolution, and inode lookup.
- `inode.h:inode_reserve`, `inode.h:inode_remove`, `inode.h:inode_free`, `inode.h:inode_addref`, `inode.h:inode_release`, `inode.h:foreach_inode` - Inode allocation, unlinking, reference counting, and tree traversal.
- `inode.h:inode_stat`, `inode.h:inode_chstat`, `inode.h:inode_checkperm`, `inode.h:inode_checkpathperm`, `inode.h:inode_checkopenperm` - Pseudo-filesystem metadata and access permission checks.
- `fs_files.c:file_allocate`, `fs_files.c:file_deallocate`, `fs_files.c:file_allocate_from_inode`, `fs_files.c:file_get2`, `fs_files.c:file_ref`, `fs_files.c:file_put`, `fs_files.c:sync` - Open `struct file` lifecycle, reference counting, and global filesystem sync.
- `fs_files.c:fdlist_copy`, `fs_files.c:fdlist_dup2`, `fs_files.c:fdlist_close` - Per-process file descriptor table cloning, duplication, and closure.

## Invariants
- Callers of `inode.h:inode_search`, `inode.h:inode_reserve`, and `inode.h:inode_remove` must hold the inode tree lock (`inode.h:inode_lock` or `inode.h:inode_rlock`).
- `fs_files.c:fdlist_extend` must never call `fs_heap_free` or sleep while holding the spinlock `list->fl_lock`.
- An unlinked inode or closed `struct file` is freed only when its atomic reference count (`i_crefs` or `f_refs`) decrements to zero (`inode.h:inode_release`, `fs_files.c:file_put`).

## Side Effects
- Dynamically expands per-task-group file descriptor block arrays (`fs_files.c:fdlist_extend`) using `fs_heap_malloc`/`fs_heap_zalloc`.
- Closes underlying VFS files and releases inode references when the last reference is dropped (`fs_files.c:file_put`).
- Iterates across all scheduled tasks to flush open file descriptors during `fs_files.c:sync`.

## Verification
- Run: `make test`
