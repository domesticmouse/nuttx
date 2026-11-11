# ICMPv4 (`net/icmp`)

## Overview
The `net/icmp` component implements the IPv4 Internet Control Message Protocol (ICMP). It handles inbound ICMP Echo Requests and Replies (`icmp_input`), generates outbound ICMP error responses (`icmp_reply`), implements `SOCK_DGRAM`/`SOCK_RAW` `IPPROTO_ICMP` sockets (`g_icmp_sockif`), and maintains an IPv4 Path MTU Discovery (PMTUD) destination cache (`icmp_pmtu.c`).

## Interface
- `[icmp.h:struct icmp_conn_s]` - Connection structure for `IPPROTO_ICMP` sockets, tracking echo request ID, device filter, poll callbacks, and `readahead` IOB queue.
- `[icmp.h:struct icmp_poll_s]` - Poll context structure associating an `icmp_conn_s` with a network device and `struct pollfd`.
- `[icmp.h:struct icmp_pmtu_entry]` - IPv4 Path MTU Discovery destination cache entry (`daddr`, `pmtu`, `time`).
- `[icmp_sockif.c:g_icmp_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `IPPROTO_ICMP` sockets.
- `[icmp_input.c:icmp_input]` - Processes incoming ICMPv4 packets on `dev`, generating Echo Replies in-place, updating PMTU state on `ICMP_DEST_UNREACH`/`ICMP_FRAG_NEEDED`, and delivering copies to matching `IPPROTO_ICMP` sockets.
- `[icmp_reply.c:icmp_reply]` - Formats an ICMP error message (e.g., Destination Unreachable, Time Exceeded) in `dev->d_iob` in response to an offending IPv4 packet.
- `[icmp_conn.c:icmp_alloc]` - Allocates a new `struct icmp_conn_s` from the connection pool.
- `[icmp_conn.c:icmp_free]` - Frees an `struct icmp_conn_s` and purges its `readahead` queue.
- `[icmp_conn.c:icmp_active]` - Searches for an active `IPPROTO_ICMP` socket matching a given Echo ID.
- `[icmp_conn.c:icmp_nextconn]` - Iterates through active `IPPROTO_ICMP` connections.
- `[icmp_conn.c:icmp_findconn]` - Finds a connection bound to `dev` and `id`.
- `[icmp_conn.c:icmp_foreach]` - Invokes a callback for every active `IPPROTO_ICMP` connection.
- `[icmp_conn.c:icmp_conn_list_lock]` - Acquires the global ICMP connection list lock (`[icmp_conn.c:icmp_conn_list_unlock]` releases it).
- `[icmp_poll.c:icmp_poll]` - Polls an `struct icmp_conn_s` for pending outbound ICMP requests on `dev`.
- `[icmp_sendmsg.c:icmp_sendmsg]` - Sends an ICMP packet from an `IPPROTO_ICMP` socket.
- `[icmp_recvmsg.c:icmp_recvmsg]` - Receives an ICMP reply from a connection's `readahead` queue.
- `[icmp_netpoll.c:icmp_pollsetup]` - Registers `poll`/`select` monitoring on an `IPPROTO_ICMP` socket (`[icmp_netpoll.c:icmp_pollteardown]` tears it down).
- `[icmp_ioctl.c:icmp_ioctl]` - Handles `FIONREAD` and `FIONSPACE` ioctls on `IPPROTO_ICMP` sockets.
- `[icmp_pmtu.c:icmpv4_find_pmtu_entry]` - Looks up an IPv4 PMTU entry for a destination address.
- `[icmp_pmtu.c:icmpv4_add_pmtu_entry]` - Creates or updates an IPv4 PMTU cache entry, evicting the oldest entry if full.

## Invariants
- `[icmp_input.c:icmp_input]`, `[icmp_poll.c:icmp_poll]`, and `[icmp_reply.c:icmp_reply]` must be called with the network lock held.
- Per RFC 1122 Section 3.2.2, `[icmp_reply.c:icmp_reply]` never generates an ICMP error message in response to another ICMP error message, a packet destined to an IPv4 broadcast/multicast address, a link-layer broadcast, or a non-initial IPv4 fragment.

## Side Effects
- Rewrites `dev->d_iob` in-place to construct Echo Replies (`[icmp_input.c:icmp_input]`) or ICMP error messages (`[icmp_reply.c:icmp_reply]`).
- Clones and queues incoming ICMP packets onto `readahead` queues of active `[icmp.h:struct icmp_conn_s]` sockets and updates the global IPv4 PMTU cache (`[icmp_pmtu.c:icmpv4_add_pmtu_entry]`).

## Verification
- Run: `make test`
