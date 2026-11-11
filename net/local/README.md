# Unix Domain Sockets (`net/local`)

## Overview
The `net/local` component implements Unix domain (`AF_UNIX` / `AF_LOCAL`, `PF_LOCAL`) sockets in NuttX. It supports connected `SOCK_STREAM`, connectionless `SOCK_DGRAM`, and `socketpair` sockets backed by VFS FIFOs/pipes under `/var/socket`, along with optional `SCM_RIGHTS` file-descriptor passing and `SCM_CREDENTIALS` peer credential exchange (`CONFIG_NET_LOCAL_SCM`).

## Interface
- `[local.h:enum local_type_e]` - Unix domain socket framing type (`LOCAL_TYPE_UNNAMED`, `LOCAL_TYPE_PATHNAME`, `LOCAL_TYPE_ABSTRACT`).
- `[local.h:enum local_state_s]` - Connection lifecycle states (`LOCAL_STATE_UNBOUND`, `LOCAL_STATE_BOUND`, `LOCAL_STATE_LISTENING`, `LOCAL_STATE_ACCEPT`, `LOCAL_STATE_CONNECTING`, `LOCAL_STATE_CONNECTED`, `LOCAL_STATE_DISCONNECTED`).
- `[local.h:struct local_conn_s]` - Unix domain socket connection structure holding path, state, client/server locks, VFS `struct file` handles (`lc_infile`, `lc_outfile`), backlog queues, and SCM control file arrays (`lc_cfps`).
- `[local_sockif.c:g_local_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `PF_LOCAL`.
- `[local_conn.c:g_local_lock]` - Global recursive mutex protecting the Unix domain connection list (`[local.h:local_lock]`, `[local.h:local_unlock]`).
- `[local_conn.c:local_alloc]` - Allocates and initializes a new `struct local_conn_s` (`[local_conn.c:local_alloc_accept]` allocates a server-side accepted connection).
- `[local_conn.c:local_free]` - Frees a `struct local_conn_s` and closes any open FIFO handles and control files.
- `[local_conn.c:local_addref]` - Increments the reference count `lc_crefs` on a connection (`[local_conn.c:local_subref]` decrements it and frees on zero).
- `[local_conn.c:local_nextconn]` - Iterates through active Unix domain connections (`[local_conn.c:local_findconn]` and `[local_conn.c:local_peerconn]` locate bound/peer connections).
- `[local_conn.c:local_getaddr]` - Formats a `struct sockaddr_un` from a connection's bound address (`[local_conn.c:local_generate_instance_id]` generates unique FIFO instance IDs).
- `[local_bind.c:psock_local_bind]` - Binds a Unix domain socket to a pathname or abstract address.
- `[local_connect.c:psock_local_connect]` - Connects a client Unix domain socket to a listening server or datagram peer.
- `[local_listen.c:local_listen]` - Transitions a bound `SOCK_STREAM` socket into `LOCAL_STATE_LISTENING`.
- `[local_accept.c:local_accept]` - Accepts a pending client connection from a listening server's `lc_waiters` queue.
- `[local_release.c:local_release]` - Releases FIFO resources when a connected `SOCK_STREAM` socket closes.
- `[local_sendmsg.c:local_sendmsg]` - Sends stream or datagram data (and optional `SCM_RIGHTS` descriptors) over a local socket (`[local_sendpacket.c:local_send_preamble]` and `[local_sendpacket.c:local_send_packet]` frame datagram packets).
- `[local_recvmsg.c:local_recvmsg]` - Receives stream or datagram data (and optional `SCM_RIGHTS`/`SCM_CREDENTIALS` ancillary messages) from a local socket (`[local_recvutils.c:local_fifo_read]` reads exact payloads from the underlying FIFO).
- `[local_fifo.c:local_create_fifos]` - Creates full-duplex client/server FIFOs (`[local_fifo.c:local_release_fifos]` unlinks them; `[local_fifo.c:local_create_halfduplex]` and `[local_fifo.c:local_release_halfduplex]` manage datagram FIFOs).
- `[local_fifo.c:local_open_client_rx]` - Opens FIFO endpoints (`[local_fifo.c:local_open_client_tx]`, `[local_fifo.c:local_open_server_rx]`, `[local_fifo.c:local_open_server_tx]`, `[local_fifo.c:local_open_receiver]`, `[local_fifo.c:local_open_sender]`, `[local_fifo.c:local_set_pollthreshold]`, `[local_fifo.c:local_set_nonblocking]`).
- `[local_netpoll.c:local_event_pollnotify]` - Notifies poll waiters on state changes (`[local_netpoll.c:local_pollsetup]` and `[local_netpoll.c:local_pollteardown]` manage `poll` registrations).

## Invariants
- Global connection list searches and mutations must hold `[local.h:local_lock]` (`[local_conn.c:g_local_lock]`).
- Per-connection read, write, and poll operations synchronize via `lc_recvlock`, `lc_sendlock`, and `lc_polllock` on `[local.h:struct local_conn_s]`.

## Side Effects
- Creates, opens, reads, writes, and unlinks VFS named pipes/FIFOs under `/var/socket` (`[local_fifo.c:local_create_fifos]`, `[local_fifo.c:local_release_fifos]`).
- Clones and installs file descriptors into the receiving process's file table (`file_dup`, `fdlist_dup2`) when `SCM_RIGHTS` control messages are processed.

## Verification
- Run: `make test`
