# ez80 (`nuttx/arch/z80/src/ez80`)

## Overview
Hardware abstraction and architecture package for `ez80` (ez80 Peripheral Support) under `nuttx/arch/z80/src/ez80`, providing 9 header file(s) and 14 source file(s) (including `chip.h`, `ez80_i2c.h`, `ez80_rtc.h`, `ez80_spi.h`).

## Interface
- `[chip.h:EZ80_C_FLAG]`
- `[chip.h:EZ80_N_FLAG]`
- `[chip.h:EZ80_PV_FLAG]`
- `[chip.h:EZ80_H_FLAG]`
- `[chip.h:EZ80_Z_FLAG]`
- `[chip.h:EZ80_S_FLAG]`
- `[ez80_i2c.h:ez80_i2cbus_initialize]`
- `[ez80_i2c.h:ez80_i2cbus_uninitialize]`
- `[ez80_i2c.h:I2C_SAR_GCE]`
- `[ez80_i2c.h:I2C_SAR_SLA_SHIFT]`
- `[ez80_i2c.h:I2C_SAR_SLA_MASK]`
- `[ez80_i2c.h:I2C_CTL_AAK]`
- `[ez80_i2c.h:I2C_CTL_IFLG]`
- `[ez80_i2c.h:I2C_CTL_STP]`
- `[ez80_i2c.h:I2C_CTL_STA]`
- `[ez80_i2c.h:I2C_CTL_ENAB]`
- `[ez80_i2c.h:I2C_CTL_IEN]`
- `[ez80_i2c.h:I2C_SR_SHIFT]`
- `[ez80_i2c.h:I2C_SR_MASK]`
- `[ez80_i2c.h:I2C_SR_BUSERR]`
- `[ez80_rtc.h:ez80_rtc_setdatetime]`
- `[ez80_rtc.h:ez80_rtc_lowerhalf]`
- `[ez80_rtc.h:ez80_rtc_setalarm]`
- `[ez80_rtc.h:ez80_rtc_rdalarm]`
- `[ez80_rtc.h:ez80_rtc_cancelalarm]`
- `[ez80_rtc.h:alm_setalarm_s]`
- `[ez80_rtc.h:EZ80_RTC_ASECEN]`
- `[ez80_rtc.h:EZ80_RTC_AMINEN]`
- `[ez80_rtc.h:EZ80_RTC_AHRSEN]`
- `[ez80_rtc.h:EZ80_RTC_ADOWEN]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Register definitions not provided for this chip
- `[ez80_emac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ez80_emac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ez80_emac.c:#error]` Compile-time configuration constraint: Work queue support is required in this configuration (CONFIG_SCHED_WORKQUEUE)
- `[ez80_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ez80_rtc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ez80_rtc.c:#error]` Compile-time configuration constraint: CONFIG_RTC_DATETIME must be set to use this driver
- `[ez80_rtc_lowerhalf.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ez80_rtc_lowerhalf.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ez80_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ez80_serial.c:#error]` Compile-time configuration constraint: No Rx FIFO trigger level
- `[ez80_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[ez80_emac.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ez80_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ez80_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[ez80_rtc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ez80_rtc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ez80_rtc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[ez80_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ez80_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ez80_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
