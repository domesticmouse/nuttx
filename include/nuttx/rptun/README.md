# NuttX Remote Processor Tunnel (`include/nuttx/rptun`)

## Overview
Defines the Remote Processor Tunnel (`RPTUN`) driver interface integrating OpenAMP `remoteproc` lifecycle management, shared-memory resource tables, address translation environments, bare-metal peer booting (`rptun_bmp`), and PCI `ivshmem` tunneling (`rptun_ivshmem`).

## Interface
- `rptun.h:rptun_dev_s`, `rptun.h:rptun_ops_s`, `rptun.h:rptun_rsc_s`, `rptun.h:rptun_addrenv_s`, `rptun.h:rptun_cmd_s` - RPTUN lower-half device structure, operations vtable (`get_cpuname`, `get_firmware`, `get_addrenv`, `get_resource`, `is_autostart`, `is_master`, `config`, `start`, `stop`, `notify`, `register_callback`), shared resource table layout, and address translation descriptors.
- `rptun.h:rptun_initialize`, `rptun.h:rptun_boot`, `rptun.h:rptun_poweroff`, `rptun.h:rptun_reset`, `rptun.h:rptun_panic` - Remote processor tunnel registration and lifecycle control APIs.
- `rptun.h:RPTUNIOC_START`, `rptun.h:RPTUNIOC_STOP`, `rptun.h:RPTUNIOC_RESET`, `rptun.h:RPTUNIOC_PANIC`, `rptun.h:RPTUN_NOTIFY_ALL` - `/dev/rptun/*` ioctl commands and vring notification constants.
- `rptun_bmp.h:rptun_bmp_init` - Bare-metal remote processor tunnel initialization using shared memory and inter-processor interrupts.
- `rptun_ivshmem.h:pci_register_rptun_ivshmem_driver` - PCI Inter-VM Shared Memory (`ivshmem`) RPTUN driver registration.

## Invariants
- `rptun.h:rptun_rsc_s` must be aligned to an 8-byte boundary (`aligned_data(8)`) in shared memory so both master and remote processors observe identical `rsc_tbl_hdr`, `rpmsg_vdev`, and `rpmsg_vring` offsets.
- Address translation tables returned by `get_addrenv` (`rptun.h:rptun_addrenv_s`) must terminate with an entry where `size == 0`.

## Side Effects
- `rptun.h:rptun_initialize` spawns the RPTUN worker thread, registers `/dev/rptun/<cpuname>`, and if `is_autostart` is true, boots the remote core and initializes OpenAMP VirtIO/RPMsg rings.
- `rptun.h:rptun_boot`, `rptun.h:rptun_poweroff`, `rptun.h:rptun_reset`, and `rptun.h:rptun_panic` load firmware into target memory and trigger hardware inter-processor interrupts or reset lines.

## Verification
- Run: `make test`
