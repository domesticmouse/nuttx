# Network ProcFS (`net/procfs`)

## Overview
The `net/procfs` component implements the `/proc/net` virtual filesystem entries (`CONFIG_FS_PROCFS` and `!CONFIG_FS_PROCFS_EXCLUDE_NET`). It exposes human-readable kernel networking statistics, per-interface link and address status, IPv4/IPv6 routing tables (`/proc/net/route`), MLD group memberships (`/proc/net/mld`), and active TCP (`/proc/net/tcp`) and UDP (`/proc/net/udp`) socket tables using a line-generator cursor architecture.

## Interface
- `[procfs.h:struct netprocfs_file_s]` - Open file state for `/proc/net` files containing the line generator cursor (`lineno`), line buffer (`line`), and union state (`u`).
- `[procfs.h:struct netprocfs_level1_s]` - Directory cursor state for enumerating `/proc/net` entries.
- `[procfs.h:linegen_t]` - Function pointer type for generating the `lineno`-th line of a `/proc/net` virtual file.
- `[net_procfs.c:g_net_procfs]` - ProcFS operations table (`struct procfs_operations`) for `/proc/net`.
- `[net_procfs.c:g_procfs_ennev]` - ProcFS entry registration for `net` and `net/*`.
- `[net_procfs.c:netprocfs_read_linegen]` - Generic line-by-line reader driving a `linegen_t` table to satisfy VFS `read()` calls.
- `[net_statistics.c:netprocfs_read_netstats]` - Reads global protocol stack statistics (`/proc/net/stat`).
- `[netdev_statistics.c:netprocfs_read_devstats]` - Reads per-device configuration, addresses, and RX/TX counters (`/proc/net/<dev>`).
- `[net_procfs_route.c:netprocfs_read_routes]` - Reads IPv4 and IPv6 routing tables (`/proc/net/route`).
- `[net_mld.c:netprocfs_read_mldstats]` - Reads IPv6 MLD multicast group memberships (`/proc/net/mld`).
- `[net_tcp.c:netprocfs_read_tcpstats]` - Reads active TCP connections (`/proc/net/tcp`).
- `[net_udp.c:netprocfs_read_udpstats]` - Reads active UDP sockets (`/proc/net/udp`).

## Invariants
- Line generator functions (`[procfs.h:linegen_t]`) format output into `priv->line` bounded by `NET_LINELEN` (80 bytes) while holding the appropriate network/connection locks during table inspection.

## Side Effects
- Allocates and frees `[procfs.h:struct netprocfs_file_s]` and `[procfs.h:struct netprocfs_level1_s]` on the kernel heap during `open`/`opendir` and `close`/`closedir`, and acquires network locks while sampling kernel state.

## Verification
- Run: `make test`
