# ZIP Archive Read-Only File System (`fs/zipfs`)

## Overview
Implements a read-only VFS mountpoint (`zipfs`) backed by a `.zip` archive file on an underlying filesystem using `minizip` / `zlib` (`<unzip.h>`).

## Interface
- `zip_vfs.c:g_zipfs_operations` - Global `struct mountpt_operations` table implementing read-only VFS operations (`zipfs_open`, `zipfs_close`, `zipfs_read`, `zipfs_seek`, `zipfs_dup`, `zipfs_fstat`, `zipfs_opendir`, `zipfs_closedir`, `zipfs_readdir`, `zipfs_rewinddir`, `zipfs_bind`, `zipfs_unbind`, `zipfs_statfs`, `zipfs_stat`).
- `zip_vfs.c:struct zipfs_mountpt_s` - Per-mountpoint state storing the canonical path (`abspath`) to the backing `.zip` archive file.
- `zip_vfs.c:struct zipfs_file_s` - Per-open-file state holding the `unzFile` handle, mutex (`lock`), temporary `seekbuf`, and relative member path (`relpath`).

## Invariants
- `zip_vfs.c:zipfs_open` only permits read-only access; if `(oflags & O_WRONLY) != 0`, it returns `-EACCES`.
- `zip_vfs.c:zipfs_bind` requires `data` to specify the path to an existing, valid ZIP archive that can be opened with `unzOpen2_64(data, &zipfs_real_ops)`.

## Side Effects
- Opens, reads, seeks, and closes the underlying `.zip` archive file via kernel VFS file operations (`file_open`, `file_read`, `file_seek`, `file_close`).
- Allocates mountpoint state, `unzFile` decompression streams, and `CONFIG_FS_ZIPFS_SEEK_SIZE` seek buffers from the filesystem heap (`fs_heap_malloc`, `fs_heap_zalloc`, `fs_heap_free`).

## Verification
- Run: `make test`
