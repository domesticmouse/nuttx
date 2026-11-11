# Network Address, Byte-Order, and Interface Utilities (`libs/libc/net`)

## Overview
Implements standard POSIX and BSD `<arpa/inet.h>`, `<net/if.h>`, `<ifaddrs.h>`, `<netinet/ether.h>`, and `<sys/socket.h>` user-space networking helpers in `libc`. Covers network/host byte-order conversions (`htons`, `htonl`, `htonq`), IPv4/IPv6 text-to-binary address parsing and formatting (`inet_pton`, `inet_ntop`, `inet_aton`, `inet_ntoa`, `inet_addr`, `inet_network`), Ethernet MAC formatting (`ether_aton`, `ether_ntoa`), Base64 encoding (`b64_ntop`, `b64_pton`), network interface index/address enumeration (`getifaddrs`, `freeifaddrs`, `if_nametoindex`, `if_indextoname`, `if_nameindex`, `if_freenameindex`), routing table `ioctl` wrappers (`addroute`, `delroute`), and `accept()`.

## Interface
- `[lib_htons.c:htons]`, `[lib_htons.c:ntohs]`, `[lib_htonl.c:htonl]`, `[lib_htonl.c:ntohl]`, `[lib_htonq.c:htonq]`, `[lib_htonq.c:ntohq]` - 16-bit, 32-bit, and 64-bit host/network byte-order conversions.
- `[lib_inetpton.c:inet_pton]`, `[lib_inetntop.c:inet_ntop]` - Converts IPv4 (`AF_INET`) and IPv6 (`AF_INET6`) addresses between presentation strings and binary network byte order.
- `[lib_inetaton.c:inet_aton]`, `[lib_inetaddr.c:inet_addr]`, `[lib_inetnetwork.c:inet_network]`, `[lib_inetntoa.c:inet_ntoa]`, `[lib_inetntoa.c:inet_ntoa_r]` - IPv4 dotted-decimal string parsing and formatting functions.
- `[lib_etheraton.c:ether_aton]`, `[lib_etheraton.c:ether_aton_r]`, `[lib_etherntoa.c:ether_ntoa]`, `[lib_etherntoa.c:ether_ntoa_r]` - Converts 48-bit Ethernet MAC addresses between colon-separated hex strings and `struct ether_addr`.
- `[lib_base64.c:b64_ntop]`, `[lib_base64.c:b64_pton]` - Encodes binary buffers into Base64 strings and decodes Base64 strings back into binary.
- `[lib_getifaddrs.c:getifaddrs]`, `[lib_freeifaddrs.c:freeifaddrs]` - Enumerates local network interfaces and their IPv4/IPv6 addresses, netmasks, broadcast/destination addresses, and hardware addresses into a linked list of `struct ifaddrs`.
- `[lib_nametoindex.c:if_nametoindex]`, `[lib_indextoname.c:if_indextoname]`, `[lib_nameindex.c:if_nameindex]`, `[lib_freenameindex.c:if_freenameindex]` - Maps between network interface names and interface indices (`SIOCGIFINDEX`, `SIOCGIFNAME`).
- `[lib_addroute.c:addroute]`, `[lib_delroute.c:delroute]` - Formats `struct rtentry` and issues `SIOCADDRT` / `SIOCDELRT` routing table `ioctl` calls.
- `[lib_accept.c:accept]` - Wrapper around `accept4(sockfd, addr, addrlen, 0)`.
- `[lib_addrconfig.c:in6addr_any]`, `[lib_addrconfig.c:in6addr_loopback]`, `[lib_loopback.c:g_lo_hostname]`, `[lib_loopback.c:g_lo_ipv4addr]`, `[lib_loopback.c:g_lo_ipv4mask]`, `[lib_loopback.c:g_lo_ipv6addr]`, `[lib_loopback.c:g_lo_ipv6mask]` - Global IPv6 wildcard/loopback address constants and local loopback constants (`CONFIG_NET_LOOPBACK`).

## Invariants
- `src` and `dest` passed to `[lib_inetpton.c:inet_pton]` and `[lib_inetntop.c:inet_ntop]` must be non-NULL (`DEBUGASSERT(src && dest)`).
- Non-reentrant `[lib_inetntoa.c:inet_ntoa]` and `[lib_etherntoa.c:ether_ntoa]` return pointers to static buffers that are overwritten on subsequent calls.

## Side Effects
- `[lib_getifaddrs.c:getifaddrs]`, `[lib_nametoindex.c:if_nametoindex]`, `[lib_indextoname.c:if_indextoname]`, and `[lib_nameindex.c:if_nameindex]` open a temporary socket (`socket()`), issue network device `ioctl` calls (`SIOCGIFNAME`, `SIOCGIFFLAGS`, `SIOCGIFADDR`, `SIOCGLIFADDR`, `SIOCGIFINDEX`), and close the socket.
- `[lib_getifaddrs.c:getifaddrs]`, `[lib_freeifaddrs.c:freeifaddrs]`, `[lib_nameindex.c:if_nameindex]`, and `[lib_freenameindex.c:if_freenameindex]` allocate and free heap memory via `lib_zalloc()`, `lib_malloc()`, and `lib_free()`.
- Sets thread `errno` (`EAFNOSUPPORT`, `ENOSPC`, `EINVAL`, `ENOBUFS`) on error.

## Verification
- Run: `make test`
