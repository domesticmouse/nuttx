# PCI and PCI Endpoint Subsystem (`drivers/pci`)

## Overview
Implements the PCI/PCIe host bus enumeration, configuration/IO space access, BAR mapping, MSI/MSI-X interrupt management, ECAM controller, PCI Endpoint Controller (EPC) and Endpoint Function (EPF) frameworks, Inter-VM Shared Memory (`ivshmem`), and QEMU test/EDU drivers.

## Interface
- `[pci.c:pci_register_controller]`, `[pci.c:pci_register_driver]`, `[pci.c:pci_unregister_driver]`, `[pci.c:pci_enable_device]`, `[pci.c:pci_disable_device]`, `[pci.c:pci_set_master]`, `[pci.c:pci_clear_master]`, `[pci.c:pci_map_bar]`, `[pci.c:pci_map_bar_region]`, `[pci.c:pci_find_capability]`, `[pci.c:pci_alloc_irq]`, `[pci.c:pci_release_irq]`, `[pci.c:pci_connect_irq]`, `[pci.c:pci_bus_read_config]`, `[pci.c:pci_bus_write_config]`, `[pci.c:pci_dev_register]` - Core PCI host bus enumeration, configuration space access, BAR mapping, IRQ management, and `/dev/pci` character device registration.
- `[pci_ecam.c:pci_ecam_register]`, `[pci_drivers.c:pci_register_drivers]` - Generic PCIe ECAM host controller (`[pci_ecam.c:struct pci_ecam_s]`) and built-in PCI driver initialization.
- `[pci_epc.c:pci_epc_create]`, `[pci_epc.c:pci_epc_destroy]`, `[pci_epc.c:pci_get_epc]`, `[pci_epc.c:pci_epc_add_epf]`, `[pci_epc.c:pci_epc_set_bar]`, `[pci_epc.c:pci_epc_map_addr]`, `[pci_epc.c:pci_epc_raise_irq]`, `[pci_epc_mem.c:pci_epc_mem_init]`, `[pci_epc_mem.c:pci_epc_mem_alloc_addr]` - PCI Endpoint Controller (EPC) core and outbound address window allocator.
- `[pci_epf.c:pci_epf_device_register]`, `[pci_epf.c:pci_epf_register_driver]`, `[pci_epf.c:pci_epf_alloc_space]` - PCI Endpoint Function (EPF) bus and BAR space allocation.
- `[pci_ivshmem.c:pci_ivshmem_register]`, `[pci_ivshmem.c:ivshmem_register_driver]`, `[pci_ivshmem.c:ivshmem_get_shmem]`, `[pci_ivshmem.c:ivshmem_kick_peer]`, `[pci_uio_ivshmem.c:pci_register_uio_ivshmem_driver]` - QEMU Inter-VM Shared Memory (`ivshmem`) bus and `/dev/uio_ivshmem*` character driver.
- `[pci_qemu_edu.c:pci_register_qemu_edu_driver]`, `[pci_qemu_epc.c:pci_register_qemu_epc_driver]`, `[pci_qemu_test.c:pci_register_qemu_test_driver]`, `[pci_ep_test.c:pci_register_ep_test_driver]`, `[pci_epf_test.c:pci_register_epf_test_driver]` - QEMU educational, EPC, and PCI endpoint test drivers.

## Invariants
- PCI configuration and I/O space word/dword accesses must be naturally aligned (`[pci.c:PCI_word_BAD]`, `[pci.c:PCI_dword_BAD]`), returning `-EINVAL` on misaligned offsets.
- Global PCI bus/driver lists, EPC controllers, EPF drivers, and ivshmem registries are synchronized via mutexes (`[pci.c:nxmutex_lock]`, `[pci_epc.c:nxmutex_lock]`, `[pci_epf.c:nxmutex_lock]`, `[pci_ivshmem.c:nxmutex_lock]`).

## Side Effects
- Enumerates PCI buses, programs bridge/device BARs and command registers, maps physical MMIO regions into virtual memory, allocates and connects hardware/MSI/MSI-X interrupts, and registers `/dev/pci` and `/dev/uio_ivshmem*` VFS character drivers.

## Verification
- Run: `make test`
