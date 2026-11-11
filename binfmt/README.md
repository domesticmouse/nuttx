# NuttX Binary Format Loader Subsystem (`binfmt`)

## Overview
Binary format loader subsystem managing registration of format handlers (builtin, script `#!`, ELF, NXFLAT), module loading/unloading, symbol table binding, argument/environment/file-action copying, permission checks, and task execution/spawning.

## Interface
- `[binfmt.h:g_binfmts]`
- `[binfmt_globals.c:g_binfmts]`
- `[binfmt_initialize.c:binfmt_initialize]`
- `[binfmt_register.c:register_binfmt]`
- `[binfmt_unregister.c:unregister_binfmt]`
- `[binfmt_loadmodule.c:load_module]`
- `[binfmt_unloadmodule.c:unload_module]`
- `[binfmt_execmodule.c:exec_module]`
- `[binfmt_exec.c:exec_spawn]`
- `[binfmt_exec.c:exec]`
- `[binfmt_copyargv.c:binfmt_copyargv]`
- `[binfmt_copyargv.c:binfmt_freeargv]`
- `[binfmt.h:binfmt_copyenv]`
- `[binfmt.h:binfmt_freeenv]`
- `[binfmt_copyactions.c:binfmt_copyactions]`
- `[binfmt_copyactions.c:binfmt_freeactions]`
- `[binfmt_dumpmodule.c:binfmt_dumpmodule]`
- `[binfmt_checkexec.c:binfmt_checkexecperm]`
- `[binfmt_exit.c:binfmt_exit]`
- `[binfmt_execsymtab.c:exec_getsymtab]`
- `[binfmt_execsymtab.c:exec_setsymtab]`
- `[builtin.c:builtin_initialize]`
- `[builtin.c:builtin_uninitialize]`
- `[script.c:script_initialize]`
- `[script.c:script_uninitialize]`
- `[elf.c:elf_initialize]`
- `[elf.c:elf_uninitialize]`
- `[nxflat.c:nxflat_initialize]`
- `[nxflat.c:nxflat_uninitialize]`
- [`libnxflat`](./libnxflat/README.md) - NXFLAT binary format header verification, loading, address environment allocation, and symbol/GOT relocation library.

## Invariants
- Handlers are prepended to `g_binfmts`, so `script_initialize` is registered first in `binfmt_initialize` to ensure `#!` scripts are tried last after binary formats `[binfmt_initialize.c:binfmt_initialize]`.
- `load_absmodule` halts handler traversal immediately on `-EACCES` so fallback loaders cannot bypass execute-permission checks `[binfmt_loadmodule.c:load_absmodule]`.
- Caller must possess `PR_CAP_SPAWN` capability (`nxsched_capable(PR_CAP_SPAWN)`) and total `argv` + `envp` byte size must not exceed `ARG_MAX` `[binfmt_exec.c:exec_internal]`.
- User argument count must not exceed `CONFIG_TASK_MAX_ARGS` `[binfmt_copyargv.c:binfmt_nargs]`.
- Spawn file action chain length must not exceed `MAX_FILE_ACTIONS` (`256`) `[binfmt_copyactions.c:binfmt_copyactions]`.
- Shebang script recursion depth (`binp->scriptdepth`) must not exceed `SCRIPT_DEPTH_MAX` (`4`), returning `-ELOOP` otherwise `[script.c:script_loadbinary]`.
- When `CONFIG_BINFMT_BUILTIN_STRICT_PATH` is enabled, builtin paths containing `/` must reside on a mounted `BINFS` (`g_binfs_operations`) `[builtin.c:builtin_inbinfs]`.
- Fully linked ELF executables (`ET_EXEC`) reject non-empty exported symbol tables (`nexports > 0`) with `-ENOEXEC` `[elf.c:elf_loadbinary]`.
- `bin` passed to `binfmt_exit` must be non-NULL (`DEBUGASSERT(bin != NULL)`) and allocated via `kmm_malloc` `[binfmt_exit.c:binfmt_exit]`.
- If `CONFIG_EXECFUNCS_HAVE_SYMTAB` is enabled under `CONFIG_LIBC_EXECFUNCS`, both `CONFIG_EXECFUNCS_SYMTAB_ARRAY` and `CONFIG_EXECFUNCS_NSYMBOLS_VAR` must be defined `[binfmt_execsymtab.c:CONFIG_EXECFUNCS_HAVE_SYMTAB]`.

## Side Effects
- Mutates global linked list `g_binfmts` on registration/unregistration `[binfmt_register.c:register_binfmt]`.
- Allocates and frees kernel memory (`kmm_malloc`, `kmm_zalloc`, `kmm_free`) for `struct binary_s`, `struct tcb_s`, copied `argv`/`envp`/file actions, and PIC `dspace_s` `[binfmt_execmodule.c:exec_module]`.
- Switches and attaches address environments (`addrenv_select`, `addrenv_restore`, `addrenv_attach`) and initializes user heap (`umm_initialize`) in kernel builds `[binfmt_execmodule.c:exec_module]`.
- Swaps parent and child PIDs, `g_pidhash` entries, task group IDs, and TLS PID fields under critical section when `spawn` is false (`exec_swap`) `[binfmt_execmodule.c:exec_swap]`.
- Applies `S_ISUID`/`S_ISGID` credentials, sets `GROUP_FLAG_SECURE_EXEC`, clears `GROUP_FLAG_FD_BACKTRACE | GROUP_FLAG_DUMPABLE`, and sanitizes environment (`env_sanitize_secure`) `[binfmt_execmodule.c:exec_module]`.
- Initializes and activates new tasks (`nxtask_init`, `nxtask_activate`) and sets `errno` in `exec()` on failure `[binfmt_exec.c:exec]`.
- Unmaps memory-mapped files (`file_munmap`) in `unload_module` `[binfmt_unloadmodule.c:unload_module]`.
- Acquires spinlock with interrupts disabled (`spin_lock_irqsave(&g_exec_lock)`) to read or update `g_exec_symtab` and `g_exec_nsymbols` `[binfmt_execsymtab.c:exec_setsymtab]`.

## Verification
- Run: `make test`
