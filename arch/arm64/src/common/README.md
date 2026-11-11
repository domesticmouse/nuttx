# common (`nuttx/arch/arm64/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/arm64/src/common`, providing 15 header file(s) and 56 source file(s) (including `addrenv.h`, `arm64_arch.h`, `arm64_arch_timer.h`, `arm64_cpu_psci.h`).

## Interface
- `[addrenv.h:arm64_get_pgtable]`
- `[addrenv.h:arm64_map_pages]`
- `[addrenv.h:arm64_unmap_pages]`
- `[addrenv.h:ARCH_ADDRENV_VBASE]`
- `[addrenv.h:ARCH_ADDRENV_MAX_SIZE]`
- `[addrenv.h:ARCH_ADDRENV_VEND]`
- `[arm64_arch.h:modifyreg8]`
- `[arm64_arch.h:modifyreg16]`
- `[arm64_arch.h:modifyreg32]`
- `[arm64_arch.h:arch_cpu_idle]`
- `[arm64_arch.h:arm64_cpu_disable]`
- `[arm64_arch.h:arm64_cpu_enable]`
- `[arm64_arch.h:arm64_get_mpid]`
- `[arm64_arch.h:arm64_get_cpuid]`
- `[arm64_arch.h:arm64_mte_init]`
- `[arm64_arch.h:___ARCH_ARM64_SRC_COMMON_ARM64_ARCH_H]`
- `[arm64_arch.h:BIT64]`
- `[arm64_arch.h:BIT_MASK]`
- `[arm64_arch.h:BIT64_MASK]`
- `[arm64_arch.h:DAIFSET_FIQ_BIT]`
- `[arm64_arch.h:DAIFSET_IRQ_BIT]`
- `[arm64_arch.h:DAIFSET_ABT_BIT]`
- `[arm64_arch.h:DAIFSET_DBG_BIT]`
- `[arm64_arch.h:DAIFCLR_FIQ_BIT]`
- `[arm64_arch.h:DAIFCLR_IRQ_BIT]`
- `[arm64_arch.h:DAIFCLR_ABT_BIT]`
- `[arm64_arch.h:DAIFCLR_DBG_BIT]`
- `[arm64_arch_timer.h:arm64_oneshot_initialize]`
- `[arm64_cpu_psci.h:psci_version]`
- `[arm64_cpu_psci.h:psci_cpu_off]`

## Invariants
- `[arm64_internal.h:#error]` Compile-time guard: CONFIG_ARCH_INTERRUPTSTACK must be defined (4096 at least) at arm64
- `[pgalloc.h:#error]` Compile-time guard: ARM64 needs CONFIG_ARCH_PGPOOL_MAPPING
- `[arm64_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm64_addrenv_mmu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm64_addrenv_mmu.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[arm64_addrenv_mmu.c:#error]` Compile-time configuration constraint: This module is intended to be used with CONFIG_BUILD_KERNEL
- `[arm64_addrenv_mpu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm64_addrenv_pgmap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm64_addrenv_shm.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm64_arch_timer.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm64_cache.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm64_cpuidlestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[arm64_arch.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[arm64_arch.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[arm64_arch.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[arm64_arch.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[arm64_mmu.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[arm64_aes.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[arm64_arch_timer.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[arm64_arch_timer.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[arm64_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[arm64_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[arm64_cache.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[arm64_gicv2.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
