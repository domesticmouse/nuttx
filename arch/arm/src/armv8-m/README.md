# armv8-m (`nuttx/arch/arm/src/armv8-m`)

## Overview
Hardware abstraction and architecture package for `armv8-m` (ARMv8-M Configuration Options) under `nuttx/arch/arm/src/armv8-m`, providing 14 header file(s) and 32 source file(s) (including `dwt.h`, `etm.h`, `exc_return.h`, `fpb.h`).

## Interface
- `[dwt.h:DWT_BASE]`
- `[dwt.h:DWT_CTRL]`
- `[dwt.h:DWT_CYCCNT]`
- `[dwt.h:DWT_CPICNT]`
- `[dwt.h:DWT_EXCCNT]`
- `[dwt.h:DWT_SLEEPCNT]`
- `[dwt.h:DWT_LSUCNT]`
- `[dwt.h:DWT_FOLDCNT]`
- `[dwt.h:DWT_PCSR]`
- `[dwt.h:DWT_COMP0]`
- `[dwt.h:DWT_FUNCTION0]`
- `[dwt.h:DWT_MASK0]`
- `[etm.h:ETM_BASE]`
- `[etm.h:ETM_ETMCR_OFFSET]`
- `[etm.h:ETM_ETMCCR_OFFSET]`
- `[etm.h:ETM_ETMTRIGGER_OFFSET]`
- `[etm.h:ETM_ETMSR_OFFSET]`
- `[etm.h:ETM_ETMSCR_OFFSET]`
- `[etm.h:ETM_ETMTEEVR_OFFSET]`
- `[etm.h:ETM_ETMTECR1_OFFSET]`
- `[etm.h:ETM_ETMFFLR_OFFSET]`
- `[etm.h:ETM_ETMCNTRLDVR1_OFFSET]`
- `[etm.h:ETM_ETMSYNCFR_OFFSET]`
- `[etm.h:ETM_ETMIDR_OFFSET]`
- `[exc_return.h:EXC_RETURN_EXC_SECURE]`
- `[exc_return.h:EXC_RETURN_PROCESS_STACK]`
- `[exc_return.h:EXC_RETURN_THREAD_MODE]`
- `[exc_return.h:EXC_RETURN_STD_CONTEXT]`
- `[exc_return.h:EXC_RETURN_DEF_STACKING]`
- `[exc_return.h:EXC_RETURN_SECURE_STACK]`

## Invariants
- `[mpu.h:#error]` Compile-time guard: FIXME: Unsupported number of MPU regions
- `[arm_busfault.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_busfault.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[arm_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_doirq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[arm_hardfault.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_hardfault.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[arm_itm_syslog.c:#error]` Compile-time configuration constraint: CONFIG_ARMV8M_ITMSYSLOG_SWODIV should be at least equal to 1
- `[arm_memfault.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_memfault.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[arm_mpu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_ramvec_attach.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[mpu.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[pmu.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[pmu.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sau.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[arm_busfault.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_cache.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_cache.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[arm_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[arm_cache.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[arm_cpuinfo.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_dbgmonitor.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
