# TCP (`net/tcp`)

## Overview
The `net/tcp` component implements the Transmission Control Protocol (TCP) for IPv4 and IPv6 in NuttX. It manages the TCP connection state machine (`CLOSED`, `SYN_RCVD`, `SYN_SENT`, `ESTABLISHED`, `FIN_WAIT_1`, `FIN_WAIT_2`, `CLOSING`, `TIME_WAIT`, `LAST_ACK`), passive listen backlogs (`struct tcp_backlog_s`), buffered (`struct tcp_wrbuffer_s`) and unbuffered transmission, zero-copy `sendfile`, read-ahead and out-of-order (`struct tcp_ofoseg_s`) RX segment queues, Selective Acknowledgments (SACK), RFC 7323 window scaling, NewReno congestion control (`tcp_cc.c`), keep-alive probing, and per-connection retransmission timers.

## Interface
- `[tcp.h:struct tcp_conn_s]` - TCP connection control block holding IPv4/IPv6 addresses, ports, sequence/acknowledgment numbers (`sndseq`, `rcvseq`), window sizes, RTT estimators, congestion control variables (`cwnd`, `ssthresh`), timers, `readahead`, `write_q`, and `unacked_q`.
- `[tcp.h:struct tcp_poll_s]` - Poll context structure linking a `struct tcp_conn_s`, `struct net_driver_s`, and `struct pollfd`.
- `[tcp.h:struct tcp_ofoseg_s]` - Out-of-order TCP segment descriptor (`left`, `right`, `data`).
- `[tcp.h:struct tcp_sack_s]` - SACK block range (`left`, `right`).
- `[tcp.h:struct tcp_wrbuffer_s]` - Outbound TCP write buffer entry (`wb_node`, `wb_iob`, `wb_seqno`, `wb_sent`, `wb_nrtx`).
- `[tcp.h:struct tcp_backlog_s]` - Listen backlog container and pending connection queue (`bl_pend`, `bl_free`).
- `[tcp_conn.c:tcp_alloc]` - Allocates a new `struct tcp_conn_s` (`[tcp_conn.c:tcp_free]` frees it; `[tcp_conn.c:tcp_free_rx_buffers]` releases RX and out-of-order IOBs).
- `[tcp_conn.c:tcp_active]` - Finds an active TCP connection matching an incoming segment (`[tcp_conn.c:tcp_nextconn]` iterates active connections; `[tcp_conn.c:tcp_conn_list_lock]` and `[tcp_conn.c:tcp_conn_list_unlock]` lock/unlock the connection list).
- `[tcp_conn.c:tcp_alloc_accept]` - Allocates and initializes a new `struct tcp_conn_s` for an incoming `SYN` on a listener (`[tcp_conn.c:tcp_selectport]`, `[tcp_conn.c:tcp_bind]`, `[tcp_conn.c:tcp_connect]`, `[tcp_conn.c:tcp_add_active_conn]`, and `[tcp_conn.c:tcp_removeconn]` manage connection binding and registration).
- `[tcp_connect.c:psock_tcp_connect]` - Initiates an active TCP three-way handshake on a socket.
- `[tcp_accept.c:psock_tcp_accept]` - Dequeues an established connection from a listening socket's backlog.
- `[tcp_listen.c:tcp_listen]` - Starts listening on a bound `struct tcp_conn_s` (`[tcp_listen.c:tcp_unlisten]` stops listening; `[tcp_listen.c:tcp_findlistener]` and `[tcp_listen.c:tcp_accept_connection]` dispatch incoming `SYN` connections).
- `[tcp_close.c:tcp_close]` - Initiates graceful (`FIN`) or abortive (`RST`) teardown of a TCP socket (`[tcp_shutdown.c:tcp_shutdown]` shuts down read/write halves).
- `[tcp_input.c:tcp_ipv4_input]` - Processes inbound IPv4 TCP segments (`[tcp_input.c:tcp_ipv6_input]` processes IPv6 TCP segments).
- `[tcp_send.c:tcp_send]` - Constructs a TCP control/data segment (`[tcp_send.c:tcp_fill_header]`, `[tcp_send.c:tcp_reset]`, and `[tcp_send.c:tcp_synack]` format headers, `RST`, and `SYN|ACK` segments).
- `[tcp_appsend.c:tcp_appsend]` - Builds a TCP segment carrying application payload (`[tcp_appsend.c:tcp_rexmit]` formats a retransmission).
- `[tcp_send_buffered.c:psock_tcp_send]` - Buffered socket `send` implementation (`[tcp_send_buffered.c:psock_tcp_cansend]` checks write space; `[tcp_send_unbuffered.c:psock_tcp_send]` implements unbuffered `send`; `[tcp_sendfile.c:tcp_sendfile]` implements zero-copy file transmission).
- `[tcp_recvfrom.c:psock_tcp_recvfrom]` - Reads received stream bytes from `conn->readahead` and triggers window updates.
- `[tcp_callback.c:tcp_callback]` - Handles network device events (`TCP_NEWDATA`, `TCP_ACKDATA`, `TCP_REXMIT`, `TCP_POLL`) and buffers unread payload via `[tcp_callback.c:tcp_datahandler]`.
- `[tcp_devpoll.c:tcp_poll]` - Polls a `struct tcp_conn_s` for pending outbound data/control transmissions on `dev`.
- `[tcp_timer.c:tcp_timer]` - Processes periodic retransmission, delayed-ACK, `TIME_WAIT`, `FIN_WAIT_2`, and keep-alive timers (`[tcp_timer.c:tcp_update_timer]` and `[tcp_timer.c:tcp_stop_timer]` schedule/cancel per-connection timers).
- `[tcp_backlog.c:tcp_backlogcreate]` - Creates a listener backlog (`[tcp_backlog.c:tcp_backlogdestroy]`, `[tcp_backlog.c:tcp_backlogadd]`, and `[tcp_backlog.c:tcp_backlogremove]` manage backlog entries).
- `[tcp_wrbuffer.c:tcp_wrbuffer_alloc]` - Allocates a `struct tcp_wrbuffer_s` (`[tcp_wrbuffer.c:tcp_wrbuffer_release]` releases it).
- `[tcp_cc.c:tcp_cc_init]` - Initializes congestion control state (`[tcp_cc.c:tcp_cc_update]` and `[tcp_cc.c:tcp_cc_recv_ack]` adjust `cwnd` and `ssthresh`).
- `[tcp_monitor.c:tcp_start_monitor]` - Registers link-down/close monitoring on a connected socket (`[tcp_monitor.c:tcp_stop_monitor]` and `[tcp_monitor.c:tcp_lost_connection]` handle disconnection).
- `[tcp_netpoll.c:tcp_pollsetup]` - Sets up `poll`/`select` monitoring (`[tcp_netpoll.c:tcp_pollteardown]` tears it down).
- `[tcp_notifier.c:tcp_readahead_notifier_setup]` - Registers workqueue notifiers for read-ahead, write-buffer (`[tcp_notifier.c:tcp_writebuffer_notifier_setup]`), and disconnect (`[tcp_notifier.c:tcp_disconnect_notifier_setup]`) events.
- `[tcp_txdrain.c:tcp_txdrain]` - Waits for `write_q` and `unacked_q` to drain.
- `[tcp_getsockopt.c:tcp_getsockopt]` - Queries `IPPROTO_TCP` options (`[tcp_setsockopt.c:tcp_setsockopt]` configures `TCP_NODELAY`, `TCP_KEEPIDLE`, `TCP_MAXSEG`, etc.; `[tcp_ioctl.c:tcp_ioctl]` handles `FIONREAD`/`FIONSPACE`).

## Invariants
- `[tcp_input.c:tcp_ipv4_input]`, `[tcp_input.c:tcp_ipv6_input]`, `[tcp_devpoll.c:tcp_poll]`, `[tcp_timer.c:tcp_timer]`, and `[tcp_send.c:tcp_send]` must be called with the network lock held.
- All 32-bit TCP sequence number comparisons must use the modular arithmetic macros `[tcp.h:TCP_SEQ_LT]`, `[tcp.h:TCP_SEQ_LTE]`, `[tcp.h:TCP_SEQ_GT]`, and `[tcp.h:TCP_SEQ_GTE]` to handle wrap-around correctly.

## Side Effects
- Mutates TCP connection state (`tcpstateflags`), sequence counters, congestion windows, and `readahead`/`ofosegs`/`write_q`/`unacked_q` buffer queues.
- Schedules per-connection workqueue timers (`[tcp_timer.c:tcp_update_timer]`), wakes blocked readers/writers/pollers via workqueue notifiers, and triggers device TX notifications (`netdev_txnotify_dev`).

## Verification
- Run: `make test`
