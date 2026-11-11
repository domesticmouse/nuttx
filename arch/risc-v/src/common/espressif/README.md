# espressif (`nuttx/arch/risc-v/src/common/espressif`)

## Overview
Hardware abstraction and architecture package for `espressif` (Espressif DFS Options; Espressif Log Level) under `nuttx/arch/risc-v/src/common/espressif`, providing 54 header file(s) and 61 source file(s) (including `chip.h`, `esp_adc.h`, `esp_aes.h`, `esp_ana_cmpr.h`).

## Subdirectories & Boundaries
- `platform_include`: [./platform_include/README.md](./platform_include/README.md) - Hardware abstraction and architecture package for `platform_include` under `nuttx/arch/risc-v/src/common/espressif/platform_include`, providing 1 header file(s) and 0 source file(s) (including `stdatomic.h`).

## Interface
- `[chip.h:EXCEPTION_SECTION]`
- `[esp_adc.h:esp_adc_initialize]`
- `[esp_adc.h:ESP_ADC_MAX_CHANNELS]`
- `[esp_aes.h:esp_aes_ecb_cypher]`
- `[esp_aes.h:esp_aes_cbc_cypher]`
- `[esp_aes.h:esp_aes_ctr_cypher]`
- `[esp_aes.h:esp_aes_xts_cypher]`
- `[esp_aes.h:esp_aes_setkey]`
- `[esp_aes.h:esp_aes_xts_setkey]`
- `[esp_aes.h:esp_aes_init]`
- `[esp_aes.h:esp_aes_s]`
- `[esp_aes.h:esp_aes_xts_s]`
- `[esp_ana_cmpr.h:esp_cmprinitialize]`
- `[esp_ana_cmpr.h:ESPRESSIF_COMP0]`
- `[esp_ana_cmpr.h:ESPRESSIF_COMP1]`
- `[esp_config.h:HAVE_UART_DEVICE]`
- `[esp_config.h:HAVE_RS485]`
- `[esp_config.h:HAVE_SERIAL_CONSOLE]`
- `[esp_config.h:CONSOLE_UART]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_write]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_read]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_new_bundle]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_del_bundle]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_flags_s]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_config_s]`
- `[esp_efuse.h:esp_efuse_initialize]`
- `[esp_efuse.h:ESP_EFUSE_BLK_LEN]`
- `[esp_emac.h:esp_emac_init]`
- `[esp_gpio.h:esp_configgpio]`
- `[esp_gpio.h:esp_gpio_matrix_in]`
- [./platform_include/README.md](./platform_include/README.md)

## Invariants
- `[esp_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_adc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp_adc.c:#error]` Compile-time configuration constraint: Continuous mode not implemented
- `[esp_aes.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_ana_cmpr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_crypto.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_dedic_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_dedic_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp_efuse.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_efuse.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp_emac.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[esp_gptimer.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_i2c.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_i2c.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp_i2c_slave.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_i2c_slave.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[esp_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[esp_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp_mcpwm.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_mipi_dsi.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_oneshot.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
