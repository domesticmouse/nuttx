# Socket File Descriptor Adaptation Layer (`fs/socket`)

## Overview
Bridges the NuttX networking stack (`struct socket` / `psock_*`) with the VFS file descriptor table, allowing BSD sockets to be represented as standard `struct file` entries supporting `read`, `write`, `ioctl`, `poll`, `dup`, and `close`.

## Interface
- `socket.c:sockfd_allocate` - Allocates a process file descriptor bound to the static `g_sock_inode` (`FSNODEFLAG_TYPE_SOCKET`) and attaches `psock` as `filep->f_priv`.
- `socket.c:file_socket` - Extracts the underlying `FAR struct socket *` from a `struct file *` if its inode is a socket (`INODE_IS_SOCKET`).
- `socket.c:sockfd_socket` - Resolves a numeric socket file descriptor `sockfd` to both its `struct file *` (incrementing reference count via `file_get`) and its `struct socket *`.
- `socket.c:socket` - Standard POSIX `socket(domain, type, protocol)` system call entry point that allocates a `struct socket`, initializes it via `psock_socket`, and binds a file descriptor via `sockfd_allocate`.
- `accept.c:accept4` - Accepts an incoming connection on a listening socket (`psock_accept`), optionally mapping user address buffers (`kmm_map_user`), and allocates a new socket file descriptor with `SOCK_NONBLOCK` / `SOCK_CLOEXEC` flags.
- `accept.c:accept` - Standard POSIX `accept` wrapper delegating to `accept4(..., 0)`.
- `socketpair.c:socketpair` - Creates a pair of connected sockets (`psock_socketpair`) and allocates two file descriptors in `sv[2]`.

## Invariants
- All socket `struct file` instances reference the singleton `g_sock_inode` with `FSNODEFLAG_TYPE_SOCKET` and `g_sock_fileops`.
- `socket.c:sockfd_socket` only retains the `file_get` reference count when `*socketp != NULL`; if the descriptor is not a socket, it calls `file_put` and returns `-ENOTSOCK`.
- `accept.c:accept4` rejects any `flags` bits outside `SOCK_NONBLOCK | SOCK_CLOEXEC` with `EINVAL`.

## Side Effects
- Allocates and frees `struct socket` containers on the filesystem heap (`fs_heap_zalloc`, `fs_heap_free`).
- Allocates and closes process file descriptors (`file_allocate_from_inode`, `nx_close`) and triggers `SIGPIPE` (`psock_sigpipe`) on broken-pipe socket writes.

## Verification
- Run: `make test`
