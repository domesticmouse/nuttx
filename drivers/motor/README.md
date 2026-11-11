# Motor Control Drivers (`drivers/motor`)

## Overview
Provides generic DC/BLDC motor and stepper motor upper-half character drivers, stepper microstepping lower-half drivers (A4988, DRV8825), and the Field-Oriented Control (FOC) subsystem.

## Interface
- `[motor.c:motor_register]` - Registers a generic motor control character device bound to `struct motor_lowerhalf_s` (`[motor.c:struct motor_upperhalf_s]`).
- `[stepper.c:stepper_register]` - Registers a stepper motor character device bound to `struct stepper_lowerhalf_s` (`[stepper.c:struct stepper_upperhalf_s]`).
- `[a4988.c:a4988_register]` - Registers an Allegro A4988 microstepping bipolar stepper motor driver (`[a4988.c:struct a4988_dev_s]`).
- `[drv8825.c:drv8825_register]` - Registers a TI DRV8825 stepper motor controller driver (`[drv8825.c:struct drv8825_dev_s]`).
- Subdirectories:
  - [./foc/README.md](./foc/README.md) - Field-Oriented Control (FOC) character driver framework and 3-phase gate drivers.

## Invariants
- Device open/close lifecycle in `[motor.c:struct motor_upperhalf_s]` and `[stepper.c:struct stepper_upperhalf_s]` is serialized by `closelock` (`nxmutex_lock`) and capped at 255 concurrent opens (`uint8_t ocount`).

## Side Effects
- Registers VFS character device nodes (`[motor.c:register_driver]`, `[stepper.c:register_driver]`) and actuates physical motor GPIO/PWM hardware through lower-half callbacks.

## Verification
- Run: `make test`
