# rx65n (`nuttx/arch/renesas/src/rx65n`)

## Overview
Hardware abstraction and architecture package for `rx65n` (RX65N Configuration Options; RX65N Peripheral Selections) under `nuttx/arch/renesas/src/rx65n`, providing 18 header file(s) and 26 source file(s) (including `chip.h`, `rx65n_cgc.h`, `rx65n_cmt.h`, `rx65n_cmtw.h`).

## Interface
- `[rx65n_cgc.h:r_cgc_create]`
- `[rx65n_cgc.h:_00000000_CGC_PCLKD_DIV_1]`
- `[rx65n_cgc.h:_00000001_CGC_PCLKD_DIV_2]`
- `[rx65n_cgc.h:_00000002_CGC_PCLKD_DIV_4]`
- `[rx65n_cgc.h:_00000003_CGC_PCLKD_DIV_8]`
- `[rx65n_cgc.h:_00000004_CGC_PCLKD_DIV_16]`
- `[rx65n_cgc.h:_00000005_CGC_PCLKD_DIV_32]`
- `[rx65n_cgc.h:_00000006_CGC_PCLKD_DIV_64]`
- `[rx65n_cgc.h:_00000000_CGC_PCLKC_DIV_1]`
- `[rx65n_cgc.h:_00000010_CGC_PCLKC_DIV_2]`
- `[rx65n_cgc.h:_00000020_CGC_PCLKC_DIV_4]`
- `[rx65n_cgc.h:_00000030_CGC_PCLKC_DIV_8]`
- `[rx65n_cgc.h:_00000040_CGC_PCLKC_DIV_16]`
- `[rx65n_cmt.h:_00_CMT_PRIORITY_LEVEL0]`
- `[rx65n_cmt.h:_01_CMT_PRIORITY_LEVEL1]`
- `[rx65n_cmt.h:_02_CMT_PRIORITY_LEVEL2]`
- `[rx65n_cmt.h:_03_CMT_PRIORITY_LEVEL3]`
- `[rx65n_cmt.h:_04_CMT_PRIORITY_LEVEL4]`
- `[rx65n_cmt.h:_05_CMT_PRIORITY_LEVEL5]`
- `[rx65n_cmt.h:_06_CMT_PRIORITY_LEVEL6]`
- `[rx65n_cmt.h:_07_CMT_PRIORITY_LEVEL7]`
- `[rx65n_cmt.h:_08_CMT_PRIORITY_LEVEL8]`
- `[rx65n_cmt.h:_09_CMT_PRIORITY_LEVEL9]`
- `[rx65n_cmt.h:_0A_CMT_PRIORITY_LEVEL10]`
- `[rx65n_cmt.h:_0B_CMT_PRIORITY_LEVEL11]`
- `[rx65n_cmtw.h:_0000_CMTW_CMWSTR_COUNTER_STOP]`
- `[rx65n_cmtw.h:_0001_CMTW_CMWSTR_COUNTER_START]`
- `[rx65n_cmtw.h:_0000_CMTW_CMWCR_CLOCK_PCLK8]`
- `[rx65n_cmtw.h:_0001_CMTW_CMWCR_CLOCK_PCLK32]`
- `[rx65n_cmtw.h:_0002_CMTW_CMWCR_CLOCK_PCLK128]`

## Invariants
- `[rx65n_usbhost.h:#error]` Compile-time guard: Phani needs to look into this AHB SRAM Bank1 is not available for OHCI RAM
- `[rx65n_cgc.c:#error]` Compile-time configuration constraint: RX_RESONATOR is not defined in board.h
- `[rx65n_dtc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rx65n_dtc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rx65n_eth.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rx65n_eth.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[rx65n_eth.c:#error]` Compile-time configuration constraint: Logic to support multiple Ethernet interfaces is incomplete
- `[rx65n_lowputc.c:#error]` Compile-time configuration constraint: Serial console selected, but corresponding SCI not enabled
- `[rx65n_riic.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rx65n_rspi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rx65n_rspi.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rx65n_rspi_sw.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[rx65n_cmtw0.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rx65n_dtc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rx65n_dtc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rx65n_eth.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rx65n_eth.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rx65n_eth.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[rx65n_eth.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[rx65n_eth.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rx65n_eth.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rx65n_eth.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[rx65n_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rx65n_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
