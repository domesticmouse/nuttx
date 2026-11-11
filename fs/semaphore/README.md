# POSIX Named Semaphore VFS Integration (`fs/semaphore`)

## Overview
Implements the VFS pseudo-filesystem backing (`CONFIG_FS_NAMED_SEMAPHORES_VFS_PATH`) for POSIX named semaphores (`sem_open`, `sem_close`, `sem_unlink`), binding `struct nsem_inode_s` instances directly to VFS inodes.

## Interface
- `sem_open.c:nxsem_open` - Opens an existing named semaphore or creates a new named semaphore (`O_CREAT`, `O_EXCL`) under `CONFIG_FS_NAMED_SEMAPHORES_VFS_PATH` and returns a pointer to its `sem_t`.
- `sem_close.c:nxsem_close` - Decrements the reference count on a named semaphore's backing inode and destroys/frees the semaphore (`nxsem_destroy`, `inode_free`) if it was previously unlinked and has no remaining references.
- `sem_unlink.c:nxsem_unlink` - Removes a named semaphore's inode from the VFS namespace (`inode_remove`) and defers destruction until the last open reference is closed via `nxsem_close`.
- `semaphore.h:MAX_SEMPATH` - Maximum path buffer size (`64` bytes) for a named semaphore path in the VFS namespace.

## Invariants
- `sem_open.c:nxsem_open` requires the initial semaphore `value` (when `O_CREAT` is set) to be `<= SEM_VALUE_MAX`, returning `-EINVAL` otherwise.
- `sem_close.c:nxsem_close` asserts (`DEBUGASSERT`) that `sem` is non-NULL, casts to `struct nsem_inode_s *`, and when freeing an unlinked inode asserts `inode->i_peer == NULL`.
- `sem_unlink.c:nxsem_unlink` refuses to unlink an inode that has child inodes (`inode->i_child != NULL`), returning `-ENOTEMPTY`.

## Side Effects
- `sem_open.c:nxsem_open` allocates `struct nsem_inode_s` via `group_malloc`, acquires the VFS inode lock (`inode_lock`), reserves an inode (`inode_reserve`), sets `INODE_SET_NAMEDSEM`, and initializes the semaphore (`nxsem_init`).
- `sem_close.c:nxsem_close` atomically decrements `inode->i_crefs`, destroys the underlying semaphore (`nxsem_destroy`), frees group memory (`group_free`), notifies inotify watchers (`notify_close2`), and frees the inode (`inode_free`).

## Verification
- Run: `make test`
