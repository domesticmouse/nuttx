# Network Device Registry (`net/netdev`)

## Overview
The `net/netdev` component manages the global registry of network devices (`g_netdevices`) in NuttX. It handles driver registration and unregistration, interface index assignment, device lookup by name/index/IPv4/IPv6 address, per-device and list locking, network interface `ioctl` operations (`SIOCGIFCONF`, `SIOCSIFFLAGS`, IPv4/IPv6 address management, hardware ioctls), carrier state transitions (`netdev_carrier_on`/`netdev_carrier_off`), device IOB buffer preparation, upper-layer pseudo-header checksum calculation, and network-down workqueue notifications.

## Interface
- `[netdev_register.c:g_netdevices]` - Singly-linked list of registered `struct net_driver_s` network interfaces.
- `[netdev_register.c:netdev_register]` - Registers a `struct net_driver_s` driver, assigns its interface name (`d_ifname`) and index (`d_ifindex`), and initializes device locks and protocol state (`[netdev_unregister.c:netdev_unregister]` unregisters it).
- `[netdev_lock.c:netdev_lock]` - Acquires the per-device recursive mutex `dev->d_lock` (`[netdev_lock.c:netdev_unlock]` releases it; `[netdev_lock.c:netdev_list_lock]` and `[netdev_lock.c:netdev_list_unlock]` protect `g_netdevices`).
- `[netdev_verify.c:netdev_verify]` - Verifies that `dev` is currently registered in `g_netdevices`.
- `[netdev_foreach.c:netdev_foreach]` - Iterates over all registered network devices, invoking `callback(dev, arg)`.
- `[netdev_default.c:netdev_default]` - Returns the default network interface (preferring up/running interfaces or the default route device).
- `[netdev_count.c:netdev_count]` - Returns the number of registered network devices.
- `[netdev_findbyname.c:netdev_findbyname]` - Finds a registered network device by interface name (`d_ifname`).
- `[netdev_findbyindex.c:netdev_findbyindex]` - Finds a registered network device by interface index (`d_ifindex`; `[netdev_findbyindex.c:netdev_nextindex]` finds the next assigned index).
- `[netdev_findbyaddr.c:netdev_findby_lipv4addr]` - Finds a device by local IPv4 address (`[netdev_findbyaddr.c:netdev_findby_lipv6addr]`, `[netdev_findbyaddr.c:netdev_findby_ripv4addr]`, and `[netdev_findbyaddr.c:netdev_findby_ripv6addr]` resolve by local IPv6 or remote next-hop IPv4/IPv6 address).
- `[netdev_txnotify.c:netdev_ipv4_txnotify]` - Notifies the device serving an IPv4 destination that TX data is queued (`[netdev_txnotify.c:netdev_ipv6_txnotify]` and `[netdev_txnotify.c:netdev_txnotify_dev]` notify by IPv6 address or `dev` pointer).
- `[netdev_ifconf.c:netdev_ipv4_ifconf]` - Populates `SIOCGIFCONF` records for IPv4 interfaces (`[netdev_ifconf.c:netdev_ipv6_ifconf]` populates `SIOCGLIFCONF` for IPv6).
- `[netdev_ioctl.c:netdev_ifr_ioctl]` - Dispatches `struct ifreq` / `struct lifreq` socket `ioctl` commands.
- `[netdev_carrier.c:netdev_carrier_on]` - Marks `IFF_RUNNING` on `dev` and emits Netlink device notifications (`[netdev_carrier.c:netdev_carrier_off]` clears `IFF_RUNNING`).
- `[netdev_iob.c:netdev_iob_prepare]` - Allocates or prepares `dev->d_iob` with L2 header headroom (`[netdev_iob.c:netdev_iob_replace]`, `[netdev_iob.c:netdev_iob_clear]`, and `[netdev_iob.c:netdev_iob_release]` manage `dev->d_iob`).
- `[netdev_input.c:netdev_input]` - Hands an incoming IOB chain to `dev` and invokes `in_callback`.
- `[netdev_ipv6.c:netdev_ipv6_add]` - Adds an IPv6 address/prefix to `dev` (`[netdev_ipv6.c:netdev_ipv6_del]` removes it; `[netdev_ipv6.c:netdev_ipv6_addmcastmac]` and `[netdev_ipv6.c:netdev_ipv6_removemcastmac]` update solicited-node multicast MAC filters).
- `[netdev_checksum.c:ipv4_upperlayer_header_chksum]` - Computes IPv4 upper-layer pseudo-header checksum (`[netdev_checksum.c:ipv4_upperlayer_payload_chksum]`, `[netdev_checksum.c:ipv6_upperlayer_header_chksum]`, and `[netdev_checksum.c:ipv6_upperlayer_payload_chksum]` compute payload and IPv6 checksums).
- `[netdown_notifier.c:netdown_notifier_setup]` - Registers a workqueue notifier triggered when `dev` goes down (`[netdown_notifier.c:netdown_notifier_teardown]` and `[netdown_notifier.c:netdown_notifier_signal]` manage teardown and signaling).
- `[netdev_notify_recvcpu.c:netdev_notify_recvcpu]` - Signals a target CPU in SMP configurations to process a flow on `dev`.

## Invariants
- Traversal and modification of `[netdev_register.c:g_netdevices]` require holding `[netdev_lock.c:netdev_list_lock]` or the global network lock.
- Per-device state mutations and driver callbacks require holding `[netdev_lock.c:netdev_lock]` (`dev->d_lock`).

## Side Effects
- Mutates `[netdev_register.c:g_netdevices]` and interface index bitmasks (`g_devfreed`, `g_nassigned`), invokes hardware driver callbacks (`d_ifup`, `d_ifdown`, `d_txavail`, `d_ioctl`, `d_addmac`, `d_rmmac`), and dispatches workqueue/Netlink notifications when interfaces change state or addresses.

## Verification
- Run: `make test`
