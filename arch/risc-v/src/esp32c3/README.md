# esp32c3 (`nuttx/arch/risc-v/src/esp32c3`)

## Overview
Hardware abstraction and architecture package for `esp32c3` under `nuttx/arch/risc-v/src/esp32c3`, providing 4 header file(s) and 6 source file(s) (including `esp_ble.h`, `esp_ble_adapter.h`, `esp_coex_adapter.h`, `esp_wireless.h`).

## Interface
- `[esp_ble.h:esp_ble_initialize]`
- `[esp_ble_adapter.h:esp_bt_controller_init]`
- `[esp_ble_adapter.h:esp_bt_controller_deinit]`
- `[esp_ble_adapter.h:esp_bt_controller_enable]`
- `[esp_ble_adapter.h:esp_bt_controller_disable]`
- `[esp_ble_adapter.h:esp_bt_controller_get_status]`
- `[esp_ble_adapter.h:esp_vhci_host_check_send_available]`
- `[esp_ble_adapter.h:esp_vhci_host_send_packet]`
- `[esp_ble_adapter.h:esp_vhci_register_callback]`
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
- `[esp_wireless.h:esp_init_semcache]`
- `[esp_wireless.h:esp_post_semcache]`
- `[esp_wireless.h:esp_init_queuecache]`
- `[esp_wireless.h:esp_send_queuecache]`
- `[esp_wireless.h:esp_wireless_init]`
- `[esp_wireless.h:esp_wireless_deinit]`

## Invariants
- `[esp_ble_adapter.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_ble_adapter.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[esp_ble_adapter.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp_coex_adapter.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp_wireless.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp_wireless.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[esp_ble_adapter.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp_wifi_adapter.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp_wireless.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp_wireless.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp_wireless.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
