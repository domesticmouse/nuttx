# rk3399 (`nuttx/arch/arm64/src/rk3399`)

## Overview
Hardware abstraction and architecture package for `rk3399` (Rockchip RK3399 Peripheral Selection) under `nuttx/arch/arm64/src/rk3399`, providing 3 header file(s) and 2 source file(s) (including `chip.h`, `rk3399_boot.h`, `rk3399_serial.h`, `rk3399_boot.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/rk3399/hardware`, providing 1 header file(s) and 0 source file(s) (including `rk3399_memorymap.h`).

## Interface
- `[rk3399_boot.h:rk3399_board_initialize]`
- `[rk3399_serial.h:RK3399_UART2_ADDR]`
- `[rk3399_serial.h:RK3399_UART0_IRQ]`
- `[rk3399_serial.h:RK3399_UART1_IRQ]`
- `[rk3399_serial.h:RK3399_UART2_IRQ]`
- `[rk3399_serial.h:RK3399_UART3_IRQ]`
- `[rk3399_serial.h:RK3399_UART4_IRQ]`
- `[rk3399_boot.c:arm64_el_init]`
- `[rk3399_boot.c:arm64_chip_boot]`
- `[rk3399_boot.c:arm64_netinitialize]`
- `[rk3399_serial.c:arm64_earlyserialinit]`
- `[rk3399_serial.c:up_putc]`
- `[rk3399_serial.c:arm64_serialinit]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_RK3399_UART]`
- `[Kconfig:CONFIG_RK3399_UART1]`
- `[Kconfig:CONFIG_RK3399_UART2]`
- `[Kconfig:CONFIG_RK3399_UART3]`
- `[Kconfig:CONFIG_RK3399_UART4]`
- `[Make.defs:CHIP_CSRCS]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[rk3399_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[rk3399_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rk3399_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rk3399_serial.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[rk3399_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rk3399_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rk3399_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
