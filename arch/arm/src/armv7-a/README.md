# armv7-a (`nuttx/arch/arm/src/armv7-a`)

## Overview
Hardware abstraction and architecture package for `armv7-a` (ARMv7-A Configuration Options; L2 Cache Configuration) under `nuttx/arch/arm/src/armv7-a`, providing 15 header file(s) and 42 source file(s) (including `addrenv.h`, `arm.h`, `arm_cpu_psci.h`, `arm_timer.h`).

## Interface
- `[addrenv.h:arm_addrenv_create_region]`
- `[addrenv.h:arm_addrenv_fork_region]`
- `[addrenv.h:arm_addrenv_destroy_region]`
- `[addrenv.h:arm_addrenv_va_to_pa]`
- `[addrenv.h:ENTRIES_PER_L2TABLE]`
- `[arm.h:arm_data_initialize]`
- `[arm.h:arm_fault_kill]`
- `[arm.h:PSR_MODE_SHIFT]`
- `[arm.h:PSR_MODE_MASK]`
- `[arm.h:PSR_MODE_USR]`
- `[arm.h:PSR_MODE_FIQ]`
- `[arm.h:PSR_MODE_IRQ]`
- `[arm.h:PSR_MODE_SVC]`
- `[arm.h:PSR_MODE_MON]`
- `[arm.h:PSR_MODE_ABT]`
- `[arm.h:PSR_MODE_HYP]`
- `[arm.h:PSR_MODE_UND]`
- `[arm.h:PSR_MODE_SYS]`
- `[arm.h:PSR_T_BIT]`
- `[arm_cpu_psci.h:arm_smccc_hvc]`
- `[arm_cpu_psci.h:arm_smccc_smc]`
- `[arm_cpu_psci.h:psci_version]`
- `[arm_cpu_psci.h:psci_cpu_off]`
- `[arm_cpu_psci.h:psci_cpu_on]`
- `[arm_cpu_psci.h:psci_sys_poweroff]`
- `[arm_cpu_psci.h:psci_sys_reset]`
- `[arm_cpu_psci.h:arm_smccc_res]`
- `[arm_cpu_psci.h:arm_smccc_conduit]`
- `[arm_cpu_psci.h:psci_interface]`
- `[arm_cpu_psci.h:arm_smccc_res_t]`

## Invariants
- `[mmu.h:#error]` Compile-time guard: Cannot support both CONFIG_LEGACY_PAGING/CONFIG_ARCH_ADDRENV and CONFIG_ARCH_ROMPGTABLE
- `[pgalloc.h:#error]` Compile-time guard: ARMv7-A needs CONFIG_ARCH_PGPOOL_MAPPING
- `[pgalloc.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers
- `[smp.h:#error]` Compile-time guard: This logic needs to extended for CONFIG_SMP_NCPUS > 4
- `[arm_addrenv.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_addrenv.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_TEXT_VBASE not aligned to section boundary
- `[arm_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_addrenv_shm.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_addrenv_ustack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_addrenv_ustack.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_STACK_VBASE not aligned to section boundary
- `[arm_addrenv_utils.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_allocpage.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[gic.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[arm_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[arm_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[arm_gicv2.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_gicv2.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_gicv2.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[arm_gicv2.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[arm_gicv2.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[arm_gicv2_dump.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_gicv2m.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_l2cc_pl310.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_l2cc_pl310.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
