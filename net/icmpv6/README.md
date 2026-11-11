# ICMPv6 (`net/icmpv6`)

## Overview
The `net/icmpv6` component implements the IPv6 Internet Control Message Protocol (ICMPv6). In addition to Echo Request/Reply processing, error generation (`icmpv6_reply`), and `IPPROTO_ICMPV6` sockets (`g_icmpv6_sockif`), it provides IPv6 Neighbor Discovery (Neighbor Solicitation and Neighbor Advertisement), Router Discovery (Router Solicitation and Router Advertisement), Stateless Address Autoconfiguration (SLAAC, `icmpv6_autoconfig`), and IPv6 Path MTU Discovery (`icmpv6_pmtu.c`).

## Interface
- `[icmpv6.h:struct icmpv6_conn_s]` - Connection structure for `IPPROTO_ICMPV6` sockets.
- `[icmpv6.h:struct icmpv6_notify_s]` - Waiter notification structure for Neighbor Discovery resolution (`[icmpv6_notify.c:icmpv6_wait_setup]`, `[icmpv6_notify.c:icmpv6_wait]`, `[icmpv6_notify.c:icmpv6_notify]`).
- `[icmpv6.h:struct icmpv6_rnotify_s]` - Waiter notification structure for Router Advertisement reception during SLAAC (`[icmpv6_rnotify.c:icmpv6_rwait_setup]`, `[icmpv6_rnotify.c:icmpv6_rwait]`, `[icmpv6_rnotify.c:icmpv6_rnotify]`).
- `[icmpv6.h:struct icmpv6_pmtu_entry]` - IPv6 Path MTU Discovery destination cache entry.
- `[icmpv6_sockif.c:g_icmpv6_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `IPPROTO_ICMPV6`.
- `[icmpv6_initialize.c:icmpv6_devinit]` - Initializes ICMPv6 state for a network device.
- `[icmpv6_input.c:icmpv6_input]` - Processes incoming ICMPv6 messages (Echo, Neighbor Solicitation/Advertisement, Router Solicitation/Advertisement, Packet Too Big) and updates the IPv6 Neighbor Table.
- `[icmpv6_neighbor.c:icmpv6_neighbor]` - Resolves an IPv6 destination address in the Neighbor Table, transmitting Neighbor Solicitations and waiting for an Advertisement if unresolved.
- `[icmpv6_solicit.c:icmpv6_solicit]` - Formats an ICMPv6 Neighbor Solicitation message in `dev->d_buf`.
- `[icmpv6_advertise.c:icmpv6_advertise]` - Formats an ICMPv6 Neighbor Advertisement message in `dev->d_buf`.
- `[icmpv6_rsolicit.c:icmpv6_rsolicit]` - Formats an ICMPv6 Router Solicitation message in `dev->d_buf`.
- `[icmpv6_radvertise.c:icmpv6_radvertise]` - Formats an ICMPv6 Router Advertisement message in `dev->d_buf`.
- `[icmpv6_autoconfig.c:icmpv6_autoconfig]` - Performs IPv6 Stateless Address Autoconfiguration (SLAAC) on `dev`.
- `[icmpv6_autoconfig.c:icmpv6_setaddresses]` - Configures link-local or prefix-derived IPv6 addresses on `dev` and updates multicast MAC filters.
- `[icmpv6_conn.c:icmpv6_alloc]` - Allocates a new `struct icmpv6_conn_s` (`[icmpv6_conn.c:icmpv6_free]` releases it).
- `[icmpv6_conn.c:icmpv6_active]` - Finds an active `IPPROTO_ICMPV6` connection matching `id` (`[icmpv6_conn.c:icmpv6_nextconn]` and `[icmpv6_conn.c:icmpv6_foreach]` iterate connections).
- `[icmpv6_sendmsg.c:icmpv6_sendmsg]` - Transmits an ICMPv6 message from a socket (`[icmpv6_recvmsg.c:icmpv6_recvmsg]` receives queued replies).
- `[icmpv6_netpoll.c:icmpv6_pollsetup]` - Sets up `poll`/`select` monitoring on an `IPPROTO_ICMPV6` socket (`[icmpv6_netpoll.c:icmpv6_pollteardown]` tears it down).
- `[icmpv6_poll.c:icmpv6_poll]` - Polls `dev` for pending ICMPv6 transmissions.
- `[icmpv6_linkipaddr.c:icmpv6_linkipaddr]` - Generates an EUI-64 link-local IPv6 address from a device's MAC address.
- `[icmpv6_reply.c:icmpv6_reply]` - Formats an ICMPv6 error reply in `dev->d_iob` in response to an offending IPv6 packet.
- `[icmpv6_ioctl.c:icmpv6_ioctl]` - Handles `FIONREAD` and `FIONSPACE` ioctls on `IPPROTO_ICMPV6` sockets.
- `[icmpv6_pmtu.c:icmpv6_find_pmtu_entry]` - Finds an IPv6 PMTU entry for `daddr` (`[icmpv6_pmtu.c:icmpv6_add_pmtu_entry]` adds or updates an entry).

## Invariants
- `[icmpv6_notify.c:icmpv6_wait]` and `[icmpv6_rnotify.c:icmpv6_rwait]` must be called with the network lock released after calling `[icmpv6_notify.c:icmpv6_wait_setup]` or `[icmpv6_rnotify.c:icmpv6_rwait_setup]` while holding the network lock.
- `[icmpv6_input.c:icmpv6_input]`, `[icmpv6_advertise.c:icmpv6_advertise]`, `[icmpv6_radvertise.c:icmpv6_radvertise]`, and `[icmpv6_reply.c:icmpv6_reply]` require the network lock to be held.

## Side Effects
- Mutates device IPv6 addresses and multicast MAC filters (`[icmpv6_autoconfig.c:icmpv6_setaddresses]`), updates the global IPv6 Neighbor Table (`neighbor_add`), and updates the IPv6 routing table on Router Advertisements.
- Wakes threads blocked on Neighbor Advertisement (`nt_sem`) or Router Advertisement (`rn_sem`) semaphores, and updates the IPv6 PMTU cache (`[icmpv6_pmtu.c:icmpv6_add_pmtu_entry]`).

## Verification
- Run: `make test`
