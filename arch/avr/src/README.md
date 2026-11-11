# src (`nuttx/arch/avr/src`)

## Overview
Architectural grouping for `nuttx/arch/avr/src`, coordinating 8 component subdirectories (`at32uc3`, `at90usb`, `atmega`, `avr`, `avr32`, `avrdx`, `common`, `xmega`).

## Subdirectories & Boundaries
- `at32uc3`: [./at32uc3/README.md](./at32uc3/README.md) - Hardware abstraction and architecture package for `at32uc3` (AT32U3 Configuration Options; AT32U3 Peripheral Selections) under `nuttx/arch/avr/src/at32uc3`, providing 27 header file(s) and 8 source file(s) (including `at32uc3.h`, `at32uc3_abdac.h`, `at32uc3_adc.h`, `at32uc3_config.h`).
- `at90usb`: [./at90usb/README.md](./at90usb/README.md) - Hardware abstraction and architecture package for `at90usb` (AT90USB Configuration Options; AT90USB Peripheral Selections) under `nuttx/arch/avr/src/at90usb`, providing 4 header file(s) and 5 source file(s) (including `at90usb.h`, `at90usb_config.h`, `at90usb_memorymap.h`, `chip.h`).
- `atmega`: [./atmega/README.md](./atmega/README.md) - Hardware abstraction and architecture package for `atmega` (ATMega Configuration Options; ATMega Peripheral Selections) under `nuttx/arch/avr/src/atmega`, providing 4 header file(s) and 4 source file(s) (including `atmega.h`, `atmega_config.h`, `atmega_memorymap.h`, `chip.h`).
- `avr`: [./avr/README.md](./avr/README.md) - Hardware abstraction and architecture package for `avr` (AVR Configuration Options) under `nuttx/arch/avr/src/avr`, providing 2 header file(s) and 14 source file(s) (including `avr.h`, `excptmacros.h`, `avr_checkstack.c`, `avr_copystate.c`).
- `avr32`: [./avr32/README.md](./avr32/README.md) - Hardware abstraction and architecture package for `avr32` (AVR32 Configuration Options) under `nuttx/arch/avr/src/avr32`, providing 1 header file(s) and 10 source file(s) (including `avr32.h`, `avr_copystate.c`, `avr_createstack.c`, `avr_doirq.c`).
- `avrdx`: [./avrdx/README.md](./avrdx/README.md) - Hardware abstraction and architecture package for `avrdx` (AVR DA/DB Configuration Options; AVR DA/DB Peripheral Selections) under `nuttx/arch/avr/src/avrdx`, providing 11 header file(s) and 13 source file(s) (including `avrdx.h`, `avrdx_config.h`, `avrdx_delay_loop.h`, `avrdx_gpio.h`).
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/avr/src/common`, providing 1 header file(s) and 11 source file(s) (including `avr_internal.h`, `avr_allocateheap.c`, `avr_exit.c`, `avr_getintstack.c`).
- `xmega`: [./xmega/README.md](./xmega/README.md) - Architectural grouping for `nuttx/arch/avr/src/xmega`, coordinating 1 component subdirectories (`hardware`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./at32uc3/README.md](./at32uc3/README.md)
- [./at90usb/README.md](./at90usb/README.md)
- [./atmega/README.md](./atmega/README.md)
- [./avr/README.md](./avr/README.md)
- [./avr32/README.md](./avr32/README.md)
- [./avrdx/README.md](./avrdx/README.md)
- [./common/README.md](./common/README.md)
- [./xmega/README.md](./xmega/README.md)

## Invariants
- `[at32uc3_pinmux.h:#error]` Compile-time guard: Unknown AVR32 chip
- `[at32uc3_pm.h:#error]` Compile-time guard: Unknown AVR32 chip
- `[chip.h:#error]` Compile-time guard: Unsupported AVR32 chip
- `[at32uc3_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[at32uc3_gpioirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[at32uc3_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[at32uc3_clkinit.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32uc3_clkinit.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[at32uc3_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32uc3_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[at32uc3_gpioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[at32uc3_gpioirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
