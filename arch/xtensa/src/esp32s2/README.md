# esp32s2 (`nuttx/arch/xtensa/src/esp32s2`)

## Overview
Hardware abstraction and architecture package for `esp32s2` (ESP32-S2 Configuration Options; Cache Configuration) under `nuttx/arch/xtensa/src/esp32s2`, providing 24 header file(s) and 32 source file(s) (including `chip.h`, `chip_macros.h`, `chip_memory.h`, `esp32s2_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/xtensa/src/esp32s2/hardware`, providing 29 header file(s) and 0 source file(s) (including `esp32s2_aes.h`, `esp32s2_cache_memory.h`, `esp32s2_dma.h`, `esp32s2_gpio.h`).
- `rom`: [./rom/README.md](./rom/README.md) - Hardware abstraction and architecture package for `rom` under `nuttx/arch/xtensa/src/esp32s2/rom`, providing 3 header file(s) and 0 source file(s) (including `esp32s2_libc_stubs.h`, `esp32s2_opi_flash.h`, `esp32s2_spiflash.h`).

## Interface
- `[chip_macros.h:HANDLER_SECTION]`
- `[chip_memory.h:XTENSA_INSTUCTION_REGION]`
- `[esp32s2_config.h:HAVE_UART_DEVICE]`
- `[esp32s2_config.h:HAVE_RS485]`
- `[esp32s2_config.h:HAVE_SERIAL_CONSOLE]`
- `[esp32s2_dma.h:esp32s2_dma_init]`
- `[esp32s2_dma.h:esp32s2_dma_init_with_padding]`
- `[esp32s2_dma.h:esp32s2_dmadesc_s]`
- `[esp32s2_dma.h:ESP32S2_DMA_DATALEN_MAX]`
- `[esp32s2_dma.h:ESP32S2_DMA_BUFLEN_MAX]`
- `[esp32s2_freerun.h:esp32s2_freerun_initialize]`
- `[esp32s2_freerun.h:esp32s2_freerun_counter]`
- `[esp32s2_freerun.h:esp32s2_freerun_uninitialize]`
- `[esp32s2_freerun.h:esp32s2_freerun_s]`
- `[esp32s2_i2c.h:esp32s2_i2cbus_initialize]`
- `[esp32s2_i2c.h:esp32s2_i2cbus_uninitialize]`
- `[esp32s2_i2c.h:ESP32S2_I2C0]`
- `[esp32s2_i2c.h:ESP32S2_I2C1]`
- `[esp32s2_i2c.h:ESP32S2_RTC_I2C]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_set_iflow]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_set_oflow]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_enable_sysclk]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_enable_memclk]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_disable_sysclk]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_disable_memclk]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_set_sclk]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_get_sclk]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_baud]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_normal_mode]`
- `[esp32s2_lowputc.h:esp32s2_lowputc_parity]`
- [./hardware/README.md](./hardware/README.md)
- [./rom/README.md](./rom/README.md)

## Invariants
- `[esp32s2_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s2_freerun.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s2_freerun.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32s2_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s2_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32s2_i2s.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s2_i2s.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32s2_idle.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp32s2_lowputc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp32s2_oneshot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s2_oneshot_lowerhalf.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s2_oneshot_lowerhalf.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[esp32s2_touch_lowerhalf.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[esp32s2_touch_lowerhalf.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[esp32s2_i2c.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32s2_i2c.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp32s2_i2c.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32s2_i2c.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp32s2_i2c.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp32s2_i2s.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32s2_i2s.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp32s2_i2s.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32s2_i2s.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp32s2_i2s.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
