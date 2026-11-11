# xmc4 (`nuttx/arch/arm/src/xmc4`)

## Overview
Hardware abstraction and architecture package for `xmc4` (XMC4xxx Configuration Options; XMC4xxx Peripheral Support) under `nuttx/arch/arm/src/xmc4`, providing 17 header file(s) and 22 source file(s) (including `chip.h`, `xmc4_ccu4.h`, `xmc4_clockconfig.h`, `xmc4_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/xmc4/hardware`, providing 12 header file(s) and 0 source file(s) (including `xmc4_ccu4.h`, `xmc4_eru.h`, `xmc4_eru_pinmap.h`, `xmc4_ethernet.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[xmc4_ccu4.h:xmc4_ccu4_divisor]`
- `[xmc4_clockconfig.h:xmc4_clock_configure]`
- `[xmc4_clockconfig.h:xmc4_get_coreclock]`
- `[xmc4_clockconfig.h:xmc4_get_periphclock]`
- `[xmc4_clockconfig.h:xmc4_get_ccuclock]`
- `[xmc4_clockconfig.h:OFI_FREQUENCY]`
- `[xmc4_clockconfig.h:OSI_FREQUENCY]`
- `[xmc4_config.h:HAVE_UART0]`
- `[xmc4_config.h:HAVE_UART1]`
- `[xmc4_config.h:HAVE_UART2]`
- `[xmc4_config.h:HAVE_UART3]`
- `[xmc4_config.h:HAVE_UART4]`
- `[xmc4_config.h:HAVE_UART5]`
- `[xmc4_config.h:HAVE_UART_DEVICE]`
- `[xmc4_config.h:HAVE_UART_CONSOLE]`
- `[xmc4_dma.h:xmc4_dmainitilaize]`
- `[xmc4_dma.h:xmc4_dmachannel]`
- `[xmc4_dma.h:xmc4_dmafree]`
- `[xmc4_dma.h:xmc4_dmarxsetup]`
- `[xmc4_dma.h:xmc4_dmastart]`
- `[xmc4_dma.h:xmc4_dmastop]`
- `[xmc4_dma.h:xmc4_dmasample]`
- `[xmc4_dma.h:xmc4_dmadump]`
- `[xmc4_dma.h:xmc4_dmaglobalregs_s]`
- `[xmc4_dma.h:xmc4_dmachanregs_s]`
- `[xmc4_dma.h:xmc4_dmaregs_s]`
- `[xmc4_dma.h:DMA_HANDLE]`
- `[xmc4_ecat.h:xmc4_ecat_initialize]`
- `[xmc4_ecat.h:xmc4_ecat_initialize_port_control]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[xmc4_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xmc4_ecat.c:#error]` Compile-time configuration constraint: EtherCAT : Unknown MDIO configuration
- `[xmc4_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[xmc4_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[xmc4_i2c.c:#error]` Compile-time configuration constraint: not implemented
- `[xmc4_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xmc4_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[xmc4_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[xmc4_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[xmc4_lowputc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xmc4_lowputc.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting
- `[xmc4_mpuinit.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[xmc4_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[xmc4_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[xmc4_clockconfig.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xmc4_clockutils.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[xmc4_clrpend.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[xmc4_ecat.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[xmc4_ecat.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[xmc4_flash.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[xmc4_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[xmc4_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[xmc4_i2c.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[xmc4_i2c.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
