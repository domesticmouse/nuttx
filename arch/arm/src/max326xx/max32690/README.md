# max32690 (`nuttx/arch/arm/src/max326xx/max32690`)

## Overview
Hardware abstraction and architecture package for `max32690` under `nuttx/arch/arm/src/max326xx/max32690`, providing 2 header file(s) and 3 source file(s) (including `max32690_gpio.h`, `max32690_periphclks.h`, `max32690_gpio.c`, `max32690_gpioirq.c`).

## Interface
- `[max32690_gpio.h:max32690_get_gpio_bank_regptr]`
- `[max32690_gpio.h:max32690_gpio_config]`
- `[max32690_gpio.h:max32690_gpio_read]`
- `[max32690_gpio.h:max32690_gpio_write]`
- `[max32690_gpio.h:max32690_gpio_irq_enable]`
- `[max32690_gpio.h:max32690_gpio_irq_disable]`
- `[max32690_gpio.h:max32690_pinconfig_t]`
- `[max32690_gpio.h:max32690_gpio_regs_t]`
- `[max32690_gpio.h:GPIO_DRIVE_SHIFT]`
- `[max32690_gpio.h:GPIO_DRIVE_MASK]`
- `[max32690_gpio.h:GPIO_DRIVE_0_V_DIO_H]`
- `[max32690_gpio.h:GPIO_DRIVE_1_V_DIO_H]`
- `[max32690_gpio.h:GPIO_DRIVE_2_V_DIO_H]`
- `[max32690_gpio.h:GPIO_DRIVE_3_V_DIO_H]`
- `[max32690_gpio.h:GPIO_DRIVE_0_V_DIO]`
- `[max32690_gpio.h:GPIO_DRIVE_1_V_DIO]`
- `[max32690_gpio.h:GPIO_DRIVE_2_V_DIO]`
- `[max32690_gpio.h:GPIO_DRIVE_3_V_DIO]`
- `[max32690_gpio.h:GPIO_WAKEUP]`
- `[max32690_gpio.h:GPIO_IN_MODE_SHIFT]`
- `[max32690_periphclks.h:MAX32690_PERIPH_ENABLE_0]`
- `[max32690_periphclks.h:MAX32690_PERIPH_ENABLE_1]`
- `[max32690_periphclks.h:MAX32690_PERIPH_DISABLE_0]`
- `[max32690_periphclks.h:MAX32690_PERIPH_DISABLE_1]`
- `[max32690_periphclks.h:max326_pt_enableclk]`
- `[max32690_periphclks.h:max326_adc_enableclk]`
- `[max32690_periphclks.h:max326_crypto_enableclk]`
- `[max32690_periphclks.h:max326_dma_enableclk]`
- `[max32690_periphclks.h:max326_usb_enableclk]`
- `[max32690_periphclks.h:max326_cpu1_enableclk]`

## Invariants
- `[max32690_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max32690_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[max32690_gpioirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max32690_gpioirq.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[max32690_periphclks.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[max32690_gpioirq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[max32690_gpioirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[max32690_gpioirq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[max32690_icc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[max32690_icc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
