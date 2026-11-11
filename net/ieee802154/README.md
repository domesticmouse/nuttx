# IEEE 802.15.4 Sockets (`net/ieee802154`)

## Overview
The `net/ieee802154` component implements the `PF_IEEE802154` (`AF_IEEE802154`) raw packet socket family in NuttX. It manages IEEE 802.15.4 socket connections (`struct ieee802154_conn_s`), RX frame container pools (`struct ieee802154_container_s`), device lookup by PAN ID / MAC address, and frame transmission and reception over `struct radio_driver_s` drivers.

## Interface
- `[ieee802154.h:struct ieee802154_conn_s]` - Connection structure for `PF_IEEE802154` sockets containing local/remote IEEE 802.15.4 addresses (`laddr`, `raddr`) and the received frame queue (`rxhead`, `rxtail`).
- `[ieee802154.h:struct ieee802154_container_s]` - Container node wrapping a received IOB frame (`ic_iob`) and source address (`ic_src`) in a socket's RX queue.
- `[ieee802154_sockif.c:g_ieee802154_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `PF_IEEE802154`.
- `[ieee802154_conn.c:g_ieee802154_connections_lock]` - Recursive mutex protecting the global IEEE 802.15.4 connection list (`[ieee802154.h:ieee802154_conn_list_lock]`, `[ieee802154.h:ieee802154_conn_list_unlock]`).
- `[ieee802154_initialize.c:ieee802154_initialize]` - Initializes the IEEE 802.15.4 connection and frame container pools.
- `[ieee802154_conn.c:ieee802154_conn_alloc]` - Allocates and initializes a new `struct ieee802154_conn_s`.
- `[ieee802154_conn.c:ieee802154_conn_free]` - Frees a `struct ieee802154_conn_s` and releases any queued RX containers.
- `[ieee802154_conn.c:ieee802154_conn_active]` - Finds an active socket connection matching incoming frame metadata (`struct ieee802154_data_ind_s`).
- `[ieee802154_conn.c:ieee802154_conn_next]` - Iterates through active IEEE 802.15.4 socket connections.
- `[ieee802154_input.c:ieee802154_input]` - Dispatches an incoming IEEE 802.15.4 IOB frame from a radio driver to matching sockets.
- `[ieee802154_callback.c:ieee802154_callback]` - Handles radio device event callbacks for IEEE 802.15.4 sockets.
- `[ieee802154_sendmsg.c:ieee802154_sendmsg]` - Sends a frame over an IEEE 802.15.4 socket via the bound `struct radio_driver_s`.
- `[ieee802154_recvmsg.c:ieee802154_recvmsg]` - Dequeues and copies a received frame from a socket's RX queue.
- `[ieee802154_finddev.c:ieee802154_find_device]` - Locates the `struct radio_driver_s` matching a local `struct ieee802154_saddr_s`.
- `[ieee802154_poll.c:ieee802154_poll]` - Polls an IEEE 802.15.4 connection for pending outbound frames on `dev`.
- `[ieee802154_container.c:ieee802154_container_initialize]` - Initializes the RX container pool (`[ieee802154_container.c:ieee802154_container_allocate]` and `[ieee802154_container.c:ieee802154_container_free]` allocate and free containers).

## Invariants
- Outbound frame payloads must not exceed `[ieee802154.h:IEEE802154_FRAMELEN]` (125 bytes, reserving `IEEE802154_MAC_FCSSIZE` for the 2-byte FCS).
- Access to the global connection list requires holding `[ieee802154.h:ieee802154_conn_list_lock]`; `[ieee802154_input.c:ieee802154_input]` and `[ieee802154_poll.c:ieee802154_poll]` require the network lock.

## Side Effects
- Allocates and frees connection structures and RX container nodes from preallocated pools or the heap.
- Enqueues incoming frames in `rxhead`/`rxtail` on `[ieee802154.h:struct ieee802154_conn_s]` and submits outbound frames to the radio driver via `r_req_data`.

## Verification
- Run: `make test`
