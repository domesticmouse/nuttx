# esp32c2 (`nuttx/arch/risc-v/src/esp32c2`)

## Overview
Hardware abstraction and architecture package for `esp32c2` under `nuttx/arch/risc-v/src/esp32c2`, providing 2 header file(s) and 4 source file(s) (including `esp_ble.h`, `esp_coex_adapter.h`, `esp_ble.c`, `esp_chip_rev.c`).

## Interface
- `[esp_ble.h:esp_ble_initialize]`
- `[esp_coex_adapter.h:esp_coex_common_env_is_chip_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_spin_lock_create_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_int_disable_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_int_restore_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_task_yield_from_isr_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_semphr_create_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_semphr_delete_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_semphr_take_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_semphr_give_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_timer_disarm_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_timer_done_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_timer_setfn_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_timer_arm_us_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_malloc_internal_wrapper]`
- `[esp_coex_adapter.h:esp_coex_common_clk_slowclk_cal_get_wrapper]`
- `[esp_ble.c:esp_ble_initialize]`
- `[esp_chip_rev.c:esp_chip_revision_check]`
- `[esp_coex_adapter.c:esp_coex_common_env_is_chip_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_spin_lock_create_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_int_disable_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_int_restore_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_task_yield_from_isr_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_semphr_create_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_semphr_delete_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_semphr_take_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_semphr_give_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_timer_disarm_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_timer_done_wrapper]`
- `[esp_coex_adapter.c:esp_coex_common_timer_setfn_wrapper]`

## Invariants
- `[esp_coex_adapter.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[esp_wifi_adapter.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
