# common (`nuttx/arch/risc-v/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/risc-v/src/common`, providing 11 header file(s) and 54 source file(s) (including `addrenv.h`, `pgalloc.h`, `riscv_aia.h`, `riscv_common_memorymap.h`).

## Subdirectories & Boundaries
- `espressif`: [./espressif/README.md](./espressif/README.md) - Hardware abstraction and architecture package for `espressif` (Espressif DFS Options; Espressif Log Level) under `nuttx/arch/risc-v/src/common/espressif`, providing 54 header file(s) and 61 source file(s) (including `chip.h`, `esp_adc.h`, `esp_aes.h`, `esp_ana_cmpr.h`).
- `supervisor`: [./supervisor/README.md](./supervisor/README.md) - Hardware abstraction and architecture package for `supervisor` under `nuttx/arch/risc-v/src/common/supervisor`, providing 0 header file(s) and 2 source file(s) (including `riscv_perform_syscall.c`, `riscv_sbi.c`).

## Interface
- `[addrenv.h:riscv_get_pgtable]`
- `[addrenv.h:riscv_map_pages]`
- `[addrenv.h:riscv_unmap_pages]`
- `[addrenv.h:ARCH_ADDRENV_VBASE]`
- `[addrenv.h:ARCH_ADDRENV_MAX_SIZE]`
- `[addrenv.h:ARCH_ADDRENV_VEND]`
- `[riscv_aia.h:riscv_imsic_local_eix_update]`
- `[riscv_aia.h:riscv_imsic_send_ipi]`
- `[riscv_aia.h:riscv_aplic_init]`
- `[riscv_aia.h:riscv_aplic_init_msi]`
- `[riscv_aia.h:aplic_mode_arg_u]`
- `[riscv_aia.h:RISCV_IMSIC_MAX_REGS]`
- `[riscv_aia.h:RISCV_IMSIC_MMIO_PAGE_LE]`
- `[riscv_aia.h:RISCV_IMSIC_MMIO_PAGE_BE]`
- `[riscv_aia.h:RISCV_IMSIC_MMIO_PAGE_BIT]`
- `[riscv_aia.h:RISCV_IMSIC_TOPEI_ID_BIT]`
- `[riscv_aia.h:RISCV_IMSIC_EIP_BITS]`
- `[riscv_aia.h:RISCV_IMSIC_EIE_BITS]`
- `[riscv_aia.h:RISCV_IMSIC_DISABLE_EIDELIVERY]`
- `[riscv_aia.h:RISCV_IMSIC_ENABLE_EIDELIVERY]`
- `[riscv_aia.h:RISCV_IMSIC_DISABLE_EITHRESHOLD]`
- `[riscv_aia.h:RISCV_IMSIC_ENABLE_EITHRESHOLD]`
- `[riscv_aia.h:RISCV_IMSIC_IPI_ID]`
- `[riscv_common_memorymap.h:_START_TEXT]`
- `[riscv_common_memorymap.h:_END_TEXT]`
- `[riscv_common_memorymap.h:_START_BSS]`
- `[riscv_common_memorymap.h:_END_BSS]`
- `[riscv_common_memorymap.h:_DATA_INIT]`
- `[riscv_common_memorymap.h:_START_DATA]`
- `[riscv_common_memorymap.h:_END_DATA]`
- [./espressif/README.md](./espressif/README.md)
- [./supervisor/README.md](./supervisor/README.md)

## Invariants
- `[pgalloc.h:#error]` Compile-time guard: RISC-V needs CONFIG_ARCH_PGPOOL_MAPPING
- `[riscv_ipi.h:#error]` Compile-time guard: No IPI support for this SoC
- `[riscv_mmu.h:#error]` Compile-time guard: Unsupported RISC-V MMU implementation selected
- `[riscv_addrenv.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[riscv_addrenv.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[riscv_addrenv.c:#error]` Compile-time configuration constraint: This module is intended to be used with CONFIG_BUILD_KERNEL
- `[riscv_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[riscv_addrenv_pgmap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[riscv_addrenv_shm.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[riscv_backtrace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[riscv_cpuidlestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[riscv_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[riscv_aia.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[riscv_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[riscv_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[riscv_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[riscv_internal.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[riscv_ipi.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[riscv_mmu.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[riscv_mtimer.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[riscv_mtimer.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[crt0.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[riscv_aplic.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[riscv_backtrace.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
