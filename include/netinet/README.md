# POSIX Internet Protocol Family Headers (`include/netinet`)

## Overview
Provides standard POSIX/BSD `<netinet/*.h>` headers defining IPv4 (`in.h`, `ip.h`), IPv6 (`ip6.h`, `icmp6.h`), TCP (`tcp.h`), UDP (`udp.h`), ARP/Ethernet (`if_ether.h`, `ether.h`, `arp.h`), and network byte-order types (`in_systm.h`).

## Interface
- `in.h:in_port_t`, `in.h:in_addr_t`, `in.h:in_addr`, `in.h:sockaddr_in`, `in.h:ip_mreq`, `in.h:ip_mreqn`, `in.h:ip_msfilter`, `in.h:in_pktinfo`, `in.h:in6_addr`, `in.h:sockaddr_in6`, `in.h:ipv6_mreq`, `in.h:in6_pktinfo` - IPv4 and IPv6 socket address, multicast group membership, and packet info structures.
- `in.h:ntohl`, `in.h:ntohs`, `in.h:ntohq`, `in.h:htonl`, `in.h:htons`, `in.h:htonq`, `in.h:IPPROTO_IP`, `in.h:IPPROTO_TCP`, `in.h:IPPROTO_UDP`, `in.h:IPPROTO_ICMP`, `in.h:IPPROTO_IPV6`, `in.h:INADDR_ANY`, `in.h:INADDR_LOOPBACK` - Network/host byte-order conversion functions and IP protocol numbers.
- `ip.h:iphdr`, `ip.h:ip`, `ip.h:ip_timestamp`, `ip.h:IPVERSION`, `ip.h:IPDEFTTL`, `ip.h:IPTOS_LOWDELAY` - IPv4 header structures, DSCP/TOS macros, and IP option definitions.
- `ip6.h:ip6_hdr`, `ip6.h:ip6_ext`, `ip6.h:ip6_hbh`, `ip6.h:ip6_dest`, `ip6.h:ip6_rthdr`, `ip6.h:ip6_frag` - IPv6 fixed header and extension header structures.
- `icmp6.h:icmp6_hdr`, `icmp6.h:icmp6_filter`, `icmp6.h:nd_router_solicit`, `icmp6.h:nd_router_advert`, `icmp6.h:nd_neighbor_solicit`, `icmp6.h:nd_neighbor_advert`, `icmp6.h:nd_opt_hdr`, `icmp6.h:nd_opt_prefix_info` - ICMPv6 packet headers, socket filter macros (`ICMP6_FILTER_SETPASS`, `ICMP6_FILTER_SETBLOCK`), and Neighbor Discovery (`ND`) messages.
- `tcp.h:tcphdr`, `tcp.h:TCP_NODELAY`, `tcp.h:TCP_KEEPIDLE`, `tcp.h:TCP_KEEPINTVL`, `tcp.h:TCP_KEEPCNT`, `tcp.h:TCP_MAXSEG` - TCP header structure and `IPPROTO_TCP` socket options.
- `udp.h:udphdr` - UDP packet header structure.
- `if_ether.h:ethhdr`, `if_ether.h:ether_arp`, `if_ether.h:ETH_ALEN`, `if_ether.h:ETH_HLEN`, `if_ether.h:ETH_P_IP`, `arp.h:SIOCSARP`, `arp.h:SIOCDARP`, `arp.h:SIOCGARP`, `ether.h:ether_ntoa`, `ether.h:ether_ntoa_r`, `ether.h:ether_aton`, `ether.h:ether_aton_r` - Ethernet/ARP frame structures, ARP table `ioctl` commands, and MAC address string formatting.
- `in_systm.h:n_short`, `in_systm.h:n_long`, `in_systm.h:n_time` - Network-order integer typedefs.

## Invariants
- Multi-byte port and address fields in `in.h:sockaddr_in` (`sin_port`, `sin_addr`), `in.h:sockaddr_in6` (`sin6_port`, `sin6_addr`), and wire headers (`ip.h:iphdr`, `ip6.h:ip6_hdr`, `tcp.h:tcphdr`, `udp.h:udphdr`) are always stored in big-endian network byte order.
- Wire header structures (`ip.h:iphdr`, `ip6.h:ip6_hdr`, `icmp6.h:icmp6_hdr`, `if_ether.h:ethhdr`, `if_ether.h:ether_arp`) are packed (`begin_packed_struct`) to prevent compiler padding on unaligned packet buffers.

## Side Effects
- `ether.h:ether_ntoa` and `ether.h:ether_aton` use static internal buffers and are not thread-safe; reentrant callers must use `ether.h:ether_ntoa_r` and `ether.h:ether_aton_r`.

## Verification
- Run: `make test`
