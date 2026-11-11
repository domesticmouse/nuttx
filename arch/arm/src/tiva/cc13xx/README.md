# cc13xx (`nuttx/arch/arm/src/tiva/cc13xx`)

## Overview
Hardware abstraction and architecture package for `cc13xx` under `nuttx/arch/arm/src/tiva/cc13xx`, providing 8 header file(s) and 13 source file(s) (including `cc13x0_rom.h`, `cc13x2_aux_sysif.h`, `cc13x2_cc26x2_v1_rom.h`, `cc13x2_cc26x2_v2_rom.h`).

## Interface
- `[cc13x0_rom.h:uint32_t]`
- `[cc13x0_rom.h:rom_setup_coldreset_from_shutdown_cfg1]`
- `[cc13x0_rom.h:rom_setup_coldreset_from_shutdown_cfg2]`
- `[cc13x0_rom.h:rom_setup_coldreset_from_shutdown_cfg3]`
- `[cc13x0_rom.h:rom_setup_get_trim_anabypass_value1]`
- `[cc13x0_rom.h:rom_setup_get_trim_rcosc_lfrtunectuntrim]`
- `[cc13x0_rom.h:rom_setup_get_trim_xosc_hfibiastherm]`
- `[cc13x0_rom.h:rom_setup_get_trim_ampcompth1]`
- `[cc13x0_rom.h:rom_setup_get_trim_ampcompth2]`
- `[cc13x0_rom.h:rom_setup_get_trim_ampcompctrl]`
- `[cc13x0_rom.h:rom_setup_get_trim_dblrloopfilter_resetvoltage]`
- `[cc13x0_rom.h:rom_setup_get_trim_adcshmodeen]`
- `[cc13x0_rom.h:rom_setup_get_trim_adcshvbufen]`
- `[cc13x0_rom.h:rom_setup_get_trim_xosc_hfctrl]`
- `[cc13x0_rom.h:rom_setup_get_trim_xosc_hffaststart]`
- `[cc13x0_rom.h:rom_setup_get_trim_radc_extcfg]`
- `[cc13x0_rom.h:rom_setup_get_trim_rcosc_lfibiastrim]`
- `[cc13x0_rom.h:rom_setup_get_trim_lfregulator_cmirrwr_ratio]`
- `[cc13x0_rom.h:rom_setup_cachemode]`
- `[cc13x0_rom.h:rom_setup_aonrtc_subsecinc]`
- `[cc13x0_rom.h:hard_api_s]`
- `[cc13x0_rom.h:hard_api_t]`
- `[cc13x0_rom.h:ROM_HAPI_TABLE_ADDR]`
- `[cc13x0_rom.h:P_HARD_API]`
- `[cc13x0_rom.h:hapi_crc32]`
- `[cc13x0_rom.h:hapi_get_flashsize]`
- `[cc13x0_rom.h:hapi_get_chipid]`
- `[cc13x0_rom.h:hapi_reset_device]`
- `[cc13x0_rom.h:hapi_fletcher32]`
- `[cc13x0_rom.h:hapi_min]`

## Invariants
- `[cc13xx_prcm.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers
- `[cc13xx_chipinfo.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cc13xx_enableclks.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cc13xx_enablepwr.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[cc13xx_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[cc13xx_gpioirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[cc13xx_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[cc13xx_prcm.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[cc13x0_rom.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[cc13x0_rom.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[cc13xx_prcm.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[cc13xx_prcm.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[cc13xx_prcm.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[cc13x0_rom.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[cc13x0_rom.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[cc13x0_rom.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[cc13x0_rom.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[cc13x0_rom.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[cc13x0_trim.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[cc13x0_trim.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
