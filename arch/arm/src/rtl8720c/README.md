# rtl8720c (`nuttx/arch/arm/src/rtl8720c`)

## Overview
Hardware abstraction and architecture package for `rtl8720c` (AMEBA Configuration Options) under `nuttx/arch/arm/src/rtl8720c`, providing 10 header file(s) and 18 source file(s) (including `ameba_efuse.h`, `ameba_flash.h`, `ameba_uart.h`, `amebaz_coex.h`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/arm/src/rtl8720c/include`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[ameba_efuse.h:ameba_efuse_logical_read]`
- `[ameba_efuse.h:ameba_efuse_logical_write]`
- `[ameba_efuse.h:ameba_efuse_fw_verify_enable]`
- `[ameba_efuse.h:ameba_efuse_fw_verify_check]`
- `[ameba_efuse.h:ameba_efuse_boot_message_disable]`
- `[ameba_efuse.h:ameba_efuse_boot_message_enable]`
- `[ameba_uart.h:uart_ioctl]`
- `[ameba_uart.h:uart_datawidth_t]`
- `[ameba_uart.h:uart_addrwidth_t]`
- `[ameba_uart.h:HAVE_UART]`
- `[ameba_uart.h:HAVE_AMEBA_CONSOLE]`
- `[amebaz_coex.h:bt_coex_handle_cmd_complete_evt]`
- `[amebaz_coex.h:bt_coex_handle_specific_evt]`
- `[amebaz_coex.h:bt_coex_handle_xiaomi_evt]`
- `[amebaz_coex.h:bt_coex_sw_mailbox_set]`
- `[amebaz_coex.h:bt_coex_init]`
- `[amebaz_coex.h:send_coex_mailbox_to_wifi_from_btapp]`
- `[amebaz_coex.h:net_buf_simple]`
- `[amebaz_coex.h:BT_SW_MAILBOX_SCAN_OFF]`
- `[amebaz_coex.h:BT_SW_MAILBOX_SCAN_ON]`
- `[amebaz_depend.h:atomic_t]`
- `[amebaz_depend.h:list_head]`
- `[amebaz_depend.h:__queue]`
- `[amebaz_depend.h:task_struct]`
- `[amebaz_depend.h:nthread_wrapper]`
- `[amebaz_depend.h:ntimer_wrapper]`
- `[amebaz_depend.h:osdep_service_ops]`
- `[amebaz_depend.h:_queue]`
- `[amebaz_driver.h:amebaz_wl_start_scan]`
- `[amebaz_driver.h:amebaz_wl_get_scan_results]`
- [./include/README.md](./include/README.md)

## Invariants
- `[ameba_uart.h:#error]` Compile-time guard: CONFIG_AMEBA_REGINCR not defined
- `[ameba_flash.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ameba_nvic.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ameba_uart.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ameba_vectors.c:#error]` Compile-time configuration constraint: ARMV8M_PERIPHERAL_INTERRUPTS must be defined to the number of I/O interrupts to be supported
- `[ameba_wdt.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[amebaz_netdev.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[ameba_nvic.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ameba_nvic.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ameba_nvic.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_nvic.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ameba_nvic.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[ameba_start.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
