# nuttsbi (`nuttx/arch/risc-v/src/nuttsbi`)

## Overview
Hardware abstraction and architecture package for `nuttsbi` under `nuttx/arch/risc-v/src/nuttsbi`, providing 2 header file(s) and 6 source file(s) (including `sbi_internal.h`, `sbi_mcall.h`, `sbi_ipi.c`, `sbi_mcall.c`).

## Interface
- `[sbi_internal.h:sbi_mscratch_assign]`
- `[sbi_internal.h:sbi_send_ipi]`
- `[sbi_internal.h:sbi_init_mtimer]`
- `[sbi_internal.h:sbi_get_mtime]`
- `[sbi_internal.h:sbi_set_mtimecmp]`
- `[sbi_internal.h:sbi_late_initialize]`
- `[sbi_internal.h:MMODE_HART_CNT]`
- `[sbi_internal.h:MMODE_IRQSTACK]`
- `[sbi_internal.h:IPI_IRQ]`
- `[sbi_internal.h:IPI_BASE]`
- `[sbi_internal.h:MTIMER_IRQ]`
- `[sbi_internal.h:MTIMER_TIME_BASE]`
- `[sbi_internal.h:MTIMER_CMP_BASE]`
- `[sbi_internal.h:TEMP_STACK_BASE]`
- `[sbi_internal.h:TEMP_STACK]`
- `[sbi_internal.h:TEMP_STACK_SIZE]`
- `[sbi_mcall.h:SBI_EXT_FIRMWARE]`
- `[sbi_mcall.h:SBI_EXT_FIRMWARE_GET_MTIME]`
- `[sbi_ipi.c:sbi_send_ipi]`
- `[sbi_mcall.c:sbi_mcall_handle]`
- `[sbi_mexception.c:sbi_mexception]`
- `[sbi_mscratch.c:sbi_mscratch_assign]`
- `[sbi_mtimer.c:sbi_init_mtimer]`
- `[sbi_mtimer.c:sbi_get_mtime]`
- `[sbi_mtimer.c:sbi_set_mtimecmp]`
- `[sbi_start.c:sbi_start]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_NUTTSBI]`
- `[Kconfig:CONFIG_NUTTSBI_HART_CNT]`
- `[Kconfig:CONFIG_NUTTSBI_IPI_BASE]`

## Invariants
- `[sbi_start.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sbi_start.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation

## Side Effects
- `[sbi_ipi.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sbi_mexception.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[sbi_mtimer.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sbi_mtimer.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sbi_start.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
