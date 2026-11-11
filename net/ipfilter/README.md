# IP Packet Filter (`net/ipfilter`)

## Overview
The `net/ipfilter` component implements the core IPv4 and IPv6 packet filtering engine (`CONFIG_NET_IPFILTER`) for NuttX. It evaluates packets traversing `INPUT`, `FORWARD`, and `OUTPUT` chains against ordered rule lists (`struct ipv4_filter_entry_s`, `struct ipv6_filter_entry_s`) matching on device, protocol, source/destination IP subnets, TCP/UDP port ranges, or ICMP/ICMPv6 types, and applies `IPFILTER_TARGET_ACCEPT`, `IPFILTER_TARGET_DROP`, or `IPFILTER_TARGET_REJECT` verdicts.

## Interface
- `[ipfilter.h:enum ipfilter_chain_e]` - Filter hook chain identifiers (`IPFILTER_CHAIN_INPUT`, `IPFILTER_CHAIN_FORWARD`, `IPFILTER_CHAIN_OUTPUT`).
- `[ipfilter.h:struct ipfilter_entry_s]` - Common filter rule header specifying link pointers, `dev`, `proto`, `target`, match flags, and L4 port/ICMP match criteria.
- `[ipfilter.h:struct ipv4_filter_entry_s]` - IPv4 filter rule extending `struct ipfilter_entry_s` with `sip`, `dip`, `smsk`, and `dmsk`.
- `[ipfilter.h:struct ipv6_filter_entry_s]` - IPv6 filter rule extending `struct ipfilter_entry_s` with `sip`, `dip`, `smsk`, and `dmsk`.
- `[ipfilter.c:ipfilter_cfg_alloc]` - Allocates a blank IPv4 or IPv6 filter rule entry on the heap.
- `[ipfilter.c:ipfilter_cfg_add]` - Appends a configured filter rule entry to the specified `family` and `chain`.
- `[ipfilter.c:ipfilter_cfg_clear]` - Frees all filter rules in a given `family` and `chain`.
- `[ipfilter.c:ipv4_filter_in]` - Evaluates an inbound IPv4 packet on `dev` against the `INPUT` chain (`[ipfilter.c:ipv6_filter_in]` evaluates IPv6).
- `[ipfilter.c:ipfilter_out]` - Evaluates an outbound IPv4 or IPv6 packet on `dev` against the `OUTPUT` chain.
- `[ipfilter.c:ipv4_filter_fwd]` - Evaluates a forwarded IPv4 packet between `indev` and `outdev` against the `FORWARD` chain (`[ipfilter.c:ipv6_filter_fwd]` evaluates IPv6).

## Invariants
- `[ipfilter.c:ipv4_filter_in]`, `[ipfilter.c:ipv6_filter_in]`, `[ipfilter.c:ipfilter_out]`, `[ipfilter.c:ipv4_filter_fwd]`, and `[ipfilter.c:ipv6_filter_fwd]` must be called with the network lock held and `dev->d_iob`/`dev->d_len` populated.

## Side Effects
- Allocates and frees rule structures in global chain queues (`g_ipv4_filter`, `g_ipv6_filter`).
- Sets `dev->d_len = 0` when dropping packets, or overwrites `dev->d_iob` in-place with an ICMP/ICMPv6 Destination Unreachable or TCP RST response when rejecting packets (`IPFILTER_TARGET_REJECT`).

## Verification
- Run: `make test`
