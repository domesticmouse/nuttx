# hardware (`nuttx/arch/arm/src/imx9/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/imx9/hardware`, providing 23 header file(s) and 0 source file(s) (including `imx9_ccm.h`, `imx9_clock.h`, `imx9_dmamux.h`, `imx9_edma.h`).

## Subdirectories & Boundaries
- `imx93`: [./imx93/README.md](./imx93/README.md) - Hardware abstraction and architecture package for `imx93` under `nuttx/arch/arm/src/imx9/hardware/imx93`, providing 9 header file(s) and 0 source file(s) (including `imx93_ccm.h`, `imx93_clock.h`, `imx93_dmamux.h`, `imx93_edma.h`).
- `imx95`: [./imx95/README.md](./imx95/README.md) - Hardware abstraction and architecture package for `imx95` under `nuttx/arch/arm/src/imx9/hardware/imx95`, providing 7 header file(s) and 0 source file(s) (including `imx95_clock.h`, `imx95_dmamux.h`, `imx95_edma.h`, `imx95_gpio.h`).

## Interface
- `[imx9_flexcan.h:IMX9_CAN_MCR_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_CTRL1_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_TIMER_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_RXMGMASK_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_RX14MASK_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_RX15MASK_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_ECR_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_ESR1_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_IMASK2_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_IMASK1_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_IFLAG2_OFFSET]`
- `[imx9_flexcan.h:IMX9_CAN_IFLAG1_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_VERID_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_PARAM_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_CTRL_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_PIN_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_SHIFTSTAT_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_SHIFTERR_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_TIMSTAT_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_SHIFTSIEN_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_SHIFTEIEN_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_TIMIEN_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_SHIFTSDEN_OFFSET]`
- `[imx9_flexio.h:IMX9_FLEXIO_SHIFTSTATE_OFFSET]`
- `[imx9_flexspi.h:flexspi_type_s]`
- `[imx9_flexspi.h:IMX9_FLEXSPI_AHBBUFREGIONSTART0_OFFSET]`
- `[imx9_flexspi.h:IMX9_FLEXSPI_AHBBUFREGIONEND0_OFFSET]`
- `[imx9_flexspi.h:IMX9_FLEXSPI_AHBBUFREGIONSTART1_OFFSET]`
- `[imx9_flexspi.h:IMX9_FLEXSPI_AHBBUFREGIONEND1_OFFSET]`
- `[imx9_flexspi.h:IMX9_FLEXSPI_AHBBUFREGIONSTART2_OFFSET]`
- [./imx93/README.md](./imx93/README.md)
- [./imx95/README.md](./imx95/README.md)

## Invariants
- `[imx9_ccm.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_clock.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_dmamux.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_edma.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_gpio.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_iomuxc.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_memorymap.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_pinmux.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_rptun.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture
- `[imx9_rsctable.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture

## Side Effects
- None

## Verification
- Run: `make test`
