# hpm6750 (`nuttx/arch/risc-v/src/hpm6750`)

## Overview
Hardware abstraction and architecture package for `hpm6750` (HPM6750 Configuration Options; HPM6750 Peripheral Support) under `nuttx/arch/risc-v/src/hpm6750`, providing 9 header file(s) and 7 source file(s) (including `chip.h`, `hpm6750.h`, `hpm6750_clockconfig.h`, `hpm6750_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/hpm6750/hardware`, providing 6 header file(s) and 0 source file(s) (including `hpm6750_ioc.h`, `hpm6750_mchtmr.h`, `hpm6750_memorymap.h`, `hpm6750_plic.h`).

## Interface
- `[hpm6750_clockconfig.h:hpm6750_get_osc_freq]`
- `[hpm6750_clockconfig.h:hpm6750_clockconfig]`
- `[hpm6750_clockconfig.h:clock_node_t]`
- `[hpm6750_clockconfig.h:clock_source_t]`
- `[hpm6750_config.h:HAVE_UART_DEVICE]`
- `[hpm6750_config.h:HAVE_SERIAL_CONSOLE]`
- `[hpm6750_iomux.h:IOC_PA00_FUNC_CTL_GPIO_A_00]`
- `[hpm6750_iomux.h:IOC_PA00_FUNC_CTL_UART3_TXD]`
- `[hpm6750_iomux.h:IOC_PA00_FUNC_CTL_SPI0_DAT3]`
- `[hpm6750_iomux.h:IOC_PA00_FUNC_CTL_I2S1_TXD_2]`
- `[hpm6750_iomux.h:IOC_PA00_FUNC_CTL_I2S2_TXD_0]`
- `[hpm6750_iomux.h:IOC_PA00_FUNC_CTL_CAM0_D_6]`
- `[hpm6750_iomux.h:IOC_PA01_FUNC_CTL_GPIO_A_01]`
- `[hpm6750_iomux.h:IOC_PA01_FUNC_CTL_UART1_RXD]`
- `[hpm6750_iomux.h:IOC_PA01_FUNC_CTL_SPI0_SCLK]`
- `[hpm6750_iomux.h:IOC_PA01_FUNC_CTL_CAN3_RXD]`
- `[hpm6750_iomux.h:IOC_PA01_FUNC_CTL_I2S1_TXD_1]`
- `[hpm6750_iomux.h:IOC_PA01_FUNC_CTL_CAM0_D_8]`
- `[hpm6750_lowputc.h:hpm6750_lowsetup]`
- `[hpm6750_memorymap.h:HPM6750_IDLESTACK_BASE]`
- `[hpm6750_memorymap.h:HPM6750_IDLESTACK_TOP]`
- `[hpm6750_pmic_iomux.h:IOC_PY00_FUNC_CTL_PGPIO_Y_00]`
- `[hpm6750_pmic_iomux.h:IOC_PY00_FUNC_CTL_JTAG_TDO]`
- `[hpm6750_pmic_iomux.h:IOC_PY00_FUNC_CTL_PTMR_COMP_0]`
- `[hpm6750_pmic_iomux.h:IOC_PY00_FUNC_CTL_SOC_PY_00]`
- `[hpm6750_pmic_iomux.h:IOC_PY01_FUNC_CTL_PGPIO_Y_01]`
- `[hpm6750_pmic_iomux.h:IOC_PY01_FUNC_CTL_JTAG_TDI]`
- `[hpm6750_pmic_iomux.h:IOC_PY01_FUNC_CTL_PTMR_COMP_1]`
- `[hpm6750_pmic_iomux.h:IOC_PY01_FUNC_CTL_SOC_PY_01]`
- `[hpm6750_pmic_iomux.h:IOC_PY02_FUNC_CTL_PGPIO_Y_02]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[hpm6750_irq.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[hpm6750_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[hpm6750_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[hpm6750_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[hpm6750_serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[hpm6750_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[hpm6750_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm6750_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[hpm6750_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm6750_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[hpm6750_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[hpm6750_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[hpm6750_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[hpm6750_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm6750_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[hpm6750_lowputc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm6750_lowputc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[hpm6750_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
