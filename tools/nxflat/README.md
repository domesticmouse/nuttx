# nxflat

## Overview
Host-side NXFLAT (NuttX Flat Binary Format) toolchain utilities (`tools/nxflat`). Provides `mknxflat` to generate ARM/Thumb-2 dynamic import thunk assembly files directly from 32-bit ELF relocatable objects without `libbfd`, `ldnxflat` to convert linked relocatable ELF objects (`ld -r`) into loadable NXFLAT binary containers (`struct nxflat_hdr_s` + I-Space + D-Space + relocations), and `testsuite.sh` to validate NXFLAT module builds.

## Interface
- `nxflat_elf.h:nxflat_elf_s`, `nxflat_elf.c:nxflat_elf_read`, `nxflat_elf.c:nxflat_elf_symname` - Host-endian-normalizing 32-bit ELF reader (`ELFCLASS32`) shared by `mknxflat` and `ldnxflat`.
- `nxflat_thunk.h:nxflat_thunk_s`, `nxflat_thunk.h:NXFLAT_PIC_REG` (`"r9"`), `nxflat_thunk.h:NXFLAT_ABI_SYMBOL` (`"__nxflat_abi_v2"`), `thunk_arm.c:g_thunk_arm`, `thunk_thumb2.c:g_thunk_thumb2` - Architecture-specific thunk assembly templates and ABI constants.
- `mknxflat.c:main` - CLI tool (`-a <arm|thumb2> [-o <out-filename>] [-v] [-w] <elf-file>`) that scans undefined non-object symbols and emits the `__nxflat_abi_v2` marker, import string table, `__dyninfo` array, and call thunks.
- `ldnxflat.c:main` - CLI converter (`-e <entry> -o <output> [-s <stack>] [-v] <elf-file>`) that places `.text`/`.data`/`.bss` and `SHN_COMMON` symbols, builds the GOT, resolves ARM/Thumb-2 relocations (`R_ARM_THM_CALL`, `R_ARM_GOTOFF32`, `R_ARM_GOT_BREL`, `R_ARM_ABS32`, etc.), and writes the `NxFT` binary container.
- `testsuite.sh:build`, `testsuite.sh:finish` - Regression test runner that compiles and links `apps/examples/nxflat/tests` modules using `mknxflat` and `ldnxflat`.

## Invariants
- Input files to `nxflat_elf.c:nxflat_elf_read` must be valid 32-bit (`ELFCLASS32`) ELF objects containing a static `SHT_SYMTAB` symbol table.
- `nxflat_thunk.h:NXFLAT_PIC_REG` (`"r9"`) must match `PIC_REG` in `arch/arm/include/arch.h` and `-mpic-register=r9`, and `nxflat_thunk.h:NXFLAT_ABI_SYMBOL` (`"__nxflat_abi_v2"`) must match `include/nxflat.h`.
- `ldnxflat.c:main` requires both `-e <entry>` and `-o <output>` arguments and writes the 36-byte `NXFLAT_HDR_SIZE` header in network byte order followed by I-Space, D-Space (GOT first), and target-endian relocation records (`NXFLAT_RELOC_TYPE_REL32I`, `NXFLAT_RELOC_TYPE_REL32D`).

## Side Effects
- `mknxflat.c:main` creates/truncates the output `.S` thunk assembly file (or writes to stdout).
- `ldnxflat.c:main` writes the binary NXFLAT module (`-o <output>`) to disk.
- `testsuite.sh` creates `$OUTDIR` (`./nxflat-testsuite`), invokes `${CROSSDEV}gcc`, `${CROSSDEV}g++`, `${CROSSDEV}ld`, `mknxflat`, and `ldnxflat`, and writes build artifacts and logs.

## Verification
- Run: `make test`
