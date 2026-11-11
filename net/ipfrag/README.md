# IP Fragmentation and Reassembly (`net/ipfrag`)

## Overview
The `net/ipfrag` component implements IPv4 and IPv6 packet fragmentation and reassembly (`CONFIG_NET_IPFRAG`). It slices oversized outbound packets into MTU-sized IOB fragments (`ipv4_fragout`, `ipv6_fragout`), queues and reassembles incoming IPv4 and IPv6 fragments (`ipv4_fragin`, `ipv6_fragin`), enforces reassembly timeouts via a periodic watchdog timer, and reclaims fragment memory under IOB exhaustion (`ip_frag_remallfrags`).

## Interface
- `[ipfrag.h:enum ip_fragverify_e]` - Flags controlling whether inbound reassembly verifies or skips upper-layer checksums (`IP_FRAG_VERIFYCHKSUM`, `IP_FRAG_SKIPVERIFYCHKSUM`).
- `[ipfrag.h:struct ip_fraglink_s]` - Per-fragment descriptor node holding fragment offset, length, `morefrags`, and IOB pointer (`frag`).
- `[ipfrag.h:struct ip_fragsnode_s]` - Reassembly queue node representing an in-progress fragmented datagram (`dev`, `ipid`, `remember`, `verify`, `tick`, `outgoframe`, `frags`).
- `[ipfrag.c:g_ipfrag_lock]` - Mutex synchronizing access to global fragment reassembly queues.
- `[ipfrag.c:ip_frag_remnode]` - Frees all fragment descriptors and IOBs belonging to a `struct ip_fragsnode_s`.
- `[ipfrag.c:ip_fragin_enqueue]` - Inserts an incoming fragment into its matching `struct ip_fragsnode_s` in offset order and triggers reassembly once complete.
- `[ipfrag.c:ip_fragout_slice]` - Splits an oversized outbound IOB chain into MTU-sized fragment IOB chains.
- `[ipfrag.c:ip_frag_startwdog]` - Starts the periodic reassembly timeout watchdog timer if not already running.
- `[ipfrag.c:ip_frag_stop]` - Purges all pending inbound and outbound fragments associated with `dev` when the device goes down.
- `[ipfrag.c:ip_frag_remallfrags]` - Reclaims all queued fragment buffers across all devices when IOB memory is exhausted.
- `[ipfrag.c:ip_fragout]` - Dequeues the next outbound fragment from `dev->d_fragout` into `dev->d_iob` for transmission.
- `[ipv4_frag.c:ipv4_fragin]` - Processes an incoming IPv4 fragment on `dev` (`[ipv4_frag.c:ipv4_fragout]` fragments an outbound IPv4 packet).
- `[ipv6_frag.c:ipv6_fragin]` - Processes an incoming IPv6 fragment on `dev` (`[ipv6_frag.c:ipv6_fragout]` fragments an outbound IPv6 packet).

## Invariants
- Access to the global reassembly queue (`g_assemblyhead_isio`) must be protected by `[ipfrag.c:g_ipfrag_lock]`.
- `flink` must remain the first member of `[ipfrag.h:struct ip_fragsnode_s]` to support queue node casting.
- `[ipv4_frag.c:ipv4_fragout]` and `[ipv6_frag.c:ipv6_fragout]` require `dev->d_iob->io_pktlen > mtu`.

## Side Effects
- Allocates and frees IOB chains and fragment tracking nodes (`struct ip_fragsnode_s`, `struct ip_fraglink_s`), enqueues outbound fragments into `dev->d_fragout`, and runs a kernel watchdog timer (`g_fragwdog`) + workqueue worker (`g_fragwork`) to expire stale fragments.

## Verification
- Run: `make test`
