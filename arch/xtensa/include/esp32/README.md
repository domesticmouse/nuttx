# esp32 (`nuttx/arch/xtensa/include/esp32`)

## Overview
Hardware abstraction and architecture package for `esp32` under `nuttx/arch/xtensa/include/esp32`, providing 9 header file(s) and 0 source file(s) (including `chip.h`, `core-isa.h`, `esp32_himem_chardev.h`, `esp_efuse_table.h`).

## Interface
- `[chip.h:ESP32_NSPI]`
- `[chip.h:ESP32_NUARTS]`
- `[chip.h:ESP32_NGPIOS]`
- `[core-isa.h:XCHAL_HAVE_BE]`
- `[core-isa.h:XCHAL_HAVE_WINDOWED]`
- `[core-isa.h:XCHAL_NUM_AREGS]`
- `[core-isa.h:XCHAL_NUM_AREGS_LOG2]`
- `[core-isa.h:XCHAL_MAX_INSTRUCTION_SIZE]`
- `[core-isa.h:XCHAL_HAVE_DEBUG]`
- `[core-isa.h:XCHAL_HAVE_DENSITY]`
- `[core-isa.h:XCHAL_HAVE_LOOPS]`
- `[core-isa.h:XCHAL_LOOP_BUFFER_SIZE]`
- `[core-isa.h:XCHAL_HAVE_NSA]`
- `[core-isa.h:XCHAL_HAVE_MINMAX]`
- `[core-isa.h:XCHAL_HAVE_SEXT]`
- `[esp32_himem_chardev.h:himem_chardev_init]`
- `[esp32_himem_chardev.h:himem_chardev_exit]`
- `[esp32_himem_chardev.h:himem_chardev_register]`
- `[esp32_himem_chardev.h:himem_chardev_unregister]`
- `[irq.h:ESP32_CPUINT_FLAG_LEVEL]`
- `[irq.h:ESP32_CPUINT_FLAG_EDGE]`
- `[irq.h:ESP32_CPUINT_FLAG_SHARED]`
- `[irq.h:ESP32_CPUINT_FLAG_IRAM]`
- `[irq.h:ESP32_CPUINT_TRIGGER_MASK]`
- `[irq.h:ESP32_PERIPH_MAC]`
- `[irq.h:ESP32_PERIPH_MAC_NMI]`
- `[irq.h:ESP32_PERIPH_BB]`
- `[irq.h:ESP32_PERIPH_BB_MAC]`
- `[irq.h:ESP32_PERIPH_BT_BB]`
- `[irq.h:ESP32_PERIPH_BT_BB_NMI]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
