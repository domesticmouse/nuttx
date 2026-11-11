# avr32 (`nuttx/arch/avr/include/avr32`)

## Overview
Hardware abstraction and architecture package for `avr32` under `nuttx/arch/avr/include/avr32`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `avr32.h`, `inttypes.h`, `irq.h`).

## Interface
- `[avr32.h:AVR32_SR]`
- `[avr32.h:AVR32_EVBA]`
- `[avr32.h:AVR32_ACBA]`
- `[avr32.h:AVR32_CPUCR]`
- `[avr32.h:AVR32_ECR]`
- `[avr32.h:AVR32_RSR_SUP]`
- `[avr32.h:AVR32_RSR_INT0]`
- `[avr32.h:AVR32_RSR_INT1]`
- `[avr32.h:AVR32_RSR_INT2]`
- `[avr32.h:AVR32_RSR_INT3]`
- `[avr32.h:AVR32_RSR_EX]`
- `[avr32.h:AVR32_RSR_NMI]`
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
- `[inttypes.h:PRIo8]`
- `[inttypes.h:PRIo16]`
- `[irq.h:xcptcontext]`
- `[irq.h:REG_R8]`
- `[irq.h:REG_R9]`
- `[irq.h:REG_R10]`
- `[irq.h:REG_R11]`
- `[irq.h:REG_R12]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
