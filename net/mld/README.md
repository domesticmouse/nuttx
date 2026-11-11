# Multicast Listener Discovery (`net/mld`)

## Overview
The `net/mld` component implements IPv6 Multicast Listener Discovery (MLDv1 per RFC 2710 and MLDv2 per RFC 3810). It manages per-device IPv6 multicast group memberships (`struct mld_group_s`), processes incoming Multicast Listener Queries, Reports, and Done messages, runs querier and v1-compatibility watchdog timers, transmits MLDv1/MLDv2 reports, and updates Ethernet multicast MAC filters (`33:33:xx:xx:xx:xx`).

## Interface
- `[mld.h:enum mld_msgtype_e]` - Outbound MLD message types (`MLD_SEND_NONE`, `MLD_SEND_MASQUERY`, `MLD_SEND_V1REPORT`, `MLD_SEND_V2REPORT`, `MLD_SEND_DONE`).
- `[mld.h:struct mld_group_s]` - Per-device IPv6 multicast group membership structure holding `grpaddr`, `polldog`, `work`, `flags`, `msgtype`, `njoins`, and `lsts`.
- `[mld_initialize.c:mld_devinit]` - Initializes MLD state (`d_mld`) on `dev`, joins the link-local All-Nodes (`ff02::1`) group, and starts general query timers if `CONFIG_NET_MLD_ROUTER` is enabled.
- `[mld_query.c:mld_query]` - Processes incoming MLDv1 and MLDv2 Multicast Listener Query packets on `dev`.
- `[mld_report.c:mld_report_v1]` - Processes incoming MLDv1 Multicast Listener Report packets (`[mld_report.c:mld_report_v2]` processes MLDv2 reports).
- `[mld_done.c:mld_done]` - Processes incoming MLDv1 Multicast Listener Done packets.
- `[mld_group.c:mld_grpalloc]` - Allocates a new `struct mld_group_s` and adds it to `dev->d_mld.grplist`.
- `[mld_group.c:mld_grpfind]` - Finds a multicast group entry on `dev` matching `grpaddr` (`[mld_group.c:mld_grpallocfind]` allocates if absent).
- `[mld_group.c:mld_grpfree]` - Removes and frees a single `struct mld_group_s` (`[mld_group.c:mld_grpfree_all]` frees all groups on `dev`).
- `[mld_msg.c:mld_schedmsg]` - Schedules an MLD message for asynchronous transmission on `group`.
- `[mld_msg.c:mld_waitmsg]` - Schedules an MLD message and blocks on `group->sem` until transmitted.
- `[mld_msg.c:mld_report_msgtype]` - Selects `MLD_SEND_V1REPORT` or `MLD_SEND_V2REPORT` based on `dev`'s v1 compatibility state.
- `[mld_poll.c:mld_poll]` - Polls `dev->d_mld` for scheduled MLD packets ready to be sent (`[mld_poll.c:mld_new_pollcycle]` resets per-cycle report flags).
- `[mld_send.c:mld_send]` - Formats an MLDv1/MLDv2 ICMPv6 message (with Hop-by-Hop Router Alert option) in `dev->d_iob`.
- `[mld_join.c:mld_joingroup]` - Joins an IPv6 multicast group specified by `struct ipv6_mreq` and programs the device multicast MAC filter.
- `[mld_leave.c:mld_leavegroup]` - Leaves an IPv6 multicast group and removes the multicast MAC filter when the last local member leaves.
- `[mld_timer.c:mld_start_gentimer]` - Starts the general query watchdog timer (`[mld_timer.c:mld_start_v1timer]` starts the v1 compatibility timer; `[mld_timer.c:mld_start_polltimer]` starts a group report delay timer).
- `[mld_mcastmac.c:mld_addmcastmac]` - Adds an IPv6 multicast MAC (`33:33:xx:xx:xx:xx`) to `dev` (`[mld_mcastmac.c:mld_removemcastmac]` removes it).

## Invariants
- `[mld_join.c:mld_joingroup]` and `[mld_leave.c:mld_leavegroup]` require symmetrical `struct ipv6_mreq` arguments and must be called with the network lock held.
- `[mld_send.c:mld_send]` and `[mld_poll.c:mld_poll]` must execute with the network lock held.

## Side Effects
- Allocates and frees `[mld.h:struct mld_group_s]` nodes on the heap and schedules watchdog timers (`polldog`, `gendog`, `v1dog`) and workqueue jobs.
- Updates hardware multicast MAC tables (`dev->d_addmac`, `dev->d_rmmac`) and transmits MLDv1/MLDv2 ICMPv6 packets.

## Verification
- Run: `make test`
