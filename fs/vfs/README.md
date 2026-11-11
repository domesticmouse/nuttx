# Virtual File System (VFS) Core (`fs/vfs`)

## Overview
Implements the core POSIX Virtual File System (VFS) syscall and kernel file-object (`struct file`) dispatch layer, including `open`, `close`, `read`/`readv`, `write`/`writev`, `lseek`, `ioctl`, `fcntl`, `dup`/`dup2`/`dup3`, `stat`/`fstat`/`chstat`, directory traversal (`opendir`/`readdir`), I/O multiplexing (`poll`, `select`, `epoll`), POSIX record locking (`file_getlk`, `file_setlk`), filesystem event notification (`inotify`), and special file descriptors (`eventfd`, `timerfd`, `signalfd`, `pseudofile`).

## Interface
- `fs_open.c:open`, `fs_open.c:nx_open`, `fs_open.c:file_open` - Opens or creates a VFS node by path, enforcing permission checks (`inode_checkpathperm`, `inode_checkopenperm`), block character proxies (`block_proxy`), and mountpoint dispatch.
- `fs_close.c:close`, `fs_close.c:nx_close`, `fs_close.c:file_close` - Closes a file descriptor or detached `struct file`, releasing POSIX file locks (`file_closelk`) and decrementing inode/file references.
- `fs_read.c:read`, `fs_read.c:readv`, `fs_read.c:nx_read`, `fs_read.c:nx_readv`, `fs_read.c:file_read`, `fs_read.c:file_readv`, `fs_pread.c:pread`, `fs_pread.c:file_pread` - Reads data from an open file or driver into caller buffers or `struct iovec` vectors.
- `fs_write.c:write`, `fs_write.c:writev`, `fs_write.c:nx_write`, `fs_write.c:nx_writev`, `fs_write.c:file_write`, `fs_write.c:file_writev`, `fs_pwrite.c:pwrite`, `fs_pwrite.c:file_pwrite` - Writes data from caller buffers or `struct iovec` vectors to an open file or driver.
- `fs_ioctl.c:ioctl`, `fs_ioctl.c:nx_ioctl`, `fs_ioctl.c:file_ioctl` - Dispatches device/filesystem control commands and handles generic VFS commands (`FIONBIO`, `FIOCLEX`, `FIONCLEX`, `FIOC_FILEPATH`, `FIOC_GETLK`, `FIOC_SETLK`, `FIOC_SETLKW`, `BIOC_BLKSSZGET`, `BIOC_BLKGETSIZE`).
- `fs_lseek.c:lseek`, `fs_lseek.c:nx_seek`, `fs_lseek.c:file_seek`, `fs_truncate.c:ftruncate`, `fs_truncate.c:file_truncate`, `fs_fsync.c:fsync`, `fs_fsync.c:file_fsync`, `fs_sync.c:sync`, `fs_syncfs.c:syncfs` - File offset positioning, truncation, and synchronization interfaces.
- `fs_fcntl.c:fcntl`, `fs_fcntl.c:nx_fcntl`, `fs_fcntl.c:file_fcntl`, `fs_dup.c:dup`, `fs_dup2.c:dup2`, `fs_dup2.c:dup3`, `fs_dup2.c:file_dup2`, `fs_ sendfile.c:sendfile` - Descriptor control, duplication, and zero-copy transfer operations.
- `fs_stat.c:stat`, `fs_stat.c:lstat`, `fs_stat.c:nx_stat`, `fs_fstat.c:fstat`, `fs_fstat.c:file_fstat`, `fs_statfs.c:statfs`, `fs_fstatfs.c:fstatfs`, `fs_chstat.c:chmod`, `fs_chstat.c:chown`, `fs_chstat.c:utimens`, `fs_fchstat.c:fchmod`, `fs_fchstat.c:fchown`, `fs_fchstat.c:futimens` - Metadata query and modification interfaces.
- `fs_dir.c:dir_allocate`, `fs_mkdir.c:mkdir`, `fs_rmdir.c:rmdir`, `fs_unlink.c:unlink`, `fs_rename.c:rename`, `fs_symlink.c:symlink`, `fs_readlink.c:readlink`, `fs_link.c:link`, `fs_access.c:access` - Namespace and directory manipulation entry points.
- `fs_poll.c:poll`, `fs_poll.c:file_poll`, `fs_poll.c:poll_notify`, `fs_poll.c:poll_default_cb`, `fs_select.c:select`, `fs_epoll.c:epoll_create`, `fs_epoll.c:epoll_create1`, `fs_epoll.c:epoll_ctl`, `fs_epoll.c:epoll_wait`, `fs_epoll.c:epoll_pwait` - Synchronous I/O multiplexing and poll notification APIs.
- `vfs.h:file_initlk`, `vfs.h:file_closelk`, `vfs.h:file_getlk`, `vfs.h:file_setlk` - POSIX advisory byte-range record locking (`fs_lock.c`).
- `vfs.h:notify_initialize`, `vfs.h:notify_open`, `vfs.h:notify_close`, `vfs.h:notify_close2`, `vfs.h:notify_read`, `vfs.h:notify_write`, `vfs.h:notify_chstat`, `vfs.h:notify_unlink`, `vfs.h:notify_unmount`, `vfs.h:notify_mkdir`, `vfs.h:notify_create`, `vfs.h:notify_rename`, `fs_inotify.c:inotify_init`, `fs_inotify.c:inotify_init1`, `fs_inotify.c:inotify_add_watch`, `fs_inotify.c:inotify_rm_watch` - Inotify filesystem event subsystem.
- `fs_eventfd.c:eventfd`, `fs_timerfd.c:timerfd_create`, `fs_timerfd.c:timerfd_settime`, `fs_timerfd.c:timerfd_gettime`, `fs_signalfd.c:signalfd`, `fs_pseudofile.c:pseudofile_create` - Pollable event, watchdog timer, signal descriptor, and pseudo-file implementations.

## Invariants
- `fs_read.c:file_readv` and `fs_write.c:file_writev` validate `0 < iovcnt <= IOV_MAX`, check for `SSIZE_MAX` length overflow, and verify that `filep->f_oflags & O_ACCMODE` permits the requested transfer direction (`-EBADF` otherwise).
- Opening raw block or MTD inodes directly in `fs_open.c:file_vopen` requires `nxsched_capable(PR_CAP_RAWIO)` (`-EPERM` otherwise).
- `fs_poll.c:poll_setup` retains a `file_get` reference (`fds[i].filep`) on each polled descriptor until `poll_teardown` completes, preventing concurrent `close()` calls on another thread from invalidating the underlying `struct file` mid-poll.

## Side Effects
- Acquires and releases file descriptor table locks, VFS inode locks (`inode_lock`, `inode_rlock`), and per-subsystem mutexes (`g_inotify.lock`, `eph->lock`, `dev->lock`).
- Invokes underlying character driver (`file_operations`) and mounted filesystem (`mountpt_operations`) callbacks, updates `g_fs_profile` timing/call counters when `CONFIG_FS_PROFILER` is enabled, and dispatches `inotify` events when `CONFIG_FS_NOTIFY` is enabled.

## Verification
- Run: `make test`
