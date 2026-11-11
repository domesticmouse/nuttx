# Networking Utilities (`net/utils`)

## Overview
The `net/utils` component provides shared infrastructure and helper routines across the NuttX networking stack. It implements the global re-entrant network lock (`net_lock`) and ordered connection/device locking helpers (`conn_dev_lock`), generic preallocated/dynamic buffer pools (`struct net_bufpool_s`), Internet/IP/TCP/UDP/ICMP/ICMPv6 checksum calculation and incremental adjustment, ancillary control message (`cmsg`) formatting, IPv4/IPv6 netmask and prefix length conversions, timeval-to-decisecond/tick conversions, and pcap packet snooping (`net_snoop.c`).

## Interface
- `[utils.h:struct net_bufpool_s]` - Generic network structure pool descriptor (`[utils.h:NET_BUFPOOL_DECLARE]` declares a pool; `[net_bufpool.c:net_bufpool_timedalloc]`, `[net_bufpool.c:net_bufpool_free]`, `[net_bufpool.c:net_bufpool_test]`, `[net_bufpool.c:net_bufpool_navail]`, `[net_bufpool.c:net_bufpool_lock]`, and `[net_bufpool.c:net_bufpool_unlock]` manage allocation, deallocation, and synchronization).
- `[utils.h:enum tv2ds_remainder_e]` - Rounding mode for `net_timeval2dsec` (`TV2DS_TRUNC`, `TV2DS_ROUND`, `TV2DS_CEIL`).
- `[utils.h:conn_lock]` - Acquires a socket connection's recursive mutex `sconn->s_lock` (`[utils.h:conn_unlock]` releases it).
- `[utils.h:conn_dev_lock]` - Acquires both `netdev_lock(dev)` and `conn_lock(sconn)` in strict lock order (`[utils.h:conn_dev_unlock]` releases them in reverse order; `[utils.h:conn_dev_sem_timedwait]` waits on a semaphore while temporarily breaking both locks).
- `[net_lock.c:net_lock]` - Acquires the global recursive network mutex (`[net_lock.c:net_trylock]`, `[net_lock.c:net_unlock]`, `[net_lock.c:net_breaklock]`, and `[net_lock.c:net_restorelock]` manage the global lock).
- `[net_lock.c:net_sem_timedwait]` - Waits on a semaphore with optional timeout while breaking and restoring the network lock (`[net_lock.c:net_sem_timedwait2]` breaks and restores two recursive mutexes and supports atomic interrupt-disabled sleeps).
- `[net_chksum.c:net_chksum]` - Computes the 16-bit one's complement sum over a memory buffer (`[net_chksum.c:net_chksum_iob]` sums across an `struct iob_s` chain; `[net_chksum.c:net_chksum_adjust]` incrementally updates a checksum when header bytes change).
- `[net_ipchksum.c:ipv4_chksum]` - Computes the IPv4 header checksum.
- `[net_tcpchksum.c:tcp_ipv4_chksum]` - Computes the TCP over IPv4 checksum (`[net_tcpchksum.c:tcp_ipv6_chksum]` and `[net_tcpchksum.c:tcp_chksum]` compute TCP over IPv6 and generic TCP checksums).
- `[net_udpchksum.c:udp_ipv4_chksum]` - Computes the UDP over IPv4 checksum (`[net_udpchksum.c:udp_ipv6_chksum]` computes UDP over IPv6).
- `[net_icmpchksum.c:icmp_chksum]` - Computes the ICMPv4 checksum (`[net_icmpchksum.c:icmp_chksum_iob]` sums an IOB chain; `[net_icmpchksum.c:icmpv6_chksum]` computes the ICMPv6 checksum).
- `[net_cmsg.c:cmsg_append]` - Appends an ancillary `struct cmsghdr` record to a `struct msghdr` (`[net_cmsg.c:cmsg_store_timestamp]` appends a `SO_TIMESTAMP` record).
- `[net_dsec2tick.c:net_dsec2tick]` - Converts deciseconds to system clock ticks (`[net_dsec2timeval.c:net_dsec2timeval]` and `[net_timeval2dsec.c:net_timeval2dsec]` convert between deciseconds and `struct timeval`).
- `[net_mask2pref.c:net_ipv4_mask2pref]` - Converts a 32-bit IPv4 netmask to a prefix length (`[net_mask2pref.c:net_ipv6_mask2pref]`, `[net_ipv6_pref2mask.c:net_ipv6_pref2mask]`, and `[net_ipv6_pref2mask.c:net_ipv6_common_pref]` convert and compare IPv6 masks/prefixes).
- `[net_ipv6_payload.c:net_ipv6_payload]` - Advances past IPv6 extension headers to locate the upper-layer protocol payload and next-header type.
- `[net_iob_concat.c:net_iob_concat]` - Concatenates two `struct iob_s` chains (`iob1` and `iob2`).
- `[net_incr32.c:net_incr32]` - Adds a 16-bit increment to a 4-byte network-byte-order counter.
- `[net_snoop.c:snoop_open]` - Opens a pcap capture file/stream (`[net_snoop.c:snoop_dump]` writes captured packets).

## Invariants
- `[utils.h:conn_dev_lock]` always acquires `netdev_lock(dev)` prior to `conn_lock(sconn)` (and `[utils.h:conn_dev_unlock]` releases `conn_unlock(sconn)` before `netdev_unlock(dev)`) to prevent lock-inversion deadlocks.
- `[net_chksum.c:net_chksum_adjust]` requires old and new data segments to start at even byte offsets and have even byte lengths.

## Side Effects
- Acquires, breaks, and restores recursive kernel mutexes (`g_netlock`, `d_lock`, `s_lock`), allocates and frees nodes from `struct net_bufpool_s` pools and the kernel heap, and writes pcap packet capture records to VFS files in `[net_snoop.c:snoop_dump]`.

## Verification
- Run: `make test`
