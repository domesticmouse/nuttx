# xtensa (`nuttx/arch/xtensa/include/xtensa`)

## Overview
Hardware abstraction and architecture package for `xtensa` under `nuttx/arch/xtensa/include/xtensa`, providing 6 header file(s) and 0 source file(s) (including `core.h`, `core_macros.h`, `xtensa_abi.h`, `xtensa_coproc.h`).

## Interface
- `[core.h:XCHAL_SEP]`
- `[core.h:XCHAL_SEP2]`
- `[core.h:WSBITS]`
- `[core.h:WBBITS]`
- `[core.h:XCHAL_HAVE_LE]`
- `[core.h:XCHAL_MEMORY_ORDER]`
- `[core.h:XCHAL_IRQ_LEVEL]`
- `[core.h:_XCHAL_INTLEVEL_MASK]`
- `[core.h:XCHAL_INTLEVEL_MASK]`
- `[core.h:_XCHAL_INTLEVEL_ANDBELOWMASK]`
- `[core_macros.h:XTHAL_GET_CCOUNT]`
- `[core_macros.h:XTHAL_SET_CCOUNT]`
- `[xtensa_abi.h:ENTRY]`
- `[xtensa_abi.h:ENTRY0]`
- `[xtensa_abi.h:RET]`
- `[xtensa_abi.h:RET0]`
- `[xtensa_abi.h:CALL]`
- `[xtensa_abi.h:ARG1]`
- `[xtensa_abi.h:ARG2]`
- `[xtensa_abi.h:ARG3]`
- `[xtensa_abi.h:ARG4]`
- `[xtensa_abi.h:ARG5]`
- `[xtensa_abi.h:ARG6]`
- `[xtensa_abi.h:RETVAL]`
- `[xtensa_coproc.h:xtensa_cpstate_s]`
- `[xtensa_coproc.h:_CP_MASK]`
- `[xtensa_coproc.h:_CP_ALIGNUP]`
- `[xtensa_coproc.h:_CP_ALIGNDOWN]`
- `[xtensa_coproc.h:XTENSA_CP_ALLSET]`
- `[xtensa_coproc.h:XTENSA_CP0_SA]`

## Invariants
- `[xtensa_coproc.h:static_assert]` Enforces compile-time structure size and layout invariants

## Side Effects
- `[core_macros.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[xtensa_coproc.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
