# Virtual Sockets (`net/vsock`)

## Overview
Implements the `AF_VSOCK` (`PF_VSOCK`, `CONFIG_NET_VSOCK`) Virtual Socket protocol family in NuttX for communication between virtual machines and the host hypervisor (or local loopback). Provides the core `SOCK_STREAM` and `SOCK_SEQPACKET` socket interface (`vsock_sockif.c`), `struct sockaddr_vm` address validation (`vsock_addr.c`), and pluggable VirtIO (`vsock_virtio.c`, `CONFIG_NET_VSOCK_VIRTIO`), Vhost (`vsock_vhost.c`, `CONFIG_NET_VSOCK_VHOST`), and Local (`vsock_local.c`, `CONFIG_NET_VSOCK_LOCAL`) transport backends.

## Interface
- `[vsock.h:g_vsock_sockif]` - Socket interface operations table (`const struct sock_intf_s`) for `PF_VSOCK`.
- `[vsock.h:struct vsock_pkt_s]`, `[vsock.h:struct vsock_transport_ops_s]`, `[vsock.h:struct vsock_transport_s]` - VSOCK packet scatter/gather wrapper (`vb[CONFIG_NET_VSOCK_PKT_BUFCOUNT]`) and transport layer vtable (`get_localcid`, `get_remotecid`, `alloc_pkt`, `send_pkt`).
- `[vsock.h:vsock_initialize]`, `[vsock.h:vsock_transport_register]`, `[vsock.h:vsock_recv_pkt]`, `[vsock.h:vsock_queue_work]`, `[vsock.h:vsock_conn_dump]` - Core VSOCK subsystem initialization, transport registration, packet reception entry point, and dedicated kernel work queue dispatch.
- `[vsock_addr.c:vsock_addr_is_valid]`, `[vsock_addr.c:vsock_addr_set]`, `[vsock_addr.c:vsock_addr_get]`, `[vsock.h:vsock_addr_init]`, `[vsock.h:vsock_addr_equal]` - `struct sockaddr_vm` (`AF_VSOCK`) address initialization, comparison, and validation helpers.
- `[vsock_virtio.h:struct vsock_hdr_s]`, `[vsock_virtio.h:struct virtio_vsock_event_s]` - Packed VirtIO VSOCK wire header (`src_cid`, `dst_cid`, `src_port`, `dst_port`, `len`, `type`, `op`, `flags`, `buf_alloc`, `fwd_cnt`) and transport reset event structure.
- `[vsock_virtio.c:vsock_virtio_initialize]`, `[vsock_vhost.c:vsock_vhost_initialize]`, `[vsock_local.c:vsock_local_initialize]` - VirtIO guest driver, Vhost host driver, and local loopback transport initializers.

## Invariants
- `[vsock_sockif.c:static_assert]` Enforces `SHUT_RD == VIRTIO_VSOCK_SHUTDOWN_RECV` and `SHUT_WR == VIRTIO_VSOCK_SHUTDOWN_SEND` at compile time.
- `[vsock_addr.c:vsock_addr_is_valid]` Requires `addrlen >= sizeof(struct sockaddr_vm)`, `vmaddr != NULL`, `vmaddr->svm_family == AF_VSOCK`, and `!(vmaddr->svm_flags & ~VMADDR_FLAG_TO_HOST)`.
- `[vsock_virtio.h:struct vsock_hdr_s]` and `[vsock_virtio.h:struct virtio_vsock_event_s]` are packed (`begin_packed_struct`) to match the OASIS VirtIO VSOCK wire specification.
- Connection table (`g_vsock_conn`) and transport list (`g_vsock_transport`) mutations are serialized under `g_vsock_conn_lock` and `g_vsock_transport_lock` (`spin_lock_irqsave`).

## Side Effects
- `[vsock_sockif.c:vsock_initialize]` Creates a dedicated kernel work queue (`work_usrstart("vsock", ...)`) and initializes enabled VirtIO, Vhost, and Local transports.
- `[vsock_virtio.c:vsock_virtio_initialize]` and `[vsock_vhost.c:vsock_vhost_initialize]` Register `VIRTIO_ID_VSOCK` drivers (`virtio_register_driver` / `vhost_register_driver`), allocate virtqueues and aligned DMA packet buffers (`kmm_memalign`), and exchange buffers across RX/TX/EVENT virtqueues.
- `[vsock_local.c:vsock_local_initialize]` Allocates local loopback packet buffers on the kernel heap and registers the `VMADDR_CID_LOCAL` transport.

## Verification
- Run: `make test`
