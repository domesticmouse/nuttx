# libdsp

## Overview
Provides Digital Signal Processing (DSP) and motor control algorithms for NuttX in both single-precision floating-point (`float`/`f32`) and 16.16 fixed-point (`b16_t`) representations. Includes Field-Oriented Control (FOC), Space Vector Modulation (SVM3), Clarke and Park reference frame transforms, PID/PI controllers with saturation and anti-windup, sliding-mode/nonlinear-fluxlink/PLL/division motor angle and speed observers, Permanent Magnet Synchronous Motor (PMSM) physical simulation models, matrix arithmetic, and fast trigonometric/vector helpers.

## Interface
- `lib_avg.c:avg_filter_data_init`, `lib_avg.c:avg_filter`
- `lib_foc.c:foc_init`, `lib_foc.c:foc_vbase_update`, `lib_foc.c:foc_angle_update`, `lib_foc.c:foc_iabc_update`, `lib_foc.c:foc_voltage_control`, `lib_foc.c:foc_current_control`, `lib_foc.c:foc_vabmod_get`, `lib_foc.c:foc_vdq_mag_max_get`
- `lib_foc_b16.c:foc_init_b16`, `lib_foc_b16.c:foc_vbase_update_b16`, `lib_foc_b16.c:foc_angle_update_b16`, `lib_foc_b16.c:foc_iabc_update_b16`, `lib_foc_b16.c:foc_voltage_control_b16`, `lib_foc_b16.c:foc_current_control_b16`, `lib_foc_b16.c:foc_vabmod_get_b16`, `lib_foc_b16.c:foc_vdq_mag_max_get_b16`
- `lib_matrix.c:matrix_add`, `lib_matrix.c:matrix_sub`, `lib_matrix.c:matrix_mul`, `lib_matrix.c:matrix_mul_transpose`, `lib_matrix.c:matrix_transpose`, `lib_matrix.c:matrix_scalar_mul`, `lib_matrix.c:matrix_copy`, `lib_matrix.c:matrix_inv_3x3`
- `lib_misc.c:f_saturate`, `lib_misc.c:vector2d_mag`, `lib_misc.c:vector2d_saturate`, `lib_misc.c:dq_mag`, `lib_misc.c:dq_saturate`, `lib_misc.c:fast_sin`, `lib_misc.c:fast_cos`, `lib_misc.c:fast_sin2`, `lib_misc.c:fast_cos2`, `lib_misc.c:fast_atan2`, `lib_misc.c:angle_norm`, `lib_misc.c:angle_norm_2pi`, `lib_misc.c:phase_angle_update`
- `lib_misc_b16.c:f_saturate_b16`, `lib_misc_b16.c:vector2d_mag_b16`, `lib_misc_b16.c:vector2d_saturate_b16`, `lib_misc_b16.c:dq_mag_b16`, `lib_misc_b16.c:dq_saturate_b16`, `lib_misc_b16.c:fast_sin_b16`, `lib_misc_b16.c:fast_cos_b16`, `lib_misc_b16.c:fast_sin2_b16`, `lib_misc_b16.c:fast_cos2_b16`, `lib_misc_b16.c:fast_atan2_b16`, `lib_misc_b16.c:angle_norm_b16`, `lib_misc_b16.c:angle_norm_2pi_b16`, `lib_misc_b16.c:phase_angle_update_b16`
- `lib_motor.c:motor_openloop_init`, `lib_motor.c:motor_openloop`, `lib_motor.c:motor_openloop_angle_get`, `lib_motor.c:motor_angle_init`, `lib_motor.c:motor_angle_e_update`, `lib_motor.c:motor_angle_m_update`, `lib_motor.c:motor_angle_m_get`, `lib_motor.c:motor_angle_e_get`, `lib_motor.c:motor_phy_params_init`, `lib_motor.c:pmsm_phy_params_init`
- `lib_motor_b16.c:motor_openloop_init_b16`, `lib_motor_b16.c:motor_openloop_b16`, `lib_motor_b16.c:motor_openloop_angle_get_b16`, `lib_motor_b16.c:motor_angle_e_update_b16`, `lib_motor_b16.c:motor_angle_m_update_b16`, `lib_motor_b16.c:motor_angle_m_get_b16`, `lib_motor_b16.c:motor_angle_e_get_b16`, `lib_motor_b16.c:motor_phy_params_init_b16`, `lib_motor_b16.c:pmsm_phy_params_init_b16`
- `lib_observer.c:motor_sobserver_init`, `lib_observer.c:motor_aobserver_init`, `lib_observer.c:motor_aobserver_smo_init`, `lib_observer.c:motor_aobserver_smo`, `lib_observer.c:motor_sobserver_div_init`, `lib_observer.c:motor_sobserver_div`, `lib_observer.c:motor_aobserver_nfo_init`, `lib_observer.c:motor_aobserver_nfo`, `lib_observer.c:motor_sobserver_pll_init`, `lib_observer.c:motor_sobserver_pll`, `lib_observer.c:motor_sobserver_speed_get`, `lib_observer.c:motor_aobserver_angle_get`
- `lib_observer_b16.c:motor_sobserver_init_b16`, `lib_observer_b16.c:motor_aobserver_init_b16`, `lib_observer_b16.c:motor_aobserver_smo_init_b16`, `lib_observer_b16.c:motor_aobserver_smo_b16`, `lib_observer_b16.c:motor_sobserver_div_init_b16`, `lib_observer_b16.c:motor_sobserver_div_b16`, `lib_observer_b16.c:motor_aobserver_nfo_init_b16`, `lib_observer_b16.c:motor_aobserver_nfo_b16`, `lib_observer_b16.c:motor_sobserver_pll_init_b16`, `lib_observer_b16.c:motor_sobserver_pll_b16`, `lib_observer_b16.c:motor_sobserver_speed_get_b16`, `lib_observer_b16.c:motor_aobserver_angle_get_b16`
- `lib_pid.c:pid_controller_init`, `lib_pid.c:pi_controller_init`, `lib_pid.c:pid_saturation_set`, `lib_pid.c:pi_saturation_set`, `lib_pid.c:pi_antiwindup_enable`, `lib_pid.c:pi_ireset_enable`, `lib_pid.c:pid_integral_reset`, `lib_pid.c:pi_integral_reset`, `lib_pid.c:pi_controller`, `lib_pid.c:pid_controller`
- `lib_pid_b16.c:pid_controller_init_b16`, `lib_pid_b16.c:pi_controller_init_b16`, `lib_pid_b16.c:pid_saturation_set_b16`, `lib_pid_b16.c:pi_saturation_set_b16`, `lib_pid_b16.c:pi_antiwindup_enable_b16`, `lib_pid_b16.c:pi_ireset_enable_b16`, `lib_pid_b16.c:pid_integral_reset_b16`, `lib_pid_b16.c:pi_integral_reset_b16`, `lib_pid_b16.c:pi_controller_b16`, `lib_pid_b16.c:pid_controller_b16`
- `lib_pmsm_model.c:pmsm_model_initialize`, `lib_pmsm_model.c:pmsm_model_elec`, `lib_pmsm_model.c:pmsm_model_mech`
- `lib_pmsm_model_b16.c:pmsm_model_initialize_b16`, `lib_pmsm_model_b16.c:pmsm_model_elec_b16`, `lib_pmsm_model_b16.c:pmsm_model_mech_b16`
- `lib_svm.c:svm3`, `lib_svm.c:svm3_current_correct`, `lib_svm.c:svm3_init`
- `lib_svm_b16.c:svm3_b16`, `lib_svm_b16.c:svm3_current_correct_b16`, `lib_svm_b16.c:svm3_init_b16`
- `lib_transform.c:clarke_transform`, `lib_transform.c:inv_clarke_transform`, `lib_transform.c:park_transform`, `lib_transform.c:inv_park_transform`
- `lib_transform_b16.c:clarke_transform_b16`, `lib_transform_b16.c:inv_clarke_transform_b16`, `lib_transform_b16.c:park_transform_b16`, `lib_transform_b16.c:inv_park_transform_b16`

