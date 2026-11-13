# tools

## Overview
Top-level host build, configuration, code generation, style verification, debugging, and packaging tools for Apache NuttX (`tools`). Contains the core configuration engine (`configure.sh`, `configure.c`, `process_config.py`, `mkconfig.c`, `mkversion.c`), build dependency and include-path generators (`mkdeps.c`, `incdir.c`), symbol/syscall/ROMFS table generators (`mksymtab.c`, `mksyscall.c`, `mkallsyms.py`, `gencromfs.c`), C coding standard checker (`nxstyle.c`, `checkpatch.sh`), crash/core-dump and GDB remote debugging scripts (`coredump.py`, `gdbserver.py`), CI test runner (`testbuild.sh`), and target-specific host tool subdirectories.

## Interface
- `cfgdefine.h:generate_definitions`, `mkconfig.c:main`, `mkversion.c:main` - Parses `.config` and `.version` files and emits `include/nuttx/config.h` and `include/nuttx/version.h` (`CONFIG_VERSION`).
- `cfgparser.h:variable_s`, `cfgparser.c:parse_file`, `cfgparser.c:find_variable`, `configure.c:main`, `configure.sh:dumpcfgs`, `process_config.py:expand_file` - Board configuration selection, `#include` defconfig expansion, host OS customization (`sethost.sh`), and `refresh.sh` defconfig normalization.
- `csvparser.h:parse_csvline`, `csvparser.h:read_line`, `mksymtab.c:main`, `mksyscall.c:main` - Parses syscall/library CSV specifications to generate `symtab_s` symbol tables (`g_symtab`, `g_nsymbols`) and user/kernel syscall proxies (`PROXY_*.c`) and stubs (`STUB_*.c`).
- `mkdeps.c:main`, `cnvwindeps.c:main`, `incdir.c:main` - Cross-platform compiler dependency generator (`COMPILER_GNU`, `COMPILER_TASKING`) and `-I`/`-isystem` path formatter across Linux, macOS, BSD, Windows Native, Cygwin, and MSYS.
- `gencromfs.c:main`, `mkromfsimg.sh`, `mkfsdata.py`, `bdf-converter.c:main`, `b16.c:main` - Generates LZF-compressed CROMFS C headers (`cromfs_volume_s`, `cromfs_node_s`), ROMFS images, HTTP fsdata arrays, NuttX BDF font headers, and `b16_t` fixed-point conversions.
- `mkallsyms.py:SymbolTables`, `abi_check.py`, `kasan_global.py`, `callstack.py`, `parsecallstack.py`, `parsememdump.py`, `parsetrace.py`, `size_report.py`, `stackusage.py` - ELF symbol table emission (`g_allsyms`, `g_nallsyms`), KASAN global instrumentation, and binary/trace analysis utilities.
- `coredump.py:decompress`, `coredump.py:main`, `gdbserver.py:GDBServer`, `jlink-nuttx.c` - LZF/hex/base64 core dump decoder and log/coredump/rawbin-backed GDB RSP server (`reg_table`).
- `nxstyle.c:main`, `checkpatch.sh:usage`, `checkkconfig.py`, `detab.c:main`, `rmcr.c:main`, `lowhex.c:main`, `convert-comments.c:main` - NuttX C coding style validator (`g_section_info`), patch/commit linter, Kconfig checker, and source formatting utilities.
- `testbuild.sh:showusage`, `mkexport.sh`, `zipme.sh`, `checkrelease.sh`, `doreleasenotes.py` - Multi-configuration build/test orchestrator, SDK export packager (`nuttx-export-*.tar.gz`), and release verification tools.
- `isotp_pty.py:main` - ISO-TP (`CAN_ISOTP`) socket to pseudo-terminal (`PTY`) host bridge utility.
- [./ameba/README.md](./ameba/README.md) - Realtek Ameba KM0/KM4 flash image packaging utility (`afimg`).
- [./bcm2711/README.md](./bcm2711/README.md) - Broadcom BCM2711 (Raspberry Pi 4B) bootable SD card image creator (`mkraspboot`).
- [./ci/README.md](./ci/README.md) - Continuous Integration (`cibuild.sh`), Docker/host platform provisioning, and CMake/Make parity verification scripts.
- [./codeowners/README.md](./codeowners/README.md) - GitHub `.github/CODEOWNERS` processor and watcher (`nuttx_codeowners.py`).
- [./cxd56/README.md](./cxd56/README.md) - Sony Spresense (CXD56xx) AES-128-CBC ELF-to-SPK firmware packager (`mkspk`).
- [./espressif/README.md](./espressif/README.md) - Espressif ESP32 family post-build image, QEMU flash merge, and OpenOCD configuration rules (`Config.mk`).
- [./imxrt1180/README.md](./imxrt1180/README.md) - NXP i.MX RT1180 AHAB container and FlexSPI NOR flash image builder (`mkahab`, `build_flash_image.sh`).
- [./licensing/README.md](./licensing/README.md) - Git history IP clearance, Apache ICLA verification (`log2json.sh`, `check.py`), and Apache 2.0 header migration (`apachize.py`).
- [./lwl/README.md](./lwl/README.md) - OpenOCD TCL RPC Lightweight Link (LWL) debug console client (`ocdconsole.py`).
- [./nxflat/README.md](./nxflat/README.md) - NXFLAT dynamic import thunk generator (`mknxflat`) and ELF-to-NXFLAT binary converter (`ldnxflat`).
- [./pic32/README.md](./pic32/README.md) - Microchip PIC32 Intel HEX physical address adjuster (`mkpichex`).
- [./pynuttx/README.md](./pynuttx/README.md) - Python GDB initialization entrypoint (`gdbinit.py`) and `nxgdb` kernel debugging package.
- [./rp2040/README.md](./rp2040/README.md) - Raspberry Pi RP2040 SmartFS flash image generator (`make_flash_fs`) and UF2 build rules (`Config.mk`).
- [./simwifi/README.md](./simwifi/README.md) - NuttX Simulator (`sim`) Wi-Fi `mac80211_hwsim` and real-NIC bridge manager (`sim_wifi.sh`).
- [./zds/README.md](./zds/README.md) - Zilog ZDS-II toolchain librarian wrapper (`zdsar`) and build rules (`Config.mk`).

