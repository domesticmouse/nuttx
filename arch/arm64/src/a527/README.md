# a527 (`nuttx/arch/arm64/src/a527`)

## Overview
Hardware abstraction and architecture package for `a527` under `nuttx/arch/arm64/src/a527`, providing 2 header file(s) and 4 source file(s) (including `a527_boot.h`, `chip.h`, `a527_boot.c`, `a527_initialize.c`).

## Interface
- `[a527_boot.h:a527_board_initialize]`
- `[a527_boot.h:CONFIG_SYS_CLOCK_HW_CYCLES_PER_SEC]`
- `[a527_boot.c:arm64_get_mpid]`
- `[a527_boot.c:arm64_get_cpuid]`
- `[a527_boot.c:arm64_el_init]`
- `[a527_boot.c:arm64_chip_boot]`
- `[a527_initialize.c:arm64_pminitialize]`
- `[a527_initialize.c:up_idle]`
- `[a527_serial.c:arm64_earlyserialinit]`
- `[a527_serial.c:arm64_serialinit]`
- `[a527_textheap.c:up_textheap_memalign]`
- `[a527_textheap.c:up_textheap_free]`
- `[a527_textheap.c:up_textheap_heapmember]`
- `[CMakeLists.txt:target_sources]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[a527_boot.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation

## Side Effects
- None

## Verification
- Run: `make test`