## Invariants
- Phase angle must be updated via `lib_foc.c:foc_angle_update` (or `lib_foc_b16.c:foc_angle_update_b16`) before calling `lib_foc.c:foc_iabc_update` or `lib_foc.c:foc_voltage_control`.
- Clarke and inverse Clarke transforms (`lib_transform.c:clarke_transform`, `lib_transform_b16.c:clarke_transform_b16`) assume a balanced three-phase system (`a + b + c = 0`) and non-power-invariant scaling (`k = 2/3`).
- Modulation voltage vectors passed to `lib_svm.c:svm3` and `lib_svm_b16.c:svm3_b16` must be normalized to magnitude in `[0.0, 1.0]`, and `s->sector` must remain within `[1, 6]`.
- `lib_pid.c:pid_saturation_set`, `lib_pid.c:pi_saturation_set`, and their `_b16` equivalents require `min < max` (`LIBDSP_DEBUGASSERT(min < max)`).
- Observer and open-loop periods (`per`), sample counts (`samples`), gains (`kslide`, `pll_kp`, `pll_ki`), and pole pairs (`p`) must be strictly positive (`LIBDSP_DEBUGASSERT`).

## Side Effects
- Mutates caller-provided DSP controller, observer, filter, SVM, and motor model state structures in place (`foc_data_f32_s`, `foc_data_b16_s`, `pid_controller_f32_t`, `pid_controller_b16_t`, `svm3_state_f32_s`, `svm3_state_b16_s`, `motor_aobserver_f32_s`, `motor_sobserver_f32_s`, `pmsm_model_f32_s`, etc.); performs no dynamic memory allocation, I/O, or locking.

## Verification
- Run: `make test`
