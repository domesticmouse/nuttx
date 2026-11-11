# IGMP (`net/igmp`)

## Overview
The `net/igmp` component implements the Internet Group Management Protocol Version 2 (IGMPv2, RFC 2236) for IPv4 multicast group management. It tracks per-device multicast group memberships (`struct igmp_group_s`), processes incoming Membership Queries and Reports (`igmp_input`), schedules randomized report timers (`wdog_s`), transmits Membership Reports and Leave Group messages (`igmp_send`), and configures NIC multicast MAC address filters (`igmp_addmcastmac`, `igmp_removemcastmac`).

## Interface
- `[igmp.h:struct igmp_group_s]` - Per-device multicast group membership node containing `grpaddr`, `wdog`, `work`, `flags`, `msgid`, and `njoins`.
- `[igmp_initialize.c:g_ipv4_allsystems]` - Well-known `224.0.0.1` All-Systems multicast group address (`[igmp_initialize.c:g_ipv4_allrouters]` holds `224.0.0.2`).
- `[igmp_initialize.c:igmp_initialize]` - Initializes global IGMP state.
- `[igmp_initialize.c:igmp_devinit]` - Initializes the multicast group list (`d_igmp_grplist`) on `dev` and adds the `g_ipv4_allsystems` entry.
- `[igmp_input.c:igmp_input]` - Processes incoming IGMPv1/IGMPv2 Membership Queries and Reports on `dev`.
- `[igmp_group.c:igmp_grpalloc]` - Allocates a new `struct igmp_group_s` and attaches it to `dev->d_igmp_grplist`.
- `[igmp_group.c:igmp_grpfind]` - Searches `dev->d_igmp_grplist` for `grpaddr` (`[igmp_group.c:igmp_grpallocfind]` allocates if not found).
- `[igmp_group.c:igmp_grpfree]` - Removes and frees a `struct igmp_group_s` from `dev->d_igmp_grplist`.
- `[igmp_msg.c:igmp_schedmsg]` - Schedules an outgoing IGMP message (`IGMP_SCHED_MSG`) on a group and notifies `dev`.
- `[igmp_msg.c:igmp_waitmsg]` - Schedules an IGMP message and blocks on `group->sem` until transmission completes.
- `[igmp_poll.c:igmp_poll]` - Polls `dev->d_igmp_grplist` for scheduled IGMP messages ready for transmission.
- `[igmp_send.c:igmp_send]` - Constructs and formats an IGMPv2 packet (with IP Router Alert option) in `dev->d_buf`.
- `[igmp_join.c:igmp_joingroup]` - Joins an IPv4 multicast group on `dev`, incrementing `njoins`, programming the multicast MAC filter, and sending an unsolicited Membership Report.
- `[igmp_leave.c:igmp_leavegroup]` - Decrements `njoins` for a multicast group on `dev`, sending a Leave Group message and removing the multicast MAC filter when the last member leaves.
- `[igmp_timer.c:igmp_startticks]` - Starts a group's report delay watchdog timer (`[igmp_timer.c:igmp_starttimer]` and `[igmp_timer.c:igmp_cmptimer]` manage decisecond timers).
- `[igmp_mcastmac.c:igmp_addmcastmac]` - Maps an IPv4 multicast address to an Ethernet multicast MAC (`01:00:5e:xx:xx:xx`) and invokes `dev->d_addmac` (`[igmp_mcastmac.c:igmp_removemcastmac]` invokes `dev->d_rmmac`).

## Invariants
- Every IGMP-enabled network device initialized by `[igmp_initialize.c:igmp_devinit]` maintains the `224.0.0.1` (`[igmp_initialize.c:g_ipv4_allsystems]`) group entry in `dev->d_igmp_grplist`.
- `[igmp_send.c:igmp_send]`, `[igmp_input.c:igmp_input]`, and `[igmp_poll.c:igmp_poll]` must be called with the network lock held.

## Side Effects
- Allocates and frees `[igmp.h:struct igmp_group_s]` structures on the kernel heap and schedules watchdog timers (`wdog_s`) and workqueue jobs (`work_s`).
- Programs hardware multicast MAC filters via `dev->d_addmac` and `dev->d_rmmac`, and transmits IGMPv2 packets via `netdev_txnotify_dev`.

## Verification
- Run: `make test`
