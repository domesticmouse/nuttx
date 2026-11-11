# gd32w51x (`nuttx/arch/arm/src/gd32w51x`)

## Overview
Hardware abstraction and architecture package for `gd32w51x` (GD32W51x Configuration Options; GD32W51x Peripheral Support) under `nuttx/arch/arm/src/gd32w51x`, providing 21 header file(s) and 25 source file(s) (including `chip.h`, `gd32w51x.h`, `gd32w51x_adc.h`, `gd32w51x_capture.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/gd32w51x/hardware`, providing 18 header file(s) and 0 source file(s) (including `gd32w51x_adc.h`, `gd32w51x_crc.h`, `gd32w51x_dma.h`, `gd32w51x_exti.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[gd32w51x.h:gd32w51x_boardinitialize]`
- `[gd32w51x.h:gd32w51x_tzinit]`
- `[gd32w51x.h:gd32w51x_gpio_setsecure]`
- `[gd32w51x.h:gd32w51x_icache_enable]`
- `[gd32w51x_adc.h:gd32_adc_initialize]`
- `[gd32w51x_capture.h:gd32_cap_initialize]`
- `[gd32w51x_clockconfig.h:gd32w51x_clockconfig]`
- `[gd32w51x_clockconfig.h:GD32W51X_HXTAL_FREQ]`
- `[gd32w51x_clockconfig.h:GD32W51X_SYSCLK_FREQ]`
- `[gd32w51x_clockconfig.h:GD32W51X_AHB_FREQ]`
- `[gd32w51x_clockconfig.h:GD32W51X_PCLK2_FREQ]`
- `[gd32w51x_clockconfig.h:GD32W51X_PCLK1_FREQ]`
- `[gd32w51x_config.h:HAVE_UART_DEVICE]`
- `[gd32w51x_config.h:HAVE_SERIAL_CONSOLE]`
- `[gd32w51x_crc.h:gd32_crc_initialize]`
- `[gd32w51x_crc.h:gd32_crc_reset]`
- `[gd32w51x_crc.h:gd32_crc32_calculate]`
- `[gd32w51x_crc.h:gd32_crc32_accumulate]`
- `[gd32w51x_crc.h:gd32_crc_fdata_read]`
- `[gd32w51x_crc.h:gd32_crc_fdata_write]`
- `[gd32w51x_dma.h:gd32_dma_channel_alloc]`
- `[gd32w51x_dma.h:gd32_dma_channel_free]`
- `[gd32w51x_dma.h:gd32_dma_setup]`
- `[gd32w51x_dma.h:gd32_dma_start]`
- `[gd32w51x_dma.h:gd32_dma_stop]`
- `[gd32w51x_dma.h:gd32_dma_tansnum_get]`
- `[gd32w51x_dma.h:gd32_dma_sample]`
- `[gd32w51x_dma.h:gd32_dma_dump]`
- `[gd32w51x_dma.h:gd32_dma_config_s]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[gd32w51x_progmem.h:#error]` Compile-time guard: CONFIG_GD32W51X_PROGMEM_START_ADDR is not defined
- `[gd32w51x_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32w51x_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32w51x_capture.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32w51x_capture.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32w51x_clockconfig.c:#error]` Compile-time configuration constraint: BOARD_HXTAL_FREQUENCY must be a whole number of MHz, 2..63 MHz
- `[gd32w51x_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32w51x_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32w51x_exti.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32w51x_fwdgt.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32w51x_fwdgt.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32w51x_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[gd32w51x_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[gd32w51x_adc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[gd32w51x_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[gd32w51x_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[gd32w51x_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[gd32w51x_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[gd32w51x_capture.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[gd32w51x_capture.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[gd32w51x_capture.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[gd32w51x_capture.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[gd32w51x_capture.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[gd32w51x_capture.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
