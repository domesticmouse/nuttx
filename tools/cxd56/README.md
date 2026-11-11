# Sony CXD56xx (Spresense) SPK Image Generator (`mkspk`)

## Overview
Host tool (`mkspk`) and CLEFIA cipher implementation used to convert a 32-bit NuttX ELF executable (`nuttx`) into a signed/CMAC-authenticated `.spk` firmware image (`nuttx.spk`) for Sony CXD56xx multi-core microcontrollers.

## Interface
- `mkspk.c:main` - CLI entry point (`mkspk [-c <number>] <filename> <save name> [<output file>]`) that parses an ELF32 binary, constructs an SPK image header and loadable segment table, appends a 16-byte CLEFIA CMAC and `MKSPK_BN_FOOTER`, and writes the `.spk` file.
- `mkspk.h:spk_header`, `mkspk.h:spk_prog_info`, `mkspk.h:elf_file`, `mkspk.h:alignup` - SPK binary header structures and parsed ELF container definitions.
- `clefia.h:cipher`, `clefia.c:cipher_init`, `clefia.c:cipher_deinit`, `clefia.c:cipher_calc_cmac`, `clefia.c:clefiakeyset`, `clefia.c:clefiaencrypt`, `clefia.c:bytexor` - 128-bit CLEFIA block cipher and CMAC calculation functions.
- `elf32.h:Elf32_Ehdr`, `elf32.h:Elf32_Shdr`, `elf32.h:Elf32_Sym`, `elf32.h:Elf32_Phdr`, `elf32.h:Elf32_Rel`, `elf32.h:Elf32_Rela`, `elf32.h:Elf32_Dyn` - Standalone 32-bit ELF format structures and macros.
- `Config.mk:POSTBUILD` - Makefile post-build macro enabled when `CONFIG_CXD56_BINARY=y` that builds `mkspk` via `Makefile.host` and generates `nuttx.spk`.

## Invariants
- `clefia.c:cipher_calc_cmac` requires the input `size` to be a multiple of 16 bytes (`if (size & 0xf) return -1;`); `mkspk.c:create_image` pads `savename` and each `PT_LOAD` segment's `p_filesz` to 16-byte alignment via `mkspk.h:alignup`.
- `mkspk.c:parse_args` requires a non-negative core ID (`-c <number>`), `savename` length `<= 63` bytes, and a valid 32-bit ELF file (`\x7fELF` magic in `mkspk.c:load_elf`).

## Side Effects
- Reads the input ELF file into heap memory (`mkspk.c:load_elf`) and writes the resulting `.spk` binary image to `<output file>` (`mkspk.c:main`).
- `Config.mk:POSTBUILD` compiles `tools/cxd56/mkspk`, writes `nuttx.spk`, and appends `nuttx.spk` to `nuttx.manifest`.

## Verification
- Run: `make test`
