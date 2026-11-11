# esp32c3-legacy (`nuttx/arch/risc-v/src/esp32c3-legacy`)

## Overview
Hardware abstraction and architecture package for `esp32c3-legacy` (ESP32-C3 Configuration Options; ESP32-C3 Peripheral Support) under `nuttx/arch/risc-v/src/esp32c3-legacy`, providing 51 header file(s) and 61 source file(s) (including `chip.h`, `esp32c3.h`, `esp32c3_adc.h`, `esp32c3_aes.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/esp32c3-legacy/hardware`, providing 39 header file(s) and 0 source file(s) (including `apb_ctrl_reg.h`, `bb_reg.h`, `esp32c3_aes.h`, `esp32c3_cache_memory.h`).
- `rom`: [./rom/README.md](./rom/README.md) - Hardware abstraction and architecture package for `rom` under `nuttx/arch/risc-v/src/esp32c3-legacy/rom`, providing 2 header file(s) and 0 source file(s) (including `esp32c3_libc_stubs.h`, `esp32c3_spiflash.h`).

## Interface
- `[chip.h:EXCEPTION_SECTION]`
- `[esp32c3.h:setbits]`
- `[esp32c3.h:resetbits]`
- `[esp32c3_adc.h:esp32c3_adc_init]`
- `[esp32c3_aes.h:esp32c3_aes_ecb_cypher]`
- `[esp32c3_aes.h:esp32c3_aes_cbc_cypher]`
- `[esp32c3_aes.h:esp32c3_aes_ctr_cypher]`
- `[esp32c3_aes.h:esp32c3_aes_xts_cypher]`
- `[esp32c3_aes.h:esp32c3_aes_setkey]`
- `[esp32c3_aes.h:esp32c3_aes_xts_setkey]`
- `[esp32c3_aes.h:esp32c3_aes_init]`
- `[esp32c3_aes.h:esp32c3_aes_s]`
- `[esp32c3_aes.h:esp32c3_aes_xts_s]`
- `[esp32c3_attr.h:IRAM_ATTR]`
- `[esp32c3_attr.h:DRAM_ATTR]`
- `[esp32c3_attr.h:RTC_IRAM_ATTR]`
- `[esp32c3_attr.h:RTC_DATA_ATTR]`
- `[esp32c3_attr.h:RTC_RODATA_ATTR]`
- `[esp32c3_bignum.h:esp32c3_mpi_init]`
- `[esp32c3_bignum.h:esp32c3_mpi_free]`
- `[esp32c3_bignum.h:esp32c3_mpi_grow]`
- `[esp32c3_bignum.h:esp32c3_mpi_shrink]`
- `[esp32c3_bignum.h:esp32c3_mpi_copy]`
- `[esp32c3_bignum.h:esp32c3_mpi_swap]`
- `[esp32c3_bignum.h:esp32c3_mpi_safe_cond_assign]`
- `[esp32c3_bignum.h:esp32c3_mpi_safe_cond_swap]`
- `[esp32c3_bignum.h:esp32c3_mpi_lset]`
- `[esp32c3_bignum.h:esp32c3_mpi_get_bit]`
- `[esp32c3_bignum.h:esp32c3_mpi_set_bit]`
- `[esp32c3_bignum.h:esp32c3_mpi_lsb]`
- [./hardware/README.md](./hardware/README.md)
- [./rom/README.md](./rom/README.md)

## Invariants
- `[esp32c3_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32c3_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32c3_aes.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32c3_bignum.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32c3_ble_adapter.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32c3_ble_adapter.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32c3_crypto.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32c3_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32c3_efuse.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32c3_efuse_lowerhalf.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32c3_efuse_lowerhalf.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32c3_freerun.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[esp32c3.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[esp32c3_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32c3_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32c3_aes.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32c3_aes.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32c3_bignum.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32c3_bignum.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp32c3_bignum.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32c3_ble_adapter.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp32c3_ble_adapter.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[esp32c3_ble_adapter.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[esp32c3_ble_adapter.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
