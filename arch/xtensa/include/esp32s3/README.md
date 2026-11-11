# esp32s3 (`nuttx/arch/xtensa/include/esp32s3`)

## Overview
Hardware abstraction and architecture package for `esp32s3` under `nuttx/arch/xtensa/include/esp32s3`, providing 7 header file(s) and 0 source file(s) (including `chip.h`, `core-isa.h`, `irq.h`, `memory_layout.h`).

## Interface
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
- `[irq.h:ESP32S3_INT_PRIO_DEF]`
- `[irq.h:ESP32S3_CPUINT_FLAG_LEVEL]`
- `[irq.h:ESP32S3_CPUINT_FLAG_EDGE]`
- `[irq.h:ESP32S3_CPUINT_FLAG_SHARED]`
- `[irq.h:ESP32S3_CPUINT_FLAG_IRAM]`
- `[irq.h:ESP32S3_PERIPH_MAC]`
- `[irq.h:ESP32S3_PERIPH_MAC_NMI]`
- `[irq.h:ESP32S3_PERIPH_PWR]`
- `[irq.h:ESP32S3_PERIPH_BB]`
- `[irq.h:ESP32S3_PERIPH_BT_MAC]`
- `[irq.h:ESP32S3_PERIPH_BT_BB]`
- `[irq.h:ESP32S3_PERIPH_BT_BB_NMI]`
- `[memory_layout.h:HEAP_REGION1_END]`
- `[memory_layout.h:HEAP_REGION2_START]`
- `[memory_layout.h:XTENSA_IMEM_REGION_SIZE]`
- `[partition.h:ota_img_ctrl_e]`
- `[partition.h:ota_img_bootseq_e]`
- `[tie-asm.h:XTHAL_SAS_TIE]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
