# Compressed Read-Only Memory File System (CROMFS)

## Overview
Implements an in-memory, LZF-compressed read-only filesystem (`CONFIG_FS_CROMFS`) backed by a contiguous linked image (`g_cromfs_image`).

## Interface
- `fs_cromfs.c:g_cromfs_operations` - VFS mountpoint operations table (`struct mountpt_operations`) for CROMFS.
- `fs_cromfs.c:g_cromfs_image` - External symbol referencing the in-memory `struct cromfs_volume_s` filesystem image.
- `cromfs.h:struct cromfs_volume_s`, `cromfs.h:struct cromfs_node_s` - Packed volume header and node metadata structures describing compressed blocks, hard links, directories, and files.

## Invariants
- Volume header `cv_magic` must match `CROMFS_MAGIC` during mount binding (`fs_cromfs.c:cromfs_bind`), and all node/block offsets must lie strictly within `cv_fsize` (`fs_cromfs.c:cromfs_offset2addr`).
- Only `O_RDONLY` file access is permitted (`fs_cromfs.c:cromfs_open`), and hard-link traversal depth is bounded by `fs_cromfs.c:CROMFS_MAX_LINKS` to prevent infinite loops (`fs_cromfs.c:cromfs_follow_link`).

## Side Effects
- Allocates per-file decompression buffers and directory structures from the filesystem heap (`fs_cromfs.c:cromfs_open`, `fs_cromfs.c:cromfs_close`, `fs_cromfs.c:cromfs_opendir`, `fs_cromfs.c:cromfs_closedir`).
- Decompresses LZF blocks into per-file cache buffers during reads (`fs_cromfs.c:cromfs_read`).

## Verification
- Run: `make test`
