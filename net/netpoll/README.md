# Polling Network I/O (`net/netpoll`)

## Overview
The `net/netpoll` component implements a polling-mode UDP and packet I/O interface (`CONFIG_NET_UDP_NOINTS`) designed for interrupt-free and kernel panic/crash-dump contexts. It bypasses normal interrupt-driven socket queues and communicates directly with lower-half network drivers (`struct netdev_lowerhalf_s`) via `txpoll`, `transmit`, and `receive` driver operations.

## Interface
- `[netpoll_pkt.c:netpoll_pkt_alloc]` - Allocates a `netpkt_t` buffer from `lower`, polling `lower->ops->txpoll` up to `NETPOLL_PKT_ALLOC_RETRY` times to reclaim buffers if exhausted.
- `[netpoll_udp.c:netpoll_udp_init]` - Initializes a `struct netpoll_udp_s` handle, resolving the outgoing lower-half network device, source IP address, and destination MAC address (from the ARP/Neighbor table or broadcast).
- `[netpoll_udp.c:netpoll_udp_pkt_alloc]` - Allocates a `netpkt_t` pre-offset past L2, L3 (IPv4/IPv6), and UDP headers.
- `[netpoll_udp.c:netpoll_udp_pkt_send]` - Prepends L2 Ethernet, L3 IPv4/IPv6, and UDP headers (with checksums) to `pkt` and transmits it via `lower->ops->transmit`.
- `[netpoll_udp.c:netpoll_udp_send]` - Allocates, copies, and transmits a UDP datagram buffer over `np`.
- `[netpoll_udp.c:netpoll_udp_recv]` - Polls `lower->ops->receive` for an incoming UDP datagram matching `np`'s local port, verifying L3/UDP checksums and optionally capturing the peer address/MAC.

## Invariants
- `[netpoll_udp.c:netpoll_udp_init]` requires a non-NULL `np->dev` whose `lower->ops->txpoll` callback is implemented (`NETDEV_UPPERHALF`).
- `[netpoll_udp.c:netpoll_udp_pkt_send]` requires `IFF_IS_RUNNING(lower->netdev.d_flags)` and asserts that either the OS is in panic state (`OSINIT_IS_PANIC()`) or the caller holds `lower->netdev.d_lock`.

## Side Effects
- Directly invokes `lower->ops->txpoll`, `lower->ops->transmit`, and `lower->ops->receive` on the hardware driver.
- Drops and frees non-matching incoming packets observed while polling in `[netpoll_udp.c:netpoll_udp_recv]`.

## Verification
- Run: `make test`
