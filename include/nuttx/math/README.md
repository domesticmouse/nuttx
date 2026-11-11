# Hardware Math Accelerators Subsystem Headers (`include/nuttx/math`)

## Overview
Defines the NuttX hardware math acceleration framework, providing upper-half character drivers, `ioctl` interfaces, and lower-half operation tables for Coordinate Rotation Digital Computer (`cordic`), Fast Fourier Transform / Discrete Cosine Transform (`fft`), and Multi-Precision Integer (`mpi`) accelerators.

## Interface
- `math.h:math_config_s`, `math.h:math_register`, `math_ioctl.h:MATHIOC_CORDIC_CALC`, `math_ioctl.h:MATHIOC_FFT_CALC`, `math_ioctl.h:MATHIOC_MPI_CALC` - Composite math device configuration, registration, and `ioctl` command codes.
- `cordic.h:cordic_calc_func_e`, `cordic.h:cordic_calc_s`, `cordic.h:cordic_ops_s`, `cordic.h:cordic_lowerhalf_s`, `cordic.h:cordic_register`, `cordic.h:ftoq31`, `cordic.h:q31tof`, `cordic.h:b16toq31`, `cordic.h:q31tob16` - CORDIC trigonometric/hyperbolic/logarithmic accelerator interface and Q1.31 fixed-point conversion macros.
- `fft.h:fft_type`, `fft.h:fft_calc_s`, `fft.h:fft_ops_s`, `fft.h:fft_lowerhalf_s`, `fft.h:fft_register` - FFT and DCT Type II/III/IV hardware accelerator interface.
- `mpi.h:mpi_calc_func_e`, `mpi.h:mpiparam`, `mpi.h:mpi_calc_s`, `mpi.h:mpi_ops_s`, `mpi.h:mpi_lowerhalf_s`, `mpi.h:mpi_register`, `mpi.h:MPI_MAXPARAM` - Multi-precision integer modular arithmetic accelerator interface.

## Invariants
- `mpi.h:mpi_calc_s.param` holds at most `MPI_MAXPARAM` (`4`) multi-precision integer operands per calculation.
- When `CONFIG_MATH_CORDIC_USE_Q31` is enabled, `cordic.h:cordic_num_t` is `int32_t` in Q1.31 format (`[-1, 1)` mapped to `[-2^31, 2^31 - 1]`).

## Side Effects
- `math.h:math_register`, `cordic.h:cordic_register`, `fft.h:fft_register`, and `mpi.h:mpi_register` register character devices in the VFS.
- Invoking `calc` callbacks on `cordic_ops_s`, `fft_ops_s`, or `mpi_ops_s` programs hardware math co-processor registers and writes computed results into caller-provided buffers (`cordic_calc_s`, `fft_calc_s`, `mpi_calc_s`).

## Verification
- Run: `make test`
