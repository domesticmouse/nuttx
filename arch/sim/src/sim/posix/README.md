# posix (`nuttx/arch/sim/src/sim/posix`)

## Overview
Hardware abstraction and architecture package for `posix` under `nuttx/arch/sim/src/sim/posix`, providing 2 header file(s) and 23 source file(s) (including `sim_i2c.h`, `sim_spi.h`, `sim_alsa.c`, `sim_bsimtime.c`).

## Subdirectories & Boundaries
- `vpnkit`: [./vpnkit/README.md](./vpnkit/README.md) - Hardware abstraction and architecture package for `vpnkit` under `nuttx/arch/sim/src/sim/posix/vpnkit`, providing 1 header file(s) and 2 source file(s) (including `sim_protocol.h`, `sim_negotiate.c`, `sim_protocol.c`).

## Interface
- `[sim_i2c.h:i2c_msg_s]`
- `[sim_i2c.h:i2c_master_s]`
- `[sim_i2c.h:i2c_ops_s]`
- `[sim_i2c.h:NUTTX_I2C_M_READ]`
- `[sim_i2c.h:NUTTX_I2C_M_TEN]`
- `[sim_i2c.h:NUTTX_I2C_M_NOSTOP]`
- `[sim_i2c.h:NUTTX_I2C_M_NOSTART]`
- `[sim_spi.h:spi_mode_e]`
- `[sim_spi.h:spi_ops_s]`
- `[sim_spi.h:spi_dev_s]`
- `[sim_spi.h:spi_trans_s]`
- `[sim_spi.h:spi_sequence_s]`
- `[sim_spi.h:spi_hwfeatures_t]`
- `[sim_spi.h:HWFEAT_CS_INACTIVE]`
- `[sim_spi.h:HWFEAT_CS_ACTIVE]`
- `[sim_spi.h:HWFEAT_LSBFIRST]`
- `[sim_alsa.c:sim_audio_initialize]`
- `[sim_bsimtime.c:host_bsimtime_init]`
- `[sim_bsimtime.c:host_bsimtime_gettime]`
- `[sim_bsimtime.c:host_bsimtime_is_enabled]`
- `[sim_bsimtime.c:host_bsimtime_sleepuntil]`
- `[sim_bsimtime.c:host_bsimtime_disconnect]`
- `[sim_errno.c:host_errno_convert]`
- `[sim_errno.c:host_errno_get]`
- `[sim_errno.c:host_errno_set]`
- `[sim_host_v4l2.c:host_video_get_device_count]`
- `[sim_host_v4l2.c:host_video_is_available]`
- `[sim_host_v4l2.c:host_video_init]`
- `[sim_host_v4l2.c:host_video_dqbuf]`
- `[sim_host_v4l2.c:host_video_uninit]`
- [./vpnkit/README.md](./vpnkit/README.md)

## Invariants
- `[sim_hostirq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[sim_hostirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[sim_hostirq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
