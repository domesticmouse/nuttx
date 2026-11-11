# Network Address Translation (`net/nat`)

## Overview
The `net/nat` component implements IPv4 (NAT44) and IPv6 (NAT66) Network Address and Port Translation (`CONFIG_NET_NAT`). It supports both full-cone and symmetric NAT modes across TCP, UDP, and ICMP/ICMPv6, including translation of embedded L3/L4 headers inside ICMP/ICMPv6 error messages, hash-indexed inbound/outbound connection tracking tables with idle expiration, and incremental checksum updates.

## Interface
- `[nat.h:struct ipv4_nat_entry_s]` - NAT44 translation binding entry storing `dev`, `local_ip`, `external_ip`, `peer_ip`, `local_port`, `external_port`, `peer_port`, `protocol`, and `expire_time`.
- `[nat.h:struct ipv6_nat_entry_s]` - NAT66 translation binding entry storing IPv6 local, external, and peer addresses/ports, `protocol`, and `expire_time`.
- `[nat.h:enum nat_manip_type_e]` - Address/port manipulation direction (`NAT_MANIP_SRC`, `NAT_MANIP_DST`).
- `[nat.c:nat_enable]` - Enables NAT on an external network interface `dev` (`[nat.c:nat_disable]` disables NAT and purges active entries for `dev`).
- `[nat.c:nat_lock]` - Acquires the global NAT mutex (`[nat.c:nat_unlock]` releases it).
- `[nat.c:nat_port_inuse]` - Checks whether a `(domain, protocol, ip, port)` tuple is already in use by local sockets or NAT bindings.
- `[nat.c:nat_port_select]` - Selects an available external port/ICMP ID for a new NAT binding.
- `[nat.c:nat_expire_time]` - Computes the expiration tick for a protocol (`TCP`, `UDP`, `ICMP`, `ICMPv6`).
- `[ipv4_nat.c:ipv4_nat_inbound]` - Translates destination addresses/ports on inbound IPv4 packets arriving on a NAT-enabled device.
- `[ipv4_nat.c:ipv4_nat_outbound]` - Translates source addresses/ports on outbound IPv4 packets leaving a NAT-enabled device.
- `[ipv4_nat_entry.c:ipv4_nat_entry_foreach]` - Iterates over all active NAT44 entries (`[ipv4_nat_entry.c:ipv4_nat_entry_clear]` clears all entries for `dev`).
- `[ipv4_nat_entry.c:ipv4_nat_inbound_entry_find]` - Looks up a NAT44 entry for inbound traffic (`[ipv4_nat_entry.c:ipv4_nat_outbound_entry_find]` looks up or creates an entry for outbound traffic).
- `[ipv6_nat.c:ipv6_nat_inbound]` - Translates destination addresses/ports on inbound IPv6 packets (`[ipv6_nat.c:ipv6_nat_outbound]` translates outbound IPv6 packets).
- `[ipv6_nat_entry.c:ipv6_nat_entry_foreach]` - Iterates over active NAT66 entries (`[ipv6_nat_entry.c:ipv6_nat_entry_clear]`, `[ipv6_nat_entry.c:ipv6_nat_inbound_entry_find]`, `[ipv6_nat_entry.c:ipv6_nat_outbound_entry_find]` manage NAT66 bindings).

## Invariants
- All reads and mutations of the NAT44 and NAT66 inbound/outbound hash tables must be protected by `[nat.c:nat_lock]` / `[nat.c:nat_unlock]`.
- `[nat.c:nat_port_select]` guarantees that newly allocated external ports do not collide with any active local TCP/UDP/ICMP socket or existing NAT binding.

## Side Effects
- Rewrites IPv4/IPv6 source or destination addresses, L4 ports/ICMP IDs, and incremental checksums (`[nat.h:nat_chksum_adjust]`) directly inside packet IOBs.
- Allocates, refreshes, and reclaims `[nat.h:struct ipv4_nat_entry_s]` and `[nat.h:struct ipv6_nat_entry_s]` nodes on the kernel heap and emits Netlink conntrack notifications (`netlink_conntrack_notify`) when `CONFIG_NETLINK_NETFILTER` is enabled.

## Verification
- Run: `make test`
