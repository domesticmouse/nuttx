# ARP (`net/arp`)

## Overview
The `net/arp` component implements the IPv4 Address Resolution Protocol (ARP) for Ethernet network interfaces in NuttX. It manages the global ARP translation cache, formats and processes ARP request and reply frames, intercepts outbound IPv4 packets to resolve or prepend Ethernet headers (`arp_out`), queues pending outbound packets while resolution is in progress (`CONFIG_NET_ARP_SEND_QUEUE`), and implements RFC 5227 IPv4 Address Conflict Detection (`CONFIG_NET_ARP_ACD`).

## Interface
- `[arp.h:struct arp_hdr_s]` - On-wire Ethernet ARP frame payload header structure.
- `[arp.h:struct arp_entry_s]` - ARP cache table entry mapping an IPv4 address (`at_ipaddr`) to an Ethernet MAC address (`at_ethaddr`).
- `[arp.h:struct arp_send_s]` - State structure tracking device callback polling for on-demand ARP request transmission.
- `[arp.h:struct arp_notify_s]` - Waiter notification node signaled when a target IPv4 address is resolved.
- `[arp_format.c:arp_format]` - Formats an ARP packet directly into `dev->d_buf`.
- `[arp_ipin.c:arp_ipin]` - Harvests source IP-to-MAC mappings from inbound IPv4 Ethernet frames.
- `[arp_out.c:arp_out]` - Resolves destination MAC addresses for outbound IPv4 packets, either prepending the Ethernet header, queueing the packet, or replacing it with an ARP request.
- `[arp_input.c:arp_input]` - Processes incoming ARP requests and replies on `dev`.
- `[arp_send.c:arp_send]` - Sends a synchronous ARP request and waits for resolution if necessary.
- `[arp_send.c:arp_send_async]` - Schedules an asynchronous ARP request for `ipaddr`.
- `[arp_poll.c:arp_poll]` - Checks whether queued outbound ARP frames are ready to be transmitted on `dev`.
- `[arp_notify.c:arp_wait_setup]` - Registers a waiter notification entry before transmitting an ARP request.
- `[arp_notify.c:arp_wait]` - Blocks with the network lock released until `arp_notify` signals resolution or `timeout` expires.
- `[arp_notify.c:arp_notify]` - Wakes any thread waiting in `arp_wait` for `ipaddr`.
- `[arp_table.c:arp_find]` - Looks up an ARP cache entry matching `ipaddr` and `dev`.
- `[arp_table.c:arp_update]` - Inserts or refreshes an IP-to-MAC mapping in the ARP table and flushes queued packets.
- `[arp_table.c:arp_delete]` - Removes an entry from the ARP cache table.
- `[arp_table.c:arp_cleanup]` - Purges all non-static ARP entries associated with `dev`.
- `[arp_table.c:arp_snapshot]` - Copies active ARP cache entries into a caller-supplied array.
- `[arp_table.c:arp_queue_iob]` - Enqueues an outbound IOB chain onto an unresolved `struct arp_entry_s` (`CONFIG_NET_ARP_SEND_QUEUE`).
- `[arp_acd.c:arp_acd_setup]` - Initializes RFC 5227 Address Conflict Detection state on `dev`.
- `[arp_acd.c:arp_acd_update]` - Feeds incoming ARP frames into the ACD state machine to detect address conflicts.
- `[arp_acd.c:arp_acd_set_addr]` - Starts ACD probing/announcement when a device's IPv4 address is configured.
- `[arp_dump.c:arp_dump]` - Logs ARP header contents to syslog when `CONFIG_NET_ARP_DUMP` is enabled.

## Invariants
- Callers of `[arp.h:arp_find]`, `[arp.h:arp_update]`, `[arp.h:arp_delete]`, `[arp.h:arp_cleanup]`, `[arp.h:arp_poll]`, and `[arp.h:arp_notify]` must hold the global network lock (`net_lock`).
- `[arp.h:arp_wait_setup]` must be called while holding the network lock prior to sending an ARP request, and `[arp.h:arp_wait]` must be invoked with the network unlocked to prevent race conditions with incoming ARP replies.

## Side Effects
- Mutates the global ARP cache table (`[arp_table.c:arp_update]`, `[arp_table.c:arp_delete]`, `[arp_table.c:arp_cleanup]`).
- Prepends Ethernet headers to `dev->d_buf`, queues unresolved packet IOBs onto `[arp.h:struct arp_entry_s]`, or overwrites `dev->d_buf` with an ARP request in `[arp_out.c:arp_out]`.
- Signals waiting threads via `nt_sem` in `[arp_notify.c:arp_notify]` and emits Netlink neighbor notifications when `CONFIG_NETLINK_ROUTE` is enabled.

## Verification
- Run: `make test`
