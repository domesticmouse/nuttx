# espressif (`nuttx/arch/xtensa/src/common/espressif`)

## Overview
Hardware abstraction and architecture package for `espressif` (Espressif Log Level; Interrupt Configuration) under `nuttx/arch/xtensa/src/common/espressif`, providing 34 header file(s) and 38 source file(s) (including `esp_adc.h`, `esp_aes.h`, `esp_dedic_gpio.h`, `esp_efuse.h`).

## Subdirectories & Boundaries
- `platform_include`: [./platform_include/README.md](./platform_include/README.md) - Hardware abstraction and architecture package for `platform_include` under `nuttx/arch/xtensa/src/common/espressif/platform_include`, providing 1 header file(s) and 0 source file(s) (including `stdatomic.h`).
- `utils`: [./utils/README.md](./utils/README.md) - Hardware abstraction and architecture package for `utils` under `nuttx/arch/xtensa/src/common/espressif/utils`, providing 1 header file(s) and 0 source file(s) (including `memory_reserve.h`).

## Interface
- `[esp_adc.h:esp_adc_initialize]`
- `[esp_adc.h:ESP_ADC_MAX_CHANNELS]`
- `[esp_aes.h:esp_aes_ecb_cypher]`
- `[esp_aes.h:esp_aes_cbc_cypher]`
- `[esp_aes.h:esp_aes_ctr_cypher]`
- `[esp_aes.h:esp_aes_xts_cypher]`
- `[esp_aes.h:esp_aes_setkey]`
- `[esp_aes.h:esp_aes_xts_setkey]`
- `[esp_aes.h:esp_aes_init]`
- `[esp_aes.h:esp_aes_test]`
- `[esp_aes.h:esp_aes_s]`
- `[esp_aes.h:esp_aes_xts_s]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_set_cb]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_write]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_read]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_new_bundle]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_del_bundle]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_flags_s]`
- `[esp_dedic_gpio.h:esp_dedic_gpio_config_s]`
- `[esp_efuse.h:esp_efuse_hal_chip_revision]`
- `[esp_efuse.h:esp_efuse_initialize]`
- `[esp_efuse.h:esp_efuse_blk_num_t]`
- `[esp_efuse.h:ESP_EFUSE_BLK_LEN]`
- `[esp_espnow_pktradio.h:pktradio_espnow]`
- `[esp_gpio.h:esp_configgpio]`
- `[esp_gpio.h:esp_getconfiggpio]`
- `[esp_gpio.h:esp_gpio_matrix_in]`
- `[esp_gpio.h:esp_gpio_matrix_out]`
- `[esp_gpio.h:esp_gpiowrite]`
- `[esp_gpio.h:esp_gpioread]`
- [./platform_include/README.md](./platform_include/README.md)
- [./utils/README.md](./utils/README.md)

## Invariants
- `[esp_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_adc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp_adc.c:#error]` Compile-time configuration constraint: Continuous mode not implemented
- `[esp_aes.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_crypto.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_dedic_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_dedic_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp_efuse.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_efuse.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp_espnow_pktradio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_espnow_pktradio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp_espnow_pktradio.c:#error]` Compile-time configuration constraint: Worker thread support is required (CONFIG_SCHED_WORKQUEUE)

## Side Effects
- `[esp_dedic_gpio.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_dedic_gpio.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp_efuse.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp_i2c_slave.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_i2c_slave.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp_i2s.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp_i2s.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp_i2s.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp_i2s.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_i2s.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp_i2s.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[esp_i2s.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)

## Verification
- Run: `make test`
