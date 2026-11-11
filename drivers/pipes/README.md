# Pipe and FIFO Drivers (`drivers/pipes`)

## Overview
Implements POSIX anonymous pipes (`pipe`, `pipe2`, `file_pipe`) and named FIFOs (`nx_mkfifo`) backed by a shared ring-buffer character driver implementation (`pipe_common`).

## Interface
- `[pipe.c:pipe2]`, `[pipe.c:file_pipe]` - Creates an anonymous pipe pair with configurable buffer size and open flags (`[pipe.c:CONFIG_DEV_PIPE_SIZE]`, `[pipe.c:CONFIG_DEV_PIPE_VFS_PATH]`).
- `[fifo.c:nx_mkfifo]` - Creates a named FIFO special file in the VFS namespace (`[fifo.c:CONFIG_DEV_FIFO_SIZE]`).
- `[pipe_common.h:pipecommon_allocdev]`, `[pipe_common.h:pipecommon_freedev]`, `[pipe_common.h:pipecommon_open]`, `[pipe_common.h:pipecommon_close]`, `[pipe_common.h:pipecommon_read]`, `[pipe_common.h:pipecommon_write]`, `[pipe_common.h:pipecommon_poll]`, `[pipe_common.h:pipecommon_ioctl]`, `[pipe_common.h:pipecommon_unlink]` - Common circular buffer allocation and VFS file operations (`[pipe_common.h:struct pipe_dev_s]`).

## Invariants
- Pipe minor number allocation is serialized via `[pipe.c:g_pipelock]` (`nxmutex_lock`), and circular buffer access/reader-writer synchronization is coordinated through per-device semaphores (`[pipe_common.c:nxsem_wait]`, `[pipe_common.c:nxsem_post]`).
- Requested buffer sizes cannot exceed `[pipe_common.h:CONFIG_DEV_PIPE_MAXSIZE]`.

## Side Effects
- Allocates kernel memory for `struct pipe_dev_s` and circular buffers, registers/unregisters VFS character drivers (`register_driver`, `unregister_driver`), and wakes blocked reader/writer/poll threads.

## Verification
- Run: `make test`
