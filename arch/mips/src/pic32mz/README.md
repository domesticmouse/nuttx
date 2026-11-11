# pic32mz (`nuttx/arch/mips/src/pic32mz`)

## Overview
Hardware abstraction and architecture package for `pic32mz` (PIC32MZ Configuration Options; PIC32MZ Peripheral Support) under `nuttx/arch/mips/src/pic32mz`, providing 16 header file(s) and 24 source file(s) (including `pic32mz_ba414e.h`, `pic32mz_config.h`, `pic32mz_dma.h`, `pic32mz_excptmacros.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/mips/src/pic32mz/hardware`, providing 25 header file(s) and 0 source file(s) (including `pic32mz_dma.h`, `pic32mz_ethernet.h`, `pic32mz_features.h`, `pic32mz_i2c.h`).

## Interface
- `[pic32mz_ba414e.h:pic32mz_ba414e_initialize]`
- `[pic32mz_ba414e.h:pic32mz_ba414e_modadd]`
- `[pic32mz_ba414e.h:pic32mz_ba414e_modsub]`
- `[pic32mz_ba414e.h:pic32mz_ba414e_modmul]`
- `[pic32mz_ba414e.h:pic32mz_ba414e_modexp]`
- `[pic32mz_ba414e.h:pic32mz_ba414e_ecc_add]`
- `[pic32mz_ba414e.h:pic32mz_ba414e_ecc_mul]`
- `[pic32mz_ba414e.h:pic32mz_ba414e_ecc_check]`
- `[pic32mz_ba414e.h:ba414e_curve_s]`
- `[pic32mz_ba414e.h:BA414E_MAX_BYTES]`
- `[pic32mz_ba414e.h:BA414E_OK]`
- `[pic32mz_ba414e.h:BA414E_POINT_AT_INF]`
- `[pic32mz_ba414e.h:BA414E_NOT_ON_CURVE]`
- `[pic32mz_config.h:PIC32MZ_DCACHE_LINESIZE]`
- `[pic32mz_config.h:PIC32MZ_ICACHE_LINESIZE]`
- `[pic32mz_config.h:HAVE_UART_DEVICE]`
- `[pic32mz_config.h:HAVE_SERIAL_CONSOLE]`
- `[pic32mz_config.h:CONFIG_PIC32MZ_SPI]`
- `[pic32mz_config.h:CONFIG_PIC32MZ_I2C]`
- `[pic32mz_config.h:CONFIG_PIC32MZ_USERID]`
- `[pic32mz_dma.h:pic32mz_dma_alloc]`
- `[pic32mz_dma.h:pic32mz_dma_free]`
- `[pic32mz_dma.h:pic32mz_dma_chcfg]`
- `[pic32mz_dma.h:pic32mz_dma_xfrsetup]`
- `[pic32mz_dma.h:pic32mz_dma_start]`
- `[pic32mz_dma.h:pic32mz_dma_stop]`
- `[pic32mz_dma.h:pic32mz_dma_sample]`
- `[pic32mz_dma.h:pic32mz_dma_dump]`
- `[pic32mz_dma.h:pic32mz_dma_chmode_e]`
- `[pic32mz_dma.h:pic32mz_dma_event_e]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[pic32mz_config.h:#error]` Compile-time guard: Unsupported BOARD_PLL_IDIV
- `[pic32mz_decodeirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mz_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mz_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[pic32mz_ethernet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mz_ethernet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[pic32mz_ethernet.c:#error]` Compile-time configuration constraint: Work queue support is required in this configuration (CONFIG_SCHED_WORKQUEUE)
- `[pic32mz_freerun.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mz_freerun.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[pic32mz_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[pic32mz_gpioirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mz_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[pic32mz_ba414e.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[pic32mz_ba414e.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[pic32mz_ba414e.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[pic32mz_ba414e.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[pic32mz_ba414e.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[pic32mz_ba414e.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[pic32mz_decodeirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[pic32mz_dma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[pic32mz_dma.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[pic32mz_dma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[pic32mz_dma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[pic32mz_dma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
