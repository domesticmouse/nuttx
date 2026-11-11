# sim (`nuttx/arch/sim/src/sim`)

## Overview
Hardware abstraction and architecture package for `sim` under `nuttx/arch/sim/src/sim`, providing 12 header file(s) and 54 source file(s) (including `sim_gpiochip.h`, `sim_hostcan.h`, `sim_hosthcisocket.h`, `sim_hostusrsock.h`).

## Subdirectories & Boundaries
- `macos`: [./macos/README.md](./macos/README.md) - Hardware abstraction and architecture package for `macos` under `nuttx/arch/sim/src/sim/macos`, providing 0 header file(s) and 1 source file(s) (including `sim_host_avfoundation_backend.m`).
- `posix`: [./posix/README.md](./posix/README.md) - Hardware abstraction and architecture package for `posix` under `nuttx/arch/sim/src/sim/posix`, providing 2 header file(s) and 23 source file(s) (including `sim_i2c.h`, `sim_spi.h`, `sim_alsa.c`, `sim_bsimtime.c`).
- `win`: [./win/README.md](./win/README.md) - Hardware abstraction and architecture package for `win` under `nuttx/arch/sim/src/sim/win`, providing 0 header file(s) and 8 source file(s) (including `sim_errno.c`, `sim_hostfs.c`, `sim_hostirq.c`, `sim_hostmemory.c`).

## Interface
- `[sim_gpiochip.h:host_gpiochip_alloc]`
- `[sim_gpiochip.h:host_gpiochip_free]`
- `[sim_gpiochip.h:host_gpiochip_get_line]`
- `[sim_gpiochip.h:host_gpiochip_readpin]`
- `[sim_gpiochip.h:host_gpiochip_writepin]`
- `[sim_gpiochip.h:host_gpiochip_direction]`
- `[sim_gpiochip.h:host_gpiochip_irq_request]`
- `[sim_gpiochip.h:host_gpiochip_irq_active]`
- `[sim_gpiochip.h:host_gpiochip_dev]`
- `[sim_gpiochip.h:GPIOCHIP_LINE_FLAG_DISABLE]`
- `[sim_gpiochip.h:GPIOCHIP_LINE_FLAG_RISING]`
- `[sim_gpiochip.h:GPIOCHIP_LINE_FLAG_FALLING]`
- `[sim_gpiochip.h:GPIOCHIP_LINE_FLAG_BOTH]`
- `[sim_hostcan.h:host_can_init]`
- `[sim_hostcan.h:host_can_read]`
- `[sim_hostcan.h:host_can_send]`
- `[sim_hostcan.h:host_can_ifup]`
- `[sim_hostcan.h:host_can_ifdown]`
- `[sim_hostcan.h:host_can_avail]`
- `[sim_hostcan.h:host_can_loopback]`
- `[sim_hostcan.h:sim_can_s]`
- `[sim_hostcan.h:SIM_CAN_MAX_DLEN]`
- `[sim_hosthcisocket.h:host_bthcisock_open]`
- `[sim_hosthcisocket.h:host_bthcisock_configure]`
- `[sim_hosthcisocket.h:host_bthcisock_send]`
- `[sim_hosthcisocket.h:host_bthcisock_receive]`
- `[sim_hosthcisocket.h:host_bthcisock_avail]`
- `[sim_hosthcisocket.h:host_bthcisock_close]`
- `[sim_hostusrsock.h:usrsock_event_callback]`
- `[sim_hostusrsock.h:host_usrsock_socket]`
- [./macos/README.md](./macos/README.md)
- [./posix/README.md](./posix/README.md)
- [./win/README.md](./win/README.md)

## Invariants
- `[sim_backtrace.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sim_checkhostfstypes.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[sim_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sim_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sim_framebuffer.c:#error]` Compile-time configuration constraint: Unsupported BPP
- `[sim_idle.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sim_lcd.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sim_lcd.c:#error]` Compile-time configuration constraint: Unsupported BPP
- `[sim_mouse.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sim_oneshot.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sim_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sim_sigdeliver.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[sim_oneshot.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[sim_oneshot.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[sim_smpsignal.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[sim_smpsignal.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
