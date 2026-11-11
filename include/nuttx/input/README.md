# Input Devices Subsystem Headers (`include/nuttx/input`)

## Overview
Defines the NuttX human interface device (HID) and input subsystem, including upper-half character drivers and event ring buffers for touchscreens, keyboards, mice, discrete/analog joysticks, buttons, force-feedback (haptic) actuators, virtual user input (`uinput`), keycode/keysym encodings (NuttX keyboard codec, Linux/VirtIO `evdev` event codes, X11/XF86 keysyms), and hardware input controller drivers.

## Interface
- `touchscreen.h:touch_lowerhalf_s`, `touchscreen.h:touch_sample_s`, `touchscreen.h:touch_point_s`, `touchscreen.h:g_tscaldata_s`, `touchscreen.h:touch_register`, `touchscreen.h:touch_unregister`, `touchscreen.h:touch_event`, `touchscreen.h:TSIOC_SETCALIB`, `touchscreen.h:TSIOC_DOACALIB`, `touchscreen.h:TSIOC_GRAB` - Touchscreen upper/lower-half interface, multi-touch sample reporting, and calibration `ioctl` commands.
- `keyboard.h:keyboard_lowerhalf_s`, `keyboard.h:keyboard_event_s`, `keyboard.h:keyboard_register`, `keyboard.h:keyboard_unregister`, `keyboard.h:keyboard_event`, `keyboard.h:keyboard_translate_virtio_code` - Keyboard driver registration, event reporting, and VirtIO keycode translation.
- `kbd_codec.h:kbd_keycode_e`, `kbd_codec.h:kbd_getstate_s`, `kbd_codec.h:kbd_press`, `kbd_codec.h:kbd_release`, `kbd_codec.h:kbd_specpress`, `kbd_codec.h:kbd_specrel`, `kbd_codec.h:kbd_decode` - Keyboard stream encoding and decoding helpers.
- `mouse.h:mouse_lowerhalf_s`, `mouse.h:mouse_report_s`, `mouse.h:mouse_register`, `mouse.h:mouse_unregister`, `mouse.h:mouse_event`, `mouse.h:MSIOC_VENDOR` - Mouse upper/lower-half driver and sample reporting interface.
- `buttons.h:btn_lowerhalf_s`, `buttons.h:btn_notify_s`, `buttons.h:btn_pollevents_s`, `buttons.h:btn_register`, `buttons.h:btn_lower_initialize`, `buttons.h:BTNIOC_SUPPORTED`, `buttons.h:BTNIOC_POLLEVENTS`, `buttons.h:BTNIOC_REGISTER` - Button input character driver interface.
- `ajoystick.h:ajoy_lowerhalf_s`, `ajoystick.h:ajoy_sample_s`, `ajoystick.h:ajoy_register`, `djoystick.h:djoy_lowerhalf_s`, `djoystick.h:djoy_register`, `nunchuck.h:nunchuck_sample_s`, `nunchuck.h:nunchuck_register`, `xbox-controller.h:xbox_controller_buttonstate_s`, `ioctl.h:_DJOYIOC`, `ioctl.h:_AJOYIOC`, `ioctl.h:_NUNCHUCKIOC` - Analog/discrete joystick, Wii Nunchuck, and Xbox controller interfaces.
- `ff.h:ff_lowerhalf_s`, `ff.h:ff_effect`, `ff.h:ff_event_s`, `ff.h:ff_register`, `ff.h:ff_unregister`, `ff.h:ff_event`, `ff_dummy.h:ff_dummy_initialize`, `aw86225.h:aw86225_initialize` - Force-feedback / haptic actuator framework and AW86225 LRA haptic driver.
- `uinput.h:uinput_touch_initialize`, `uinput.h:uinput_keyboard_initialize`, `uinput.h:uinput_button_initialize`, `uinput.h:uinput_mouse_initialize`, `goldfish_events.h:goldfish_events_register` - Virtual user-space input injection (`uinput`) and Android Goldfish emulator input event drivers.
- `ads7843e.h:ads7843e_register`, `cypress_mbr3108.h:cypress_mbr3108_register`, `ft5x06.h:ft5x06_register`, `gt9xx.h:gt9xx_register`, `kmatrix.h:kmatrix_register`, `kmatrix.h:kmatrix_i2c_register`, `max11802.h:max11802_register`, `mpr121.h:mpr121_register`, `mxt.h:mxt_register`, `sbutton.h:sbutton_register`, `spq10kbd.h:spq10kbd_register`, `st7123.h:st7123_register`, `stmpe811.h:stmpe811_instantiate`, `stmpe811.h:stmpe811_register`, `tsc2007.h:tsc2007_register` - Hardware touchscreen, keypad matrix, capacitive touch, and multifunction controller drivers.
- `virtio-input-event-codes.h:EV_SYN`, `virtio-input-event-codes.h:EV_KEY`, `virtio-input-event-codes.h:EV_REL`, `virtio-input-event-codes.h:EV_ABS`, `x11_keysym.h:XK_MISCELLANY`, `x11_keysymdef.h:XK_VoidSymbol`, `x11_xf86keysym.h:XF86XK_ModeLock` - Standard Linux/VirtIO input event codes and X11/XF86 keysym definitions.

## Invariants
- `touchscreen.h:SIZEOF_TOUCH_SAMPLE_S(n)` must be used to size variable-length multi-touch `touch_sample_s` structures containing `n` touch points.
- Hardware touchscreen drivers (`ads7843e.h`, `ft5x06.h`, `max11802.h`, `mxt.h`, `stmpe811.h`, `tsc2007.h`) require `CONFIG_SCHED_WORKQUEUE` to defer SPI/I2C bus sampling out of interrupt context.

## Side Effects
- Upper-half registration routines (`touch_register`, `keyboard_register`, `mouse_register`, `btn_register`, `ajoy_register`, `djoy_register`, `ff_register`) allocate circular event buffers and create character device nodes in the VFS.
- Event notification functions (`touch_event`, `keyboard_event`, `mouse_event`, `ff_event`) push input samples to open file descriptors, wake blocked readers, and notify `poll()` waiters or registered `sigevent` signals.

## Verification
- Run: `make test`
