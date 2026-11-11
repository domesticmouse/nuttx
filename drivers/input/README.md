# Input Device Drivers (`drivers/input`)

## Overview
Provides the NuttX input subsystem upper-half character drivers (touchscreen, keyboard, mouse, button, analog/digital joystick, force-feedback/haptics, and `uinput` virtual/RPMsg input devices) along with lower-half hardware drivers for resistive/capacitive touchscreens, keypads, joysticks, haptic controllers, and VirtIO/Goldfish input event sources.

## Interface
- `touchscreen_upper.c:touch_register`, `touchscreen_upper.c:touch_unregister`, `touchscreen_upper.c:touch_event` - Upper-half character driver and event injection API for touchscreen devices (`touchscreen_upper.c:touch_upperhalf_s`).
- `keyboard_upper.c:keyboard_register`, `keyboard_upper.c:keyboard_unregister`, `keyboard_upper.c:keyboard_event`, `virtio_key_decode.c:keyboard_translate_virtio_code` - Upper-half keyboard character driver (`keyboard_upper.c:keyboard_upperhalf_s`) and VirtIO keycode translator.
- `mouse_upper.c:mouse_register`, `mouse_upper.c:mouse_unregister`, `mouse_upper.c:mouse_event` - Upper-half mouse character driver (`mouse_upper.c:mouse_upperhalf_s`).
- `button_upper.c:btn_register`, `button_lower.c:btn_lower_initialize`, `sbutton.c:sbutton_register` - Upper-half and generic lower-half button drivers (`button_upper.c:btn_upperhalf_s`) plus single-button switch driver.
- `ajoystick.c:ajoy_register`, `djoystick.c:djoy_register`, `nunchuck.c:nunchuck_register` - Analog joystick (`ajoystick.c:ajoy_upperhalf_s`), discrete joystick (`djoystick.c:djoy_upperhalf_s`), and Wii Nunchuck I2C joystick drivers.
- `ff_upper.c:ff_register`, `ff_upper.c:ff_unregister`, `ff_upper.c:ff_event`, `ff_dummy.c:ff_dummy_initialize`, `aw86225.c:aw86225_initialize` - Force-feedback (haptic) upper-half driver (`ff_upper.c:ff_upperhalf_s`), dummy test driver, and Awinic AW86225 LRA haptic driver.
- `uinput.c:uinput_touch_initialize`, `uinput.c:uinput_keyboard_initialize`, `uinput.c:uinput_mouse_initialize`, `uinput.c:uinput_button_initialize`, `goldfish_events.c:goldfish_events_register` - Virtual user-space/RPMsg input devices and QEMU Goldfish input event driver.
- `ads7843e.c:ads7843e_register`, `cypress_mbr3108.c:cypress_mbr3108_register`, `ft5x06.c:ft5x06_register`, `gt9xx.c:gt9xx_register`, `kmatrix.c:kmatrix_register`, `kmatrix_i2c.c:kmatrix_i2c_register`, `max11802.c:max11802_register`, `mpr121.c:mpr121_register`, `mxt.c:mxt_register`, `spq10kbd.c:spq10kbd_register`, `st7123.c:st7123_register`, `stmpe811_tsc.c:stmpe811_register`, `stmpe811_adc.c:stmpe811_adcinitialize`, `stmpe811_gpio.c:stmpe811_gpioconfig`, `stmpe811_temp.c:stmpe811_tempinitialize`, `tsc2007.c:tsc2007_register` - Hardware drivers for SPI/I2C touch controllers, capacitive sensors, and matrix keypads.

## Invariants
- Upper-half event ring buffers (`circbuf_s`) are per-open-instance (`touch_openpriv_s`, `keyboard_opriv_s`, `mouse_openpriv_s`), requiring `nums > 0` during registration (`touchscreen_upper.c:touch_register`, `keyboard_upper.c:keyboard_register`, `mouse_upper.c:mouse_register`).
- Hardware lower halves assert valid bus handles (`i2c != NULL` or `spi != NULL`) and board configuration callbacks (`config != NULL`) during registration (`ads7843e.c:ads7843e_register`, `ft5x06.c:ft5x06_register`, `spq10kbd.c:spq10kbd_register`, `tsc2007.c:tsc2007_register`).

## Side Effects
- Registers and unregisters input character devices under `/dev` via `register_driver` and `unregister_driver` (`touchscreen_upper.c:touch_register`, `keyboard_upper.c:keyboard_register`, `mouse_upper.c:mouse_register`, `button_upper.c:btn_register`, `ff_upper.c:ff_register`).
- Performs I2C (`I2C_TRANSFER`) and SPI (`SPI_SEND`, `SPI_EXCHANGE`) bus transactions to sample touch/key coordinates and program haptic waveforms (`ft5x06.c:ft5x06_register`, `ads7843e.c:ads7843e_register`, `aw86225.c:aw86225_initialize`).
- Schedules interrupt bottom-halves and polling timers via `work_queue` and `wd_start`, synchronizes state via `nxmutex_lock` and `enter_critical_section`, wakes blocked readers via `nxsem_post` and `poll_notify`, and bridges cross-core input events via `rpmsg_register_callback` (`uinput.c:uinput_touch_initialize`).

## Verification
- Run: `make test`
