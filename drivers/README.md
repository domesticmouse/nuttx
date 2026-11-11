# NuttX Device Drivers Subsystem (`drivers`)

## Overview
Top-level device driver initialization (`drivers_initialize.c`) and build/Kconfig aggregation for all kernel device driver subsystems in NuttX.

## Interface
- `[drivers_initialize.c:drivers_early_initialize]`
- `[drivers_initialize.c:drivers_initialize]`
- `[Kconfig:CONFIG_SPECIFIC_DRIVERS]`
- [`1wire`](./1wire/README.md) - 1-Wire bus master infrastructure, ROM search/selection, CRC helpers, and 1-Wire slave drivers.
- [`aie`](./aie/README.md) - Upper-half character driver for AI Engine (AIE) hardware accelerators.
- [`analog`](./analog/README.md) - Upper-half and chip-specific drivers for ADCs, DACs, comparators, op-amps, PGAs, and digital potentiometers.
- [`audio`](./audio/README.md) - Lower-half audio codec, DSP, I2S/DMA bridge, and tone generator drivers.
- [`bch`](./bch/README.md) - Block-to-Character (`bch`) translation library and VFS character driver wrapper.
- [`can`](./can/README.md) - Controller Area Network (CAN) upper-half character driver, priority TX queue manager, and CAN controller drivers.
- [`clk`](./clk/README.md) - Hierarchical clock tree framework (`clk_s`), clock providers, and RPMsg clock proxy.
- [`contactless`](./contactless/README.md) - SPI character drivers for 13.56 MHz contactless RFID/NFC transceivers (MFRC522, PN532).
- [`coresight`](./coresight/README.md) - ARM CoreSight hardware trace topology manager and ETM/STM/Funnel/Replicator/ETB/TPIU/TMC drivers.
- [`crypto`](./crypto/README.md) - Character device drivers for `/dev/urandom`, hardware TRNG (`rng90`), and NXP SE05x Secure Element.
- [`devfreq`](./devfreq/README.md) - Dynamic device frequency scaling (`devfreq`) framework, governors, QoS constraints, and procfs entry.
- [`devicetree`](./devicetree/README.md) - Flattened Device Tree (FDT) registration, property/address/IRQ parsers, and FDT bus discovery.
- [`dma-buf`](./dma-buf/README.md) - DMA buffer sharing (`dma-buf`) and `/dev/dma_heap/*` heap allocation subsystem.
- [`eeprom`](./eeprom/README.md) - Byte-addressable VFS character drivers for I2C (`24xx`) and SPI (`25xx`) serial EEPROMs.
- [`efuse`](./efuse/README.md) - Upper-half character driver for non-volatile One-Time Programmable (OTP) eFuse controllers.
- [`i2c`](./i2c/README.md) - I2C master/slave character drivers, transfer helpers, bit-bang drivers, and I2C bus multiplexers.
- [`i2s`](./i2s/README.md) - Generic `/dev/i2scharN` character device wrapper for streaming audio buffers over I2S.
- [`i3c`](./i3c/README.md) - MIPI I3C bus master core, CCC dispatch, Dynamic Address Assignment, IBI handling, and `/dev/i3cN` driver.
- [`input`](./input/README.md) - Input subsystem upper-half drivers (touchscreen, keyboard, mouse, button, joystick, haptics, uinput) and controller drivers.
- [`ioexpander`](./ioexpander/README.md) - GPIO character driver (`/dev/gpio*`), I/O expander adapters, RPMsg I/O expander proxies, and I2C/SPI expander drivers.
- [`ipcc`](./ipcc/README.md) - Upper-half character driver (`/dev/ipccN`) for Inter-Processor Communication Controller channels.
- [`lcd`](./lcd/README.md) - LCD character driver, LCD-to-framebuffer bridge, SPI LCD wrapper, and TFT/OLED/e-ink/segment display drivers.
- [`leds`](./leds/README.md) - User LED upper-half character driver and PWM/I2C/SPI LED controller and addressable RGB strip drivers.
- [`loop`](./loop/README.md) - Loopback block device driver (`/dev/loop`) binding regular files as block devices.
- [`math`](./math/README.md) - Upper-half character drivers for hardware CORDIC, FFT, and MPI (multi-precision integer) accelerators.
- [`misc`](./misc/README.md) - Miscellaneous pseudo-devices (`/dev/null`, `/dev/zero`, `/dev/mem`, `/dev/ascii`), RAM disk, rwbuffer, LWL console, Goldfish pipe, and OP-TEE drivers.
- [`mmcsd`](./mmcsd/README.md) - MMC/SD/SDIO block driver and SPI/SDIO slot card management.
- [`modem`](./modem/README.md) - Cellular modem drivers including the Sony Altair ALT1250 LTE modem driver.
- [`motor`](./motor/README.md) - Upper-half DC motor, stepper motor, and Field-Oriented Control (FOC) motor drivers.
- [`mtd`](./mtd/README.md) - Memory Technology Device (MTD) drivers for NOR/NAND/SPI flash, FTL, SMART flash, NVS, and MTD partitions.
- [`net`](./net/README.md) - Network interface drivers (Ethernet MACs, PHYs, slip, tun, telnet, loopback, vnet, rpmsgdrv, usbnet, OA-TC6).
- [`note`](./note/README.md) - Scheduler instrumentation (`sched_note`) RAM/log/stream/sysview/RTT capture drivers and `/dev/note`.
- [`pci`](./pci/README.md) - PCI and PCIe host controller, ECAM, endpoint, QEMU test/edu/ivshmem, and bus enumeration framework.
- [`pinctrl`](./pinctrl/README.md) - Pin control and pin multiplexing (`pinctrl`) upper-half character driver.
- [`pipes`](./pipes/README.md) - POSIX pipe (`pipe2`) and named FIFO (`mkfifo`) character driver implementation.
- [`power`](./power/README.md) - Power management (`pm`), battery charger/gauge/monitor, power supply/regulator, and relay drivers.
- [`rc`](./rc/README.md) - Remote control (`lirc`) infrared receiver/transmitter upper-half and dummy drivers.
- [`regmap`](./regmap/README.md) - Register map (`regmap`) abstraction subsystem over I2C and SPI buses.
- [`reset`](./reset/README.md) - Hardware reset controller framework (`reset_control`) and RPMsg reset proxy.
- [`rf`](./rf/README.md) - RF digital step attenuator (`dat-31r5-sp`) and RF peripheral drivers.
- [`rpmsg`](./rpmsg/README.md) - RPMsg transport core, character device, router, port/virtio/ivshmem transports, and ping diagnostics.
- [`rptun`](./rptun/README.md) - Remote Processor Tunneling (`rptun`) OpenAMP remoteproc lifecycle and virtio transport bridge.
- [`segger`](./segger/README.md) - SEGGER Real-Time Transfer (RTT) console/serial/syslog/stream and SystemView trace drivers.
- [`sensors`](./sensors/README.md) - Sensor upper-half framework (`sensor_register`), uORB/RPMsg sensor proxy, and environmental/IMU/GNSS/optical sensor drivers.
- [`serial`](./serial/README.md) - UART/USART upper-half serial driver, PTY/termios/H4/SLIP/GDB-stub line disciplines, and 16550/CMSDK/RPMsg UART drivers.
- [`spi`](./spi/README.md) - SPI master/slave character drivers, transfer helpers, bit-bang SPI, and QSPI flash wrappers.
- [`syslog`](./syslog/README.md) - System logging (`syslog`) channel manager, RAM log, interrupt buffer, stream/file/console/device/RPMSG sinks.
- [`thermal`](./thermal/README.md) - Thermal zone management framework, step-wise governor, cooling devices, and procfs thermal interface.
- [`timers`](./timers/README.md) - Hardware timer, oneshot, freerunning, watchdog, PWM, capture, QE, RTC, and PTP clock drivers.
- [`usbdev`](./usbdev/README.md) - USB device class drivers (CDC-ACM, CDC-ECM, RNDIS, MSC, HID, Audio, DFU, MTP, ADB, USBTMC, composite).
- [`usbhost`](./usbhost/README.md) - USB host controller helpers, hub enumeration, and class drivers (MSC, CDC-ACM, HID, XBox, BTHCI, FT232R).
- [`usbmisc`](./usbmisc/README.md) - USB miscellaneous Type-C/PD controller (`fusb301`, `fusb302`) and USB mux (`ts3usb30`) drivers.
- [`usbmonitor`](./usbmonitor/README.md) - Background USB device/host trace monitoring thread.
- [`usrsock`](./usrsock/README.md) - Userspace socket (`/dev/usrsock`) character driver and RPMsg userspace socket bridge.
- [`vhost`](./vhost/README.md) - Virtual host (`vhost`) device/driver bus and vhost-rng implementation.
- [`video`](./video/README.md) - Video framebuffer (`fb`), V4L2/video capture (`video`, `isx012`, ` isx019`, `ov2640`), Goldfish FB/camera, MIPI-DSI, and VNC server drivers.
- [`virtio`](./virtio/README.md) - VirtIO bus, MMIO/PCI transports, and VirtIO block, net, console, GPU, input, RNG, RPMsg, sound, and 9P drivers.
- [`wireless`](./wireless/README.md) - Wireless radio device drivers for Bluetooth HCI, IEEE 802.11 (BCM43xxx, GS2200M), IEEE 802.15.4 (CC1101, MRF24J40, XBee), LPWAN (SX127x, RN2xx3), NRF24L01, and SPIRIT.

