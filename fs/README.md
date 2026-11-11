# NuttX File System Subsystem (`fs`)

## Overview
Top-level NuttX filesystem subsystem containing the Virtual File System (VFS) core, inode namespace tree, dedicated filesystem memory heap (`fs_heap_*`), boot-time filesystem initialization (`fs_initialize`), POSIX IPC pseudo-filesystems (`mqueue`, `semaphore`, `shm`, `event`), and concrete block, flash, RAM, virtual, and network filesystem implementations.

## Interface
- `fs_initialize.c:fs_initialize` - Boot-time initialization entry point that initializes the filesystem heap (`fs_heap_initialize`), inode tree (`inode_initialize`), POSIX file locks (`file_initlk`), AIO (`aio_initialize`), RPMsg filesystem server (`rpmsgfs_server_init`), inotify (`notify_initialize`), shared memory (`shmfs_initialize`), and registers a reboot notifier (`g_sync_nb`) to invoke `sync()` on power-off or restart.
- `fs_heap.h:fs_heap_initialize`, `fs_heap.h:fs_heap_zalloc`, `fs_heap.h:fs_heap_malloc`, `fs_heap.h:fs_heap_malloc_size`, `fs_heap.h:fs_heap_realloc`, `fs_heap.h:fs_heap_memalign`, `fs_heap.h:fs_heap_free`, `fs_heap.h:fs_heap_strdup`, `fs_heap.h:fs_heap_strndup`, `fs_heap.h:fs_heap_asprintf`, `fs_heap.h:fs_heap_mallinfo_task` - Dedicated filesystem memory allocator (`g_fs_heap` when `CONFIG_FS_HEAPSIZE > 0`, or direct aliases to `kmm_*` otherwise).
- `./aio/README.md` - POSIX Asynchronous I/O (`aio_read`, `aio_write`, `aio_fsync`, `lio_listio`) scheduling and worker queue subsystem.
- `./binfs/README.md` - Built-in application binary pseudo-filesystem (`binfs`).
- `./cromfs/README.md` - Compressed Read-Only Memory File System (`cromfs`) using LZF compression.
- `./driver/README.md` - Character, block, and MTD device driver VFS registration and proxy layer.
- `./event/README.md` - NXEVENT VFS pseudo-filesystem integration.
- `./fat/README.md` - FAT12/FAT16/FAT32 filesystem implementation and DMA sector allocator.
- `./hostfs/README.md` - Host simulator passthrough filesystem (`hostfs`).
- `./inode/README.md` - VFS in-memory inode tree, file descriptor table (`fdlist`), and open file table management.
- `./littlefs/README.md` - LittleFS MTD flash filesystem VFS wrapper.
- `./mmap/README.md` - POSIX `mmap`, `munmap`, `msync`, and `mprotect` memory mapping and anonymous mapping layer.
- `./mnemofs/README.md` - MnemoFS NAND flash filesystem with journal, wear-leveling block allocator, and B+ tree CTZ logs.
- `./mount/README.md` - VFS `mount`/`umount2` syscall handlers, mountpoint iteration, and removable media automounter.
- `./mqueue/README.md` - POSIX named message queue (`mq_open`, `mq_close`, `mq_unlink`) VFS integration.
- `./nfs/README.md` - Network File System Version 3 (NFSv3) UDP/RPC client.
- `./nxffs/README.md` - NuttX wear-leveling NOR/NAND Flash File System (`nxffs`).
- `./partition/README.md` - Block and MTD partition table parsers (GPT, MBR, PTABLE, TXTABLE).
- `./procfs/README.md` - Process and system diagnostic virtual filesystem (`/proc`).
- `./romfs/README.md` - Read-Only Memory File System (`romfs`) with XIP and node caching support.
- `./rpmsgfs/README.md` - Remote Processor Messaging (`rpmsgfs`) client and server filesystem over OpenAMP.
- `./semaphore/README.md` - POSIX named semaphore (`nxsem_open`, `nxsem_close`, `nxsem_unlink`) VFS integration.
- `./shm/README.md` - POSIX shared memory (`shm_open`, `shm_unlink`, `shmfs`) VFS and page-mapping implementation.
- `./smartfs/README.md` - Sector Map Allocation for Really Tiny (`smartfs`) flash filesystem.
- `./socket/README.md` - BSD socket file descriptor and VFS adaptation layer (`socket`, `accept4`, `socketpair`).
- `./spiffs/README.md` - SPI NOR Flash File System (`spiffs`) blueprint and VFS/core implementation.
- `./tmpfs/README.md` - Volatile in-memory RAM filesystem (`tmpfs`).
- `./unionfs/README.md` - Union overlay filesystem (`unionfs`) combining two mounted filesystems.
- `./userfs/README.md` - User-space filesystem proxy (`userfs`) over local UDP loopback.
- `./v9fs/README.md` - Plan 9 (9P2000.L) remote filesystem client over VirtIO and TCP sockets.
- `./vfs/README.md` - Core VFS system calls, `poll`/`select`/`epoll`, POSIX file locks, `inotify`, `eventfd`, `timerfd`, and `signalfd`.
- `./xipfs/README.md` - Power-fail-safe Execute-In-Place (`xipfs`) flash filesystem with online defragmentation.
- `./zipfs/README.md` - Read-only `.zip` archive filesystem (`zipfs`).

## Invariants
- `fs_initialize.c:fs_initialize` must be invoked during OS bring-up before any VFS, driver registration, or mount operations occur, ensuring `g_fs_heap` and the root inode tree (`inode_initialize`) are initialized first.
- When `CONFIG_FS_HEAPSIZE > 0`, `fs_heap.c:fs_heap_initialize` asserts (`DEBUGASSERT(buf != NULL)`) that the backing heap buffer was allocated before initializing `g_fs_heap` via `mm_initialize_pool`.

## Side Effects
- `fs_initialize.c:fs_initialize` initializes global VFS tables, allocates the filesystem heap (`g_fs_heap`), starts subsystem services (AIO, RPMsg server, inotify, shmfs), and registers `g_sync_nb` with `register_reboot_notifier` so all filesystems flush (`sync()`) on `SYS_POWER_OFF` or `SYS_RESTART`.
- `fs_heap.c` functions allocate and free memory from the dedicated `g_fs_heap` memory pool (`mm_malloc`, `mm_zalloc`, `mm_realloc`, `mm_memalign`, `mm_free`).

## Verification
- Run: `make test`
