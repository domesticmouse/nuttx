# tiva (`nuttx/arch/arm/src/tiva`)

## Overview
Hardware abstraction and architecture package for `tiva` (Tiva/Stellaris Configuration Options; Tiva/Stellaris Peripheral Support) under `nuttx/arch/arm/src/tiva`, providing 23 header file(s) and 0 source file(s) (including `chip.h`, `tiva_adc.h`, `tiva_can.h`, `tiva_chipinfo.h`).

## Subdirectories & Boundaries
- `cc13xx`: [./cc13xx/README.md](./cc13xx/README.md) - Hardware abstraction and architecture package for `cc13xx` under `nuttx/arch/arm/src/tiva/cc13xx`, providing 8 header file(s) and 13 source file(s) (including `cc13x0_rom.h`, `cc13x2_aux_sysif.h`, `cc13x2_cc26x2_v1_rom.h`, `cc13x2_cc26x2_v2_rom.h`).
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/arm/src/tiva/common`, providing 2 header file(s) and 26 source file(s) (including `lmxx_tm4c_enableclks.h`, `lmxx_tm4c_enablepwr.h`, `lm4xx_tm3c_sysctrl.c`, `lmxx_tm4c_gpioirq.c`).
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/tiva/hardware`, providing 37 header file(s) and 0 source file(s) (including `tiva_adc.h`, `tiva_adi2_refsys.h`, `tiva_adi3_refsys.h`, `tiva_adi4_aux.h`).
- `lm`: [./lm/README.md](./lm/README.md) - Hardware abstraction and architecture package for `lm` under `nuttx/arch/arm/src/tiva/lm`, providing 2 header file(s) and 3 source file(s) (including `lm3s_gpio.h`, `lm4f_gpio.h`, `lm3s_ethernet.c`, `lm3s_gpio.c`).
- `tm4c`: [./tm4c/README.md](./tm4c/README.md) - Hardware abstraction and architecture package for `tm4c` under `nuttx/arch/arm/src/tiva/tm4c`, providing 1 header file(s) and 3 source file(s) (including `tm4c_gpio.h`, `tm4c129_sysctrl.c`, `tm4c_ethernet.c`, `tm4c_gpio.c`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[tiva_adc.h:tiva_adc_initialize]`
- `[tiva_adc.h:tiva_adc_lock]`
- `[tiva_adc.h:tiva_adc_unlock]`
- `[tiva_adc.h:tiva_adc_one_time_init]`
- `[tiva_adc.h:tiva_adc_configure]`
- `[tiva_adc.h:tiva_adc_sse_cfg]`
- `[tiva_adc.h:tiva_adc_step_cfg]`
- `[tiva_adc.h:tiva_adc_get_trigger]`
- `[tiva_adc.h:tiva_adc_get_ain]`
- `[tiva_adc.h:tiva_adc_irq_attach]`
- `[tiva_adc.h:tiva_adc_irq_detach]`
- `[tiva_adc.h:tiva_adc_getirq]`
- `[tiva_adc.h:tiva_adc_enable]`
- `[tiva_adc.h:tiva_adc_clock]`
- `[tiva_adc.h:tiva_adc_vref]`
- `[tiva_adc.h:tiva_adc_sample_rate]`
- `[tiva_adc.h:tiva_adc_proc_trig]`
- `[tiva_adc.h:tiva_adc_int_status]`
- `[tiva_adc.h:tiva_adc_sse_enable]`
- `[tiva_adc.h:tiva_adc_sse_trigger]`
- `[tiva_adc.h:tiva_adc_sse_pwm_trig]`
- `[tiva_adc.h:tiva_adc_sse_int_enable]`
- `[tiva_adc.h:tiva_adc_sse_int_status]`
- `[tiva_adc.h:tiva_adc_sse_clear_int]`
- `[tiva_adc.h:tiva_adc_sse_data]`
- `[tiva_adc.h:tiva_adc_sse_priority]`
- `[tiva_adc.h:tiva_adc_sse_register_chn]`
- `[tiva_adc.h:tiva_adc_sse_differential]`
- `[tiva_adc.h:tiva_adc_sse_sample_hold_time]`
- [./cc13xx/README.md](./cc13xx/README.md)
- [./common/README.md](./common/README.md)
- [./hardware/README.md](./hardware/README.md)
- [./lm/README.md](./lm/README.md)
- [./tm4c/README.md](./tm4c/README.md)

## Invariants
- `[tiva_adc.h:#error]` Compile-time guard: TIVA_tiva_adc_clock: unsupported architecture
- `[tiva_enableclks.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink clock controls
- `[tiva_enablepwr.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink power controls
- `[tiva_gpio.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink GPIO

## Side Effects
- `[tiva_chipinfo.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[tiva_periphrdy.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[tiva_timer.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
