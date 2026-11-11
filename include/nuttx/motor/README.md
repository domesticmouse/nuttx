# Motor & Stepper Driver Interfaces (`include/nuttx/motor`)

## Overview
Defines upper-half, lower-half, and IC-specific driver interfaces for DC/BLDC/PMSM motors and stepper motors in NuttX. Includes the generic motor upper-half state machine, operating modes, feedback, and limits (`motor.h`, `motor_ioctl.h`), generic stepper motor upper-half job/status interfaces (`stepper.h`, `stepper_ioctl.h`), A4988 and DRV8825 stepper driver interfaces (`a4988.h`, `drv8825.h`), and the Field-Oriented Control (FOC) subpackage (`./foc/README.md`).

## Interface
- `./foc/README.md` - Field-Oriented Control (FOC) motor upper-half, lower-half, power stage, and gate driver interfaces
- `motor.h:struct motor_lowerhalf_s`, `motor.h:struct motor_ops_s`, `motor.h:struct motor_state_s`, `motor.h:struct motor_feedback_s`, `motor.h:struct motor_limits_s`, `motor.h:struct motor_params_s`, `motor.h:enum motor_opmode_e`, `motor.h:enum motor_state_e`, `motor.h:enum motor_fault_e`, `motor.h:enum motor_direction_e`, `motor.h:motor_register`
- `motor_ioctl.h:MTRIOC_START`, `motor_ioctl.h:MTRIOC_STOP`, `motor_ioctl.h:MTRIOC_GET_STATE`, `motor_ioctl.h:MTRIOC_CLEAR_FAULT`, `motor_ioctl.h:MTRIOC_SET_PARAMS`, `motor_ioctl.h:MTRIOC_SET_CONFIG`, `motor_ioctl.h:MTRIOC_GET_INFO`, `motor_ioctl.h:MTRIOC_SET_MODE`, `motor_ioctl.h:MTRIOC_SET_LIMITS`
- `stepper.h:struct stepper_lowerhalf_s`, `stepper.h:struct stepper_ops_s`, `stepper.h:struct stepper_status_s`, `stepper.h:struct stepper_job_s`, `stepper.h:enum stepper_state_e`, `stepper.h:enum stepper_fault_e`, `stepper.h:enum stepper_idle_e`, `stepper.h:stepper_register`
- `stepper_ioctl.h:STEPIOC_IDLE`, `stepper_ioctl.h:STEPIOC_CLEAR_FAULT`, `stepper_ioctl.h:STEPIOC_MICROSTEPPING`, `stepper_ioctl.h:STEPIOC_SET_CURRENT_POS`
- `a4988.h:struct a4988_ops_s`, `a4988.h:a4988_register`
- `drv8825.h:struct drv8825_ops_s`, `drv8825.h:drv8825_register`

## Invariants
- `motor.h:struct motor_limits_s` and `motor.h:struct motor_params_s` include a `lock` flag preventing concurrent modification once locked by the driver.
- Motor and stepper fault bitmasks (`motor.h:enum motor_fault_e`, `stepper.h:enum stepper_fault_e`) must be explicitly cleared via `fault_clear` / `clear` (`motor_ioctl.h:MTRIOC_CLEAR_FAULT`, `stepper_ioctl.h:STEPIOC_CLEAR_FAULT`) before resuming `MOTOR_STATE_RUN` or `STEPPER_STATE_RUN`.

## Side Effects
- `motor.h:motor_register`, `stepper.h:stepper_register`, `a4988.h:a4988_register`, and `drv8825.h:drv8825_register` create character device nodes in the VFS namespace.
- Invoking `motor.h:struct motor_ops_s` or `stepper.h:struct stepper_ops_s` callbacks actuates PWM bridges, GPIO step/direction/enable lines, and power stage hardware.

## Verification
- Run: `make test`
