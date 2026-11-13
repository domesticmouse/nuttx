# NuttX Serial & UART Subsystem (`include/nuttx/serial`)

## Overview
Provides the upper-half and lower-half UART/serial character driver architecture (`serial.h`), terminal and RS-485 `ioctl` commands (`tioctl.h`, `mxser.h`), pseudo-terminal interfaces (`pty.h`), and reusable lower-half UART driver headers (16550, PL011, CMSDK, Xilinx PS, Bluetooth H4/H5, RPMsg, RAM, and HostFS).

## Interface
- `serial.h:uart_dev_s`, `serial.h:uart_dev_t`, `serial.h:uart_ops_s`, `serial.h:uart_buffer_s`, `serial.h:uart_dmaxfer_s`, `serial.h:serial_icounter_s`, `serial.h:sbuf_size_t` - Core UART device structure, lower-half vtable (`setup`, `shutdown`, `attach`, `detach`, `ioctl`, `receive`, `rxint`, `rxavailable`, `send`, `txint`, `txready`, `txempty`, `dmasend`, `dmareceive`), TX/RX ring buffer, and DMA transfer descriptors.
- `serial.h:uart_register`, `serial.h:uart_xmitchars`, `serial.h:uart_recvchars`, `serial.h:uart_datareceived`, `serial.h:uart_datasent`, `serial.h:uart_connected`, `serial.h:uart_xmitchars_dma`, `serial.h:uart_xmitchars_done`, `serial.h:uart_recvchars_dma`, `serial.h:uart_recvchars_done`, `serial.h:uart_reset_sem`, `serial.h:uart_check_special`, `serial.h:uart_gdbstub_register` - Upper-half registration, ISR character/DMA transfer helpers, signal/special-character handling, and GDB stub binding.
- `tioctl.h:winsize`, `tioctl.h:serial_rs485`, `tioctl.h:TCGETS`, `tioctl.h:TCSETS`, `tioctl.h:TIOCGWINSZ`, `tioctl.h:TIOCSWINSZ`, `tioctl.h:TIOCSRS485`, `tioctl.h:TIOCGRS485`, `mxser.h:MOXA_SET_OP_MODE` - Terminal `termios`, window size, modem control, and RS-232/RS-422/RS-485 mode `ioctl` commands.
- `pty.h:ptmx_register`, `pty.h:pty_register` - Master/slave pseudo-terminal registration.
- `uart_16550.h:u16550_s`, `uart_16550.h:u16550_ops_s`, `uart_16550.h:u16550_earlyserialinit`, `uart_16550.h:u16550_serialinit`, `uart_pci_16550.h:pci_u16550_init` - Generic and PCI 16550 UART driver interfaces.
- `uart_pl011.h:pl011_earlyserialinit`, `uart_pl011.h:pl011_serialinit`, `uart_cmsdk.h:cmsdk_earlyserialinit`, `uart_cmsdk.h:cmsdk_serialinit`, `uart_xlnx_ps.h:xlnxps_earlyserialinit`, `uart_xlnx_ps.h:xlnxps_serialinit` - ARM PL011, Cortex-M CMSDK, and Xilinx Zynq PS UART drivers.
- `uart_bth4.h:uart_bth4_register`, `uart_bth5.h:uart_bth5_register`, `uart_rpmsg.h:uart_rpmsg_init`, `uart_rpmsg_raw.h:uart_rpmsg_raw_init`, `uart_ram.h:uart_ram_register`, `uart_hostfs.h:uart_hostfs_init` - Virtual UART transports over Bluetooth H4/H5, RPMsg, shared RAM, and HostFS.
- `netdev_console.h:netdev_console_init` - Network-device remote console driver initializer.

## Invariants
- Callers of `serial.h:uart_register` must pre-allocate and initialize `xmit.buffer`, `xmit.size`, `recv.buffer`, `recv.size`, `isconsole`, and `ops` in `serial.h:uart_dev_s`; the upper-half initializes `xmitsem`, `recvsem`, and `closelock`.
- A device marked with `isconsole = true` in `serial.h:uart_dev_s` is never shut down or detached when its file descriptor is closed.
- On architectures with `CONFIG_ARCH_LDST_16BIT_NOT_ATOMIC`, `serial.h:sbuf_size_t` is restricted to `uint8_t` so concurrent ISR and thread accesses to buffer `head`/`tail` indices remain atomic.

## Side Effects
- `serial.h:uart_xmitchars` and `serial.h:uart_recvchars` drain/fill the upper-half ring buffers from interrupt context and invoke `serial.h:uart_datasent` / `serial.h:uart_datareceived` to post `xmitsem`/`recvsem` and wake pollers.
- `serial.h:uart_check_special` removes `VINTR`/`VSUSP`/panic control bytes from the input stream and delivers `SIGINT`/`SIGTSTP` to the foreground process group (`dev->pid`) or triggers a kernel panic.

## Verification
- Run: `make test`
