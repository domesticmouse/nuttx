# Routing Table (`net/route`)

## Overview
The `net/route` component implements IPv4 and IPv6 routing tables (`CONFIG_NET_ROUTE`) for NuttX. It supports in-memory (`CONFIG_ROUTE_IN_RAM`), read-only (`CONFIG_ROUTE_IN_ROM`), and VFS file-backed (`CONFIG_ROUTE_IN_FILE`) routing tables, longest-prefix-match next-hop resolution (`net_ipv4_router`, `net_ipv6_router`), device-scoped route lookups (`netdev_ipv4_router`, `netdev_ipv6_router`), and an optional LRU route cache (`CONFIG_NET_CACHEROUTE`).

## Interface
- `[route.h:struct net_route_ipv4_s]` - IPv4 route entry containing `target`, `netmask`, and `router` addresses (`[route.h:struct net_route_ipv6_s]` stores IPv6 `target`, `netmask`, and `router`).
- `[route.h:route_handler_ipv4_t]` - Callback signature for `net_foreachroute_ipv4` (`[route.h:route_handler_ipv6_t]` is used by `net_foreachroute_ipv6`).
- `[net_initroute.c:net_init_route]` - Initializes the IPv4 and IPv6 routing tables and optional route caches at boot.
- `[net_add_ramroute.c:net_addroute_ipv4]` - Adds a new IPv4 route entry (`[net_add_ramroute.c:net_addroute_ipv6]` adds an IPv6 route; also implemented in `net_fileroute.c` when `CONFIG_ROUTE_IN_FILE` is selected).
- `[net_del_ramroute.c:net_delroute_ipv4]` - Deletes matching IPv4 route entries and flushes the route cache (`[net_del_ramroute.c:net_delroute_ipv6]` deletes IPv6 routes).
- `[net_router.c:net_ipv4_router]` - Resolves the next-hop router IPv4 address for an off-link `target` (`[net_router.c:net_ipv6_router]` resolves IPv6 next-hop routers).
- `[netdev_router.c:netdev_ipv4_router]` - Resolves the next-hop IPv4 router reachable via a specific `dev` (`[netdev_router.c:netdev_ipv6_router]` resolves for IPv6 on `dev`).
- `[net_foreach_ramroute.c:net_foreachroute_ipv4]` - Traverses all IPv4 routes, invoking `handler` until non-zero is returned (`[net_foreach_ramroute.c:net_foreachroute_ipv6]` traverses IPv6 routes).
- `[net_dumproute.c:net_ipv4_dumproute]` - Logs an IPv4 route entry (`[net_dumproute.c:net_ipv6_dumproute]` logs an IPv6 route).
- `[net_alloc_ramroute.c:net_allocroute_ipv4]` - Allocates an in-memory IPv4 route entry (`[net_alloc_ramroute.c:net_allocroute_ipv6]`, `[net_alloc_ramroute.c:net_freeroute_ipv4]`, and `[net_alloc_ramroute.c:net_freeroute_ipv6]` allocate/free in-RAM route entries).
- `[net_cacheroute.c:net_init_cacheroute]` - Initializes the route cache (`[net_cacheroute.c:net_addcache_ipv4]`, `[net_cacheroute.c:net_addcache_ipv6]`, `[net_cacheroute.c:net_flushcache_ipv4]`, and `[net_cacheroute.c:net_flushcache_ipv6]` manage cached routes).
- `[net_fileroute.c:net_openroute_ipv4]` - Opens the backing VFS file for IPv4 routes (`[net_fileroute.c:net_openroute_ipv6]` opens the IPv6 backing file).

## Invariants
- `[net_router.c:net_ipv4_router]` and `[net_router.c:net_ipv6_router]` select the longest-prefix match whose prefix length is strictly greater than `prefixlen` (starting from `-1` so `/0` default routes match).
- All routing table and cache traversals and modifications must hold `net_lockroute_ipv4` / `net_lockroute_ipv6`.

## Side Effects
- Allocates and frees route entries in `g_ipv4_routes`/`g_ipv6_routes` (or reads/writes VFS files under `CONFIG_ROUTE_FILEDIR`), updates or flushes `g_ipv4_cacheroutes`/`g_ipv6_cacheroutes`, and emits Netlink route notifications (`netlink_route_notify`).

## Verification
- Run: `make test`
