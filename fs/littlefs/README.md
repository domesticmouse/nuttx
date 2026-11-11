# LittleFS VFS Adapter

## Overview
Integrates the ARM Mbed LittleFS fail-safe flash filesystem into the NuttX VFS layer (`g_littlefs_operations`), bridging MTD or block drivers to LittleFS block device callbacks and supporting optional POSIX file attribute persistence (`CONFIG_FS_LITTLEFS_ATTR_UPDATE`).

## Interface
- `lfs_vfs.c:g_littlefs_operations` - VFS mountpoint operations table (`struct mountpt_operations`) for LittleFS volumes.
- `lfs_vfs.c:struct littlefs_mountpt_s`, `lfs_vfs.c:struct littlefs_file_s`, `lfs_vfs.c:struct littlefs_dir_s`, `lfs_vfs.c:struct littlefs_attr_s` - Mountpoint context, reference-counted open file wrapper, directory handle, and on-disk attribute structure.
- `lfs_vfs.h` - NuttX debug and utility header bridge for LittleFS (`littlefs/lfs_util.h`).

## Invariants
- Requires `CONFIG_C99_BOOL` to be enabled at compile time (`lfs_vfs.c`).
- All LittleFS volume operations on a mountpoint are serialized via `fs->lock` (`lfs_vfs.c:struct littlefs_mountpt_s`).
- LittleFS error codes (`enum lfs_error`) are translated to standard negated POSIX errno values via `lfs_vfs.c:littlefs_convert_result`.

## Side Effects
- Reads, programs, erases, and syncs flash blocks through the underlying MTD or block device driver bound during `lfs_vfs.c:littlefs_bind`.
- Allocates and frees mountpoint, file cache, and directory structures via `fs_heap_malloc`, `fs_heap_zalloc`, and `fs_heap_free`.

## Verification
- Run: `make test`
