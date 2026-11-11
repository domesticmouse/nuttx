# ameba (`nuttx/arch/arm/src/common/ameba`)

## Overview
Hardware abstraction and architecture package for `ameba` (Ameba Peripheral Support) under `nuttx/arch/arm/src/common/ameba`, providing 12 header file(s) and 13 source file(s) (including `ameba_adc.h`, `ameba_flash_mtd.h`, `ameba_gpio.h`, `ameba_i2c.h`).

## Subdirectories & Boundaries
- `sdk_shim`: [./sdk_shim/README.md](./sdk_shim/README.md) - Hardware abstraction and architecture package for `sdk_shim` under `nuttx/arch/arm/src/common/ameba/sdk_shim`, providing 1 header file(s) and 0 source file(s) (including `os_wrapper_specific.h`).
- `tools`: [./tools/README.md](./tools/README.md) - Hardware abstraction and architecture package for `tools` under `nuttx/arch/arm/src/common/ameba/tools`, providing 0 header file(s) and 11 source file(s) (including `ameba_asdk_version.sh`, `ameba_build_np.sh`, `ameba_fetch_sdk.sh`, `ameba_fetch_toolchain.sh`).
- `wifi`: [./wifi/README.md](./wifi/README.md) - Hardware abstraction and architecture package for `wifi` under `nuttx/arch/arm/src/common/ameba/wifi`, providing 0 header file(s) and 2 source file(s) (including `ameba_wifi.c`, `ameba_wifi_depend.c`).

## Interface
- `[ameba_adc.h:ameba_adc_register]`
- `[ameba_adc.h:AMEBA_ADC_PIN_NC]`
- `[ameba_flash_mtd.h:ameba_flash_mtd_initialize]`
- `[ameba_flash_mtd.h:ameba_flash_fs_initialize]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_SECTOR_SIZE]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_PAGE_SIZE]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_VFS1_OFFSET_XIP]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_VFS1_SIZE_CFG]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_XIP_BASE]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_VFS1_OFFSET]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_VFS1_SIZE]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_FS_DEVPATH]`
- `[ameba_flash_mtd.h:AMEBA_FLASH_FS_MOUNTPT]`
- `[ameba_flash_mtd.h:AMEBA_KV_DIR]`
- `[ameba_gpio.h:ameba_gpio_register]`
- `[ameba_gpio.h:AMEBA_PORT_A]`
- `[ameba_gpio.h:AMEBA_PORT_B]`
- `[ameba_gpio.h:AMEBA_PIN]`
- `[ameba_gpio.h:AMEBA_PORT_C]`
- `[ameba_gpio.h:AMEBA_PA]`
- `[ameba_gpio.h:AMEBA_PB]`
- `[ameba_gpio.h:AMEBA_PC]`
- `[ameba_i2c.h:ameba_i2c_register]`
- `[ameba_i2c.h:AMEBA_I2C0]`
- `[ameba_i2c.h:AMEBA_I2C1]`
- `[ameba_i2c.h:AMEBA_I2C2]`
- `[ameba_os_wrap.h:ameba_qobj_alloc]`
- `[ameba_os_wrap.h:ameba_qobj_free]`
- `[ameba_os_wrap.h:ameba_qobj_take]`
- `[ameba_os_wrap.h:ameba_qobj_give]`
- [./sdk_shim/README.md](./sdk_shim/README.md)
- [./tools/README.md](./tools/README.md)
- [./wifi/README.md](./wifi/README.md)

## Invariants
- `[ameba_adc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[ameba_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ameba_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ameba_os_wrap.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ameba_rtc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ameba_timer.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ameba_uart.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ameba_wdg.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ameba_wlan.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[ameba_gpio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_gpio.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ameba_rtc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_rtc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ameba_timer.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_timer.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ameba_timer.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[ameba_uart.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_uart.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ameba_uart.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[ameba_wdg.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_wdg.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
