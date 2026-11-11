# Process and System Information File System (`fs/procfs`)

## Overview
Implements the virtual `/proc` filesystem (`procfs`), providing a table-driven plugin architecture (`struct procfs_entry_s`) for kernel subsystems and user code to expose system metrics, per-process state (`/proc/<pid>`), memory statistics, CPU load, and device diagnostics as virtual files and directories.

## Interface
- `fs_procfs.c:g_procfs_operations` - Global `struct mountpt_operations` table implementing VFS mountpoint operations for `procfs`.
- `fs_procfs.c:procfs_register` - Dynamically registers an additional `struct procfs_entry_s` handler when `CONFIG_FS_PROCFS_REGISTER` is enabled.
- `fs_procfsutil.c:procfs_memcpy` - Copies generated text data into the caller's `read` buffer while handling file offset (`offset`) advancement and truncation.
- `fs_procfsutil.c:procfs_snprintf` - Formats a string into a fixed buffer safely for `procfs` output generation.
- `fs_procfsutil.c:procfs_sprintf` - Appends formatted strings to a buffer while tracking remaining capacity.
- `fs_procfsproc.c:g_proc_operations` - Per-task/process (`/proc/<pid>/...` and `/proc/self/...`) `procfs_operations` table.
- `fs_procfsmeminfo.c:g_meminfo_operations`, `fs_procfsmeminfo.c:g_memdump_operations`, `fs_procfsmempool.c:g_mempool_operations` - Memory heap and pool statistics/dump handlers.
- `fs_procfscpuinfo.c:g_cpuinfo_operations`, `fs_procfscpuload.c:g_cpuload_operations`, `fs_procfscritmon.c:g_critmon_operations`, `fs_procfsuptime.c:g_uptime_operations`, `fs_procfsversion.c:g_version_operations`, `fs_procfstcbinfo.c:g_tcbinfo_operations`, `fs_procfsiobinfo.c:g_iobinfo_operations`, `fs_procfsfdt.c:g_fdt_operations`, `fs_procfspressure.c:g_pressure_operations`, `fs_procfs_profile.c:g_fsprofile_operations` - Built-in system status `procfs_operations` tables.

## Invariants
- Static entries in `g_base_entries` (`fs_procfs.c`) must remain sorted in alphabetical order by `pathpattern` so wildcard and directory matching operate deterministically.
- `procfs` is a pseudo-filesystem that does not bind to a block driver (`procfs_bind` ignores `blkdriver`) and does not support creating or unlinking files (`unlink`, `mkdir`, `rmdir`, `rename` are NULL).

## Side Effects
- Reading or writing `/proc` entries invokes subsystem callbacks (`procfs_operations`) that inspect kernel TCBs, heap allocators, IOB queues, and performance counters, and in writable entries (such as `/proc/memdump` or `/proc/<pid>/critmon`) trigger memory dumps or reset monitoring counters.
- `fs_procfs.c:procfs_register` reallocates and appends to the runtime `g_procfs_entries` array on the filesystem heap.

## Verification
- Run: `make test`
