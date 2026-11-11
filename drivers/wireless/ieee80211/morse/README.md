# Morse Micro IEEE 802.11ah (Wi-Fi HaLow) Driver (`drivers/wireless/ieee80211/morse`)

## Overview
Implements the NuttX network device driver (`morse_netdev.c`), hardware abstraction layer (`morse_mmhal.c`), OS abstraction layer (`morse_mmosal.c`), and architecture port macros (`mmport.h`) for Morse Micro MM6108 / MM8108 IEEE 802.11ah (Wi-Fi HaLow) SPI transceivers.

## Interface
- `[morse_netdev.c:morse_register]` - Initializes the Morse Micro WLAN stack and registers a NuttX `wlanN` network interface supporting Ethernet TX/RX and `SIOCSIW*`/`SIOCGIW*` wireless extensions.
- `[morse_mmhal.c:morse_hal_initialize]`, `[morse_mmhal.c:morse_hal_has_powersave]`, `[morse_mmhal.c:mmhal_wlan_init]`, `[morse_mmhal.c:mmhal_wlan_deinit]`, `[morse_mmhal.c:mmhal_read_mac_addr]`, `[morse_mmhal.c:mmhal_wlan_pktmem_init]`, `[morse_mmhal.c:mmhal_wlan_spi_read_write]`, `[morse_mmhal.c:mmhal_random_u32]`, `[morse_mmhal.c:mmhal_set_deep_sleep_veto]`, `[morse_mmhal.c:mmhal_clear_deep_sleep_veto]` - Morse Micro HAL callbacks for SPI transfers, firmware/BCF binary loading, busy/wake/reset GPIO pins, and deep sleep veto control.
- `[morse_mmosal.c:mmosal_task_create]`, `[morse_mmosal.c:mmosal_task_delete]`, `[morse_mmosal.c:mmosal_task_sleep]`, `[morse_mmosal.c:mmosal_task_enter_critical]`, `[morse_mmosal.c:mmosal_task_exit_critical]`, `[morse_mmosal.c:mmosal_mutex_create]`, `[morse_mmosal.c:mmosal_sem_create]`, `[morse_mmosal.c:mmosal_semb_create]`, `[morse_mmosal.c:mmosal_queue_create]`, `[morse_mmosal.c:mmosal_timer_create]` - OSAL primitives mapping Morse SDK threads, mutexes, semaphores, message queues (`mqueue`), and timers (`work_queue`) to NuttX kernel APIs.
- `[mmport.h:MMPORT_BREAKPOINT]`, `[mmport.h:MMPORT_GET_LR]`, `[mmport.h:MMPORT_GET_PC]`, `[mmport.h:MMPORT_MEM_SYNC]` - Architecture-specific compiler/CPU intrinsics required by Morse Micro SDK headers.

## Invariants
- `[morse_netdev.c:morse_register]` and `[morse_mmhal.c:morse_hal_initialize]` assert `DEBUGASSERT(spi != NULL && lower != NULL)` and require non-null lower-half callbacks `reset`, `irq_attach`, `irq_enable`, and `irq_asserted`.
- `[morse_mmosal.c:mmosal_task_exit_critical]` asserts `DEBUGASSERT(g_critical_nest > 0)`.

## Side Effects
- Performs SPI transactions (`SPI_EXCHANGE`, `SPI_SNDBLOCK`, `SPI_RECVBLOCK`), opens firmware and board configuration files from the VFS (`file_open`), and toggles hardware reset/wake GPIOs.
- Spawns SDK worker threads (`kthread_create`), creates POSIX message queues (`file_mq_open`), schedules timers on `LPWORK`, and registers a network device (`netdev_register`).

## Verification
- Run: `make test`
