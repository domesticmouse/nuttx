# include (`nuttx/arch/xtensa/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/xtensa/include`, providing 11 header file(s) and 0 source file(s) (including `arch.h`, `elf.h`, `inttypes.h`, `irq.h`).

## Subdirectories & Boundaries
- `esp32`: [./esp32/README.md](./esp32/README.md) - Hardware abstraction and architecture package for `esp32` under `nuttx/arch/xtensa/include/esp32`, providing 9 header file(s) and 0 source file(s) (including `chip.h`, `core-isa.h`, `esp32_himem_chardev.h`, `esp_efuse_table.h`).
- `esp32s2`: [./esp32s2/README.md](./esp32s2/README.md) - Hardware abstraction and architecture package for `esp32s2` under `nuttx/arch/xtensa/include/esp32s2`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `core-isa.h`, `irq.h`, `tie-asm.h`).
- `esp32s3`: [./esp32s3/README.md](./esp32s3/README.md) - Hardware abstraction and architecture package for `esp32s3` under `nuttx/arch/xtensa/include/esp32s3`, providing 7 header file(s) and 0 source file(s) (including `chip.h`, `core-isa.h`, `irq.h`, `memory_layout.h`).
- `lx6`: [./lx6/README.md](./lx6/README.md) - Hardware abstraction and architecture package for `lx6` under `nuttx/arch/xtensa/include/lx6`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).
- `lx7`: [./lx7/README.md](./lx7/README.md) - Hardware abstraction and architecture package for `lx7` under `nuttx/arch/xtensa/include/lx7`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).
- `xtensa`: [./xtensa/README.md](./xtensa/README.md) - Hardware abstraction and architecture package for `xtensa` under `nuttx/arch/xtensa/include/xtensa`, providing 6 header file(s) and 0 source file(s) (including `core.h`, `core_macros.h`, `xtensa_abi.h`, `xtensa_coproc.h`).

## Interface
- `[arch.h:xtensa_imm_initialize]`
- `[arch.h:xtensa_imm_malloc]`
- `[arch.h:xtensa_imm_calloc]`
- `[arch.h:xtensa_imm_realloc]`
- `[arch.h:xtensa_imm_zalloc]`
- `[arch.h:xtensa_imm_free]`
- `[arch.h:xtensa_imm_memalign]`
- `[arch.h:xtensa_imm_heapmember]`
- `[arch.h:xtensa_imm_mallinfo]`
- `[arch.h:arch_addrenv_s]`
- `[arch.h:arch_addrenv_t]`
- `[elf.h:xtensa_elf_greg_t]`
- `[elf.h:elf_gregset_t]`
- `[elf.h:R_XTENSA_NONE]`
- `[elf.h:R_XTENSA_32]`
- `[elf.h:R_XTENSA_ASM_EXPAND]`
- `[elf.h:R_XTENSA_SLOT0_OP]`
- `[elf.h:EM_ARCH]`
- `[elf.h:EF_FLAG]`
- `[elf.h:XTENSA_ELF_NGREG]`
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRId64]`
- `[inttypes.h:PRIdPTR]`
- `[inttypes.h:PRIi8]`
- `[inttypes.h:PRIi16]`
- `[inttypes.h:PRIi32]`
- `[inttypes.h:PRIi64]`
- `[inttypes.h:PRIiPTR]`
- [./esp32/README.md](./esp32/README.md)
- [./esp32s2/README.md](./esp32s2/README.md)
- [./esp32s3/README.md](./esp32s3/README.md)
- [./lx6/README.md](./lx6/README.md)
- [./lx7/README.md](./lx7/README.md)
- [./xtensa/README.md](./xtensa/README.md)

## Invariants
- `[irq.h:#error]` Compile-time guard: Unknown XTENSA architecture
- `[irq.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
