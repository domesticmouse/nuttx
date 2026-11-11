# Network Database and DNS Resolver (`libs/libc/netdb`)

## Overview
Implements the POSIX `<netdb.h>` and `<resolv.h>` network database and DNS client resolver subsystem (`CONFIG_LIBC_NETDB`). Provides host and service name resolution (`getaddrinfo`, `freeaddrinfo`, `getnameinfo`, `gethostbyname`, `gethostbyaddr`, `getservbyname`, `getservbyport`, `getprotobyname`), `/etc/hosts` parsing (`CONFIG_NETDB_HOSTFILE`), DNS client UDP/TCP querying, DNS response caching, nameserver configuration (`/etc/resolv.conf` or in-memory), and `rexec()` remote command execution.

## Interface
- `[lib_getaddrinfo.c:getaddrinfo]`, `[lib_freeaddrinfo.c:freeaddrinfo]`, `[lib_getnameinfo.c:getnameinfo]`, `[lib_gaistrerror.c:gai_strerror]` - Protocol-independent address-to-name and name-to-address translation and `struct addrinfo` lifecycle management.
- `[lib_gethostbyname.c:gethostbyname]`, `[lib_gethostbynamer.c:gethostbyname_r]`, `[lib_gethostbyname2.c:gethostbyname2]`, `[lib_gethostbyname2r.c:gethostbyname2_r]`, `[lib_gethostentbynamer.c:gethostentbyname_r]`, `[lib_gethostbyaddr.c:gethostbyaddr]`, `[lib_gethostbyaddrr.c:gethostbyaddr_r]` - Host entry (`struct hostent`) resolution via loopback check, `/etc/hosts`, DNS cache, and live DNS queries.
- `[lib_getservbyname.c:getservbyname]`, `[lib_getservbynamer.c:getservbyname_r]`, `[lib_getservbyport.c:getservbyport]`, `[lib_getservbyportr.c:getservbyport_r]` - Service database (`struct servent`) lookups by name or port number against `g_services_db` / `/etc/services`.
- `[lib_proto.c:setprotoent]`, `[lib_proto.c:endprotoent]`, `[lib_proto.c:getprotoent]`, `[lib_proto.c:getprotobyname]`, `[lib_proto.c:getprotobynumber]`, `[lib_protor.c:setprotoent_r]`, `[lib_protor.c:endprotoent_r]`, `[lib_protor.c:getprotoent_r]`, `[lib_protor.c:getprotobyname_r]`, `[lib_protor.c:getprotobynumber_r]` - Protocol database (`/etc/protocols`) iteration and lookup functions.
- `[lib_dnsaddserver.c:dns_add_nameserver]`, `[lib_dnsdelserver.c:dns_del_nameserver]`, `[lib_dnsdelserver.c:dns_del_nameserver_by_index]`, `[lib_dnsdefaultserver.c:dns_default_nameserver]`, `[lib_dnsforeach.c:dns_foreach_nameserver]`, `[lib_dnsnotify.c:dns_register_notify]`, `[lib_dnsnotify.c:dns_unregister_notify]`, `[lib_dnsnotify.c:dns_notify_nameserver]` - DNS nameserver registration, removal, enumeration, and change notification callbacks (`CONFIG_NETDB_DNSCLIENT`).
- `[lib_dnsinit.c:dns_lock]`, `[lib_dnsinit.c:dns_unlock]`, `[lib_dnsinit.c:dns_breaklock]`, `[lib_dnsinit.c:dns_restorelock]`, `[lib_dnsbind.c:dns_bind]`, `[lib_dnsquery.c:dns_query]`, `[lib_dnsqueryfamily.c:dns_is_queryfamily]`, `[lib_dnsqueryfamily.c:dns_set_queryfamily]`, `[lib_dnscache.c:dns_save_answer]`, `[lib_dnscache.c:dns_clear_answer]`, `[lib_dnscache.c:dns_find_answer]` - Internal DNS mutex locking, socket binding, query transmission, and TTL-aware answer cache management.
- `[lib_dn.c:dn_comp]`, `[lib_dn.c:dn_expand]`, `[lib_dn.c:dn_skipname]`, `[lib_resinit.c:res_init]`, `[lib_resinit.c:__res_state]`, `[lib_resmkquery.c:res_mkquery]`, `[lib_resquery.c:res_query]`, `[lib_resquery.c:res_search]`, `[lib_ressend.c:res_send]` - `<resolv.h>` domain name compression/expansion and raw DNS resolver packet construction/transmission.
- `[lib_netdb.c:g_hostent]`, `[lib_netdb.c:g_hostbuffer]`, `[lib_netdb.c:h_errno]`, `[lib_netdb.c:convert_hostent]`, `[lib_parsehostfile.c:parse_hostfile]`, `[lib_herror.c:herror]`, `[lib_herror.c:hstrerror]`, `[lib_rexec.c:rexec]`, `[lib_rexec.c:rexec_af]` - Shared hostent buffers, `h_errno` error reporting, `/etc/hosts` line parser, and remote execution client.

## Invariants
- Non-reentrant functions (`[lib_gethostbyname.c:gethostbyname]`, `[lib_gethostbyaddr.c:gethostbyaddr]`) use shared static storage (`[lib_netdb.c:g_hostent]`, `[lib_netdb.c:g_hostbuffer]`) and global `[lib_netdb.c:h_errno]`.
- DNS hostname lengths in `[lib_dnsquery.c:dns_query]` must not exceed `CONFIG_NETDB_DNSCLIENT_NAMESIZE`.
- Address family arguments to `[lib_dnsqueryfamily.c:dns_is_queryfamily]` and `[lib_gethostbyaddrr.c:gethostbyaddr_r]` must be `AF_INET` or `AF_INET6`.

## Side Effects
- Acquires and releases the recursive DNS mutex `g_dns_lock` (`[lib_dnsinit.c:dns_lock]`, `[lib_dnsinit.c:dns_unlock]`) when mutating or querying the DNS cache, nameserver table, or notification list.
- Opens sockets, binds UDP/TCP ports (`[lib_dnsbind.c:dns_bind]`), sends DNS queries (`send`/`recv`), and updates `g_dns_cache` (`[lib_dnscache.c:dns_save_answer]`).
- Reads and writes `/etc/hosts`, `/etc/resolv.conf`, and `/etc/protocols` files when file-backed configurations (`CONFIG_NETDB_HOSTFILE`, `CONFIG_NETDB_RESOLVCONF`) are enabled.

## Verification
- Run: `make test`
