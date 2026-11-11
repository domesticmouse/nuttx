# hardware (`nuttx/arch/arm/src/tiva/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/tiva/hardware`, providing 37 header file(s) and 0 source file(s) (including `tiva_adc.h`, `tiva_adi2_refsys.h`, `tiva_adi3_refsys.h`, `tiva_adi4_aux.h`).

## Subdirectories & Boundaries
- `cc13x0`: [./cc13x0/README.md](./cc13x0/README.md) - Hardware abstraction and architecture package for `cc13x0` under `nuttx/arch/arm/src/tiva/hardware/cc13x0`, providing 24 header file(s) and 0 source file(s) (including `cc13x0_adi2_refsys.h`, `cc13x0_adi3_refsys.h`, `cc13x0_adi4_aux.h`, `cc13x0_aon_batmon.h`).
- `cc13x2_cc26x2`: [./cc13x2_cc26x2/README.md](./cc13x2_cc26x2/README.md) - Hardware abstraction and architecture package for `cc13x2_cc26x2` under `nuttx/arch/arm/src/tiva/hardware/cc13x2_cc26x2`, providing 23 header file(s) and 0 source file(s) (including `cc13x2_cc26x2_adi2_refsys.h`, `cc13x2_cc26x2_adi3_refsys.h`, `cc13x2_cc26x2_adi4_aux.h`, `cc13x2_cc26x2_aon_batmon.h`).
- `lm`: [./lm/README.md](./lm/README.md) - Hardware abstraction and architecture package for `lm` under `nuttx/arch/arm/src/tiva/hardware/lm`, providing 14 header file(s) and 0 source file(s) (including `lm3s_ethernet.h`, `lm3s_flash.h`, `lm3s_gpio.h`, `lm3s_memorymap.h`).
- `tm4c`: [./tm4c/README.md](./tm4c/README.md) - Hardware abstraction and architecture package for `tm4c` under `nuttx/arch/arm/src/tiva/hardware/tm4c`, providing 13 header file(s) and 0 source file(s) (including `tm4c123_gpio.h`, `tm4c123_i2c.h`, `tm4c123_sysctrl.h`, `tm4c123_timer.h`).

## Interface
- `[tiva_adc.h:TIVA_ADC_ACTSS_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_RIS_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_IM_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_ISC_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_OSTAT_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_EMUX_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_USTAT_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_TSSEL_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_SSPRI_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_SPC_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_PSSI_OFFSET]`
- `[tiva_adc.h:TIVA_ADC_SAC_OFFSET]`
- `[tiva_can.h:TIVA_CAN_NUM_IFACES]`
- `[tiva_can.h:TIVA_CAN_NUM_MBOXES]`
- `[tiva_can.h:TIVA_CAN_OFFSET_CTL]`
- `[tiva_can.h:TIVA_CAN_OFFSET_STS]`
- `[tiva_can.h:TIVA_CAN_OFFSET_ERR]`
- `[tiva_can.h:TIVA_CAN_OFFSET_BIT]`
- `[tiva_can.h:TIVA_CAN_OFFSET_INT]`
- `[tiva_can.h:TIVA_CAN_OFFSET_TST]`
- `[tiva_can.h:TIVA_CAN_OFFSET_BRPE]`
- `[tiva_can.h:TIVA_CAN_OFFSET_IFACE1_BASE]`
- `[tiva_can.h:TIVA_CAN_OFFSET_IF1CRQ]`
- `[tiva_can.h:TIVA_CAN_OFFSET_IF1CMSK]`
- `[tiva_eeprom.h:TIVA_EEPROM_EESIZE_OFFSET]`
- `[tiva_eeprom.h:TIVA_EEPROM_EEBLOCK_OFFSET]`
- `[tiva_eeprom.h:TIVA_EEPROM_EEOFFSET_OFFSET]`
- `[tiva_eeprom.h:TIVA_EEPROM_EERDWR_OFFSET]`
- `[tiva_eeprom.h:TIVA_EEPROM_EERDWRINC_OFFSET]`
- `[tiva_eeprom.h:TIVA_EEPROM_EEDONE_OFFSET]`
- [./cc13x0/README.md](./cc13x0/README.md)
- [./cc13x2_cc26x2/README.md](./cc13x2_cc26x2/README.md)
- [./lm/README.md](./lm/README.md)
- [./tm4c/README.md](./tm4c/README.md)

## Invariants
- `[tiva_adi2_refsys.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink ADI2 REFSYS
- `[tiva_adi3_refsys.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink ADI3 REFSYS
- `[tiva_adi4_aux.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink ADI4 AUX
- `[tiva_aon_batmon.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AON BATMON
- `[tiva_aon_ioc.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AON IOC
- `[tiva_aon_pmctl.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AON PMCTL
- `[tiva_aon_rtc.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AON RTC
- `[tiva_aon_sysctl.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AON SYSCTL
- `[tiva_aon_wuc.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AON WUC
- `[tiva_aux_smph.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AUX SMPH
- `[tiva_aux_sysif.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AUX SYSIF
- `[tiva_aux_wuc.h:#error]` Compile-time guard: Unsupported Tiva/Stellaris/SimpleLink AUX WUC

## Side Effects
- None

## Verification
- Run: `make test`
