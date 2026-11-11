# imxrt (`nuttx/arch/arm/src/imxrt`)

## Overview
Hardware abstraction and architecture package for `imxrt` (i.MX RT Configuration Options; Application Image Configuration) under `nuttx/arch/arm/src/imxrt`, providing 44 header file(s) and 62 source file(s) (including `chip.h`, `imxrt118x_ele.h`, `imxrt118x_start_cm7.h`, `imxrt118x_trdc.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/imxrt/hardware`, providing 37 header file(s) and 0 source file(s) (including `imxrt_adc.h`, `imxrt_adc_etc.h`, `imxrt_adc_ver1.h`, `imxrt_adc_ver2.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV8M_DCACHE_LINESIZE]`
- `[chip.h:ARMV8M_ICACHE_LINESIZE]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[imxrt118x_ele.h:imxrt118x_ele_init]`
- `[imxrt118x_ele.h:imxrt118x_ele_load_fw]`
- `[imxrt118x_ele.h:imxrt118x_ele_release_rdc]`
- `[imxrt118x_ele.h:imxrt118x_ele_read_common_fuse]`
- `[imxrt118x_ele.h:imxrt118x_ele_get_key]`
- `[imxrt118x_ele.h:imxrt118x_ele_get_events]`
- `[imxrt118x_ele.h:imxrt118x_ele_close_device]`
- `[imxrt118x_ele.h:imxrt118x_ele_get_lifecycle]`
- `[imxrt118x_ele.h:imxrt118x_ele_get_soc_revision]`
- `[imxrt118x_ele.h:imxrt118x_ele_auth_oem_ctnr]`
- `[imxrt118x_ele.h:imxrt118x_ele_release_container]`
- `[imxrt118x_ele.h:imxrt118x_ele_verify_image]`
- `[imxrt118x_ele.h:imxrt118x_ele_start_rng]`
- `[imxrt118x_ele.h:imxrt118x_ele_get_trng_state]`
- `[imxrt118x_ele.h:imxrt118x_ele_get_random]`
- `[imxrt118x_ele.h:imxrt118x_ele_commit]`
- `[imxrt118x_ele.h:imxrt118x_ele_enable_apc]`
- `[imxrt118x_ele.h:imxrt118x_ele_voltage_change_start]`
- `[imxrt118x_ele.h:imxrt118x_ele_voltage_change_finish]`
- `[imxrt118x_ele.h:imxrt118x_ele_check_fw_version]`
- `[imxrt118x_start_cm7.h:imxrt118x_prepare_cm7]`
- `[imxrt118x_start_cm7.h:imxrt118x_start_cm7]`
- `[imxrt118x_trdc.h:imxrt118x_trdc_config]`
- `[imxrt118x_trdc.h:imxrt118x_trdc_init]`
- `[imxrt118x_trdc.h:trdc_glbac_config]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[imxrt_hprtc.h:#error]` Compile-time guard: CONFIG_RTC_DATETIME should not be selected with this driver
- `[imxrt_lpsrtc.h:#error]` Compile-time guard: CONFIG_RTC_DATETIME should not be selected with this driver
- `[imxrt_serial.h:#error]` Compile-time guard: IMXRT LPUART receive or transmit DMA requires CONFIG_IMXRT_EDMA
- `[imxrt106x_flash.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imxrt117x_daisy.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imxrt118x_ele.c:#error]` Compile-time configuration constraint: IMXRT_ELE_FW_ABS_PATH must be set via CFLAGS
- `[imxrt_adc_ver1.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imxrt_adc_ver1.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[imxrt_adc_ver2.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imxrt_adc_ver2.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[imxrt_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imxrt_allocateheap.c:#error]` Compile-time configuration constraint: IMXRT_ITCM must be divisible by 32

## Side Effects
- `[imxrt106x_flash.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imxrt117x_daisy.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imxrt118x_ele.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imxrt118x_ele.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imxrt118x_ele.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[imxrt118x_ele.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[imxrt118x_start_cm7.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imxrt118x_start_cm7.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[imxrt118x_start_cm7.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imxrt118x_start_cm7.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[imxrt118x_trdc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imxrt118x_trdc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
