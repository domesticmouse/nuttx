# esp32 (`nuttx/arch/xtensa/src/esp32`)

## Overview
Hardware abstraction and architecture package for `esp32` (ESP32 Configuration Options; ESP32 Peripheral Selection) under `nuttx/arch/xtensa/src/esp32`, providing 41 header file(s) and 55 source file(s) (including `chip.h`, `chip_macros.h`, `chip_memory.h`, `esp32_aes.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/xtensa/src/esp32/hardware`, providing 26 header file(s) and 0 source file(s) (including `esp32_aes.h`, `esp32_apb_ctrl.h`, `esp32_dma.h`, `esp32_dport.h`).
- `rom`: [./rom/README.md](./rom/README.md) - Hardware abstraction and architecture package for `rom` under `nuttx/arch/xtensa/src/esp32/rom`, providing 3 header file(s) and 0 source file(s) (including `esp32_efuse.h`, `esp32_libc_stubs.h`, `esp32_spiflash.h`).

## Interface
- `[chip.h:OPENETH_PERIPH_MAC]`
- `[chip.h:OPENETH_CPUINT_LEVEL]`
- `[chip.h:OPENETH_IRQ_MAC]`
- `[chip.h:OPENETH_SETUP_IRQ]`
- `[chip.h:RX_BUF_COUNT]`
- `[chip_macros.h:HANDLER_SECTION]`
- `[chip_macros.h:PIDCTRL_PID_KERNEL]`
- `[chip_macros.h:PIDCTRL_PID_USER]`
- `[chip_macros.h:xtensa_saveprivilege]`
- `[chip_macros.h:xtensa_restoreprivilege]`
- `[chip_macros.h:xtensa_lowerprivilege]`
- `[chip_macros.h:xtensa_raiseprivilege]`
- `[chip_memory.h:XTENSA_INSTUCTION_REGION]`
- `[esp32_aes.h:esp32_aes_ecb_cypher]`
- `[esp32_aes.h:esp32_aes_cbc_cypher]`
- `[esp32_aes.h:esp32_aes_ctr_cypher]`
- `[esp32_aes.h:esp32_aes_xts_cypher]`
- `[esp32_aes.h:esp32_aes_setkey]`
- `[esp32_aes.h:esp32_aes_xts_setkey]`
- `[esp32_aes.h:esp32_aes_init]`
- `[esp32_aes.h:esp32_aes_s]`
- `[esp32_aes.h:esp32_aes_xts_s]`
- `[esp32_ble.h:esp32_ble_initialize]`
- `[esp32_ble_adapter.h:esp32_bt_controller_init]`
- `[esp32_ble_adapter.h:esp32_bt_controller_deinit]`
- `[esp32_ble_adapter.h:esp32_bt_controller_enable]`
- `[esp32_ble_adapter.h:esp32_bt_controller_disable]`
- `[esp32_ble_adapter.h:esp_bt_controller_get_status]`
- `[esp32_ble_adapter.h:esp32_vhci_host_check_send_available]`
- `[esp32_ble_adapter.h:esp32_vhci_host_send_packet]`
- [./hardware/README.md](./hardware/README.md)
- [./rom/README.md](./rom/README.md)

## Invariants
- `[esp32_aes.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32_ble_adapter.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32_ble_adapter.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[esp32_ble_adapter.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32_cpustart.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32_crypto.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32_dac.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[esp32_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32_emac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32_emac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32_emac.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[esp32_touch_lowerhalf.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[esp32_aes.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32_aes.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp32_aes.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32_cpustart.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32_cpustart.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32_cpustart.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp32_cpustart.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[esp32_dac.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32_dac.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp32_dac.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32_emac.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
