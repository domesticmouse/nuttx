# mpfs (`nuttx/arch/risc-v/src/mpfs`)

## Overview
Hardware abstraction and architecture package for `mpfs` (Polarfire Configuration Options; MPFS Peripheral Support) under `nuttx/arch/risc-v/src/mpfs`, providing 31 header file(s) and 36 source file(s) (including `chip.h`, `mpfs.h`, `mpfs_cache.h`, `mpfs_can.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/mpfs/hardware`, providing 26 header file(s) and 0 source file(s) (including `mpfs250t_484_pinmap.h`, `mpfs_cache.h`, `mpfs_can.h`, `mpfs_clint.h`).

## Interface
- `[mpfs_cache.h:mpfs_enable_cache]`
- `[mpfs_can.h:mpfs_can_init]`
- `[mpfs_clockconfig.h:mpfs_get_cpuclk]`
- `[mpfs_clockconfig.h:mpfs_get_pll0clk]`
- `[mpfs_clockconfig.h:mpfs_clockconfig]`
- `[mpfs_config.h:HAVE_UART_DEVICE]`
- `[mpfs_config.h:HAVE_SERIAL_CONSOLE]`
- `[mpfs_coremmc.h:mpfs_coremmc_sdio_initialize]`
- `[mpfs_coremmc.h:mpfs_coremmc_sdio_mediachange]`
- `[mpfs_coremmc.h:mpfs_coremmc_sdio_wrprotect]`
- `[mpfs_corepwm.h:mpfs_corepwm_init]`
- `[mpfs_corespi.h:mpfs_corespibus_initialize]`
- `[mpfs_corespi.h:mpfs_corespibus_uninitialize]`
- `[mpfs_corespi.h:mpfs_corespi_select]`
- `[mpfs_ddr.h:mpfs_ddr_init]`
- `[mpfs_dma.h:mpfs_dma_setup_transfer]`
- `[mpfs_dma.h:mpfs_dma_set_transaction_size]`
- `[mpfs_dma.h:mpfs_dma_start]`
- `[mpfs_dma.h:mpfs_dma_get_transfer_type]`
- `[mpfs_dma.h:mpfs_dma_get_bytes_remaining]`
- `[mpfs_dma.h:mpfs_dma_get_current_destination]`
- `[mpfs_dma.h:mpfs_dma_get_current_source]`
- `[mpfs_dma.h:mpfs_dma_get_complete_status]`
- `[mpfs_dma.h:mpfs_dma_get_error_status]`
- `[mpfs_dma.h:mpfs_dma_clear_complete_status]`
- `[mpfs_dma.h:mpfs_dma_clear_error_status]`
- `[mpfs_dma.h:mpfs_dma_channel_config]`
- `[mpfs_dma.h:MPFS_DMA_NUM_CHANNELS]`
- `[mpfs_dma_alloc.h:mpfs_dma_alloc_init]`
- `[mpfs_dsn.h:mpfs_read_dsn]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[mpfs_cache.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mpfs_cache.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[mpfs_can.c:#error]` Compile-time configuration constraint: This should not be compiled if MSS CAN block is not enabled
- `[mpfs_clockconfig.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mpfs_coremmc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mpfs_coremmc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[mpfs_coremmc.c:#error]` Compile-time configuration constraint: Callback support requires CONFIG_SCHED_WORKQUEUE
- `[mpfs_corepwm.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mpfs_corepwm.c:#error]` Compile-time configuration constraint: This should not be compiled as CorePWM block is not defined/configured
- `[mpfs_corespi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mpfs_corespi.c:#error]` Compile-time configuration constraint: Too many CoreSPI instances, maximum is 8
- `[mpfs_ddr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[mpfs_cache.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mpfs_can.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mpfs_can.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[mpfs_can.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mpfs_can.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[mpfs_can.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[mpfs_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mpfs_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[mpfs_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mpfs_clockconfig.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[mpfs_coremmc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mpfs_coremmc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
