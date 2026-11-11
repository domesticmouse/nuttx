# tlsr82 (`nuttx/arch/arm/src/tlsr82`)

## Overview
Hardware abstraction and architecture package for `tlsr82` (TLSR82XX Configuration Options; TLSR82 Peripheral Support) under `nuttx/arch/arm/src/tlsr82`, providing 18 header file(s) and 20 source file(s) (including `chip.h`, `tlsr82_adc.h`, `tlsr82_analog.h`, `tlsr82_clock.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/tlsr82/hardware`, providing 14 header file(s) and 0 source file(s) (including `tlsr82_adc.h`, `tlsr82_aes.h`, `tlsr82_analog.h`, `tlsr82_clock.h`).
- `tc32`: [./tc32/README.md](./tc32/README.md) - Hardware abstraction and architecture package for `tc32` under `nuttx/arch/arm/src/tlsr82/tc32`, providing 1 header file(s) and 6 source file(s) (including `tc32.h`, `tc32_backtrace.c`, `tc32_doirq.c`, `tc32_initialstate.c`).

## Interface
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:arm_fullcontextrestore]`
- `[tlsr82_adc.h:tlsr82_adc_init]`
- `[tlsr82_adc.h:ADC_CHAN_0]`
- `[tlsr82_adc.h:ADC_CHAN_1]`
- `[tlsr82_adc.h:ADC_CHAN_2]`
- `[tlsr82_adc.h:ADC_CHAN_3]`
- `[tlsr82_adc.h:ADC_CHAN_4]`
- `[tlsr82_adc.h:ADC_CHAN_5]`
- `[tlsr82_adc.h:ADC_CHAN_6]`
- `[tlsr82_adc.h:ADC_CHAN_7]`
- `[tlsr82_adc.h:ADC_CHAN_TEMP]`
- `[tlsr82_adc.h:ADC_CHAN_VBAT]`
- `[tlsr82_adc.h:ADC_CHAN_NONE]`
- `[tlsr82_adc.h:ADC_CHAN_TYPE_NONE]`
- `[tlsr82_clock.h:tlsr82_clock_init]`
- `[tlsr82_cpu.h:tlsr82_cpu_wakeup_init]`
- `[tlsr82_cpu.h:power_mode_t]`
- `[tlsr82_cpu.h:xtal_t]`
- `[tlsr82_flash.h:tlsr82_flash_erase_sector]`
- `[tlsr82_flash.h:tlsr82_flash_read_data]`
- `[tlsr82_flash.h:tlsr82_flash_write_data]`
- `[tlsr82_flash.h:tlsr82_flash_read_status]`
- `[tlsr82_flash.h:tlsr82_flash_write_status]`
- `[tlsr82_flash.h:tlsr82_flash_protect]`
- `[tlsr82_flash.h:tlsr82_flash_unprotect]`
- `[tlsr82_flash.h:tlsr82_flash_miduid_check]`
- `[tlsr82_flash.h:tlsr82_flash_calibrate]`
- `[tlsr82_flash.h:FLASH_VOLTAGE_1V6]`
- `[tlsr82_flash.h:FLASH_VOLTAGE_1V65]`
- [./hardware/README.md](./hardware/README.md)
- [./tc32/README.md](./tc32/README.md)

## Invariants
- `[tlsr82_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tlsr82_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tlsr82_adc.c:#error]` Compile-time configuration constraint: The filter number must be multiple of 4 !
- `[tlsr82_analog.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tlsr82_clock.c:#error]` Compile-time configuration constraint: sys clock error or undefined
- `[tlsr82_flash.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tlsr82_flash.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tlsr82_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tlsr82_gpio_cfg.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tlsr82_pulsecount.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tlsr82_pulsecount.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tlsr82_pwm.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation

## Side Effects
- `[tlsr82_gpio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[tlsr82_gpio.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[tlsr82_gpio.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[tlsr82_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[tlsr82_pulsecount.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[tlsr82_pulsecount.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[tlsr82_pulsecount.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[tlsr82_pwm.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[tlsr82_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[tlsr82_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[tlsr82_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[tlsr82_timer.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
