# Netfilter / Iptables (`net/netfilter`)

## Overview
The `net/netfilter` component implements the Linux-compatible `iptables` (`IPPROTO_IP`) and `ip6tables` (`IPPROTO_IPV6`) socket option control plane (`CONFIG_NET_IPTABLES`) for NuttX. It handles `IPT_SO_GET_INFO`, `IPT_SO_GET_ENTRIES`, and `IPT_SO_SET_REPLACE` (and their IPv6 `IP6T_*` counterparts), translating userspace `struct ipt_replace` and `struct ip6t_replace` rule tables into active configurations in the `net/nat` (`TABLE_NAT`) and `net/ipfilter` (`TABLE_FILTER`) subsystems.

## Interface
- `[ipt_sockopt.c:ipt_setsockopt]` - Handles `IPT_SO_SET_REPLACE` and `IPT_SO_SET_ADD_COUNTERS` socket options to replace IPv4 `nat` or `filter` tables.
- `[ipt_sockopt.c:ipt_getsockopt]` - Handles `IPT_SO_GET_INFO`, `IPT_SO_GET_ENTRIES`, and `IPT_SO_GET_REVISION_*` socket options to query IPv4 table metadata and rules.
- `[ipt_sockopt.c:ipt_alloc_table]` - Allocates and initializes a `struct ipt_replace` table with default standard/error targets for the requested `hook_mask`.
- `[ip6t_sockopt.c:ip6t_setsockopt]` - Handles `IP6T_SO_SET_REPLACE` and `IP6T_SO_SET_ADD_COUNTERS` socket options for IPv6 tables.
- `[ip6t_sockopt.c:ip6t_getsockopt]` - Handles `IP6T_SO_GET_INFO`, `IP6T_SO_GET_ENTRIES`, and `IP6T_SO_GET_REVISION_*` socket options for IPv6 tables.
- `[ip6t_sockopt.c:ip6t_alloc_table]` - Allocates and initializes a `struct ip6t_replace` table with default rules for the requested `hook_mask`.
- `[ipt_nat.c:ipt_nat_init]` - Initializes the default empty `nat` table (`[ipt_nat.c:ipt_nat_apply]` validates a replacement `nat` table and enables/disables `nat_enable`/`nat_disable` on target interfaces).
- `[ipt_filter.c:ipt_filter_init]` - Initializes the default IPv4 `filter` table (`[ipt_filter.c:ipt_filter_apply]` validates and applies `struct ipt_replace` rules to `net/ipfilter`).
- `[ipt_filter.c:ip6t_filter_init]` - Initializes the default IPv6 `filter` table (`[ipt_filter.c:ip6t_filter_apply]` validates and applies `struct ip6t_replace` rules to `net/ipfilter`).

## Invariants
- `[ipt_nat.c:ipt_nat_apply]`, `[ipt_filter.c:ipt_filter_apply]`, and `[ipt_filter.c:ip6t_filter_apply]` validate all entry offsets, match structures, and targets in `struct ipt_replace`/`struct ip6t_replace` before mutating active NAT or filter state, leaving the previous configuration intact if validation fails.

## Side Effects
- Allocates and frees `struct ipt_replace` and `struct ip6t_replace` rule tables on the kernel heap.
- Enables or disables NAT on network devices (`nat_enable`, `nat_disable`) and rebuilds `net/ipfilter` chains (`ipfilter_cfg_clear`, `ipfilter_cfg_add`).

## Verification
- Run: `make test`