## Invariants
- `mkconfig.c:main` and `mkversion.c:main` require `<topdir>/.config` and `<topdir>/.version` to exist before generating `include/nuttx/config.h` and `include/nuttx/version.h`.
- `csvparser.h:parse_csvline` enforces at most `MAX_FIELDS` (`16`) comma-separated fields of length up to `MAX_PARMSIZE` (`256`) per CSV entry for `mksymtab` and `mksyscall`.
- `nxstyle.c:main` validates C source and header files against section ordering in `nxstyle.c:g_section_info` (`FIRST_SECTION` to `LAST_SECTION`) and line width (`DEFAULT_WIDTH = 78` unless overridden).

## Side Effects
- Configuration tools (`configure.c`, `configure.sh`, `refresh.sh`, `sethost.sh`, `process_config.py`) copy and mutate `.config`, `Make.defs`, and `.version` in the top-level NuttX directory and invoke `make` / `kconfig-mconf` / `olddefconfig`.
- Code generators (`mkconfig`, `mkversion`, `mksymtab`, `mksyscall`, `mkallsyms.py`, `gencromfs`, `mkpasswd`) write generated C headers and source files (`PROXY_*.c`, `STUB_*.c`, symbol tables, ROMFS/CROMFS images) to disk or stdout.
- Network/simulation scripts (`simbridge.sh`, `simhostroute.sh`, `netusb.sh`) configure host network bridges, TAP/USB interfaces, and `iptables` NAT rules.

## Verification
- Run: `make test`
