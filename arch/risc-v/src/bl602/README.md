# bl602 (`nuttx/arch/risc-v/src/bl602`)

## Overview
Hardware abstraction and architecture package for `bl602` (BL602 Configuration Options; BL602 Peripheral Support) under `nuttx/arch/risc-v/src/bl602`, providing 23 header file(s) and 26 source file(s) (including `bl602_boot2.h`, `bl602_config.h`, `bl602_dma.h`, `bl602_efuse.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/bl602/hardware`, providing 22 header file(s) and 0 source file(s) (including `bl602_aon.h`, `bl602_cci.h`, `bl602_cks.h`, `bl602_clic.h`).

## Interface
- `[bl602_boot2.h:pt_config_s]`
- `[bl602_boot2.h:pt_entry_config_s]`
- `[bl602_boot2.h:pt_stuff_config_s]`
- `[bl602_boot2.h:boot2_partition_table_s]`
- `[bl602_boot2.h:PT_ERROR_SUCCESS]`
- `[bl602_boot2.h:PT_ERROR_TABLE_NOT_VALID]`
- `[bl602_boot2.h:PT_ERROR_ENTRY_NOT_FOUND]`
- `[bl602_boot2.h:PT_ERROR_ENTRY_UPDATE_FAIL]`
- `[bl602_boot2.h:PT_ERROR_CRC32]`
- `[bl602_boot2.h:PT_ERROR_PARAMETER]`
- `[bl602_boot2.h:PT_ERROR_FALSH_READ]`
- `[bl602_boot2.h:PT_ERROR_FALSH_WRITE]`
- `[bl602_boot2.h:PT_ERROR_FALSH_ERASE]`
- `[bl602_boot2.h:PT_TABLE_ID_0]`
- `[bl602_boot2.h:PT_TABLE_ID_1]`
- `[bl602_boot2.h:PT_TABLE_ID_INVALID]`
- `[bl602_config.h:HAVE_UART_DEVICE]`
- `[bl602_config.h:HAVE_SERIAL_CONSOLE]`
- `[bl602_dma.h:bl602_dma_channel_request]`
- `[bl602_dma.h:bl602_dma_channel_release]`
- `[bl602_dma.h:bl602_dma_channel_start]`
- `[bl602_dma.h:bl602_dma_channel_stop]`
- `[bl602_dma.h:bl602_dma_init]`
- `[bl602_dma.h:bl602_dmasample]`
- `[bl602_dma.h:bl602_dmadump]`
- `[bl602_dma.h:bl602_dmaregs_s]`
- `[bl602_dma.h:bl602_dma_ctrl_s]`
- `[bl602_dma.h:BL602_DMA_NCHANNELS]`
- `[bl602_dma.h:BL602_DMA_INT_EVT_TC]`
- `[bl602_dma.h:BL602_DMA_INT_EVT_ERR]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[bl602_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bl602_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bl602_efuse.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bl602_flash.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[bl602_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[bl602_hbn.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bl602_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bl602_irq.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[bl602_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[bl602_netdev.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bl602_netdev.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[bl602_netdev.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[bl602_dma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bl602_dma.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[bl602_dma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bl602_dma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bl602_dma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bl602_efuse.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bl602_glb.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[bl602_glb.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bl602_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bl602_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[bl602_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bl602_hbn.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
