# Field-Oriented Control (FOC) Motor Interfaces (`include/nuttx/motor/foc`)

## Overview
Defines the kernel upper-half, lower-half, power-stage, and gate-driver interfaces for Field-Oriented Control (FOC) multi-phase motor control in NuttX. Includes fixed/floating-point duty cycle conversions and device structures (`foc.h`), lower-half hardware operations and callbacks (`foc_lower.h`), power stage abstraction (`foc_pwr.h`), simulated FOC device support (`foc_dummy.h`), and the TI DRV8301 3-phase gate driver interface (`drv8301.h`).

## Interface
- `foc.h:struct foc_dev_s`, `foc.h:struct foc_cfg_s`, `foc.h:struct foc_state_s`, `foc.h:struct foc_params_s`, `foc.h:struct foc_info_s`, `foc.h:struct foc_info_hw_s`, `foc.h:enum foc_fault_e`, `foc.h:foc_current_t`, `foc.h:foc_voltage_t`, `foc.h:foc_duty_t`, `foc.h:foc_register`, `foc.h:FOCDUTY_FROM_FLOAT`, `foc.h:FOCDUTY_TO_FLOAT`
- `foc_lower.h:struct foc_lower_s`, `foc_lower.h:struct foc_lower_ops_s`, `foc_lower.h:struct foc_callbacks_s`, `foc_lower.h:enum foc_trace_type_e`, `foc_lower.h:FOC_OPS_CONFIGURE`, `foc_lower.h:FOC_OPS_SETUP`, `foc_lower.h:FOC_OPS_SHUTDOWN`, `foc_lower.h:FOC_OPS_START`, `foc_lower.h:FOC_OPS_PWMOFF`, `foc_lower.h:FOC_OPS_DUTY`
- `foc_pwr.h:struct focpwr_dev_s`, `foc_pwr.h:struct focpwr_ops_s`, `foc_pwr.h:focpwr_initialize`
- `foc_dummy.h:foc_dummy_initialize`, `foc_dummy.h:foc_dummy_update`
- `drv8301.h:struct drv8301_ops_s`, `drv8301.h:struct drv8301_cfg_s`, `drv8301.h:struct drv8301_board_s`, `drv8301.h:enum drv8301_gatecurr_e`, `drv8301.h:enum drv8301_gain_e`, `drv8301.h:enum drv8301_pwmmode_e`, `drv8301.h:drv8301_register`

## Invariants
- `foc_lower.h` may only be included in kernel context (`#ifndef __KERNEL__` triggers a preprocessor error).
- Phase current (`foc.h:struct foc_state_s`), voltage, and duty cycle (`foc.h:struct foc_params_s`) arrays are sized to `CONFIG_MOTOR_FOC_PHASES`.

## Side Effects
- `foc.h:foc_register` and `drv8301.h:drv8301_register` register FOC character devices and bind power-stage drivers to `foc.h:struct foc_dev_s`.
- Lower-half operations (`foc_lower.h:struct foc_lower_ops_s`) and DRV8301 callbacks (`drv8301.h:struct drv8301_ops_s`) configure PWM timers, ADC phase current sampling, SPI gate driver registers, and fault interrupts.

## Verification
- Run: `make test`
