# lpc17xx_40xx (`nuttx/arch/arm/src/lpc17xx_40xx`)

## Overview
Hardware abstraction and architecture package for `lpc17xx_40xx` (LPC17xx/40xx Configuration Options; LPC17xx/LPC40xx Peripheral Support) under `nuttx/arch/arm/src/lpc17xx_40xx`, providing 33 header file(s) and 37 source file(s) (including `chip.h`, `lpc176x_gpio.h`, `lpc178x_40xx_gpio.h`, `lpc17_40_adc.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/lpc17xx_40xx/hardware`, providing 36 header file(s) and 0 source file(s) (including `lpc176x_memorymap.h`, `lpc176x_pinconfig.h`, `lpc176x_pinconn.h`, `lpc176x_syscon.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:NVIC_VECTAB_TBLOFF_MASK]`
- `[lpc176x_gpio.h:lpc17_40_pinset_t]`
- `[lpc176x_gpio.h:GPIO_FUNC_SHIFT]`
- `[lpc176x_gpio.h:GPIO_FUNC_MASK]`
- `[lpc176x_gpio.h:GPIO_INPUT]`
- `[lpc176x_gpio.h:GPIO_INTFE]`
- `[lpc176x_gpio.h:GPIO_INTRE]`
- `[lpc176x_gpio.h:GPIO_INTBOTH]`
- `[lpc176x_gpio.h:GPIO_OUTPUT]`
- `[lpc176x_gpio.h:GPIO_ALT1]`
- `[lpc176x_gpio.h:GPIO_ALT2]`
- `[lpc176x_gpio.h:GPIO_ALT3]`
- `[lpc176x_gpio.h:GPIO_EDGE_SHIFT]`
- `[lpc176x_gpio.h:GPIO_EDGE_MASK]`
- `[lpc178x_40xx_gpio.h:lpc17_40_pinset_t]`
- `[lpc178x_40xx_gpio.h:GPIO_INBUFF_SHIFT]`
- `[lpc178x_40xx_gpio.h:GPIO_INBUFF_MASK]`
- `[lpc178x_40xx_gpio.h:GPIO_HYSTERESIS]`
- `[lpc178x_40xx_gpio.h:GPIO_INVERT]`
- `[lpc178x_40xx_gpio.h:GPIO_SLEW_SHIFT]`
- `[lpc178x_40xx_gpio.h:GPIO_SLEW_MASK]`
- `[lpc178x_40xx_gpio.h:GPIO_SLEW_NORMAL]`
- `[lpc178x_40xx_gpio.h:GPIO_SLEW_FAST]`
- `[lpc178x_40xx_gpio.h:GPIO_ADMODE_SHIFT]`
- `[lpc178x_40xx_gpio.h:GPIO_ADMODE_MASK]`
- `[lpc178x_40xx_gpio.h:GPIO_MODE_DIGITAL]`
- `[lpc178x_40xx_gpio.h:GPIO_MODE_ANALOG]`
- `[lpc17_40_adc.h:lpc17_40_adcinitialize]`
- `[lpc17_40_can.h:lpc17_40_caninitialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[lpc17_40_adc.h:#error]` Compile-time guard: CONFIG_LPC17_40_ADC_CHANLIST must defined in this configuration
- `[lpc17_40_emacram.h:#error]` Compile-time guard: AHB SRAM Bank0 is not available for EMAC RAM
- `[lpc17_40_gpio.h:#error]` Compile-time guard: Unrecognized LPC17xx/LPC40xx family
- `[lpc17_40_lcd.h:#error]` Compile-time guard: 24 BPP is only available for a TFT panel
- `[lpc17_40_ohciram.h:#error]` Compile-time guard: AHB SRAM Bank1 is not available for OHCI RAM
- `[lpc17_40_pwm.h:#error]` Compile-time guard: PWM subsystem has more channels then physical channels enabled
- `[lpc176x_clockconfig.c:#error]` Compile-time configuration constraint: The logic in this file applies only to the LPC176x family
- `[lpc176x_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc176x_rtc.c:#error]` Compile-time configuration constraint: CONFIG_RTC_DATETIME must be set to use this driver
- `[lpc178x_40xx_clockconfig.c:#error]` Compile-time configuration constraint: The logic in this file applies only to the LPC178x/40xx family
- `[lpc178x_40xx_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc17_40_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[lpc176x_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc176x_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc176x_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc176x_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc176x_rtc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc176x_rtc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc176x_rtc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[lpc176x_rtc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lpc178x_40xx_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc178x_40xx_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc178x_40xx_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc178x_40xx_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
