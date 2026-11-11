# qemu (`nuttx/arch/arm/src/qemu`)

## Overview
Hardware abstraction and architecture package for `qemu` (Qemu Virt Chip Selection) under `nuttx/arch/arm/src/qemu`, providing 4 header file(s) and 10 source file(s) (including `chip.h`, `qemu_irq.h`, `qemu_memorymap.h`, `qemu_userspace.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/qemu/hardware`, providing 1 header file(s) and 0 source file(s) (including `qemu_memorymap.h`).

## Interface
- `[chip.h:QEMU_SPI_IRQ_BASE]`
- `[chip.h:CHIP_MPCORE_VBASE]`
- `[chip.h:MPCORE_ICD_OFFSET]`
- `[chip.h:MPCORE_ICC_OFFSET]`
- `[chip.h:MPCORE_V2M_OFFSET]`
- `[chip.h:PGTABLE_SIZE]`
- `[chip.h:PGTABLE_BASE_PADDR]`
- `[chip.h:PGTABLE_BASE_VADDR]`
- `[chip.h:CONFIG_RAM_END]`
- `[chip.h:NUTTX_TEXT_VADDR]`
- `[chip.h:NUTTX_TEXT_PADDR]`
- `[chip.h:NUTTX_TEXT_PEND]`
- `[qemu_irq.h:arm_earlyirqinit]`
- `[qemu_memorymap.h:qemu_setupmappings]`
- `[qemu_memorymap.h:VIRT_FLASH_PSECTION]`
- `[qemu_memorymap.h:VIRT_IO_PSECTION]`
- `[qemu_memorymap.h:VIRT_SEC_MEM_PSECTION]`
- `[qemu_memorymap.h:VIRT_PCIE_PSECTION]`
- `[qemu_memorymap.h:VIRT_DDR_PSECTION]`
- `[qemu_memorymap.h:VIRT_FLASH_VSECTION]`
- `[qemu_memorymap.h:VIRT_IO_VSECTION]`
- `[qemu_memorymap.h:VIRT_SEC_MEM_VSECTION]`
- `[qemu_memorymap.h:VIRT_PCIE_VSECTION]`
- `[qemu_memorymap.h:VIRT_DDR_VSECTION]`
- `[qemu_memorymap.h:VIRT_FLASH_SECSIZE]`
- `[qemu_memorymap.h:VIRT_IO_SECSIZE]`
- `[qemu_userspace.h:qemu_userspace]`
- `[qemu_allocateheap.c:up_allocate_heap]`
- `[qemu_allocateheap.c:up_allocate_kheap]`
- `[qemu_boot.c:arm_boot]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[qemu_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[qemu_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[qemu_pgalloc.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_PGPOOL_MAPPING must be selected
- `[qemu_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[qemu_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
