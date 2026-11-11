# NuttX Packet Radio Subsystem (`pktradio`)

## Overview
Non-IEEE 802.15.4 packet radio metadata pool allocator (`pktradio_metadata.c`) and simulated packet radio network loopback driver (`pktradio_loopback.c`).

## Interface
- `[pktradio_metadata.c:pktradio_metadata_initialize]`
- `[pktradio_metadata.c:pktradio_metadata_allocate]`
- `[pktradio_metadata.c:pktradio_metadata_free]`
- `[pktradio_loopback.c:pktradio_loopback]`

## Invariants
- `[pktradio_metadata.c:pktradio_metadata_initialize]` initializes the preallocated pools (`g_metafree` and `g_metafree_irq`) at most once (`g_poolinit`).
- `[pktradio_metadata.c:pktradio_metadata_allocate]` never calls `kmm_zalloc` from interrupt context (`up_interrupt_context()`), returning `NULL` if both `g_metafree` and `g_metafree_irq` are empty; `[pktradio_metadata.c:pktradio_metadata_free]` asserts `meta->pm_pool == POOL_PKTRADIO_DYNAMIC` before calling `kmm_free`.
- `[pktradio_loopback.c:lo_req_data]` asserts `priv != NULL && meta != NULL && framelist != NULL` and `iob->io_offset == MAC_HDRLEN` (2 bytes).
- `[pktradio_loopback.c:#error]` requires `CONFIG_SCHED_WORKQUEUE` and `CONFIG_NET_6LOWPAN` to be defined when `CONFIG_PKTRADIO_LOOPBACK` is enabled.

## Side Effects
- `[pktradio_metadata.c:pktradio_metadata_allocate]` and `[pktradio_metadata.c:pktradio_metadata_free]` mutate free lists `g_metafree` and `g_metafree_irq` under `enter_critical_section` or allocate/free via `kmm_zalloc`/`kmm_free`.
- `[pktradio_loopback.c:pktradio_loopback]` initializes `g_loopback`, registers the `NET_LL_PKTRADIO` network device via `netdev_register`, and brings the interface up (`lo_ifup`, `netdev_carrier_on`).
- `[pktradio_loopback.c:lo_req_data]` zeroes the 2-byte MAC header in each frame IOB, queues IOBs on `priv->lo_head`/`priv->lo_tail`, and schedules `lo_loopback_work` on `LPWORK` to pass frames into `sixlowpan_input` under `net_lock()`.

## Verification
- Run: `make test`
