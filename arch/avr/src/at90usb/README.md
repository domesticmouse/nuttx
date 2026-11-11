# at90usb (`nuttx/arch/avr/src/at90usb`)

## Overview
Hardware abstraction and architecture package for `at90usb` (AT90USB Configuration Options; AT90USB Peripheral Selections) under `nuttx/arch/avr/src/at90usb`, providing 4 header file(s) and 5 source file(s) (including `at90usb.h`, `at90usb_config.h`, `at90usb_memorymap.h`, `chip.h`).

## Interface
- `[at90usb.h:up_clkinitialize]`
- `[at90usb.h:usart1_reset]`
- `[at90usb.h:usart1_configure]`
- `[at90usb.h:up_consoleinit]`
- `[at90usb.h:at90usb_boardinitialize]`
- `[at90usb.h:gpio_irqinitialize]`
- `[at90usb.h:gpio_irqattach]`
- `[at90usb.h:gpio_irqenable]`
- `[at90usb.h:gpio_irqdisable]`
- `[at90usb_config.h:HAVE_USART_DEVICE]`
- `[at90usb_config.h:HAVE_SERIAL_CONSOLE]`
- `[at90usb_config.h:USE_SERIALDRIVER]`
- `[at90usb_config.h:USE_EARLYSERIALINIT]`
- `[chip.h:AVR_FLASH_SIZE]`
- `[chip.h:AVR_SRAM_SIZE]`
- `[chip.h:AVR_EEPROM_SIZE]`
- `[chip.h:HAVE_USBDEV]`
- `[chip.h:HAVE_USBHOST]`
- `[at90usb_lowconsole.c:usart1_reset]`
- `[at90usb_lowconsole.c:usart1_configure]`
- `[at90usb_lowconsole.c:up_consoleinit]`
- `[at90usb_lowconsole.c:avr_lowputc]`
- `[at90usb_lowinit.c:avr_lowinit]`
- `[at90usb_serial.c:avr_earlyserialinit]`
- `[at90usb_serial.c:avr_serialinit]`
- `[at90usb_serial.c:up_putc]`
- `[at90usb_timerisr.c:up_timer_initialize]`
- `[at90usb_usbdev.c:avr_usbshutdown]`
- `[at90usb_usbdev.c:avr_usbinitialize]`
- `[at90usb_usbdev.c:avr_usbuninitialize]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported AVR chip
- `[at90usb_lowconsole.c:#error]` Compile-time configuration constraint: Unsupported word size
- `[at90usb_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[at90usb_timerisr.c:#error]` Compile-time configuration constraint: Cannot represent this timer frequency
- `[at90usb_usbdev.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[at90usb_usbdev.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[at90usb_usbdev.c:#error]` Compile-time configuration constraint: Unsupported CPU clock

## Side Effects
- `[at90usb_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[at90usb_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[at90usb_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[at90usb_usbdev.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
