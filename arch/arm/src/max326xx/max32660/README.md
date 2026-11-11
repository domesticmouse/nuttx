# max32660 (`nuttx/arch/arm/src/max326xx/max32660`)

## Overview
Hardware abstraction and architecture package for `max32660` under `nuttx/arch/arm/src/max326xx/max32660`, providing 4 header file(s) and 10 source file(s) (including `max32660_clockconfig.h`, `max32660_dma.h`, `max32660_gpio.h`, `max32660_periphclks.h`).

## Interface
- `[max32660_clockconfig.h:clock_source_e]`
- `[max32660_clockconfig.h:clock_setup_s]`
- `[max32660_dma.h:max326_dma_channel]`
- `[max32660_dma.h:max326_dma_free]`
- `[max32660_dma.h:max326_dma_setup]`
- `[max32660_dma.h:max326_dma_append]`
- `[max32660_dma.h:max326_dmastart]`
- `[max32660_dma.h:max326_dmastop]`
- `[max32660_dma.h:max326_dmasample]`
- `[max32660_dma.h:max326_dmadump]`
- `[max32660_dma.h:max326_dmaregs_s]`
- `[max32660_dma.h:DMA_HANDLE]`
- `[max32660_gpio.h:max326_gpio_irqinitialize]`
- `[max32660_gpio.h:max326_gpio_config]`
- `[max32660_gpio.h:max326_gpio_irqconfig]`
- `[max32660_gpio.h:max326_gpio_write]`
- `[max32660_gpio.h:max326_gpio_read]`
- `[max32660_gpio.h:max326_gpio_irqdisable]`
- `[max32660_gpio.h:max326_gpio_irqenable]`
- `[max32660_gpio.h:max326_gpio_dump]`
- `[max32660_gpio.h:max326_pinset_t]`
- `[max32660_gpio.h:GPIO_FUNC_SHIFT]`
- `[max32660_gpio.h:GPIO_FUNC_MASK]`
- `[max32660_gpio.h:GPIO_INPUT]`
- `[max32660_gpio.h:GPIO_OUTPUT]`
- `[max32660_gpio.h:GPIO_ALT1]`
- `[max32660_gpio.h:GPIO_ALT2]`
- `[max32660_gpio.h:GPIO_ALT3]`
- `[max32660_gpio.h:GPIO_INTFE]`
- `[max32660_gpio.h:GPIO_INTRE]`

## Invariants
- `[max32660_clockconfig.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max32660_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max32660_dma.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[max32660_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max32660_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[max32660_gpioirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max32660_lowputc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max32660_lowputc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[max32660_rtc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max32660_rtc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[max32660_rtc.c:#error]` Compile-time configuration constraint: CONFIG_RTC_FREQUENCY is required for CONFIG_RTC_HIRES
- `[max32660_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[max32660_periphclks.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[max32660_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[max32660_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[max32660_dma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[max32660_dma.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[max32660_dma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[max32660_dma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[max32660_dma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[max32660_dma.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[max32660_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[max32660_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[max32660_gpioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
