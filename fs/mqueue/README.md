# POSIX Message Queue VFS Integration (`fs/mqueue`)

## Overview
Provides the VFS pseudo-filesystem interface (`CONFIG_FS_MQUEUE_VFS_PATH`) for named POSIX message queues, allowing message queues to be opened, closed, and unlinked as VFS inodes backed by file descriptors or kernel file structures.

## Interface
- `mq_open.c:mq_open` - Standard POSIX function to open or create a named message queue and return a process file descriptor (`mqd_t`).
- `mq_open.c:nxmq_open` - Internal NuttX function to open or create a named message queue without modifying `errno`.
- `mq_open.c:file_mq_open` - Kernel-internal function to open or create a named message queue using a detached `struct file` instance (`file_vopen`).
- `mq_close.c:mq_close` - Closes a message queue descriptor (`mqd_t`) via `close`.
- `mq_close.c:nxmq_close` - Closes a message queue descriptor (`mqd_t`) via `nx_close` without modifying `errno`.
- `mq_close.c:file_mq_close` - Closes a detached `struct file` message queue handle via `file_close`.
- `mq_unlink.c:mq_unlink` - Standard POSIX function to remove a named message queue from the VFS namespace.
- `mq_unlink.c:nxmq_unlink` - Internal function to remove a named message queue without modifying `errno`.
- `mq_unlink.c:file_mq_unlink` - Alias/wrapper for `nxmq_unlink` for kernel-level message queue unlinking.
- `mqueue.h:MAX_MQUEUE_PATH` - Maximum path buffer length combining `CONFIG_FS_MQUEUE_VFS_PATH` and `NAME_MAX`.

## Invariants
- `mq_open.c:mq_inode_open` and `mq_unlink.c:nxmq_unlink` skip leading `/` characters in `mq_name` and prepend `CONFIG_FS_MQUEUE_VFS_PATH "/"` using `snprintf`.
- Creating a new message queue (`O_CREAT`) requires validated attributes (`mq_attr->mq_maxmsg > 0` and `mq_attr->mq_msgsize > 0` up to `USHRT_MAX`), returning `-EINVAL` on invalid parameters.

## Side Effects
- `mq_open.c:mq_inode_open` acquires the VFS inode lock (`inode_lock`), reserves and populates a message queue inode (`inode_reserve`, `INODE_SET_MQUEUE`), allocates the underlying `struct mqueue_inode_s` (`nxmq_alloc_msgq`), and binds `g_mq_fileops`.
- `mq_unlink.c:nxmq_unlink` acquires `inode_lock()`, detaches the inode via `inode_remove` or marks it unlinked (`inode_release`), decrements the reference count, and frees the message queue via `nxmq_free_msgq` once no open references remain.

## Verification
- Run: `make test`
