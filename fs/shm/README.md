# POSIX Shared Memory File System (`fs/shm`)

## Overview
Implements POSIX shared memory objects (`shm_open`, `shm_unlink`) backed by a VFS pseudo-filesystem (`CONFIG_FS_SHMFS_VFS_PATH`), supporting `read`, `write`, `ftruncate`, and virtual/physical memory mapping (`mmap`/`munmap`).

## Interface
- `shmfs.c:g_shmfs_operations` - Global `struct file_operations` table implementing `shmfs_close`, `shmfs_read`, `shmfs_write`, `shmfs_mmap`, `shmfs_truncate`, and `shmfs_unlink`.
- `shm_open.c:shm_open` - Opens or creates a POSIX shared memory object under `CONFIG_FS_SHMFS_VFS_PATH` and returns a process file descriptor with `O_CLOEXEC`.
- `shm_unlink.c:shm_unlink` - Removes a POSIX shared memory object name from the VFS namespace (`inode_remove`) and releases its backing memory once all open descriptors and mappings are closed.
- `shmfs.h:struct shmfs_object_s` - Represents an allocated shared memory object containing `length` and physical/virtual page pointers (`paddr`).
- `shmfs.h:shmfs_alloc_object` - Allocates zero-initialized backing memory or page-pool pages (`mm_pgalloc`) for a shared memory object of `length` bytes.
- `shmfs.h:shmfs_free_object` - Releases the backing memory or physical pages (`mm_pgfree`) and frees the `struct shmfs_object_s`.

## Invariants
- `shmfs.c:shmfs_write` does not auto-expand shared memory objects; attempting to write past `sho->length` returns `-EFBIG` unless the object is first resized via `ftruncate` (`shmfs_truncate`).
- `shm_open.c:file_shm_open` and `shm_unlink.c:file_shm_unlink` strip leading `/` characters from `name`, reject empty names (`-EINVAL` / `-ENOENT`), and enforce `CONFIG_NAME_MAX` (`-ENAMETOOLONG`).

## Side Effects
- Allocates and frees kernel heap memory (`kmm_zalloc`, `kmm_free`) or page pool pages (`mm_pgalloc`, `mm_pgfree`) and maps/unmaps pages into task group address environments (`up_shmat`, `up_shmdt`, `vm_map_region`, `vm_unmap_region`).
- Mutates the VFS inode tree under `inode_lock()` (`inode_reserve`, `inode_remove`, `INODE_SET_SHM`) and triggers inotify notifications (`notify_open`, `notify_unlink`).

## Verification
- Run: `make test`
