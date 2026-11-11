# Link-Layer, Netlink & Inter-Processor Socket Address Headers (`include/netpacket`)

## Overview
Defines socket address structures (`sockaddr_*`), protocol constants, and packet/control message headers for raw link-layer packet sockets (`packet.h`), Netlink routing/configuration sockets (`netlink.h`, `if_addr.h`), Bluetooth L2CAP/HCI/RFCOMM sockets (`bluetooth.h`), IEEE 802.15.4 sockets (`ieee802154.h`), RPMsg inter-processor sockets (`rpmsg.h`), and hypervisor VM sockets (`vm_sockets.h`).

## Interface
- `packet.h:sockaddr_ll`, `packet.h:packet_mreq`, `packet.h:PACKET_HOST`, `packet.h:PACKET_BROADCAST`, `packet.h:PACKET_MULTICAST`, `packet.h:PACKET_ADD_MEMBERSHIP`, `packet.h:PACKET_DROP_MEMBERSHIP` - `AF_PACKET` link-layer socket address and multicast/promiscuous membership options.
- `netlink.h:sockaddr_nl`, `netlink.h:nlmsghdr`, `netlink.h:nlmsgerr`, `netlink.h:rtattr`, `netlink.h:ifinfomsg`, `netlink.h:rtmsg`, `netlink.h:ndmsg`, `netlink.h:NETLINK_ROUTE`, `netlink.h:NLMSG_ALIGN`, `netlink.h:NLMSG_DATA`, `netlink.h:RTA_NEXT`, `if_addr.h:ifaddrmsg`, `if_addr.h:ifa_cacheinfo` - `AF_NETLINK` message framing, routing attributes (`RTA_*`), link/neighbor/route messages, and interface address structures.
- `bluetooth.h:sockaddr_l2`, `bluetooth.h:sockaddr_hci`, `bluetooth.h:sockaddr_rc`, `bluetooth.h:BTPROTO_L2CAP`, `bluetooth.h:BTPROTO_HCI`, `bluetooth.h:BTPROTO_RFCOMM` - `AF_BLUETOOTH` socket address structures and protocol numbers.
- `ieee802154.h:sockaddr_ieee802154_s`, `ieee802154.h:ieee802154_saddr_s`, `ieee802154.h:IEEE802154_PANID_BROADCAST` - `AF_IEEE802154` short and extended PAN socket address definitions.
- `rpmsg.h:sockaddr_rpmsg`, `rpmsg.h:RPMSG_SOCKET_CPU_SIZE`, `rpmsg.h:RPMSG_SOCKET_NAME_SIZE` - `AF_RPMSG` processor-name and service-endpoint socket address structure.
- `vm_sockets.h:sockaddr_vm`, `vm_sockets.h:VMADDR_CID_ANY`, `vm_sockets.h:VMADDR_CID_HYPERVISOR`, `vm_sockets.h:VMADDR_CID_LOCAL`, `vm_sockets.h:VMADDR_CID_HOST`, `vm_sockets.h:SO_VM_SOCKETS_BUFFER_SIZE` - `AF_VSOCK` virtual machine Context ID (`CID`) and port socket address definitions.

## Invariants
- Netlink messages (`netlink.h:nlmsghdr`) and routing attributes (`netlink.h:rtattr`) must be aligned to `NLMSG_ALIGNTO` / `RTA_ALIGNTO` (4-byte boundaries) using `NLMSG_ALIGN` and `RTA_ALIGN`.
- In `rpmsg.h:sockaddr_rpmsg`, `rp_cpu` and `rp_name` character arrays must be NUL-terminated within `RPMSG_SOCKET_CPU_SIZE` and `RPMSG_SOCKET_NAME_SIZE` bytes.

## Side Effects
- None (pure socket address and protocol header definitions).

## Verification
- Run: `make test`
