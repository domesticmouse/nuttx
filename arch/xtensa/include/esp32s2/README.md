# esp32s2 (`nuttx/arch/xtensa/include/esp32s2`)

## Overview
Hardware abstraction and architecture package for `esp32s2` under `nuttx/arch/xtensa/include/esp32s2`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `core-isa.h`, `irq.h`, `tie-asm.h`).

## Interface
- `[chip.h:ESP32S2_NDAC]`
- `[chip.h:ESP32S2_NI2C]`
- `[chip.h:ESP32S2_NI2S]`
- `[chip.h:ESP32S2_NLCD]`
- `[chip.h:ESP32S2_NSPI]`
- `[chip.h:ESP32S2_NUARTS]`
- `[chip.h:ESP32S2_NUSBOTG]`
- `[chip.h:ESP32S2_NGPIOS]`
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
- `[irq.h:ESP32S2_INT_PRIO_DEF]`
- `[irq.h:ESP32S2_CPUINT_FLAG_LEVEL]`
- `[irq.h:ESP32S2_CPUINT_FLAG_EDGE]`
- `[irq.h:ESP32S2_CPUINT_FLAG_SHARED]`
- `[irq.h:ESP32S2_CPUINT_FLAG_IRAM]`
- `[irq.h:ESP32S2_PERIPH_MAC]`
- `[irq.h:ESP32S2_PERIPH_MAC_NMI]`
- `[irq.h:ESP32S2_PERIPH_PWR]`
- `[irq.h:ESP32S2_PERIPH_UHCI0]`
- `[irq.h:ESP32S2_PERIPH_TG_T0_LEVEL]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
