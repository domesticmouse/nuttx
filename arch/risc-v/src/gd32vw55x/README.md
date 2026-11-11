# gd32vw55x (`nuttx/arch/risc-v/src/gd32vw55x`)

## Overview
Hardware abstraction and architecture package for `gd32vw55x` (GD32VW55x Configuration Options; GD32VW55x Peripheral Support) under `nuttx/arch/risc-v/src/gd32vw55x`, providing 19 header file(s) and 24 source file(s) (including `chip.h`, `gd32vw55x.h`, `gd32vw55x_adc.h`, `gd32vw55x_capture.h`).

## Subdirectories & Boundaries
- `gdble`: [./gdble/README.md](./gdble/README.md) - Hardware abstraction and architecture package for `gdble` under `nuttx/arch/risc-v/src/gd32vw55x/gdble`, providing 0 header file(s) and 1 source file(s) (including `gd32_ble.c`).
- `gdwifi`: [./gdwifi/README.md](./gdwifi/README.md) - Hardware abstraction and architecture package for `gdwifi` under `nuttx/arch/risc-v/src/gd32vw55x/gdwifi`, providing 1 header file(s) and 5 source file(s) (including `gdwifi_netdev.h`, `gdwifi_glue.c`, `gdwifi_netdev.c`, `gdwifi_netif_compat.c`).
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/gd32vw55x/hardware`, providing 17 header file(s) and 0 source file(s) (including `gd32vw55x_adc.h`, `gd32vw55x_crc.h`, `gd32vw55x_dma.h`, `gd32vw55x_eclic.h`).

## Interface
- `[gd32vw55x.h:gd32vw55x_boardinitialize]`
- `[gd32vw55x.h:gd32vw55x_irq_set_trigger]`
- `[gd32vw55x_adc.h:gd32_adc_initialize]`
- `[gd32vw55x_capture.h:gd32_cap_initialize]`
- `[gd32vw55x_clockconfig.h:gd32vw55x_clockconfig]`
- `[gd32vw55x_clockconfig.h:GD32VW55X_HXTAL_FREQ]`
- `[gd32vw55x_clockconfig.h:GD32VW55X_SYSCLK_FREQ]`
- `[gd32vw55x_clockconfig.h:GD32VW55X_AHB_FREQ]`
- `[gd32vw55x_clockconfig.h:GD32VW55X_PCLK2_FREQ]`
- `[gd32vw55x_clockconfig.h:GD32VW55X_PCLK1_FREQ]`
- `[gd32vw55x_clockconfig.h:GD32VW55X_MTIME_FREQ]`
- `[gd32vw55x_config.h:HAVE_UART_DEVICE]`
- `[gd32vw55x_config.h:HAVE_SERIAL_CONSOLE]`
- `[gd32vw55x_crc.h:gd32_crc_initialize]`
- `[gd32vw55x_crc.h:gd32_crc_reset]`
- `[gd32vw55x_crc.h:gd32_crc32_calculate]`
- `[gd32vw55x_crc.h:gd32_crc32_accumulate]`
- `[gd32vw55x_crc.h:gd32_crc_fdata_read]`
- `[gd32vw55x_crc.h:gd32_crc_fdata_write]`
- `[gd32vw55x_dma.h:gd32_dma_channel_alloc]`
- `[gd32vw55x_dma.h:gd32_dma_channel_free]`
- `[gd32vw55x_dma.h:gd32_dma_setup]`
- `[gd32vw55x_dma.h:gd32_dma_start]`
- `[gd32vw55x_dma.h:gd32_dma_stop]`
- `[gd32vw55x_dma.h:gd32_dma_tansnum_get]`
- `[gd32vw55x_dma.h:gd32_dma_sample]`
- `[gd32vw55x_dma.h:gd32_dma_dump]`
- `[gd32vw55x_dma.h:gd32_dma_config_s]`
- `[gd32vw55x_dma.h:gd32_dmaregs_s]`
- `[gd32vw55x_dma.h:DMA_HANDLE]`
- [./gdble/README.md](./gdble/README.md)
- [./gdwifi/README.md](./gdwifi/README.md)
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[gd32vw55x_progmem.h:#error]` Compile-time guard: CONFIG_GD32VW55X_PROGMEM_START_ADDR is not defined
- `[gd32vw55x_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32vw55x_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32vw55x_capture.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32vw55x_capture.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32vw55x_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32vw55x_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32vw55x_exti.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32vw55x_fwdgt.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32vw55x_fwdgt.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32vw55x_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32vw55x_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[gd32vw55x_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[gd32vw55x_adc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[gd32vw55x_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[gd32vw55x_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[gd32vw55x_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[gd32vw55x_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[gd32vw55x_capture.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[gd32vw55x_capture.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[gd32vw55x_capture.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[gd32vw55x_capture.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[gd32vw55x_capture.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[gd32vw55x_capture.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
