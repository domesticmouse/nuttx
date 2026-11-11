# am67 (`nuttx/arch/arm/src/am67`)

## Overview
Hardware abstraction and architecture package for `am67` (AM67 Configuration Options) under `nuttx/arch/arm/src/am67`, providing 13 header file(s) and 13 source file(s) (including `am67_ecap.h`, `am67_ecap_hw.h`, `am67_gpio.h`, `am67_i2c.h`).

## Interface
- `[am67_ecap.h:am67_ecap_init]`
- `[am67_ecap.h:am67_ecapinitialize]`
- `[am67_ecap.h:am67_ecapdev_initialize]`
- `[am67_ecap_hw.h:AM67_ECAP0_BASE]`
- `[am67_ecap_hw.h:AM67_ECAP1_BASE]`
- `[am67_ecap_hw.h:AM67_ECAP2_BASE]`
- `[am67_ecap_hw.h:AM67_ECAP_PID_OFFSET]`
- `[am67_ecap_hw.h:AM67_ECAP_TSCNT_OFFSET]`
- `[am67_ecap_hw.h:AM67_ECAP_CNTPHS_OFFSET]`
- `[am67_ecap_hw.h:AM67_ECAP_CAP1_OFFSET]`
- `[am67_ecap_hw.h:AM67_ECAP_CAP2_OFFSET]`
- `[am67_ecap_hw.h:AM67_ECAP_CAP3_OFFSET]`
- `[am67_ecap_hw.h:AM67_ECAP_CAP4_OFFSET]`
- `[am67_ecap_hw.h:AM67_ECAP_ECCTL_OFFSET]`
- `[am67_ecap_hw.h:AM67_ECAP_ECINT_EN_FLG_OFFSET]`
- `[am67_gpio.h:am67_gpio_hat]`
- `[am67_gpio.h:am67_configgpio]`
- `[am67_gpio.h:am67_gpiowrite]`
- `[am67_gpio.h:am67_gpioread]`
- `[am67_gpio.h:am67_sensors_power_enable]`
- `[am67_gpio.h:am67_gpio_id_e]`
- `[am67_gpio.h:am67_gpio_t]`
- `[am67_gpio.h:GPIO_OUTPUT]`
- `[am67_gpio.h:GPIO_INPUT]`
- `[am67_gpio.h:AM67_GPIO_OLDI0_A0P]`
- `[am67_gpio.h:AM67_GPIO_OLDI0_A0N]`
- `[am67_gpio.h:AM67_GPIO_HAT_CS1]`
- `[am67_gpio.h:AM67_GPIO_HAT_CS3]`
- `[am67_gpio.h:AM67_GPIO_MCU0_PIN12]`
- `[am67_gpio.h:AM67_GPIO_HAT_CS2]`

## Invariants
- `[am67_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[am67_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[am67_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[am67_i2c.c:#error]` Compile-time configuration constraint: I2C slave logic is not supported yet for AM67
- `[am67_mcspi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[am67_pwm.c:#error]` Compile-time configuration constraint: AM67 EPWM requires CONFIG_PWM_NCHANNELS >= 2
- `[am67_rptun.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[am67_timer.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[am67_ecap.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am67_ecap.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am67_i2c.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am67_i2c.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[am67_i2c.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am67_i2c.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[am67_i2c.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[am67_i2c.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[am67_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[am67_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[am67_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[am67_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