## Invariants
- At most one console driver macro among `CONFIG_LWL_CONSOLE`, `CONFIG_SERIAL_CONSOLE`, `CONFIG_CDCACM_CONSOLE`, `CONFIG_PL2303_CONSOLE`, `CONFIG_SERIAL_RTT_CONSOLE`, `CONFIG_RPMSG_UART_CONSOLE`, and `CONFIG_RPMSG_UART_RAW_CONSOLE` may be defined (`#error More than one console driver selected`) `[drivers_initialize.c:CONFIG_SERIAL_CONSOLE]`.
- `drivers_early_initialize` must not rely on any system resources such as heap memory `[drivers_initialize.c:drivers_early_initialize]`.

## Side Effects
- Initializes early note driver (`note_early_initialize`) when `CONFIG_DRIVERS_NOTE` is enabled `[drivers_initialize.c:drivers_early_initialize]`.
- Registers and initializes configured device drivers and virtual `/dev` nodes (syslog, RTT, devfreq, `/dev/null`, `/dev/random`, `/dev/urandom`, `/dev/zero`, `/dev/mem`, `/dev/loop`, `/dev/ascii`, `/dev/note`, rpmsg services, serial/UART, pty, crypto, uinput, loopback/TUN/telnet network drivers, sensors, smart/mtd loop, usbhost, PCI, virtio, vhost, OP-TEE, thermal, dummy PTP clock, fake capture, DMA-BUF system heap) surrounded by `drivers_trace_begin()` and `drivers_trace_end()` `[drivers_initialize.c:drivers_initialize]`.

## Verification
- Run: `make test`
