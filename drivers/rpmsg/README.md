# Remote Processor Messaging (`rpmsg`) Subsystem (`drivers/rpmsg`)

## Overview
Implements the NuttX Remote Processor Messaging (`rpmsg`) core framework, name-service dynamic binding, `/dev/rpmsg` character control interface, `/proc/rpmsg` diagnostics, ping/test/trace/wakelock services, multi-hop RPMSG router (hub/edge), VirtIO RPMSG transport, and direct UART/SPI packet port transports.

## Interface
- `[rpmsg.c:rpmsg_initialize]`, `[rpmsg.c:rpmsg_register]`, `[rpmsg.c:rpmsg_unregister]`, `[rpmsg.c:rpmsg_device_created]`, `[rpmsg.c:rpmsg_device_destroy]`, `[rpmsg.c:rpmsg_ns_bind]`, `[rpmsg.c:rpmsg_ns_unbind]`, `[rpmsg.c:rpmsg_register_callback]`, `[rpmsg.c:rpmsg_unregister_callback]`, `[rpmsg.c:rpmsg_wait]`, `[rpmsg.c:rpmsg_post]`, `[rpmsg.c:rpmsg_ioctl]`, `[rpmsg.c:rpmsg_panic]`, `[rpmsg.c:rpmsg_dump_all]` - Core RPMSG lifecycle, name-service matching, callback registration, and synchronization (`[rpmsg.h:struct rpmsg_s]`, `[rpmsg.h:struct rpmsg_ops_s]`).
- `[rpmsg_virtio.c:rpmsg_virtio_probe]`, `[rpmsg_virtio.c:rpmsg_virtio_probe_cpuname]`, `[rpmsg_virtio.c:rpmsg_virtio_remove]` - OpenAMP VirtIO-backed RPMSG transport driver (`[rpmsg_virtio.c:struct rpmsg_virtio_priv_s]`).
- `[rpmsg_port.c:rpmsg_port_initialize]`, `[rpmsg_port.c:rpmsg_port_uninitialize]`, `[rpmsg_port.c:rpmsg_port_register]`, `[rpmsg_port.c:rpmsg_port_unregister]`, `[rpmsg_port_spi.c:rpmsg_port_spi_initialize]`, `[rpmsg_port_spi_slave.c:rpmsg_port_spi_slave_initialize]`, `[rpmsg_port_uart.c:rpmsg_port_uart_initialize]` - Packet-queue RPMSG port transport and SPI master/slave and UART physical link implementations (`[rpmsg_port.h:struct rpmsg_port_s]`).
- `[rpmsg_router_hub.c:rpmsg_router_hub_init]`, `[rpmsg_router_edge.c:rpmsg_router_edge_init]` - Multi-core RPMSG message routing hub and edge nodes (`[rpmsg_router.h:struct rpmsg_router_s]`).
- `[rpmsg_procfs.c:rpmsg_procfs_initialize]`, `[rpmsg_ping.c:rpmsg_ping_init]`, `[rpmsg_test.c:rpmsg_test_init]`, `[rpmsg_trace.c:rpmsg_trace]`, `[rpmsg_wakelock.c:rpmsg_wakelock_init]` - Built-in diagnostics, latency ping, test, trace, and PM wakelock endpoints.

## Invariants
- Global RPMSG device and callback lists (`[rpmsg.c:g_rpmsg]`, `[rpmsg.c:g_rpmsg_cb]`) are synchronized via reader-writer lock `[rpmsg.c:g_rpmsg_lock]` (`down_read` / `down_write`).
- Port TX/RX buffer queues (`[rpmsg_port.h:struct rpmsg_port_queue_s]`) enforce pre-allocated buffer counts and block callers on `rxq.sem`/`txq.sem` when full/empty.

## Side Effects
- Registers `/dev/rpmsg/*` character drivers (`[rpmsg.c:register_driver]`) and `/proc/rpmsg` procfs entries, spawns transport worker threads, and exchanges cross-core IPC frames over shared-memory VirtIO rings, SPI (`[rpmsg_port_spi.c:SPI_EXCHANGE]`), or UART channels.

## Verification
- Run: `make test`
