# IPv6 Neighbor Table (`net/neighbor`)

## Overview
The `net/neighbor` component maintains the global IPv6 Neighbor Table (`g_neighbors`) mapping IPv6 addresses to link-layer addresses (`struct neighbor_addr_s`). It provides table lookup, insertion, timestamp aging, snapshot extraction, and L2 header encapsulation or Neighbor Solicitation substitution for outbound IPv6 packets (`neighbor_out`, `neighbor_ethernet_out`).

## Interface
- `[neighbor_globals.c:g_neighbors]` - Global array of `CONFIG_NET_IPv6_NCONF_ENTRIES` `struct neighbor_entry_s` records.
- `[neighbor_findentry.c:neighbor_findentry]` - Finds the `struct neighbor_entry_s` matching `ipaddr` in `g_neighbors`.
- `[neighbor_add.c:neighbor_add]` - Inserts or updates an IPv6-to-link-layer mapping in `g_neighbors`, evicting the oldest entry if the table is full.
- `[neighbor_lookup.c:neighbor_lookup]` - Resolves the link-layer address `laddr` for an `ipaddr` from `g_neighbors` or local devices.
- `[neighbor_update.c:neighbor_update]` - Refreshes the `ne_time` timestamp on an existing Neighbor Table entry.
- `[neighbor_out.c:neighbor_out]` - Dispatches outbound IPv6 packets on `dev` to the appropriate link-layer neighbor handler (e.g., Ethernet).
- `[neighbor_ethernet_out.c:neighbor_ethernet_out]` - Prepends an Ethernet header to an outbound IPv6 packet if the next-hop MAC is known (unicast neighbor, loopback, or multicast), or overwrites `dev->d_buf` with an ICMPv6 Neighbor Solicitation if unresolved.
- `[neighbor_snapshot.c:neighbor_snapshot]` - Copies active Neighbor Table entries into a caller-provided snapshot array.
- `[neighbor_dumpentry.c:neighbor_dumpentry]` - Logs a Neighbor Table entry when `CONFIG_NET_IPv6_NEIGHBOR_DUMP` is enabled (`[neighbor_dumpentry.c:neighbor_dumpipaddr]` logs an IPv6 address).

## Invariants
- All reads and modifications of `[neighbor_globals.c:g_neighbors]` must be performed while holding the global network lock (`net_lock`).

## Side Effects
- Mutates entries and timestamps in `[neighbor_globals.c:g_neighbors]` and emits Netlink neighbor notifications (`netlink_neigh_notify`) when `CONFIG_NETLINK_ROUTE` is enabled.
- Prepends Ethernet headers to `dev->d_buf`/`dev->d_iob` or replaces an unresolved outbound IPv6 packet with an ICMPv6 Neighbor Solicitation in `[neighbor_ethernet_out.c:neighbor_ethernet_out]`.

## Verification
- Run: `make test`
