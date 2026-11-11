# imx6 (`nuttx/arch/arm/src/imx6`)

## Overview
Hardware abstraction and architecture package for `imx6` (iMX.6 Chip Selection; iMX.6 Peripheral Selection) under `nuttx/arch/arm/src/imx6`, providing 11 header file(s) and 14 source file(s) (including `chip.h`, `imx_boot.h`, `imx_clockconfig.h`, `imx_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/imx6/hardware`, providing 10 header file(s) and 0 source file(s) (including `imx_ccm.h`, `imx_ecspi.h`, `imx_enet.h`, `imx_gpio.h`).

## Interface
- `[chip.h:CHIP_MPCORE_VBASE]`
- `[chip.h:L2CC_VBASE]`
- `[imx_boot.h:imx_cpu_disable]`
- `[imx_boot.h:imx_cpu_enable]`
- `[imx_boot.h:imx_memory_initialize]`
- `[imx_boot.h:imx_board_initialize]`
- `[imx_clockconfig.h:imx_clockconfig]`
- `[imx_config.h:IMX_HAVE_UART]`
- `[imx_config.h:SUPPRESS_CONSOLE_CONFIG]`
- `[imx_config.h:IMX_HAVE_UART_CONSOLE]`
- `[imx_ecspi.h:imx_spibus_initialize]`
- `[imx_ecspi.h:imx_spi1select]`
- `[imx_ecspi.h:imx_spi1status]`
- `[imx_ecspi.h:imx_spi1cmddata]`
- `[imx_ecspi.h:imx_spi2select]`
- `[imx_ecspi.h:imx_spi2status]`
- `[imx_ecspi.h:imx_spi2cmddata]`
- `[imx_ecspi.h:imx_spi3select]`
- `[imx_ecspi.h:imx_spi3status]`
- `[imx_ecspi.h:imx_spi3cmddata]`
- `[imx_ecspi.h:imx_spi4select]`
- `[imx_ecspi.h:imx_spi4status]`
- `[imx_ecspi.h:imx_spi4cmddata]`
- `[imx_ecspi.h:imx_spi5select]`
- `[imx_ecspi.h:imx_spi5status]`
- `[imx_ecspi.h:imx_spi5cmddata]`
- `[imx_enet.h:imx_phy_boardinitialize]`
- `[imx_enet.h:EMAC_INTF]`
- `[imx_gpio.h:imx_gpioirq_initialize]`
- `[imx_gpio.h:imx_config_gpio]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[imx_memorymap.h:#error]` Compile-time guard: High vector remap cannot be performed if we are using a ROM page table
- `[imx_boot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_ecspi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_ecspi.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[imx_enet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_enet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[imx_enet.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[imx_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[imx_iomuxc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_lowputc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[imx_boot.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[imx_cpuboot.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx_cpuboot.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx_ecspi.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx_ecspi.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx_ecspi.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[imx_ecspi.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[imx_enet.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx_enet.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[imx_enet.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx_enet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[imx_enet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
