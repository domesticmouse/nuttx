# rtl8720f (`nuttx/arch/arm/src/rtl8720f`)

## Overview
Hardware abstraction and architecture package for `rtl8720f` (RTL8720F Chip Selection; RTL8720F Bring-up Options) under `nuttx/arch/arm/src/rtl8720f`, providing 12 header file(s) and 8 source file(s) (including `ameba_adc_chip.h`, `ameba_gpio_chip.h`, `ameba_i2c_chip.h`, `ameba_ipc.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/rtl8720f/hardware`, providing 1 header file(s) and 0 source file(s) (including `ameba_memorymap.h`).

## Interface
- `[ameba_adc_chip.h:AMEBA_ADC_NCHAN]`
- `[ameba_adc_chip.h:AMEBA_ADC_MAXLIST]`
- `[ameba_adc_chip.h:AMEBA_ADC_PINMUX_FID]`
- `[ameba_adc_chip.h:AMEBA_ADC_IRQ]`
- `[ameba_adc_chip.h:AMEBA_ADC_INIT_SIZE]`
- `[ameba_adc_chip.h:AMEBA_ADC_APBPERIPH]`
- `[ameba_adc_chip.h:AMEBA_ADC_APBPERIPH_CLK]`
- `[ameba_gpio_chip.h:AMEBA_GPIO_NPORTS]`
- `[ameba_gpio_chip.h:AMEBA_GPIO_PORT_IRQS]`
- `[ameba_gpio_chip.h:AMEBA_APBPERIPH_GPIO]`
- `[ameba_i2c_chip.h:AMEBA_NI2C]`
- `[ameba_i2c_chip.h:AMEBA_I2C_BASES]`
- `[ameba_i2c_chip.h:AMEBA_I2C_APBPERIPH]`
- `[ameba_i2c_chip.h:AMEBA_I2C_APBPERIPH_CLK]`
- `[ameba_i2c_chip.h:AMEBA_I2C_SCLFID]`
- `[ameba_i2c_chip.h:AMEBA_I2C_SDAFID]`
- `[ameba_i2c_chip.h:AMEBA_I2C_HAS_DMA_FIELDS]`
- `[ameba_ipc.h:ameba_ipc_initialize]`
- `[ameba_irq.h:AMEBA_IRQ_RESERVED]`
- `[ameba_irq.h:AMEBA_IRQ_NMI]`
- `[ameba_irq.h:AMEBA_IRQ_HARDFAULT]`
- `[ameba_irq.h:AMEBA_IRQ_MEMFAULT]`
- `[ameba_irq.h:AMEBA_IRQ_BUSFAULT]`
- `[ameba_irq.h:AMEBA_IRQ_USAGEFAULT]`
- `[ameba_irq.h:AMEBA_IRQ_SVCALL]`
- `[ameba_irq.h:AMEBA_IRQ_DBGMONITOR]`
- `[ameba_irq.h:AMEBA_IRQ_PENDSV]`
- `[ameba_irq.h:AMEBA_IRQ_SYSTICK]`
- `[ameba_irq.h:AMEBA_IRQ_FIRST]`
- `[ameba_pwm_chip.h:AMEBA_PWM_TIMER_IDX]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[ameba_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ameba_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[ameba_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ameba_loguart.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[ameba_ipc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_ipc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ameba_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ameba_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ameba_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ameba_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[ameba_loguart.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ameba_loguart.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ameba_loguart.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[ameba_start.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ameba_start.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
