# include (`nuttx/arch/tricore/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/tricore/include`, providing 9 header file(s) and 0 source file(s) (including `arch.h`, `barriers.h`, `csfr.h`, `inttypes.h`).

## Subdirectories & Boundaries
- `tc3xx`: [./tc3xx/README.md](./tc3xx/README.md) - Hardware abstraction and architecture package for `tc3xx` under `nuttx/arch/tricore/include/tc3xx`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).
- `tc4xx`: [./tc4xx/README.md](./tc4xx/README.md) - Hardware abstraction and architecture package for `tc4xx` under `nuttx/arch/tricore/include/tc4xx`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[arch.h:tricore_mtcr]`
- `[arch.h:tricore_mfcr]`
- `[arch.h:tricore_jump_backto_link]`
- `[barriers.h:UP_DSB]`
- `[barriers.h:UP_DMB]`
- `[barriers.h:UP_RMB]`
- `[barriers.h:UP_WMB]`
- `[barriers.h:UP_ISB]`
- `[csfr.h:TRICORE_CPU_PCXI]`
- `[csfr.h:TRICORE_CPU_PSW]`
- `[csfr.h:TRICORE_CPU_PC]`
- `[csfr.h:TRICORE_CPU_CORE_ID]`
- `[csfr.h:TRICORE_CPU_ICR]`
- `[csfr.h:TRICORE_CPU_FCX]`
- `[csfr.h:TRICORE_CPU_CORECON]`
- `[csfr.h:TRICORE_CPU_CCTRL]`
- `[csfr.h:TRICORE_CPU_CCNT]`
- `[csfr.h:TRICORE_CPU_PSTR]`
- `[csfr.h:TRICORE_CPU_DSTR]`
- `[csfr.h:TRICORE_CPU_DATR]`
- `[inttypes.h:INT32_C]`
- `[inttypes.h:INT64_C]`
- `[inttypes.h:UINT32_C]`
- `[inttypes.h:UINT64_C]`
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRId64]`
- `[inttypes.h:PRIdPTR]`
- `[inttypes.h:PRIi8]`
- [./tc3xx/README.md](./tc3xx/README.md)
- [./tc4xx/README.md](./tc4xx/README.md)

## Invariants
- None

## Side Effects
- `[arch.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
