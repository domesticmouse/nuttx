# goldfish (`nuttx/arch/arm/src/goldfish`)

## Overview
Hardware abstraction and architecture package for `goldfish` (Goldfish Virt Chip Selection) under `nuttx/arch/arm/src/goldfish`, providing 3 header file(s) and 7 source file(s) (including `chip.h`, `goldfish_irq.h`, `goldfish_memorymap.h`, `goldfish_boot.c`).

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
- `[goldfish_irq.h:arm_earlyirqinit]`
- `[goldfish_memorymap.h:goldfish_setupmappings]`
- `[goldfish_memorymap.h:VIRT_FLASH_PSECTION]`
- `[goldfish_memorymap.h:VIRT_IO_PSECTION]`
- `[goldfish_memorymap.h:VIRT_PCIE_PSECTION]`
- `[goldfish_memorymap.h:VIRT_DDR_PSECTION]`
- `[goldfish_memorymap.h:VIRT_FLASH_VSECTION]`
- `[goldfish_memorymap.h:VIRT_IO_VSECTION]`
- `[goldfish_memorymap.h:VIRT_PCIE_VSECTION]`
- `[goldfish_memorymap.h:VIRT_DDR_VSECTION]`
- `[goldfish_memorymap.h:VIRT_FLASH_SECSIZE]`
- `[goldfish_memorymap.h:VIRT_IO_SECSIZE]`
- `[goldfish_memorymap.h:VIRT_PCIE_SECSIZE]`
- `[goldfish_memorymap.h:VIRT_DDR_SECSIZE]`
- `[goldfish_boot.c:arm_boot]`
- `[goldfish_boot.c:up_cpu_start]`
- `[goldfish_cpuboot.c:arm_cpu_boot]`
- `[goldfish_irq.c:up_irqinitialize]`

## Invariants
- `[goldfish_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[goldfish_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[goldfish_pgalloc.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_PGPOOL_MAPPING must be selected
- `[goldfish_timer.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- None

## Verification
- Run: `make test`
