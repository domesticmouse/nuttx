# Math Acceleration Drivers (`drivers/math`)

## Overview
Implements the upper-half character driver interface for hardware math accelerators, including CORDIC, Fast Fourier Transform (FFT), and Multi-Precision Integer (MPI) engines.

## Interface
- `[math.c:math_register]` - Registers a generic math accelerator character driver bound to a `struct math_config_s` lower-half configuration (`[math.c:math_upperhalf_s]`).
- `[math.c:cordic_register]` - Registers a CORDIC hardware accelerator character device when `[math.c:CONFIG_MATH_CORDIC]` is enabled.
- `[math.c:fft_register]` - Registers an FFT hardware accelerator character device when `[math.c:CONFIG_MATH_FFT]` is enabled.
- `[math.c:mpi_register]` - Registers an MPI hardware accelerator character device when `[math.c:CONFIG_MATH_MPI]` is enabled.

## Invariants
- All math operations are dispatched through `ioctl` (`[math.c:math_ioctl]`), while VFS `read` and `write` (`[math.c:math_read]`, `[math.c:math_write]`) are no-op stubs returning `0`.

## Side Effects
- Registers character devices in the VFS namespace via `[math.c:register_driver]` and delegates hardware computation to the lower-half `ioctl` callback.

## Verification
- Run: `make test`
