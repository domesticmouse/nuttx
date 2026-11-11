# hardware (`nuttx/arch/arm/src/mcx-nxxx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/mcx-nxxx/hardware`, providing 13 header file(s) and 0 source file(s) (including `nxxx_clock.h`, `nxxx_flexcomm.h`, `nxxx_fmu.h`, `nxxx_gdet.h`).

## Subdirectories & Boundaries
- `n236`: [./n236/README.md](./n236/README.md) - Hardware abstraction and architecture package for `n236` under `nuttx/arch/arm/src/mcx-nxxx/hardware/n236`, providing 3 header file(s) and 0 source file(s) (including `n236_clock.h`, `n236_gpio.h`, `n236_memorymap.h`).

## Interface
- `[nxxx_clock.h:clock_gate_reg_s]`
- `[nxxx_clock.h:clock_regs_s]`
- `[nxxx_clock.h:PERIPH_CLOCK]`
- `[nxxx_clock.h:CLOCK_GATE]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM_PSELID_OFFSET]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM_PID_OFFSET]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM0_PSELID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM0_PID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM1_PSELID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM1_PID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM2_PSELID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM2_PID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM3_PSELID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM3_PID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM4_PSELID]`
- `[nxxx_flexcomm.h:NXXX_FLEXCOMM4_PID]`
- `[nxxx_fmu.h:ARCH_ARM_SRC_MCX_NXXX_HARDWARE_NXXX_FMU_H]`
- `[nxxx_fmu.h:NXXX_FMU_FSTAT]`
- `[nxxx_fmu.h:NXXX_FMU_FCNFG]`
- `[nxxx_fmu.h:NXXX_FMU_FCTRL]`
- `[nxxx_fmu.h:NXXX_FMU_FCCOB0]`
- `[nxxx_fmu.h:NXXX_FMU_FCCOB1]`
- `[nxxx_fmu.h:NXXX_FMU_FCCOB2]`
- `[nxxx_fmu.h:NXXX_FMU_FCCOB3]`
- `[nxxx_fmu.h:NXXX_FMU_FCCOB4]`
- `[nxxx_fmu.h:NXXX_FMU_FCCOB5]`
- `[nxxx_fmu.h:NXXX_FMU_FCCOB6]`
- `[nxxx_fmu.h:NXXX_FMU_FCCOB7]`
- `[nxxx_gdet.h:NXXX_GDET_ENABLE1_OFFSET]`
- `[nxxx_gdet.h:NXXX_GDET0_ENABLE1]`
- [./n236/README.md](./n236/README.md)

## Invariants
- `[nxxx_clock.h:#error]` Compile-time guard: Unrecognized NXXx architecture
- `[nxxx_gpio.h:#error]` Compile-time guard: Unrecognized NXXx architecture
- `[nxxx_memorymap.h:#error]` Compile-time guard: Unrecognized NXXx architecture

## Side Effects
- None

## Verification
- Run: `make test`
