# Netlink Sockets (`net/netlink`)

## Overview
The `net/netlink` component implements the `AF_NETLINK` (`PF_NETLINK`) socket protocol family (`CONFIG_NET_NETLINK`) for kernel-userspace communication in NuttX. It provides connection management, asynchronous response queuing (`struct netlink_response_s`), Netlink attribute validation and parsing (`nla_parse`), and protocol handlers for `NETLINK_ROUTE` (device, address, route, neighbor, and IPv6 prefix queries/notifications) and `NETLINK_NETFILTER` (NAT connection tracking queries/notifications).

## Interface
- `[netlink.h:struct netlink_conn_s]` - Netlink socket connection structure holding `pid`, multicast `groups`, `flags`, response queue `resplist`, and poll wait state.
- `[netlink.h:struct netlink_ext_ack]` - Extended acknowledgment error context structure.
- `[netlink.h:struct nla_policy]` - Netlink attribute validation policy descriptor (`type`, `len`).
- `[netlink_sockif.c:g_netlink_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `PF_NETLINK`.
- `[netlink_conn.c:netlink_lock]` - Acquires the global Netlink recursive mutex (`[netlink_conn.c:netlink_unlock]` releases it).
- `[netlink_conn.c:netlink_alloc]` - Allocates a new `struct netlink_conn_s` (`[netlink_conn.c:netlink_free]` frees it and purges queued responses; `[netlink_conn.c:netlink_nextconn]` iterates active connections).
- `[netlink_conn.c:netlink_add_response]` - Appends a `struct netlink_response_s` to a connection's `resplist` and wakes waiting readers.
- `[netlink_conn.c:netlink_add_broadcast]` - Broadcasts a Netlink notification to all connections subscribed to `group`.
- `[netlink_conn.c:netlink_add_terminator]` - Appends an `NLMSG_DONE` message to terminate a multi-part dump response.
- `[netlink_conn.c:netlink_tryget_response]` - Non-blockingly dequeues the next response from `conn->resplist` (`[netlink_conn.c:netlink_get_response]` blocks until a response is available; `[netlink_conn.c:netlink_check_response]` peeks whether `resplist` is non-empty).
- `[netlink_notifier.c:netlink_notifier_setup]` - Registers a workqueue notifier for incoming Netlink responses (`[netlink_notifier.c:netlink_notifier_teardown]` and `[netlink_notifier.c:netlink_notifier_signal]` manage teardown and signaling).
- `[netlink_attr.c:nla_next]` - Advances to the next `struct nlattr` in an attribute stream (`[netlink_attr.c:nla_parse]` validates and indexes attributes against a `struct nla_policy` table).
- `[netlink_route.c:netlink_route_sendto]` - Processes userspace `NETLINK_ROUTE` requests (`RTM_*LINK`, `RTM_*NEIGH`, `RTM_*ROUTE`, `RTM_*ADDR`).
- `[netlink_route.c:netlink_device_notify]` - Broadcasts link state change notifications (`[netlink_route.c:netlink_device_notify_ipaddr]`, `[netlink_route.c:netlink_route_notify]`, `[netlink_route.c:netlink_neigh_notify]`, and `[netlink_route.c:netlink_ipv6_prefix_notify]` broadcast address, route, neighbor, and prefix events).
- `[netlink_netfilter.c:netlink_netfilter_sendto]` - Processes `NETLINK_NETFILTER` conntrack requests (`[netlink_netfilter.c:netlink_conntrack_notify]` broadcasts conntrack creation/destruction events).

## Invariants
- Access to the active Netlink connection list (`g_active_netlink_connections`) and per-connection `resplist` queues must be serialized by `[netlink_conn.c:netlink_lock]` / `[netlink_conn.c:netlink_unlock]`.
- Attribute streams parsed by `[netlink_attr.c:nla_parse]` must satisfy `[netlink.h:nla_ok]` length bounds and policy constraints.

## Side Effects
- Allocates and queues `struct netlink_response_s` buffers on the kernel heap and wakes waiting threads via `[netlink_notifier.c:netlink_notifier_signal]`.
- Modifies kernel routing tables, ARP/Neighbor caches, and network interface states in response to `NETLINK_ROUTE` commands.

## Verification
- Run: `make test`
