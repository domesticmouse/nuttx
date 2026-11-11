# dm320 (`nuttx/arch/arm/src/dm320`)

## Overview
Hardware abstraction and architecture package for `dm320` (DM320 Configuration Options; DM320 Peripheral Selections) under `nuttx/arch/arm/src/dm320`, providing 12 header file(s) and 8 source file(s) (including `chip.h`, `dm320_ahb.h`, `dm320_busc.h`, `dm320_clkc.h`).

## Interface
- `[dm320_ahb.h:DM320_AHB_SDRAMSA]`
- `[dm320_ahb.h:DM320_AHB_SDRAMEA]`
- `[dm320_ahb.h:DM320_AHB_BUSCONTROL]`
- `[dm320_ahb.h:DM320_AHB_RSV1]`
- `[dm320_ahb.h:DM320_AHB_USBCTL]`
- `[dm320_busc.h:DM320_BUSC_ECR]`
- `[dm320_busc.h:DM320_BUSC_EBYTER]`
- `[dm320_busc.h:DM320_BUSC_EBITR]`
- `[dm320_busc.h:DM320_BUSC_REVR]`
- `[dm320_clkc.h:DM320_CLKC_PLLA]`
- `[dm320_clkc.h:DM320_CLKC_PLLB]`
- `[dm320_clkc.h:DM320_CLKC_SEL0]`
- `[dm320_clkc.h:DM320_CLKC_SEL1]`
- `[dm320_clkc.h:DM320_CLKC_SEL2]`
- `[dm320_clkc.h:DM320_CLKC_DIV0]`
- `[dm320_clkc.h:DM320_CLKC_DIV1]`
- `[dm320_clkc.h:DM320_CLKC_DIV2]`
- `[dm320_clkc.h:DM320_CLKC_DIV3]`
- `[dm320_clkc.h:DM320_CLKC_DIV4]`
- `[dm320_clkc.h:DM320_CLKC_BYP]`
- `[dm320_clkc.h:DM320_CLKC_INV]`
- `[dm320_emif.h:DM320_EMIF_CS0CTRL1]`
- `[dm320_emif.h:DM320_EMIF_CS0CTRL2]`
- `[dm320_emif.h:DM320_EMIF_CS0CTRL3]`
- `[dm320_emif.h:DM320_EMIF_CS1CTRL1A]`
- `[dm320_emif.h:DM320_EMIF_CS1CTRL1B]`
- `[dm320_emif.h:DM320_EMIF_CS2CTRL2]`
- `[dm320_emif.h:DM320_EMIF_CS2CTRL1]`
- `[dm320_emif.h:DM320_EMIF_CS1CTRL2]`
- `[dm320_emif.h:DM320_EMIF_CS3CTRL1]`

## Invariants
- `[dm320_memorymap.h:#error]` Compile-time guard: Invalid setting for CONFIG_RAM_VSTART
- `[dm320_decodeirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[dm320_decodeirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[dm320_framebuffer.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[dm320_framebuffer.c:#error]` Compile-time configuration constraint: Cursor image not supported
- `[dm320_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[dm320_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[dm320_usbdev.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[dm320_usbdev.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[dm320_usbdev.c:#error]` Compile-time configuration constraint: CONFIG_DM320_GIO_USBATTACH invalid

## Side Effects
- `[dm320_framebuffer.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[dm320_irq.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[dm320_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[dm320_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[dm320_serial.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[dm320_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[dm320_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[dm320_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[dm320_timerisr.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[dm320_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[dm320_timerisr.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[dm320_timerisr.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
