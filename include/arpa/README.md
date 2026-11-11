# POSIX ARPA Internet & DNS Headers (`include/arpa`)

## Overview
Provides standard POSIX/BSD `<arpa/inet.h>` and `<arpa/nameser.h>` definitions for IPv4/IPv6 address string conversion, network/host address manipulation, and Domain Name System (`DNS`) packet constants and opcodes.

## Interface
- `inet.h:inet_aton`, `inet.h:inet_addr`, `inet.h:inet_network`, `inet.h:inet_ntoa`, `inet.h:inet_ntoa_r`, `inet.h:inet_makeaddr`, `inet.h:inet_lnaof`, `inet.h:inet_netof`, `inet.h:inet_pton`, `inet.h:inet_ntop` - IPv4 and IPv6 binary-to-text and text-to-binary address conversion functions.
- `nameser.h:__ns_opcode`, `nameser.h:__ns_rcode`, `nameser.h:__ns_class`, `nameser.h:__ns_type` - DNS protocol opcodes (`ns_o_query`, `ns_o_update`), response codes (`ns_r_noerror`, `ns_r_nxdomain`), classes (`ns_c_in`), and resource record types (`ns_t_a`, `ns_t_aaaa`, `ns_t_cname`, `ns_t_ptr`, `ns_t_srv`, `ns_t_txt`).
- `nameser.h:NS_PACKETSZ`, `nameser.h:NS_MAXDNAME`, `nameser.h:NS_MAXCDNAME`, `nameser.h:NS_MAXLABEL`, `nameser.h:NS_HFIXEDSZ`, `nameser.h:NS_QFIXEDSZ`, `nameser.h:NS_RRFIXEDSZ` - DNS message size limits and header sizes.

## Invariants
- Callers of `inet.h:inet_ntop` must provide a destination buffer of at least `INET_ADDRSTRLEN` (16) bytes for `AF_INET` or `INET6_ADDRSTRLEN` (46) bytes for `AF_INET6`.
- DNS labels in `nameser.h` must not exceed `nameser.h:NS_MAXLABEL` (63) octets, and uncompressed domain names must not exceed `nameser.h:NS_MAXDNAME` (1025) characters.

## Side Effects
- `inet.h:inet_ntoa` writes to a shared static character buffer and is not thread-safe; multi-threaded callers should use `inet.h:inet_ntoa_r` or `inet.h:inet_ntop`.

## Verification
- Run: `make test`
