# supervisor (`nuttx/arch/risc-v/src/common/supervisor`)

## Overview
Hardware abstraction and architecture package for `supervisor` under `nuttx/arch/risc-v/src/common/supervisor`, providing 0 header file(s) and 2 source file(s) (including `riscv_perform_syscall.c`, `riscv_sbi.c`).

## Interface
- `[riscv_perform_syscall.c:riscv_perform_syscall]`
- `[riscv_sbi.c:sbi_err_map_errno]`
- `[riscv_sbi.c:riscv_sbi_set_timer]`
- `[riscv_sbi.c:riscv_sbi_get_time]`
- `[riscv_sbi.c:riscv_sbi_send_ipi]`
- `[riscv_sbi.c:riscv_sbi_boot_secondary]`
- `[riscv_sbi.c:riscv_sbi_system_reset]`
- `[CMakeLists.txt:target_sources]`
- `[Make.defs:CMN_CSRCS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
