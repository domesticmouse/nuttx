# NuttX Pin Control Subsystem (`include/nuttx/pinctrl`)

## Overview
Defines the upper-half and lower-half driver interfaces and ioctl commands for the NuttX Pin Control (`pinctrl`) subsystem, enabling runtime configuration of SoC pin multiplexing functions, drive strength, slew rate, pull-up/pull-down resistors, Schmitt trigger inputs, and GPIO selection.

## Interface
- `pinctrl.h:pinctrl_dev_s`, `pinctrl.h:pinctrl_ops_s` - Pin control device structure and lower-half operations vtable (`set_function`, `set_strength`, `set_driver`, `set_slewrate`, `select_gpio`, `get_pad`).
- `pinctrl.h:pinctrl_drivertype_e`, `pinctrl.h:pinctrl_param_s`, `pinctrl.h:pinctrl_padinfo_s`, `pinctrl.h:pinctrl_getpad_s`, `pinctrl.h:pinctrl_padname_s` - Parameter structures and driver type enumerations for pad configuration and inspection.
- `pinctrl.h:pinctrl_register`, `pinctrl.h:pinctrl_unregister` - Character driver registration and unregistration functions for `/dev/pinctrlN` nodes.
- `pinctrl.h:PINCTRLC_SETFUNCTION`, `pinctrl.h:PINCTRLC_SETSTRENGTH`, `pinctrl.h:PINCTRLC_SETDRIVER`, `pinctrl.h:PINCTRLC_SETSLEWRATE`, `pinctrl.h:PINCTRLC_SELECTGPIO`, `pinctrl.h:PINCTRLC_GETPAD` - User-space and kernel ioctl commands for pad manipulation.

## Invariants
- `pinctrl.h:pinctrl_dev_s` instances passed to `pinctrl.h:pinctrl_register` must provide a valid `pinctrl.h:pinctrl_ops_s` pointer that remains valid for the lifetime of the registered character device.
- Feature presence bitmasks in `pinctrl.h:pinctrl_padinfo_s` must use the `pinctrl.h:PINCTRL_HAVE_FUNCTION`, `pinctrl.h:PINCTRL_HAVE_STRENGTH`, `pinctrl.h:PINCTRL_HAVE_PULL`, and `pinctrl.h:PINCTRL_HAVE_SLEWRATE` flags to indicate valid fields.

## Side Effects
- `pinctrl.h:pinctrl_register` and `pinctrl.h:pinctrl_unregister` create and remove character device nodes in the VFS namespace.
- Invoking `pinctrl.h:pinctrl_ops_s` callbacks mutates hardware IOMUX and pad control registers, altering physical pin electrical characteristics and peripheral routing.

## Verification
- Run: `make test`
