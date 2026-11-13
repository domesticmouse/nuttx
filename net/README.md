# NuttX Networking Subsystem (`net`)

## Overview
The `net` directory contains the NuttX kernel networking stack. It provides the top-level subsystem initialization entry point (`net_initialize`), the BSD/POSIX and internal `psock_*` socket layer (`socket`), network device registration and upper-layer callback dispatching (`netdev`, `devif`), L2/L3/L4 protocol implementations (ARP, IPv4/IPv6, ICMP, ICMPv6, IGMP, MLD, Neighbor Discovery, TCP, UDP, 6LoWPAN, SocketCAN, Bluetooth, IEEE 802.15.4, Raw Packet, Local/Unix Domain, Netlink, RPMsg, Userspace Sockets, and `AF_VSOCK` Virtual Sockets), routing tables (`route`), packet fragmentation (`ipfrag`), cross-interface packet forwarding (`netforward`), NAT (`nat`), packet filtering and `iptables` (`ipfilter`, `netfilter`), `/proc/net` observability (`procfs`), interrupt-free polling I/O (`netpoll`), and core locking/buffer/checksum utilities (`utils`).

## Interface
- `[net_initialize.c:net_initialize]` - Top-level initialization entry point called once from `nx_start()` during OS power-up to initialize enabled networking subsystems (`bluetooth_initialize`, `ieee802154_initialize`, `net_init_route`, `sixlowpan_initialize`, `usrsock_initialize`).
- [./arp/README.md](./arp/README.md) - IPv4 Ethernet Address Resolution Protocol (ARP), ARP cache table, outbound packet queueing, and RFC 5227 Address Conflict Detection.
- [./bluetooth/README.md](./bluetooth/README.md) - `AF_BLUETOOTH` socket protocol family, connection management, RX frame container pools, and radio driver binding.
- [./can/README.md](./can/README.md) - SocketCAN (`PF_CAN`) protocol family supporting `CAN_RAW` and ISO 15765-2 (`CAN_ISOTP`) sockets.
- [./devif/README.md](./devif/README.md) - Network Device Interface (`devif`) callback chains, protocol polling (`devif_poll`), loopback handling, and `ipv4_input`/`ipv6_input` entry points.
- [./icmp/README.md](./icmp/README.md) - IPv4 ICMP Echo/Error processing, `IPPROTO_ICMP` datagram sockets, and IPv4 Path MTU Discovery cache.
- [./icmpv6/README.md](./icmpv6/README.md) - IPv6 ICMPv6 Echo/Error processing, Neighbor Discovery, Router Discovery, SLAAC (`icmpv6_autoconfig`), `IPPROTO_ICMPV6` sockets, and IPv6 PMTU cache.
- [./ieee802154/README.md](./ieee802154/README.md) - `PF_IEEE802154` raw packet socket family, connection management, and radio driver integration.
- [./igmp/README.md](./igmp/README.md) - IPv4 Internet Group Management Protocol Version 2 (IGMPv2) multicast group management and MAC filtering.
- [./inet/README.md](./inet/README.md) - `AF_INET` and `AF_INET6` socket interface dispatcher (`inet_sockif`), IPv4/IPv6 header builders, IP-level socket options, and TX drain logic.
- [./ipfilter/README.md](./ipfilter/README.md) - IPv4 and IPv6 packet filtering engine supporting `INPUT`, `FORWARD`, and `OUTPUT` chains.
- [./ipfrag/README.md](./ipfrag/README.md) - IPv4 and IPv6 outbound packet fragmentation and inbound fragment reassembly with watchdog timeouts.
- [./local/README.md](./local/README.md) - Unix domain (`AF_UNIX` / `AF_LOCAL`) stream and datagram sockets backed by VFS FIFOs with optional `SCM_RIGHTS`/`SCM_CREDENTIALS` support.
- [./mld/README.md](./mld/README.md) - IPv6 Multicast Listener Discovery (MLDv1/MLDv2) group membership state machine, timers, and multicast MAC filtering.
- [./nat/README.md](./nat/README.md) - IPv4 (NAT44) and IPv6 (NAT66) full-cone and symmetric Network Address and Port Translation across TCP, UDP, and ICMP/ICMPv6.
- [./neighbor/README.md](./neighbor/README.md) - IPv6 Neighbor Table management and outbound L2 Ethernet frame encapsulation.
- [./netdev/README.md](./netdev/README.md) - Network device registry (`g_netdevices`), interface indexing, `ioctl` dispatch, carrier state, IOB management, and upper-layer checksums.
- [./netfilter/README.md](./netfilter/README.md) - Linux-compatible `iptables` and `ip6tables` socket option control plane for configuring `ipfilter` and `nat` tables.
- [./netforward/README.md](./netforward/README.md) - Cross-device IPv4, IPv6, broadcast/multicast, and CAN frame forwarding subsystem.
- [./netlink/README.md](./netlink/README.md) - `AF_NETLINK` socket protocol implementation supporting `NETLINK_ROUTE` and `NETLINK_NETFILTER` requests and kernel event broadcasts.
- [./netpoll/README.md](./netpoll/README.md) - Interrupt-free polling UDP and packet I/O (`netpoll`) for crash-dump and panic-time networking.
- [./pkt/README.md](./pkt/README.md) - Raw L2 packet sockets (`PF_PACKET`) for direct Ethernet frame transmission and reception.
- [./procfs/README.md](./procfs/README.md) - `/proc/net` virtual filesystem entries exposing device status, stack statistics, routes, MLD groups, and active TCP/UDP sockets.
- [./route/README.md](./route/README.md) - IPv4 and IPv6 routing tables (`RAMROUTE`, `ROMROUTE`, `FILEROUTE`) and route caching (`CACHEROUTE`).
- [./rpmsg/README.md](./rpmsg/README.md) - Inter-processor `AF_RPMSG` stream and datagram sockets over OpenAMP/RPMsg endpoints.
- [./sixlowpan/README.md](./sixlowpan/README.md) - 6LoWPAN adaptation layer providing IPHC (`HC06`)/`HC1` header compression, fragmentation/reassembly, and IEEE 802.15.4 / packet radio framing.
- [./socket/README.md](./socket/README.md) - BSD/POSIX socket syscalls and internal `psock_*` VFS socket layer.
- [./tcp/README.md](./tcp/README.md) - Transmission Control Protocol (TCP) state machine, congestion control, SACK, timers, and socket I/O.
- [./udp/README.md](./udp/README.md) - User Datagram Protocol (UDP) connection management, read-ahead/write-buffer queuing, and socket I/O.
- [./usrsock/README.md](./usrsock/README.md) - Userspace socket (`usrsock`) kernel proxy forwarding socket operations over `/dev/usrsock` to a userspace daemon.
- [./utils/README.md](./utils/README.md) - Networking utilities including `net_lock`, `conn_dev_lock`, `net_bufpool_s`, Internet checksums, `cmsg` helpers, mask/prefix conversions, and `net_snoop`.
- [./vsock/README.md](./vsock/README.md) - Virtual Socket (`AF_VSOCK`) protocol family supporting VirtIO, Vhost, and local loopback transports for guest/host VM communication.

## Invariants
- `[net_initialize.c:net_initialize]` must be called once during OS bring-up before any network device driver is registered, at a stage where base OS semaphore/mutex facilities are initialized.

## Side Effects
- Initializes global connection pools, container pools, routing tables, and 6LoWPAN reassembly/compression contexts across enabled networking subcomponents.

## Verification
- Run: `make test`
