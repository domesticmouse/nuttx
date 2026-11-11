# Flattened Device Tree (FDT) Drivers (`drivers/devicetree`)

## Overview
Provides Flattened Device Tree (FDT) registration, property/address/interrupt parsing helpers built on `libfdt`, and FDT-driven bus/device discovery for CFI flash (`cfi-flash`), generic PCI ECAM host bridges (`pci-host-ecam-generic`), and VirtIO MMIO devices (`virtio,mmio`).

## Interface
- `fdt.c:fdt_register`, `fdt.c:fdt_get` - Validates the FDT magic header (`FDT_MAGIC`) and stores/retrieves the system raw FDT base pointer (`g_fdt_base`).
- `fdt.c:fdt_get_irq`, `fdt.c:fdt_get_irq_by_path`, `fdt.c:fdt_get_bankwidth`, `fdt.c:fdt_get_parent_address_cells`, `fdt.c:fdt_get_parent_size_cells`, `fdt.c:fdt_ld_by_cells`, `fdt.c:fdt_get_reg_count`, `fdt.c:fdt_get_reg_base`, `fdt.c:fdt_get_reg_base_by_index`, `fdt.c:fdt_get_reg_base_by_name`, `fdt.c:fdt_get_reg_base_by_path`, `fdt.c:fdt_get_reg_size`, `fdt.c:fdt_get_reg_size_by_index`, `fdt.c:fdt_device_is_available`, `fdt.c:fdt_get_node_label`, `fdt.c:fdt_get_clock_frequency`, `fdt.c:fdt_get_clock_frequency_from_clocks`, `fdt.c:fdt_node_index_from_label`, `fdt.c:fdt_node_from_compat`, `fdt.c:fdt_load_prop_u32` - Parses FDT nodes, register ranges, interrupts, clocks, and `status` properties.
- `fdt_cfi.c:fdt_cfi_register` - Scans the FDT for `cfi-flash` nodes and registers CFI MTD drivers via `register_cfi_driver`.
- `fdt_pci.c:fdt_pci_ecam_register` - Parses `pci-host-ecam-generic` FDT nodes and registers the PCI ECAM controller via `pci_ecam_register`.
- `fdt_virtio_mmio.c:fdt_virtio_mmio_devices_register` - Scans the FDT for `virtio,mmio` nodes and registers VirtIO MMIO devices via `virtio_register_mmio_device`.

## Invariants
- `fdt.c:fdt_register` asserts `fdt_base != NULL` and only updates `g_fdt_base` if `fdt_header->magic == be32toh(FDT_MAGIC)`.
- `fdt.c:fdt_node_from_compat` asserts `compatible_ids != NULL` and `driver_callback != NULL`; `fdt.c:fdt_load_prop_u32` asserts `property != NULL` and `value != NULL`.
- `fdt_cfi.c:fdt_cfi_register` skips flash regions that overlap the active firmware text region (`CONFIG_FLASH_START` to `CONFIG_FLASH_START + CONFIG_FLASH_SIZE`).

## Side Effects
- Updates the global `g_fdt_base` pointer (`fdt.c:fdt_register`).
- Registers CFI flash MTD devices (`register_cfi_driver` in `fdt_cfi.c:fdt_cfi_register`), PCI ECAM host controllers (`pci_ecam_register` in `fdt_pci.c:fdt_pci_ecam_register`), and VirtIO MMIO devices (`virtio_register_mmio_device` in `fdt_virtio_mmio.c:fdt_virtio_mmio_devices_register`).

## Verification
- Run: `make test`
