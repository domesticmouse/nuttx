# include (`nuttx/arch/avr/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/avr/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `debug.h`, `inttypes.h`, `irq.h`).

## Subdirectories & Boundaries
- `at32uc3`: [./at32uc3/README.md](./at32uc3/README.md) - Hardware abstraction and architecture package for `at32uc3` under `nuttx/arch/avr/include/at32uc3`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).
- `at90usb`: [./at90usb/README.md](./at90usb/README.md) - Hardware abstraction and architecture package for `at90usb` under `nuttx/arch/avr/include/at90usb`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).
- `atmega`: [./atmega/README.md](./atmega/README.md) - Hardware abstraction and architecture package for `atmega` under `nuttx/arch/avr/include/atmega`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).
- `avr`: [./avr/README.md](./avr/README.md) - Hardware abstraction and architecture package for `avr` under `nuttx/arch/avr/include/avr`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `avr.h`, `inttypes.h`, `irq.h`).
- `avr32`: [./avr32/README.md](./avr32/README.md) - Hardware abstraction and architecture package for `avr32` under `nuttx/arch/avr/include/avr32`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `avr32.h`, `inttypes.h`, `irq.h`).
- `avrdx`: [./avrdx/README.md](./avrdx/README.md) - Hardware abstraction and architecture package for `avrdx` under `nuttx/arch/avr/include/avrdx`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).
- `xmega`: [./xmega/README.md](./xmega/README.md) - Hardware abstraction and architecture package for `xmega` under `nuttx/arch/avr/include/xmega`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `xmegac_irq.h`).

## Interface
- `[debug.h:__dbg_first]`
- `[debug.h:__dbg_subst]`
- `[debug.h:__dbg_expand]`
- `[debug.h:__arch_syslog]`
- `[irq.h:STACKFRAME_ALIGN]`
- `[irq.h:up_interrupt_context]`
- `[irq.h:up_getusrsp]`
- `[syscall.h:sys_call6]`
- `[syscall.h:SYS_syscall]`
- [./at32uc3/README.md](./at32uc3/README.md)
- [./at90usb/README.md](./at90usb/README.md)
- [./atmega/README.md](./atmega/README.md)
- [./avr/README.md](./avr/README.md)
- [./avr32/README.md](./avr32/README.md)
- [./avrdx/README.md](./avrdx/README.md)
- [./xmega/README.md](./xmega/README.md)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
