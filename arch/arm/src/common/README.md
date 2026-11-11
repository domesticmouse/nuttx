# common (`nuttx/arch/arm/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/arm/src/common`, providing 3 header file(s) and 27 source file(s) (including `arm_fork.h`, `arm_internal.h`, `hwcap.h`, `arm_allocateheap.c`).

## Subdirectories & Boundaries
- `ameba`: [./ameba/README.md](./ameba/README.md) - Hardware abstraction and architecture package for `ameba` (Ameba Peripheral Support) under `nuttx/arch/arm/src/common/ameba`, providing 12 header file(s) and 13 source file(s) (including `ameba_adc.h`, `ameba_flash_mtd.h`, `ameba_gpio.h`, `ameba_i2c.h`).
- `stm32`: [./stm32/README.md](./stm32/README.md) - Hardware abstraction and architecture package for `stm32` (STM32 Configuration Options; ADC Configuration) under `nuttx/arch/arm/src/common/stm32`, providing 95 header file(s) and 132 source file(s) (including `stm32_1wire.h`, `stm32_adc.h`, `stm32_adc_m0_v1.h`, `stm32_adc_m3m4_v1v2.h`).

## Interface
- `[arm_fork.h:fork_s]`
- `[arm_fork.h:FORK_R4_OFFSET]`
- `[arm_fork.h:FORK_R5_OFFSET]`
- `[arm_fork.h:FORK_R6_OFFSET]`
- `[arm_fork.h:FORK_R7_OFFSET]`
- `[arm_fork.h:FORK_R8_OFFSET]`
- `[arm_fork.h:FORK_R9_OFFSET]`
- `[arm_fork.h:FORK_R10_OFFSET]`
- `[arm_fork.h:FORK_FP_OFFSET]`
- `[arm_fork.h:FORK_SP_OFFSET]`
- `[arm_fork.h:FORK_LR_OFFSET]`
- `[arm_fork.h:FORK_SIZEOF]`
- `[arm_internal.h:modifyreg8]`
- `[arm_internal.h:modifyreg16]`
- `[arm_internal.h:modifyreg32]`
- `[arm_internal.h:arm_boot]`
- `[arm_internal.h:arm_psci_init]`
- `[arm_internal.h:arm_decodeirq]`
- `[arm_internal.h:arm_sigdeliver]`
- `[arm_internal.h:arm_pminitialize]`
- `[arm_internal.h:arm_initialize_stack]`
- `[arm_internal.h:arm_ack_irq]`
- `[arm_internal.h:arm_doirq]`
- `[arm_internal.h:arm_dispatch_syscall]`
- `[arm_internal.h:arm_svcall]`
- `[arm_internal.h:arm_hardfault]`
- `[arm_internal.h:arm_memfault]`
- `[arm_internal.h:arm_busfault]`
- `[arm_internal.h:arm_usagefault]`
- `[arm_internal.h:arm_securefault]`
- [./ameba/README.md](./ameba/README.md)
- [./stm32/README.md](./stm32/README.md)

## Invariants
- `[arm_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_exit.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_fork.c:#error]` Compile-time configuration constraint: Missing logic
- `[arm_modifyreg.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[arm_pthread_start.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_task_start.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[arm_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[arm_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[arm_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[arm_hostfs.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[arm_hostfs.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[arm_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[arm_modifyreg.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_modifyreg.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[arm_modifyreg.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_modifyreg.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[arm_modifyreg.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[arm_tls.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
