# rtl8730e (`nuttx/arch/arm/src/rtl8730e`)

## Overview
Hardware abstraction and architecture package for `rtl8730e` (Realtek AmebaSmart (RTL8730E) Chip Selection) under `nuttx/arch/arm/src/rtl8730e`, providing 13 header file(s) and 13 source file(s) (including `ameba_adc_chip.h`, `ameba_gpio_chip.h`, `ameba_i2c_chip.h`, `ameba_pwm_chip.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/rtl8730e/hardware`, providing 2 header file(s) and 0 source file(s) (including `rtl8730e_loguart.h`, `rtl8730e_memorymap.h`).

## Interface
- `[ameba_adc_chip.h:AMEBA_ADC_NCHAN]`
- `[ameba_adc_chip.h:AMEBA_ADC_MAXLIST]`
- `[ameba_adc_chip.h:AMEBA_ADC_PINMUX_FID]`
- `[ameba_adc_chip.h:AMEBA_ADC_IRQ]`
- `[ameba_adc_chip.h:AMEBA_ADC_INIT_SIZE]`
- `[ameba_adc_chip.h:AMEBA_ADC_APBPERIPH]`
- `[ameba_adc_chip.h:AMEBA_ADC_APBPERIPH_CLK]`
- `[ameba_adc_chip.h:AMEBA_ADC_AUXCLK_PERIPH]`
- `[ameba_adc_chip.h:AMEBA_ADC_AUXCLK_CLK]`
- `[ameba_adc_chip.h:AMEBA_ADC_HAS_CLKDIV]`
- `[ameba_adc_chip.h:AMEBA_ADC_GET_CHNO]`
- `[ameba_adc_chip.h:AMEBA_ADC_GET_DATA]`
- `[ameba_gpio_chip.h:RTL8730E_GPIO_BASE]`
- `[ameba_gpio_chip.h:RTL8730E_GPIO_STRIDE]`
- `[ameba_gpio_chip.h:RTL8730E_GPIO_INT_STATUS]`
- `[ameba_gpio_chip.h:RTL8730E_GPIO_INT_EOI]`
- `[ameba_gpio_chip.h:AMEBA_GPIO_NPORTS]`
- `[ameba_gpio_chip.h:AMEBA_GPIO_PORT_IRQS]`
- `[ameba_gpio_chip.h:AMEBA_APBPERIPH_GPIO]`
- `[ameba_gpio_chip.h:AMEBA_APBPERIPH_GPIO_CLK]`
- `[ameba_i2c_chip.h:AMEBA_NI2C]`
- `[ameba_i2c_chip.h:AMEBA_I2C_BASES]`
- `[ameba_i2c_chip.h:AMEBA_I2C_APBPERIPH]`
- `[ameba_i2c_chip.h:AMEBA_I2C_APBPERIPH_CLK]`
- `[ameba_i2c_chip.h:AMEBA_I2C_SCLFID]`
- `[ameba_i2c_chip.h:AMEBA_I2C_SDAFID]`
- `[ameba_i2c_chip.h:AMEBA_I2C_NPPLL_HZ]`
- `[ameba_i2c_chip.h:AMEBA_I2C_CKD_GRP0]`
- `[ameba_i2c_chip.h:AMEBA_I2C_CKD_HBUS_SHIFT]`
- `[ameba_i2c_chip.h:AMEBA_I2C_CKD_HBUS_MASK]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[rtl8730e_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rtl8730e_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rtl8730e_pgalloc.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_PGPOOL_MAPPING must be selected
- `[rtl8730e_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rtl8730e_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[rtl8730e_flash_stubs.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[rtl8730e_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[rtl8730e_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rtl8730e_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rtl8730e_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rtl8730e_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rtl8730e_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
