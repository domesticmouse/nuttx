# Device Interface (`net/devif`)

## Overview
The `net/devif` component provides the Network Device Interface layer bridging lower-level network device drivers (`struct net_driver_s`) and upper-layer networking protocols (IPv4, IPv6, TCP, UDP, ICMP, ARP, IGMP, MLD, Packet, CAN, Bluetooth, and IEEE 802.15.4). It manages device and connection event callback chains (`struct devif_callback_s`), coordinates periodic and TX-ready polling across all protocol families (`devif_poll`), handles software loopback (`devif_loopback`), and processes inbound IPv4 and IPv6 packets (`ipv4_input`, `ipv6_input`).

## Interface
- `[devif.h:struct devif_callback_s]` - Doubly-linked callback node registering an event handler (`event`), private context (`priv`), and event flags (`flags`) on a connection or device.
- `[devif.h:devif_callback_event_t]` - Function pointer signature for device/connection event handlers.
- `[devif_callback.c:devif_callback_alloc]` - Allocates a `struct devif_callback_s` from the callback pool and attaches it to `dev->d_conncb` and the connection list (`list_head`/`list_tail`).
- `[devif_callback.c:devif_conn_callback_free]` - Detaches and frees a connection/port-level callback structure.
- `[devif_callback.c:devif_dev_callback_free]` - Detaches and frees a device-level callback structure.
- `[devif_callback.c:devif_conn_event]` - Dispatches an event mask (`flags`) along a connection's callback chain.
- `[devif_callback.c:devif_dev_event]` - Dispatches an event mask (`flags`) along `dev->d_conncb`.
- `[devif_send.c:devif_send]` - Copies a memory buffer into `dev`'s active packet buffer (`d_iob`) at the upper-layer offset and sets `d_sndlen`.
- `[devif_iobsend.c:devif_iob_send]` - Appends or chains an `struct iob_s` payload into `dev->d_iob` for transmission.
- `[devif_filesend.c:devif_file_send]` - Reads data directly from a `struct file` into `dev->d_iob` for zero-copy/sendfile transmission.
- `[devif_poll.c:devif_out]` - Builds L2/L3 headers (ARP, IPv6 neighbor, or fragmentation) for an outbound packet prepared on `dev`.
- `[devif_poll.c:devif_poll_out]` - Finalizes outbound packet framing and invokes the caller's driver callback (`callback(dev)`).
- `[devif_poll.c:devif_poll]` - Sequentially polls all enabled protocol layers (Packet, 6LoWPAN, IGMP, MLD, TCP, UDP, ICMP, ICMPv6, Forwarding, ARP, Bluetooth, IEEE 802.15.4, CAN) for pending transmissions on `dev`.
- `[devif_poll.c:devif_get_mtu]` - Returns the effective L3 MTU for `dev` (accounting for IPv6 PMTU or link MTU).
- `[devif_loopback.c:devif_is_loopback]` - Tests whether an outbound packet on `dev` is addressed to the local interface itself.
- `[devif_loopback.c:devif_loopback]` - Short-circuits a locally-addressed outbound packet on `dev` back into the inbound processing path.
- `[devif_forward.c:devif_forward]` - Transfers payload data from one `struct net_driver_s` (`dev1`) to another (`dev2`).
- `[ipv4_input.c:ipv4_input]` - Validates and dispatches an inbound IPv4 packet on `dev` (applying NAT, IP filtering, fragmentation reassembly, forwarding, and L4 protocol demultiplexing).
- `[ipv4_input.c:ipv4_in]` - Internal IPv4 input entry point after reassembly/loopback.
- `[ipv6_input.c:ipv6_input]` - Validates and dispatches an inbound IPv6 packet on `dev` (applying extension header parsing, NAT66, IPv6 filtering, reassembly, forwarding, and L4 demultiplexing).
- `[ipv6_input.c:ipv6_in]` - Internal IPv6 input entry point after reassembly/loopback.

## Invariants
- All `devif` callback allocation, freeing, polling, and packet input/output routines must execute with the network lock held.
- When `dev` is non-NULL, `[devif_callback.c:devif_callback_alloc]` verifies `netdev_verify(dev)` and that `dev->d_flags` has `IFF_UP` set before allocating a callback node.

## Side Effects
- Allocates and frees callback nodes in `g_cbprealloc`/heap and mutates `dev->d_conncb` and `dev->d_devcb` lists.
- Modifies `dev->d_iob`, `dev->d_buf`, `dev->d_len`, and `dev->d_sndlen` during inbound and outbound packet processing, and invokes driver transmission callbacks via `[devif_poll.c:devif_poll]`.

## Verification
- Run: `make test`
