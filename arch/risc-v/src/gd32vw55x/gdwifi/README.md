# gdwifi (`nuttx/arch/risc-v/src/gd32vw55x/gdwifi`)

## Overview
Hardware abstraction and architecture package for `gdwifi` under `nuttx/arch/risc-v/src/gd32vw55x/gdwifi`, providing 1 header file(s) and 5 source file(s) (including `gdwifi_netdev.h`, `gdwifi_glue.c`, `gdwifi_netdev.c`, `gdwifi_netif_compat.c`).

## Subdirectories & Boundaries
- `config`: [./config/README.md](./config/README.md) - Hardware abstraction and architecture package for `config` under `nuttx/arch/risc-v/src/gd32vw55x/gdwifi/config`, providing 4 header file(s) and 0 source file(s) (including `app_cfg.h`, `build_config.h`, `lwipopts.h`, `platform_def.h`).
- `net_compat`: [./net_compat/README.md](./net_compat/README.md) - Hardware abstraction and architecture package for `net_compat` under `nuttx/arch/risc-v/src/gd32vw55x/gdwifi/net_compat`, providing 2 header file(s) and 0 source file(s) (including `dhcpd.h`, `wifi_netif.h`).

## Interface
- `[gdwifi_netdev.h:gdwifi_netdev_register]`
- `[gdwifi_netdev.h:gdwifi_netdev_get]`
- `[gdwifi_glue.c:log_uart_putc_noint]`
- `[gdwifi_glue.c:uart_putc_noint]`
- `[gdwifi_glue.c:xGetCurrentTaskStackDepth]`
- `[gdwifi_glue.c:gdwifi_irq_attach]`
- `[gdwifi_glue.c:sntp_set_system_time]`
- `[gdwifi_glue.c:sntp_get_update_intv]`
- `[gdwifi_glue.c:system_clock_config]`
- `[gdwifi_glue.c:gdwifi_start]`
- `[gdwifi_netdev.c:net_buf_tx_alloc]`
- `[gdwifi_netdev.c:net_buf_tx_alloc_ref]`
- `[gdwifi_netdev.c:net_buf_tx_pbuf_free]`
- `[gdwifi_netdev.c:net_buf_tx_free]`
- `[gdwifi_netdev.c:net_buf_tx_cat]`
- `[gdwifi_netdev.c:net_buf_tx_info]`
- `[gdwifi_netdev.c:net_if_input]`
- `[gdwifi_netdev.c:net_if_up]`
- `[gdwifi_netdev.c:net_if_down]`
- `[gdwifi_netdev.c:net_lpbk_socket_create]`
- `[gdwifi_netdev.c:net_lpbk_socket_bind]`
- `[gdwifi_netdev.c:net_lpbk_socket_connect]`
- `[gdwifi_netdev.c:lwip_socket]`
- `[gdwifi_netdev.c:lwip_send]`
- `[gdwifi_netdev.c:lwip_recv]`
- `[gdwifi_netdev.c:lwip_close]`
- `[gdwifi_netdev.c:dhcpd_delete_ipaddr_by_macaddr]`
- `[gdwifi_netdev.c:gdwifi_netdev_get]`
- `[gdwifi_netdev.c:gdwifi_netdev_register]`
- `[gdwifi_netif_compat.c:net_init]`
- [./config/README.md](./config/README.md)
- [./net_compat/README.md](./net_compat/README.md)

## Invariants
- `[gdwifi_netdev.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[wrapper_nuttx.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[wrapper_nuttx.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[gdwifi_glue.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[gdwifi_glue.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
