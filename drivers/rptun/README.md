# Remote Processor Tunnel (`rptun`) Drivers (`drivers/rptun`)

## Overview
Implements the Remote Processor Tunnel (`rptun`) driver integrating OpenAMP `remoteproc` lifecycle management, resource-table parsing, firmware loading, VirtIO/Vhost device creation, and RPMSG VirtIO bridging, along with Bare-Metal/AMP (`rptun_bmp`) and PCI Inter-VM Shared Memory (`rptun_ivshmem`) backends.

## Interface
- `[rptun.c:rptun_initialize]` - Initializes a `struct rptun_dev_s` remoteproc tunnel instance, registers `/dev/rptun/<cpuname>`, and spawns or schedules its management context (`[rptun.c:struct rptun_priv_s]`).
- `[rptun.c:rptun_boot]`, `[rptun.c:rptun_poweroff]`, `[rptun.c:rptun_reset]` - Boots, powers off, or resets a remote processor by CPU name.
- `[rptun_bmp.c:rptun_bmp_init]` - Initializes a symmetric/bare-metal multi-core `rptun` instance using shared RAM (`[rptun_bmp.c:struct rptun_bmp_dev_s]`).
- `[rptun_ivshmem.c:pci_register_rptun_ivshmem_driver]` - Registers the PCI `ivshmem`-backed `rptun` driver for inter-VM OpenAMP communication (`[rptun_ivshmem.c:struct rptun_ivshmem_dev_s]`).

## Invariants
- Resource tables provided by lower-half `RPTUN_GET_RESOURCE` must contain valid OpenAMP `resource_table` headers before VirtIO/RPMSG devices are instantiated.
- Global `g_rptun_priv` list access is protected by `g_rptun_lock` (`nxmutex_lock`).

## Side Effects
- Registers `/dev/rptun/*` character devices (`[rptun.c:register_driver]`), loads remote firmware images from VFS (`[rptun.c:struct rptun_store_s]`), creates shared-memory carveout heaps (`[rptun.c:struct rptun_carveout_s]`), instantiates VirtIO/Vhost/RPMSG devices (`[rptun.c:rpmsg_virtio_probe_cpuname]`), and triggers cross-core hardware or PCI `ivshmem` interrupts.

## Verification
- Run: `make test`
