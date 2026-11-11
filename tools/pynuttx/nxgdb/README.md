# NuttX GDB Extension (`nxgdb`)

## Overview
Provides a comprehensive suite of Python-based GDB commands, convenience functions, and data structure inspectors for live and post-mortem debugging of NuttX kernels. It inspects threads/tasks, stacks, heaps, memory pools, memory leaks, filesystems, circular buffers, interrupts, network sockets/IOBs, RPMsg endpoints, uORB topics, watchdogs, and work queues.

## Interface
- `__init__.py:register_commands` - Auto-discovers and registers all `gdb.Command` subclasses across `nxgdb` modules when an object file is loaded into GDB.
- `utils.py:Value`, `utils.py:Backtrace`, `utils.py:ArrayIterator`, `utils.py:ContainerOf`, `utils.py:Hexdump`, `utils.py:Addr2Line`, `utils.py:lookup_type`, `utils.py:get_symbol_value`, `utils.py:container_of`, `utils.py:parse_and_eval`, `utils.py:get_tcbs`, `utils.py:get_tcb` - Core GDB value wrappers, DWARF/macro resolution, target memory/register readers, and GDB commands `hexdump`, `addr2line`, and `$container_of`.
- `macros.py:Macro`, `macros.py:fetch_macro_info`, `macros.py:try_expand` - Extracts `.debug_macro` DWARF definitions via `readelf -wm` and expands C preprocessor macros out-of-frame.
- `prefix.py:ForeachPrefix`, `prefix.py:MMPrefixCommand` - Registers prefix commands `foreach` and `mm`.
- `thread.py:Registers`, `thread.py:SetRegs`, `thread.py:Nxinfothreads`, `thread.py:Nxthread`, `thread.py:Nxcontinue`, `thread.py:Nxstep`, `thread.py:Ps`, `thread.py:DeadLock` - Thread context switching (`setregs`, `nxthread`/`thread`, `info nxthreads`, `nxcontinue`, `nxstep`), `ps` summary, and mutex `deadlock` detection.
- `stack.py:Stack`, `stack.py:StackUsage`, `stack.py:fetch_stacks` - Thread stack coloration inspection and `stack-usage` command.
- `mm.py:MMHeap`, `mm.py:MMNode`, `mm.py:MemPool`, `mm.py:MemPoolMultiple`, `mm.py:MemPoolBlock`, `mm.py:MMHeapInfo`, `mm.py:MMPoolInfo`, `mm.py:get_heaps`, `mm.py:get_pools` - Heap and memory pool models and `mm heap` / `mm pool` (`mempool`) commands.
- `memdump.py:MMDump`, `memdump.py:MMfrag`, `memdump.py:MMMap`, `memdump.py:MMFree`, `memdump.py:dump_nodes`, `memdump.py:parse_memdump_log` - Commands `mm dump` (`memdump`), `mm frag` (`memfrag`), `mm map` (`memmap`), and `mm free` (`free`).
- `memcheck.py:MMCheck` - Heap and free-list corruption checker command `mm check` (`memcheck`).
- `memleak.py:MMLeak`, `memleak.py:GlobalNode` - Reachability-based memory leak detector command `mm leak` (`memleak`).
- `fs.py:Inode`, `fs.py:Fdinfo`, `fs.py:Mount`, `fs.py:ForeachInode`, `fs.py:InfoShmfs`, `fs.py:foreach_inode`, `fs.py:foreach_file` - Filesystem inspection commands `fdinfo`, `mount`, `foreach inode`, and `info shm`.
- `lists.py:NxList`, `lists.py:NxSQueue`, `lists.py:NxDQueue`, `lists.py:ListCheck`, `lists.py:ForeachListEntry`, `lists.py:ForeachArray` - Kernel linked-list iterators and commands `list_check`, `foreach list`, and `foreach array`.
- `circbuf.py:CircBuf`, `circbuf.py:CircBufInfo` - Circular buffer inspector and `circbuf` command.
- `dmesg.py:Dmesg` - RAM log (`g_sysdev`) and RPMsg syslog (`g_syslog_rpmsg`) reader command `dmesg`.
- `diagnose.py:DiagnosePrefix`, `diagnose.py:DiagnoseReport` - Diagnostic runner command `diagnose report` aggregating JSON reports from commands implementing `diagnose()`.
- `gcore.py:NXGcore` - Core dump generator command `nxgcore`.
- `irq.py:IRQInfo`, `irq.py:IRQInfoDump`, `irq.py:get_irqs` - Interrupt vector table inspector command `irqinfo`.
- `net.py:NetStats`, `net.py:NetCheck`, `net.py:socket_for_each_entry` - Network statistics (`netstats`) and IOB check (`netcheck`) commands.
- `rpmsg.py:RPMsgDump` - RPMsg device and endpoint inspector command `rpmsgdump`.
- `uorb.py:Sensor`, `uorb.py:uORBDump`, `uorb.py:get_topics` - uORB sensor topic inspector command `uorb`.
- `wdog.py:WDog`, `wdog.py:WDogDump`, `wdog.py:get_wdog_list` - Active watchdog timer inspector command `wdog`.
- `wqueue.py:Work`, `wqueue.py:KWorker`, `wqueue.py:WorkQueue`, `wqueue.py:WorkQueueDump`, `wqueue.py:get_work_queues` - Kernel work queue inspector command `worker`.
- `debug.py:DebugPy`, `profile.py:Profile`, `profile.py:Time` - Developer utilities `debugpy`, `profile`, and `time`.
- `./protocols/README.md` - Static typing protocols (`typing.Protocol`) mirroring `gdb.Value` and NuttX kernel C structures.

## Invariants
- `prefix.py:ForeachPrefix` and `prefix.py:MMPrefixCommand` must be initialized before other modules in `__init__.py:register_commands` so subcommands (`foreach *`, `mm *`) attach to valid GDB prefix commands.
- When inspecting non-running threads via `thread.py:Registers.load` or `thread.py:SetRegs`, `thread.py:Registers.save` must preserve the active frame's registers and `thread.py:Registers.restore` must be called before resuming execution (`nxcontinue`, `nxstep`).
- Auxiliary inferior 2 created by `utils.py:get_symbol_value` or `utils.py:switch_inferior` is used only for symbol/macro scope resolution and must always switch back to inferior 1 before returning.

## Side Effects
- Mutates GDB session settings (`set pagination off`, `set python print-stack full`, `handle SIGUSR1`), registers GDB commands/aliases, and creates a secondary unattached GDB inferior in `__init__.py:register_commands` and `utils.py:switch_inferior`.
- Modifies GDB register state (`set $<reg>=...`) when switching thread contexts in `thread.py:Registers.load` and `thread.py:Registers.restore`.
- Spawns `readelf -wm` and caches parsed macro JSON in the system temp directory (`macros.py:fetch_macro_info`), caches ELF global symbol tables (`<md5>-globals.json` in `memleak.py:MMLeak.global_nodes`), writes diagnostic JSON (`diagnose.py:DiagnoseReport.invoke`), writes PNG heatmaps (`memdump.py:MMMap.save_memory_map`), and invokes `objcopy` and GDB `gcore` to generate core files (`gcore.py:NXGcore.invoke`).

## Verification
- Run: `make test`
