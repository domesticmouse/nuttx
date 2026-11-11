# imx8 (`nuttx/arch/arm64/src/imx8`)

## Overview
Hardware abstraction and architecture package for `imx8` (i.MX8 Chip Selection; i.MX8 Peripheral Selection) under `nuttx/arch/arm64/src/imx8`, providing 3 header file(s) and 2 source file(s) (including `chip.h`, `imx8_boot.h`, `imx8_serial.h`, `imx8_boot.c`).

## Interface
- `[imx8_boot.h:imx8_board_initialize]`
- `[imx8_boot.h:CONFIG_SYS_CLOCK_HW_CYCLES_PER_SEC]`
- `[imx8_serial.h:imx8_earlyserialinit]`
- `[imx8_serial.h:uart_earlyserialinit]`
- `[imx8_serial.h:uart_serialinit]`
- `[imx8_serial.h:SPI_OFFSET]`
- `[imx8_serial.h:CONFIG_IMX8QM_UART1_BASE]`
- `[imx8_serial.h:CONFIG_IMX8QM_UART1_IRQ]`
- `[imx8_boot.c:arm64_el_init]`
- `[imx8_boot.c:arm64_chip_boot]`
- `[imx8qm_serial.c:board_timerhook]`
- `[imx8qm_serial.c:arm64_earlyserialinit]`
- `[imx8qm_serial.c:up_putc]`
- `[imx8qm_serial.c:arm64_serialinit]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_IMX8_QUADMAX]`
- `[Kconfig:CONFIG_IMX8_UART1]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[imx8qm_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx8qm_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[imx8qm_serial.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[imx8qm_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx8qm_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx8qm_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[imx8qm_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[imx8qm_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
