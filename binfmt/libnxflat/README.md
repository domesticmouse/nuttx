# NuttX NXFLAT Loader Library (`libnxflat`)

## Overview
NXFLAT binary format loader library (built under `CONFIG_NXFLAT`): header verification (`libnxflat_verify.c`), binary initialization and teardown (`libnxflat_init.c`, `libnxflat_uninit.c`), I-Space file mapping and D-Space address environment allocation (`libnxflat_load.c`, `libnxflat_unload.c`, `libnxflat_addrenv.c`), file reading (`libnxflat_read.c`), and symbol import resolution, GOT relocation, and BSS zeroing (`libnxflat_bind.c`).

## Interface
- `[libnxflat_init.c:nxflat_init]`
- `[libnxflat_uninit.c:nxflat_uninit]`
- `[libnxflat_load.c:nxflat_load]`
- `[libnxflat_unload.c:nxflat_unload]`
- `[libnxflat_verify.c:nxflat_verifyheader]`
- `[libnxflat_read.c:nxflat_read]`
- `[libnxflat_bind.c:nxflat_bind]`
- `[libnxflat_addrenv.c:nxflat_addrenv_alloc]`
- `[libnxflat_addrenv.c:nxflat_addrenv_free]`
- `[libnxflat.h:nxflat_addrenv_select]`
- `[libnxflat.h:nxflat_addrenv_restore]`

## Invariants
- `[libnxflat_verify.c:nxflat_verifyheader]` requires `header != NULL` and `strncmp(header->h_magic, NXFLAT_MAGIC, 4) == 0`, returning `-ENOEXEC` otherwise.
- `[libnxflat_addrenv.c:nxflat_addrenv_alloc]` asserts `!loadinfo->dspace` on entry and sets `dspace->crefs = 1`; `[libnxflat_addrenv.c:nxflat_addrenv_free]` asserts `loadinfo != NULL` and `dspace->crefs == 1` before freeing `dspace`.
- `[libnxflat_load.c:nxflat_load]` sizes `loadinfo->dsize` as `loadinfo->datasize + MAX(loadinfo->bsssize, loadinfo->reloccount * sizeof(struct nxflat_reloc_s))` so the BSS region can temporarily hold relocation records prior to binding.
- `[libnxflat_bind.c:nxflat_gotrelocs]` asserts `offset >= loadinfo->isize` and `offset + nrelocs * sizeof(struct nxflat_reloc_s) <= loadinfo->isize + loadinfo->dsize`, and each relocation handler (`[libnxflat_bind.c:nxflat_bindrel32i]`, `[libnxflat_bind.c:nxflat_bindrel32d]`, `[libnxflat_bind.c:nxflat_bindrel32id]`) requires `offset < loadinfo->dsize` (returning `-EINVAL` otherwise).
- `[libnxflat_bind.c:nxflat_bindimports]` requires the module to import `NXFLAT_ABI_SYMBOL` (`abi_ok == true`, returning `-ENOEXEC` otherwise) and every imported symbol to resolve in `exports` via `symtab_findbyname` (returning `-ENOENT` otherwise).

## Side Effects
- `[libnxflat_init.c:nxflat_init]` zeroes `*loadinfo`, opens `filename` with `O_RDONLY | O_CLOEXEC` via `file_open`, reads and verifies the NXFLAT header, and populates `loadinfo` fields (closing `loadinfo->file` on failure); `[libnxflat_uninit.c:nxflat_uninit]` closes `loadinfo->file` if `loadinfo->file.f_inode != NULL`.
- `[libnxflat_addrenv.c:nxflat_addrenv_alloc]` and `[libnxflat_addrenv.c:nxflat_addrenv_free]` allocate/free `struct dspace_s` via `kmm_malloc`/`kmm_free` and either create/destroy a task address environment via `up_addrenv_create`/`up_addrenv_destroy` (when `CONFIG_ARCH_ADDRENV` is enabled) or allocate/free D-Space memory via `kumm_zalloc`/`kumm_free`.
- `[libnxflat_load.c:nxflat_load]` maps the I-Space segment via `file_mmap`, allocates D-Space via `nxflat_addrenv_alloc`, temporarily selects the address environment (if `CONFIG_ARCH_ADDRENV`), and reads `.data` plus relocation records into `loadinfo->dspace->region` via `nxflat_read`; `[libnxflat_unload.c:nxflat_unload]` unmaps `loadinfo->ispace` via `file_munmap` and frees D-Space via `nxflat_addrenv_free`.
- `[libnxflat_bind.c:nxflat_bind]` resolves imported symbol addresses into the D-Space import table (`nxflat_bindimports`), patches GOT entries in D-Space in-place (`nxflat_gotrelocs`), and zeroes the D-Space `.bss` region (`nxflat_clearbss`), temporarily switching address environments via `nxflat_addrenv_select`/`nxflat_addrenv_restore` when `CONFIG_ARCH_ADDRENV` is enabled.

## Verification
- Run: `make test`
