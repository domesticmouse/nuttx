# NuttX PCI Subsystem (`include/nuttx/pci`)

## Overview
Defines the Peripheral Component Interconnect (PCI and PCIe) host controller, bus enumeration, device driver, Endpoint Controller (`EPC`), Endpoint Function (`EPF`), Enhanced Configuration Access Mechanism (`ECAM`), and Inter-VM Shared Memory (`ivshmem`) interfaces for NuttX.

## Interface
- `pci.h:pci_device_s`, `pci.h:pci_bus_s`, `pci.h:pci_controller_s`, `pci.h:pci_driver_s`, `pci.h:pci_ops_s`, `pci.h:pci_resource_s`, `pci.h:pci_device_id_s` - Core PCI topology, BAR resource, host controller operations, and driver matching structures.
- `pci.h:pci_bus_read_config`, `pci.h:pci_bus_write_config`, `pci.h:pci_bus_read_io`, `pci.h:pci_bus_write_io`, `pci.h:pci_enable_device`, `pci.h:pci_disable_device`, `pci.h:pci_set_master`, `pci.h:pci_clear_master`, `pci.h:pci_map_bar`, `pci.h:pci_map_bar_region`, `pci.h:pci_find_capability`, `pci.h:pci_alloc_irq` - Configuration space, PIO/MMIO access, bus mastering, BAR mapping, capability traversal, and MSI/MSI-X IRQ allocation APIs.
- `pci_epc.h:pci_epc_ctrl_s`, `pci_epc.h:pci_epc_ops_s`, `pci_epc.h:pci_epc_features_s`, `pci_epc.h:pci_epc_set_bar`, `pci_epc.h:pci_epc_map_addr`, `pci_epc.h:pci_epc_raise_irq`, `pci_epc.h:pci_epc_start`, `pci_epc.h:pci_epc_stop` - PCIe Endpoint Controller abstraction for configuring outbound windows, BARs, and raising legacy/MSI/MSI-X interrupts to the host.
- `pci_epf.h:pci_epf_device_s`, `pci_epf.h:pci_epf_driver_s`, `pci_epf.h:pci_epf_bar_s`, `pci_epf.h:pci_epf_device_register`, `pci_epf.h:pci_epf_register_driver`, `pci_epf.h:pci_epf_alloc_space` - PCIe Endpoint Function device/driver registration and BAR backing-memory allocation.
- `pci_ecam.h:pci_ecam_register` - Generic PCIe ECAM host controller registration.
- `pci_ivshmem.h:ivshmem_driver_s`, `pci_ivshmem.h:ivshmem_register_driver`, `pci_ivshmem.h:ivshmem_get_shmem`, `pci_ivshmem.h:ivshmem_kick_peer`, `pci_ivshmem.h:pci_ivshemem_register` - QEMU/KVM Inter-VM shared memory PCI device and peer-notification interface.
- `pci_ep_test.h:pci_ep_test_param_s`, `pci_ep_test.h:pci_register_epf_test_device`, `pci_ep_test.h:PCITEST_BAR`, `pci_ep_test.h:PCITEST_MSI` - PCI endpoint test host driver ioctls and registration.
- `pci_ids.h:PCI_BASE_CLASS_STORAGE`, `pci_regs.h:PCI_VENDOR_ID`, `pci_regs.h:PCI_COMMAND`, `pci_regs.h:PCI_STD_NUM_BARS` - Standard PCI vendor/class IDs and configuration register offsets.

## Invariants
- Device/function identifiers passed as `devfn` must be encoded using `pci.h:PCI_DEVFN` (bits 7:3 for slot, bits 2:0 for function) and decoded via `pci.h:PCI_SLOT` and `pci.h:PCI_FUNC`.
- Each PCI device maintains at most `pci.h:PCI_NUM_RESOURCES` BAR and expansion ROM descriptors (`0..5` standard BARs via `pci.h:PCI_STD_RESOURCE_END`, `6` for `pci.h:PCI_ROM_RESOURCE`).

## Side Effects
- Configuration space and I/O helpers (`pci.h:pci_bus_write_config`, `pci.h:pci_write_mmio_dword`, `pci.h:pci_enable_device`, `pci.h:pci_set_master`) directly mutate hardware PCI configuration registers, BAR decoders, and DMA bus-mastering bits.
- `pci_epf.h:pci_epf_alloc_space` allocates DMA-capable memory aligned to endpoint BAR requirements, and `pci_epc.h:pci_epc_raise_irq` triggers hardware interrupts across the PCIe link.

## Verification
- Run: `make test`
