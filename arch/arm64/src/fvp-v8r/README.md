# fvp-v8r (`nuttx/arch/arm64/src/fvp-v8r`)

## Overview
Hardware abstraction and architecture package for `fvp-v8r` (FVP ARMv8-R Virt Chip Selection) under `nuttx/arch/arm64/src/fvp-v8r`, providing 3 header file(s) and 3 source file(s) (including `chip.h`, `fvp_boot.h`, `fvp_userspace.h`, `fvp_boot.c`).

## Interface
- `[fvp_boot.h:fvp_board_initialize]`
- `[fvp_boot.h:CONFIG_SYS_CLOCK_HW_CYCLES_PER_SEC]`
- `[fvp_userspace.h:fvp_userspace]`
- `[fvp_boot.c:arm64_el_init]`
- `[fvp_boot.c:arm64_get_mpid]`
- `[fvp_boot.c:arm64_get_cpuid]`
- `[fvp_boot.c:arm64_chip_boot]`
- `[fvp_boot.c:arm64_mpu_init_regiions]`
- `[fvp_serial.c:arm64_earlyserialinit]`
- `[fvp_serial.c:arm64_serialinit]`
- `[fvp_userspace.c:fvp_userspace]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_FVP_R82]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[fvp_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- None

## Verification
- Run: `make test`
