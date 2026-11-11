# Netfilter & Xtables Interfaces (`include/nuttx/net/netfilter`)

## Overview
Defines Netfilter hook constants, protocol families, Xtables rule/match/target structures, IPv4 (`iptables`), IPv6 (`ip6tables`), and Network Address Translation (`nf_nat`) data structures for packet filtering and mangling in the NuttX network stack.

## Interface
- `netfilter.h:enum nf_inet_hooks`, `netfilter.h:union nf_inet_addr`, `netfilter.h:NF_DROP`, `netfilter.h:NF_ACCEPT`, `netfilter.h:NF_STOLEN`, `netfilter.h:NF_QUEUE`, `netfilter.h:NF_REPEAT`, `netfilter.h:NF_STOP`
- `x_tables.h:struct xt_entry_target`, `x_tables.h:struct xt_standard_target`, `x_tables.h:struct xt_error_target`, `x_tables.h:struct xt_entry_match`, `x_tables.h:struct xt_counters`, `x_tables.h:struct xt_counters_info`, `x_tables.h:struct xt_tcp`, `x_tables.h:struct xt_udp`, `x_tables.h:XT_ALIGN`, `x_tables.h:XT_STANDARD_TARGET`, `x_tables.h:XT_ERROR_TARGET`, `x_tables.h:XT_MASQUERADE_TARGET`, `x_tables.h:XT_REJECT_TARGET`
- `ip_tables.h:struct ipt_ip`, `ip_tables.h:struct ipt_entry`, `ip_tables.h:struct ipt_getinfo`, `ip_tables.h:struct ipt_replace`, `ip_tables.h:struct ipt_get_entries`, `ip_tables.h:struct ipt_icmp`, `ip_tables.h:ipt_get_target`, `ip_tables.h:ipt_entry_for_every`, `ip_tables.h:IPT_MATCH`, `ip_tables.h:IPT_TARGET`, `ip_tables.h:IPT_FILL_ENTRY`, `ip_tables.h:IPT_SO_SET_REPLACE`, `ip_tables.h:IPT_SO_GET_INFO`, `ip_tables.h:IPT_SO_GET_ENTRIES`
- `ip6_tables.h:struct ip6t_ip6`, `ip6_tables.h:struct ip6t_entry`, `ip6_tables.h:struct ip6t_getinfo`, `ip6_tables.h:struct ip6t_replace`, `ip6_tables.h:struct ip6t_get_entries`, `ip6_tables.h:struct ip6t_icmp`, `ip6_tables.h:ip6t_get_target`, `ip6_tables.h:ip6t_entry_for_every`, `ip6_tables.h:IP6T_MATCH`, `ip6_tables.h:IP6T_TARGET`, `ip6_tables.h:IP6T_FILL_ENTRY`, `ip6_tables.h:IP6T_SO_SET_REPLACE`, `ip6_tables.h:IP6T_SO_GET_INFO`, `ip6_tables.h:IP6T_SO_GET_ENTRIES`
- `nf_nat.h:union nf_conntrack_man_proto`, `nf_nat.h:struct nf_nat_ipv4_range`, `nf_nat.h:struct nf_nat_ipv4_multi_range_compat`, `nf_nat.h:TABLE_NAME_NAT`

## Invariants
- Rule table entries (`ip_tables.h:struct ipt_entry`, `ip6_tables.h:struct ip6t_entry`) and match/target payloads must be aligned using `x_tables.h:XT_ALIGN` (`struct _xt_align`), with `target_offset` pointing to the embedded `xt_entry_target` and `next_offset` advancing to the subsequent entry.
- Hook indices in `ip_tables.h:struct ipt_getinfo`, `ip_tables.h:struct ipt_replace`, `ip6_tables.h:struct ip6t_getinfo`, and `ip6_tables.h:struct ip6t_replace` are bounded by `netfilter.h:NF_INET_NUMHOOKS`.

## Side Effects
- `ip_tables.h:IPT_FILL_ENTRY` and `ip6_tables.h:IP6T_FILL_ENTRY` mutate entry offsets and copy the target name into the embedded `xt_entry_target` structure.

## Verification
- Run: `make test`
