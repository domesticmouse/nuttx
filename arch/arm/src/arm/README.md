# arm (`nuttx/arch/arm/src/arm`)

## Overview
Hardware abstraction and architecture package for `arm` (ARM Configuration Options) under `nuttx/arch/arm/src/arm`, providing 2 header file(s) and 11 source file(s) (including `arm.h`, `pg_macros.h`, `arm_allocpage.c`, `arm_checkmapping.c`).

## Interface
- `[arm.h:PSR_MODE_MASK]`
- `[arm.h:PSR_MODE_USR26]`
- `[arm.h:PSR_MODE_FIQ26]`
- `[arm.h:PSR_MODE_IRQ26]`
- `[arm.h:PSR_MODE_SVC26]`
- `[arm.h:PSR_MODE_MODE32]`
- `[arm.h:PSR_MODE_USR]`
- `[arm.h:PSR_MODE_FIQ]`
- `[arm.h:PSR_MODE_IRQ]`
- `[arm.h:PSR_MODE_SVC]`
- `[arm.h:PSR_MODE_ABT]`
- `[arm.h:PSR_MODE_UND]`
- `[pg_macros.h:PGTABLE_BASE_VADDR]`
- `[pg_macros.h:PGTABLE_L2_FINE_VBASE]`
- `[pg_macros.h:PGTABLE_L2_COARSE_VBASE]`
- `[pg_macros.h:PGTABLE_L2_BASE_PADDR]`
- `[pg_macros.h:PGTABLE_L2_BASE_VADDR]`
- `[pg_macros.h:PTE_NPAGES]`
- `[pg_macros.h:PG_L1_PADDRMASK]`
- `[pg_macros.h:MMU_L1_TEXTFLAGS]`
- `[pg_macros.h:MMU_L2_TEXTFLAGS]`
- `[pg_macros.h:MMU_L1_DATAFLAGS]`
- `[pg_macros.h:MMU_L2_DATAFLAGS]`
- `[pg_macros.h:MMU_L2_ALLOCFLAGS]`
- `[arm_allocpage.c:up_allocpage]`
- `[arm_checkmapping.c:up_checkmapping]`
- `[arm_dataabort.c:arm_dataabort]`
- `[arm_doirq.c:arm_doirq]`
- `[arm_initialstate.c:up_initial_state]`
- `[arm_pginitialize.c:arm_pginitialize]`

## Invariants
- `[pg_macros.h:#error]` Compile-time guard: Cannot support both CONFIG_LEGACY_PAGING and CONFIG_ARCH_ROMPGTABLE
- `[arm_allocpage.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_checkmapping.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_syscall.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_syscall.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_va2pte.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[arm.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
