# Socket Layer (`net/socket`)

## Overview
The `net/socket` component implements the BSD/POSIX socket system calls and the internal kernel `psock_*` VFS socket abstraction in NuttX. It resolves socket domains (`PF_INET`, `PF_INET6`, `PF_LOCAL`, `PF_NETLINK`, `PF_PACKET`, `PF_CAN`, `PF_BLUETOOTH`, `PF_IEEE802154`, `PF_RPMSG`, or `usrsock`) via `net_sockif`, manages socket file descriptors (`sockfd_socket`, `sock_file_open`), enforces socket-level options (`SOL_SOCKET`) and timeouts (`net_timeo`), and dispatches operations to protocol-family `struct sock_intf_s` tables.

## Interface
- `[net_sockif.c:net_sockif]` - Resolves the `struct sock_intf_s` operations table for a given `(family, type, protocol)` tuple.
- `[net_timeo.c:net_timeo]` - Checks whether a socket send/receive timeout (`socktimeo_t`) has elapsed relative to `start_time`.
- `[socket.c:psock_socket]` - Initializes an internal `struct socket` instance (`[socket.c:socket]` is the POSIX syscall allocating a file descriptor).
- `[bind.c:psock_bind]` - Binds a `struct socket` to a local `struct sockaddr` (`[bind.c:bind]` is the POSIX syscall).
- `[connect.c:psock_connect]` - Connects a `struct socket` to a peer `struct sockaddr` (`[connect.c:connect]` is the POSIX syscall).
- `[listen.c:psock_listen]` - Marks a connection-mode `struct socket` as listening with `backlog` (`[listen.c:listen]` is the POSIX syscall).
- `[accept.c:psock_accept]` - Accepts an incoming connection into a new `struct socket` (`[accept.c:accept4]` is the POSIX syscall).
- `[send.c:psock_send]` - Sends data on a connected socket (`[send.c:send]` is the POSIX syscall).
- `[sendto.c:psock_sendto]` - Sends data to a specified destination address (`[sendto.c:sendto]` is the POSIX syscall).
- `[sendmsg.c:psock_sendmsg]` - Sends a `struct msghdr` message (`[sendmsg.c:sendmsg]` is the POSIX syscall).
- `[recv.c:psock_recv]` - Receives data from a socket (`[recv.c:recv]` is the POSIX syscall).
- `[recvfrom.c:psock_recvfrom]` - Receives data and peer address from a socket (`[recvfrom.c:recvfrom]` is the POSIX syscall).
- `[recvmsg.c:psock_recvmsg]` - Receives a `struct msghdr` message (`[recvmsg.c:recvmsg]` is the POSIX syscall).
- `[getsockopt.c:psock_getsockopt]` - Queries socket or protocol options (`[getsockopt.c:getsockopt]` is the POSIX syscall).
- `[setsockopt.c:psock_setsockopt]` - Configures socket or protocol options (`[setsockopt.c:setsockopt]` is the POSIX syscall).
- `[getsockname.c:psock_getsockname]` - Retrieves the local bound address of a socket (`[getsockname.c:getsockname]` is the POSIX syscall).
- `[getpeername.c:psock_getpeername]` - Retrieves the connected peer address of a socket (`[getpeername.c:getpeername]` is the POSIX syscall).
- `[shutdown.c:psock_shutdown]` - Shuts down part or all of a full-duplex socket connection (`[shutdown.c:shutdown]` is the POSIX syscall).
- `[socketpair.c:psock_socketpair]` - Creates an unnamed pair of connected sockets (`[socketpair.c:socketpair]` is the POSIX syscall).
- `[net_close.c:psock_close]` - Closes a `struct socket` and releases its underlying connection.
- `[net_poll.c:psock_poll]` - Sets up or tears down `poll`/`select` monitoring on a `struct socket`.
- `[net_dup2.c:psock_dup2]` - Clones a `struct socket` into another `struct socket`.
- `[net_fstat.c:psock_fstat]` - Populates `struct stat` metadata (`S_IFSOCK`) for a socket file descriptor.
- `[net_sendfile.c:psock_sendfile]` - Transfers data directly from an open `struct file` to a `struct socket`.

## Invariants
- Internal `psock_*` functions never modify the thread-local `errno` variable and instead return negative `-errno` status codes directly, whereas user-facing POSIX syscalls (`[socket.c:socket]`, `[bind.c:bind]`, `[connect.c:connect]`, etc.) set `errno` and return `-1` on error.
- A valid `FAR struct socket *` passed to `psock_*` must have `s_sockif != NULL` (initialized by `[socket.c:psock_socket]`).

## Side Effects
- Allocates VFS file descriptors (`sock_file_open`), mutates `struct socket` and `struct socket_conn_s` state flags, options, and error codes (`_SO_SETERRNO`), and invokes protocol-family `struct sock_intf_s` callbacks.

## Verification
- Run: `make test`
