# Serial and Pseudo-Terminal Drivers (`drivers/serial`)

## Overview
Implements the NuttX upper-half serial/UART character driver (`serial.c`) with interrupt-driven (`serial_io.c`) and DMA-driven (`serial_dma.c`) buffer transfer engines, POSIX pseudo-terminal master/slave drivers (`ptmx.c`, `pty.c`), GDB stub serial bridging (`serial_gdbstub.c`), and generic lower-half UART drivers including 16550 (`uart_16550.c`, `uart_pci_16550.c`), ARM PL011 (`uart_pl011.c`), ARM CMSDK (`serial_cmsdk.c`), Xilinx PS UART (`uart_xlnx_ps.c`), Bluetooth H4/H5 HCI UARTs (`uart_bth4.c`, `uart_bth5.c`), HostFS UART (`uart_hostfs.c`), RAM UART (`uart_ram.c`), and RPMSG virtual UARTs (`uart_rpmsg.c`, `uart_rpmsg_raw.c`).

## Interface
- `[serial.c:uart_register]`, `[serial.c:uart_datareceived]`, `[serial.c:uart_datasent]`, `[serial.c:uart_connected]`, `[serial.c:uart_reset_sem]`, `[serial.c:uart_check_special]`, `[serial.c:uart_putxmitchar]` - Core upper-half UART driver registration, poll/semaphore wakeup notifications, and special character (SIGINT/SIGTSTP/keyboard launch) processing.
- `[serial_io.c:uart_xmitchars]`, `[serial_io.c:uart_recvchars]` - Interrupt-level TX/RX circular buffer drain and fill routines for lower-half UART ISRs.
- `[serial_dma.c:uart_xmitchars_dma]`, `[serial_dma.c:uart_xmitchars_done]`, `[serial_dma.c:uart_recvchars_dma]`, `[serial_dma.c:uart_recvchars_done]` - DMA transfer setup and completion handlers for lower-half UART DMA engines.
- `[ptmx.c:ptmx_register]`, `[ptmx.c:ptmx_minor_free]`, `[pty.c:pty_register]`, `[pty.c:pty_register2]` - Pseudo-terminal master multiplexor (`/dev/ptmx`) and master/slave pair (`/dev/ptyN`, `/dev/ttypN` or `/dev/pts/N`) drivers.
- `[serial_gdbstub.c:uart_gdbstub_register]` - Attaches a GDB stub session over a serial port.
- Hardware and virtual UART lower-half initializers:
  - `[uart_16550.c:u16550_earlyserialinit]`, `[uart_16550.c:u16550_serialinit]`, `[uart_16550.c:u16550_bind]`, `[uart_16550.c:u16550_interrupt]`, `[uart_16550.c:u16550_putc]`, `[uart_16550.c:u16550_rxpoll]` - Generic 16550 UART driver.
  - `[uart_pci_16550.c:pci_u16550_init]` - PCI-bus 16550 UART driver.
  - `[uart_pl011.c:pl011_earlyserialinit]`, `[uart_pl011.c:pl011_serialinit]` - ARM PrimeCell PL011 UART driver.
  - `[serial_cmsdk.c:cmsdk_earlyserialinit]`, `[serial_cmsdk.c:cmsdk_serialinit]` - ARM Cortex-M System Design Kit (CMSDK) UART driver.
  - `[uart_xlnx_ps.c:xlnxps_earlyserialinit]`, `[uart_xlnx_ps.c:xlnxps_serialinit]` - Xilinx Zynq/ZynqMP Processing System UART driver.
  - `[uart_bth4.c:uart_bth4_register]`, `[uart_bth5.c:uart_bth5_register]` - Bluetooth H4 and H5 (3-wire) UART virtual serial drivers.
  - `[uart_hostfs.c:uart_hostfs_init]`, `[uart_ram.c:uart_ram_register]`, `[uart_ram.c:ram_serialinit]`, `[uart_rpmsg.c:uart_rpmsg_init]`, `[uart_rpmsg_raw.c:uart_rpmsg_raw_init]` - HostFS, shared-memory RAM, and RPMSG inter-processor UART drivers.

## Invariants
- `[serial.c:uart_register]` requires valid `uart_dev_s` buffers and operations; open/close/I/O operations assert `DEBUGASSERT(inode->i_private != NULL)`.
- `[pty.c:pty_register2]` and PTY file operations require `dev != NULL && dev->pd_devpair != NULL` and positive open reference count `devpair->pp_nopen > 0` on close.
- Hardware lower-half drivers (`[uart_16550.c:u16550_serialinit]`, `[uart_pl011.c:pl011_serialinit]`, `[serial_cmsdk.c:cmsdk_serialinit]`, `[uart_xlnx_ps.c:xlnxps_serialinit]`) assert `DEBUGASSERT(dev != NULL && dev->priv != NULL)` and valid baud rate bounds.

## Side Effects
- Registers character devices (`/dev/console`, `/dev/ttyS*`, `/dev/ttyV*`, `/dev/ptmx`, `/dev/pts/*`) via `register_driver`.
- Performs MMIO/port register reads/writes, attaches hardware IRQ handlers (`irq_attach`, `up_enable_irq`), and toggles TX/RX interrupts.
- `[serial.c:uart_check_special]` delivers POSIX signals (`nxsig_tgkill` for `SIGINT`/`SIGQUIT`/`SIGTSTP`) to foreground process groups when special control characters arrive.
- Acquires mutexes (`nxmutex_lock`), semaphores (`nxsem_wait`), spinlocks (`spin_lock_irqsave`), and critical sections (`enter_critical_section`) to serialize TX/RX ring buffer access.

## Verification
- Run: `make test`
