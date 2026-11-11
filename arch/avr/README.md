# avr (`nuttx/arch/avr`)

## Overview
Architectural grouping for `nuttx/arch/avr`, coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/avr/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `debug.h`, `inttypes.h`, `irq.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/avr/src`, coordinating 8 component subdirectories (`at32uc3`, `at90usb`, `atmega`, `avr`, `avr32`, `avrdx`, `common`, `xmega`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_ATMEGA]`
- `[Kconfig:CONFIG_ARCH_CHIP_AT90USB]`
- `[Kconfig:CONFIG_ARCH_CHIP_AVRDX]`
- `[Kconfig:CONFIG_ARCH_CHIP_AT32UC3]`
- `[Kconfig:CONFIG_ARCH_CHIP_AVR_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_FAMILY_AVR]`
- `[Kconfig:CONFIG_ARCH_FAMILY_AVR32]`
- `[Kconfig:CONFIG_ARCH_FAMILY]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

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
