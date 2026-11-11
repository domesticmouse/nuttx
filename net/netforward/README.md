# Packet Forwarding (`net/netforward`)

## Overview
The `net/netforward` component implements L2/L3 packet forwarding (`CONFIG_NET_IPFORWARD`) across network interfaces in NuttX. It manages a pool of forwarding state structures (`struct forward_s`), routes and forwards unicast and broadcast/multicast IPv4 and IPv6 packets as well as CAN frames (`CONFIG_NET_CANPROTO_OPTIONS`), decrements TTL/Hop Limit, applies `FORWARD` IP filter and outbound NAT hooks, and schedules outbound transmissions via `IPFWD_POLL` device callbacks.

## Interface
- `[netforward.h:struct forward_s]` - Forwarding context structure binding an outbound `f_dev`, packet `f_iob`, and device callback `f_cb`.
- `[netfwd_alloc.c:netfwd_alloc]` - Allocates a `struct forward_s` instance from the preallocated pool `g_freefwd`.
- `[netfwd_alloc.c:netfwd_free]` - Releases a `struct forward_s` instance, freeing its callback and any attached IOB chain.
- `[netfwd_forward.c:netfwd_forward]` - Transfers a packet from `indev` into a `struct forward_s` bound to `outdev` and notifies `outdev` for transmission.
- `[netfwd_poll.c:netfwd_poll]` - Polls `dev` for pending forwarded packets via `IPFWD_POLL` events.
- `[netfwd_dropstats.c:netfwd_dropstats]` - Increments packet drop statistics for a forwarded packet (`[netfwd_dropstats.c:ipv4_dropstats]` and `[netfwd_dropstats.c:ipv6_dropstats]` update IPv4 and IPv6 drop counters).
- `[ipv4_forward.c:ipv4_forward]` - Routes and forwards an inbound IPv4 packet not destined for the local host (`[ipv4_forward.c:ipv4_forward_broadcast]` clones and forwards broadcast/multicast packets when `CONFIG_NET_IPFORWARD_BROADCAST` is enabled).
- `[ipv6_forward.c:ipv6_forward]` - Routes and forwards an inbound IPv6 packet not destined for the local host (`[ipv6_forward.c:ipv6_forward_broadcast]` clones and forwards multicast/subnet-broadcast packets).
- `[can_forward.c:can_forward]` - Forwards CAN frames across CAN interfaces.

## Invariants
- `CONFIG_IOB_NBUFFERS` must be strictly greater than `CONFIG_NET_FORWARD_NSTRUCT` (enforced via `static_assert` in `[netforward.h:struct forward_s]`).
- `[netfwd_alloc.c:netfwd_alloc]`, `[netfwd_alloc.c:netfwd_free]`, `[ipv4_forward.c:ipv4_forward]`, and `[ipv6_forward.c:ipv6_forward]` must be called with the network lock held.

## Side Effects
- Allocates and frees `[netforward.h:struct forward_s]` nodes from `g_freefwd` and registers `IPFWD_POLL` device callbacks on target interfaces.
- Decrements IPv4 `ttl` / IPv6 `hoplimit`, updates IPv4 header checksums, invokes `ipv4_filter_fwd`/`ipv6_filter_fwd` and `ipv4_nat_outbound`/`ipv6_nat_outbound`, generates ICMP/ICMPv6 Time Exceeded or Destination Unreachable replies when forwarding fails, and wakes target devices via `netdev_txnotify_dev`.

## Verification
- Run: `make test`
