# imx9 (`nuttx/arch/arm64/src/imx9`)

## Overview
Hardware abstraction and architecture package for `imx9` (i.MX9 Chip Selection; DMA Allocator Configuration) under `nuttx/arch/arm64/src/imx9`, providing 27 header file(s) and 31 source file(s) (including `chip.h`, `imx9_boot.h`, `imx9_ccm.h`, `imx9_clockconfig.h`).

## Subdirectories & Boundaries
- `ddr`: [./ddr/README.md](./ddr/README.md) - Hardware abstraction and architecture package for `ddr` under `nuttx/arch/arm64/src/imx9/ddr`, providing 1 header file(s) and 1 source file(s) (including `imx9_ddr_training.h`, `imx9_ddr_training.c`).
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/imx9/hardware`, providing 23 header file(s) and 0 source file(s) (including `imx9_blk_ctrl.h`, `imx9_ccm.h`, `imx9_dmamux.h`, `imx9_edma.h`).

## Interface
- `[imx9_boot.h:imx9_board_initialize]`
- `[imx9_ccm.h:imx9_ccm_configure_root_clock]`
- `[imx9_ccm.h:imx9_ccm_root_clock_on]`
- `[imx9_ccm.h:imx9_ccm_gate_on]`
- `[imx9_ccm.h:imx9_ccm_shared_gpr_set]`
- `[imx9_ccm.h:imx9_ccm_clock_init]`
- `[imx9_clockconfig.h:imx9_clockconfig]`
- `[imx9_clockconfig.h:imx9_get_clock]`
- `[imx9_clockconfig.h:imx9_configure_clock]`
- `[imx9_clockconfig.h:imx9_set_clock_freq]`
- `[imx9_clockconfig.h:imx9_get_rootclock]`
- `[imx9_clockconfig.h:pll_parms_s]`
- `[imx9_clockconfig.h:pfd_parms_s]`
- `[imx9_clockconfig.h:imx9_pll_cfg_s]`
- `[imx9_clockconfig.h:imx9_pfd_cfg_s]`
- `[imx9_clockconfig.h:PLL_PARMS]`
- `[imx9_clockconfig.h:PLL_CFG]`
- `[imx9_clockconfig.h:PFD_PARMS]`
- `[imx9_clockconfig.h:PFD_CFG]`
- `[imx9_dma_alloc.h:imx9_dma_alloc_init]`
- `[imx9_dma_alloc.h:imx9_dma_alloc]`
- `[imx9_dma_alloc.h:imx9_dma_free]`
- `[imx9_edma.h:imx9_dmach_alloc]`
- `[imx9_edma.h:imx9_dmach_free]`
- `[imx9_edma.h:imx9_dmach_xfrsetup]`
- `[imx9_edma.h:imx9_dmach_start]`
- `[imx9_edma.h:imx9_dmach_stop]`
- `[imx9_edma.h:imx9_dmach_getcount]`
- `[imx9_edma.h:imx9_dmach_idle]`
- `[imx9_edma.h:imx9_dmasample]`
- [./ddr/README.md](./ddr/README.md)
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[imx9_flexio_dshot.h:#error]` Compile-time guard: Driver supports max 8 channels per flexio (CONFIG_DSHOT_NCHANNELS)
- `[imx9_serial.h:#error]` Compile-time guard: IMXRT LPUART receive or transmit DMA requires CONFIG_IMX9_EDMA
- `[imx9_edma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_edma.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[imx9_enet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_enet.c:#error]` Compile-time configuration constraint: LPWORK queue support is required
- `[imx9_flexcan.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_flexcan.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[imx9_flexio_dshot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_flexio_dshot.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[imx9_flexio_pwm.c:#error]` Compile-time configuration constraint: CONFIG_PWM_NCHANNELS < CONFIG_IMX9_FLEXIO1_PWM_NCHANNELS
- `[imx9_flexspi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[imx9_boot.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[imx9_boot.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx9_ccm.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx9_ccm.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[imx9_ccm.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx9_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx9_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[imx9_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx9_edma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx9_edma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx9_edma.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[imx9_edma.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
