# POSIX Network Interface, ARP & Routing Headers (`include/net`)

## Overview
Provides standard BSD/POSIX `<net/if.h>`, `<net/if_arp.h>`, `<net/ethernet.h>`, and `<net/route.h>` definitions for network interface naming and flags, MII and SocketCAN `ioctl` structures, Ethernet frame headers, Address Resolution Protocol (`ARP`) hardware types, and IPv4/IPv6 routing table manipulation.

## Interface
- `if.h:if_nameindex`, `if.h:ifreq`, `if.h:lifreq`, `if.h:ifconf`, `if.h:lifconf`, `if.h:mii_ioctl_notify_s`, `if.h:mii_ioctl_data_s`, `if.h:can_ioctl_data_s`, `if.h:can_ioctl_filter_s`, `if.h:can_ioctl_state_s`, `if.h:can_ioctl_errors_s` - Network interface request structures, MII PHY register access descriptors, and SocketCAN bitrate/filter/state `ioctl` payloads.
- `if.h:if_nametoindex`, `if.h:if_indextoname`, `if.h:if_nameindex`, `if.h:if_freenameindex`, `if.h:IFNAMSIZ`, `if.h:IFF_UP`, `if.h:IFF_RUNNING`, `if.h:IFF_LOOPBACK`, `if.h:IFF_MULTICAST` - Interface index/name resolution APIs and interface status flags.
- `ethernet.h:ether_addr`, `ethernet.h:ether_header`, `ethernet.h:ETHER_ADDR_LEN`, `ethernet.h:ETHERTYPE_IP`, `ethernet.h:ETHERTYPE_ARP`, `ethernet.h:ETHERTYPE_VLAN`, `ethernet.h:ETHERTYPE_IPV6` - 48-bit Ethernet MAC address, 14-byte Ethernet II header, and EtherType constants.
- `if_arp.h:arphdr`, `if_arp.h:arpreq`, `if_arp.h:ARPHRD_ETHER`, `if_arp.h:ARPHRD_LOOPBACK`, `if_arp.h:ARPHRD_IEEE802154`, `if_arp.h:ARPOP_REQUEST`, `if_arp.h:ARPOP_REPLY` - ARP packet header, ARP cache `ioctl` request structure, and hardware/operation codes.
- `route.h:rtentry`, `route.h:in6_rtmsg`, `route.h:addroute`, `route.h:delroute`, `route.h:RTF_UP`, `route.h:RTF_GATEWAY`, `route.h:RTF_HOST` - Routing table entry structures and route addition/deletion helpers.

## Invariants
- Network interface names stored in `if.h:ifreq` (`ifr_name`) and `if.h:lifreq` (`lifr_name`) must not exceed `if.h:IFNAMSIZ` (16) bytes including the terminating NUL character.
- Array results returned by `if.h:if_nameindex` are dynamically allocated and terminated by an entry with `if_index == 0` and `if_name == NULL`, and must be freed via `if.h:if_freenameindex`.

## Side Effects
- `route.h:addroute` and `route.h:delroute` issue `SIOCADDRT` / `SIOCDELRT` `ioctl` calls on a socket descriptor, mutating the kernel IPv4/IPv6 routing table.

## Verification
- Run: `make test`
