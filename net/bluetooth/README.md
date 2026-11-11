# Bluetooth (`net/bluetooth`)

## Overview
The `net/bluetooth` component implements the `AF_BLUETOOTH` (`PF_BLUETOOTH`) socket family in NuttX. It manages Bluetooth socket connections (`struct bluetooth_conn_s`), preallocated and dynamic RX frame containers (`struct bluetooth_container_s`), device lookup and polling over `struct radio_driver_s`, and `sendmsg`/`recvmsg` framing for Bluetooth protocols.

## Interface
- `[bluetooth.h:struct bluetooth_conn_s]` - Representation of an `AF_BLUETOOTH` socket connection, holding local/remote addresses, protocol, channel, and RX frame queue (`bc_rxhead`/`bc_rxtail`).
- `[bluetooth.h:struct bluetooth_container_s]` - Metadata wrapper linking a received IOB frame (`bn_iob`) with its source address and channel in a connection's RX queue.
- `[bluetooth_sockif.c:g_bluetooth_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `PF_BLUETOOTH`.
- `[bluetooth_conn.c:g_bluetooth_connections_lock]` - Recursive mutex protecting the global Bluetooth connection list (`[bluetooth.h:bluetooth_conn_list_lock]`, `[bluetooth.h:bluetooth_conn_list_unlock]`).
- `[bluetooth_initialize.c:bluetooth_initialize]` - Initializes the Bluetooth socket connection and frame container pools at boot.
- `[bluetooth_conn.c:bluetooth_conn_alloc]` - Allocates and initializes a new `struct bluetooth_conn_s` instance.
- `[bluetooth_conn.c:bluetooth_conn_free]` - Releases a `struct bluetooth_conn_s` instance and drains any queued RX containers.
- `[bluetooth_conn.c:bluetooth_conn_active]` - Finds an active connection matching an incoming frame metadata header (`struct bluetooth_frame_meta_s`).
- `[bluetooth_conn.c:bluetooth_conn_next]` - Iterates through active Bluetooth socket connections.
- `[bluetooth_input.c:bluetooth_input]` - Dispatches an incoming Bluetooth IOB frame from a radio driver to matching sockets.
- `[bluetooth_callback.c:bluetooth_callback]` - Handles device-level event notifications from the radio driver.
- `[bluetooth_sendmsg.c:bluetooth_sendmsg]` - Transmits a message over a Bluetooth socket via the bound radio device.
- `[bluetooth_recvmsg.c:bluetooth_recvmsg]` - Dequeues and copies an incoming frame from a Bluetooth socket's RX queue.
- `[bluetooth_poll.c:bluetooth_poll]` - Polls a Bluetooth connection for pending outbound transmissions on `dev`.
- `[bluetooth_finddev.c:bluetooth_find_device]` - Resolves the `struct radio_driver_s` matching a local Bluetooth address.
- `[bluetooth_finddev.c:bluetooth_find_device_byindex]` - Resolves a Bluetooth radio driver by HCI device ID.
- `[bluetooth_container.c:bluetooth_container_initialize]` - Initializes the RX frame container free pool.
- `[bluetooth_container.c:bluetooth_container_allocate]` - Allocates an RX frame container from the preallocated pool or heap.
- `[bluetooth_container.c:bluetooth_container_free]` - Frees an RX frame container and its attached IOB chain.

## Invariants
- Access to the global Bluetooth connection list must be serialized with `[bluetooth.h:bluetooth_conn_list_lock]` (`[bluetooth_conn.c:g_bluetooth_connections_lock]`).
- `[bluetooth_input.c:bluetooth_input]` and `[bluetooth_poll.c:bluetooth_poll]` must be called with the network lock held.
- The number of queued RX frames in `bc_backlog` on any `[bluetooth.h:struct bluetooth_conn_s]` must not exceed `CONFIG_NET_BLUETOOTH_BACKLOG`.

## Side Effects
- Allocates and frees connection structures and frame containers from preallocated pools or the kernel heap (`[bluetooth_conn.c:bluetooth_conn_alloc]`, `[bluetooth_container.c:bluetooth_container_allocate]`).
- Mutates per-connection RX queues (`bc_rxhead`/`bc_rxtail`) and submits outgoing frames to the underlying `struct radio_driver_s`.

## Verification
- Run: `make test`
