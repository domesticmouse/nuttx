# a64 (`nuttx/arch/arm64/src/a64`)

## Overview
Hardware abstraction and architecture package for `a64` (Allwinner A64 Peripheral Selection) under `nuttx/arch/arm64/src/a64`, providing 12 header file(s) and 10 source file(s) (including `a64_boot.h`, `a64_de.h`, `a64_mipi_dphy.h`, `a64_mipi_dsi.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/a64/hardware`, providing 3 header file(s) and 0 source file(s) (including `a64_memorymap.h`, `a64_pio.h`, `a64_twi.h`).

## Interface
- `[a64_boot.h:a64_board_initialize]`
- `[a64_de.h:a64_de_init]`
- `[a64_de.h:a64_de_blender_init]`
- `[a64_de.h:a64_de_ui_channel_init]`
- `[a64_de.h:a64_de_enable]`
- `[a64_mipi_dphy.h:a64_mipi_dphy_enable]`
- `[a64_mipi_dsi.h:a64_mipi_dsi_enable]`
- `[a64_mipi_dsi.h:a64_mipi_dsi_write]`
- `[a64_mipi_dsi.h:a64_mipi_dsi_start]`
- `[a64_mipi_dsi.h:A64_MIPI_DSI_VIRTUAL_CHANNEL]`
- `[a64_pinmux.h:PIO_TWI0_SCK]`
- `[a64_pinmux.h:PIO_TWI0_SDA]`
- `[a64_pinmux.h:PIO_TWI1_SCK]`
- `[a64_pinmux.h:PIO_TWI1_SDA]`
- `[a64_pinmux.h:PIO_TWI2_SCK]`
- `[a64_pinmux.h:PIO_TWI2_SDA]`
- `[a64_pio.h:a64_pio_config]`
- `[a64_pio.h:a64_pio_write]`
- `[a64_pio.h:a64_pio_read]`
- `[a64_pio.h:a64_pio_irqenable]`
- `[a64_pio.h:a64_pio_irqdisable]`
- `[a64_pio.h:pio_pinset_t]`
- `[a64_pio.h:PIO_MODE_SHIFT]`
- `[a64_pio.h:PIO_MODE_MASK]`
- `[a64_pio.h:PIO_PERIPH0]`
- `[a64_pio.h:PIO_PERIPH1]`
- `[a64_pio.h:PIO_PERIPH2]`
- `[a64_pio.h:PIO_PERIPH3]`
- `[a64_pio.h:PIO_PERIPH4]`
- `[a64_pio.h:PIO_PERIPH5]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[a64_de.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_mipi_dsi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_pio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_pio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[a64_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[a64_twi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_twi.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[a64_twi.c:#error]` Compile-time configuration constraint: I2C slave logic is not supported yet for A64
- `[mipi_dsi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[a64_de.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_de.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a64_mipi_dphy.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_mipi_dsi.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_mipi_dsi.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a64_pio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_pio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a64_rsb.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_rsb.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a64_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a64_serial.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
