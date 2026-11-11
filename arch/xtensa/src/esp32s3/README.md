# esp32s3 (`nuttx/arch/xtensa/src/esp32s3`)

## Overview
Hardware abstraction and architecture package for `esp32s3` (ESP32-S3 Configuration Options; Cache configuration) under `nuttx/arch/xtensa/src/esp32s3`, providing 46 header file(s) and 62 source file(s) (including `chip.h`, `chip_macros.h`, `chip_memory.h`, `esp32s3_addrenv.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/xtensa/src/esp32s3/hardware`, providing 41 header file(s) and 0 source file(s) (including `esp32s3_aes.h`, `esp32s3_apb_ctrl.h`, `esp32s3_bb.h`, `esp32s3_cache_memory.h`).
- `rom`: [./rom/README.md](./rom/README.md) - Hardware abstraction and architecture package for `rom` under `nuttx/arch/xtensa/src/esp32s3/rom`, providing 2 header file(s) and 0 source file(s) (including `esp32s3_libc_stubs.h`, `esp32s3_spiflash.h`).

## Interface
- `[chip.h:OPENETH_PERIPH_MAC]`
- `[chip.h:OPENETH_CPUINT_LEVEL]`
- `[chip.h:OPENETH_IRQ_MAC]`
- `[chip.h:OPENETH_SETUP_IRQ]`
- `[chip.h:RX_BUF_COUNT]`
- `[chip_macros.h:HANDLER_SECTION]`
- `[chip_macros.h:WCL_WORLD_KERNEL]`
- `[chip_macros.h:WCL_WORLD_USER]`
- `[chip_macros.h:xtensa_saveprivilege]`
- `[chip_macros.h:xtensa_restoreprivilege]`
- `[chip_macros.h:xtensa_lowerprivilege]`
- `[chip_macros.h:xtensa_raiseprivilege]`
- `[chip_memory.h:XTENSA_INSTUCTION_REGION]`
- `[esp32s3_addrenv.h:esp32s3_pgmap]`
- `[esp32s3_addrenv.h:esp32s3_pgunmap]`
- `[esp32s3_addrenv.h:esp32s3_pgwipe]`
- `[esp32s3_addrenv.h:esp32s3_pgpool_unmap]`
- `[esp32s3_addrenv.h:esp32s3_addrenv_mapnew]`
- `[esp32s3_addrenv.h:ESP32S3_KMAP_VBASE]`
- `[esp32s3_addrenv.h:ESP32S3_KMAP_NPAGES]`
- `[esp32s3_addrenv.h:ESP32S3_KMAP_VEND]`
- `[esp32s3_addrenv.h:ESP32S3_PGPOOL_PBASE]`
- `[esp32s3_addrenv.h:ESP32S3_PGPOOL_SIZE]`
- `[esp32s3_addrenv.h:ESP32S3_PGPOOL_PEND]`
- `[esp32s3_addrenv.h:ESP32S3_TEXT_VBASE]`
- `[esp32s3_addrenv.h:ESP32S3_TEXT_VEND]`
- `[esp32s3_addrenv.h:ESP32S3_DATA_VBASE]`
- `[esp32s3_addrenv.h:ESP32S3_DATA_VEND]`
- `[esp32s3_addrenv.h:ESP32S3_HEAP_VBASE]`
- `[esp32s3_addrenv.h:ESP32S3_HEAP_VEND]`
- [./hardware/README.md](./hardware/README.md)
- [./rom/README.md](./rom/README.md)

## Invariants
- `[esp32s3_addrenv.h:#error]` Compile-time guard: ESP32-S3 must not map the page pool; see esp32s3_pgmap()
- `[esp32s3_addrenv.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s3_addrenv.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32s3_addrenv_utils.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s3_addrenv_utils.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[esp32s3_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s3_ble_adapter.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s3_ble_adapter.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[esp32s3_ble_adapter.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[esp32s3_ble_adapter.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[esp32s3_cam.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[esp32s3_cam.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[esp32s3_dma.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[esp32s3_dma.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[esp32s3_dma.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[esp32s3_touch_lowerhalf.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[esp32s3_touch_lowerhalf.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[esp32s3_ble_adapter.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[esp32s3_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[esp32s3_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[esp32s3_cam.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[esp32s3_cam.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[esp32s3_cpustart.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[esp32s3_cpustart.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
