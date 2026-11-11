# NuttX Remote Processor Messaging (`include/nuttx/rpmsg`)

## Overview
Provides the NuttX Remote Processor Messaging (`RPMsg`) framework headers, defining transport-agnostic inter-processor communication management, VirtIO-backed RPMsg (`rpmsg_virtio`), SPI/UART port-backed RPMsg (`rpmsg_port`), and multi-hop hub/edge routing (`rpmsg_router`).

## Interface
- `rpmsg.h:rpmsg_initialize`, `rpmsg.h:rpmsg_wait`, `rpmsg.h:rpmsg_post`, `rpmsg.h:rpmsg_get_local_cpuname`, `rpmsg.h:rpmsg_get_cpuname`, `rpmsg.h:rpmsg_get_signals`, `rpmsg.h:rpmsg_get_timestamp`, `rpmsg.h:rpmsg_register_callback`, `rpmsg.h:rpmsg_unregister_callback`, `rpmsg.h:rpmsg_ioctl`, `rpmsg.h:rpmsg_panic`, `rpmsg.h:rpmsg_dump_all` - Core RPMsg lifecycle, device discovery callbacks, synchronization helpers, and diagnostics.
- `rpmsg.h:rpmsg_ping_s`, `rpmsg.h:rpmsg_timestamp_s`, `rpmsg.h:RPMSGIOC_PANIC`, `rpmsg.h:RPMSGIOC_DUMP`, `rpmsg.h:RPMSGIOC_PING`, `rpmsg.h:RPMSGIOC_TEST`, `rpmsg.h:RPMSGIOC_RUNNING`, `rpmsg.h:RPMSGIOC_ACQUIRE_WAKELOCK`, `rpmsg.h:RPMSGIOC_RELEASE_WAKELOCK` - Control ioctl commands and payload structures for `/dev/rpmsg/*`.
- `rpmsg_virtio.h:rpmsg_virtio_probe`, `rpmsg_virtio.h:rpmsg_virtio_probe_cpuname`, `rpmsg_virtio.h:rpmsg_virtio_remove` - VirtIO RPMsg transport binding and teardown.
- `rpmsg_port.h:rpmsg_port_config_s`, `rpmsg_port.h:rpmsg_port_spi_config_s`, `rpmsg_port.h:rpmsg_port_spi_initialize`, `rpmsg_port.h:rpmsg_port_spi_slave_initialize`, `rpmsg_port.h:rpmsg_port_uart_initialize` - SPI master/slave and UART serial transport initialization for RPMsg over physical links.
- `rpmsg_router.h:rpmsg_router_hub_init`, `rpmsg_router.h:rpmsg_router_edge_init` - Multi-processor RPMsg router hub and edge initialization.

## Invariants
- `rpmsg.h:rpmsg_wait` and `rpmsg.h:rpmsg_post` must be used instead of raw semaphore waits when blocking inside an RPMsg endpoint callback so the worker thread can continue dispatching incoming messages on non-preemptive or shared queues.

## Side Effects
- `rpmsg.h:rpmsg_register_callback` immediately invokes `device_created` for all currently active remote processors and registers the listener in the global callback list.
- `rpmsg.h:rpmsg_panic` and `rpmsg.h:RPMSGIOC_PANIC` force a remote processor panic across the inter-processor transport.

## Verification
- Run: `make test`
