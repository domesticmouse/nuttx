# IPv4/IPv6 Socket Interface (`net/inet`)

## Overview
The `net/inet` component implements the `AF_INET` and `AF_INET6` (`PF_INET` / `PF_INET6`) socket interface layer (`inet_sockif`). It validates and dispatches socket operations to TCP, UDP, ICMP, ICMPv6, or 6LoWPAN protocol handlers, provides IPv4 and IPv6 L3 header builders (`ipv4_build_header`, `ipv6_build_header`), handles IP-level socket options (`IPPROTO_IP`, `IPPROTO_IPV6`), implements `getsockname`/`getpeername` for IPv4/IPv6, defines global well-known IPv6 addresses, and drains pending TX buffers on socket close (`inet_close`, `inet_txdrain`).

## Interface
- `[inet_sockif.c:inet_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `PF_INET` and `PF_INET6`.
- `[inet_sockif.c:inet_close]` - Closes an `AF_INET` or `AF_INET6` socket and releases protocol connection resources.
- `[inet_txdrain.c:inet_txdrain]` - Waits for queued TCP or UDP write buffers to drain before closing or shutting down a socket.
- `[ipv4_build_header.c:ipv4_build_header]` - Populates an `struct ipv4_hdr_s` header and computes the IPv4 header checksum.
- `[ipv6_build_header.c:ipv6_build_header]` - Populates an `struct ipv6_hdr_s` header with version, traffic class, flow label, payload length, next header, hop limit, and source/destination addresses.
- `[ipv4_setsockopt.c:ipv4_setsockopt]` - Handles `IPPROTO_IP` socket option mutations (`IP_TTL`, `IP_TOS`, `IP_MULTICAST_*`, `IP_ADD_MEMBERSHIP`, `IP_DROP_MEMBERSHIP`, `IP_PKTINFO`, `IPT_SO_SET_*`).
- `[ipv6_setsockopt.c:ipv6_setsockopt]` - Handles `IPPROTO_IPV6` socket option mutations (`IPV6_V6ONLY`, `IPV6_TCLASS`, `IPV6_UNICAST_HOPS`, `IPV6_MULTICAST_*`, `IPV6_JOIN_GROUP`, `IPV6_LEAVE_GROUP`, `IP6T_SO_SET_*`).
- `[ipv4_getsockopt.c:ipv4_getsockopt]` - Queries `IPPROTO_IP` socket options.
- `[ipv6_getsockopt.c:ipv6_getsockopt]` - Queries `IPPROTO_IPV6` socket options.
- `[ipv4_getsockname.c:ipv4_getsockname]` - Retrieves the local `struct sockaddr_in` bound to an IPv4 socket (`[ipv6_getsockname.c:ipv6_getsockname]` retrieves `struct sockaddr_in6`).
- `[ipv4_getpeername.c:ipv4_getpeername]` - Retrieves the remote peer `struct sockaddr_in` of a connected IPv4 socket (`[ipv6_getpeername.c:ipv6_getpeername]` retrieves `struct sockaddr_in6`).
- `[inet_globals.c:g_ipv6_unspecaddr]` - Constant IPv6 unspecified address (`::`).
- `[inet_globals.c:g_ipv6_loopback]` - Constant IPv6 loopback address (`::1`).
- `[inet_globals.c:g_ipv6_allnodes]` - Constant IPv6 link-local all-nodes multicast address (`ff02::1`).
- `[inet_globals.c:g_ipv6_allrouters]` - Constant IPv6 link-local all-routers multicast address (`ff02::2`).

## Invariants
- `[inet_sockif.c:inet_sockif]` only accepts `AF_INET` and `AF_INET6` socket domains and enforces valid `(type, protocol)` pairs against compiled-in stack protocols (`CONFIG_NET_TCP`, `CONFIG_NET_UDP`, `CONFIG_NET_ICMP_SOCKET`, `CONFIG_NET_ICMPv6_SOCKET`).

## Side Effects
- Mutates connection bindings, IP-level socket options (`sconn->s_ttl`, `sconn->s_tos`, `sconn->s_flags`), and multicast memberships (`igmp_joingroup`/`mld_joingroup`), and blocks the calling thread in `[inet_txdrain.c:inet_txdrain]` while write queues drain.

## Verification
- Run: `make test`
