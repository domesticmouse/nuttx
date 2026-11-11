# misc

## Overview
Provides kernel assertion and panic orchestration, ELF core dump generation (`CONFIG_COREDUMP`), mutex deadlock cycle detection (`CONFIG_ARCH_DEADLOCKDUMP`), and atomic panic/reboot notifier chains.

## Interface
- `assert.c:_assert` - Kernel assertion failure and panic entry point that logs diagnostics, invokes panic/reboot notifiers, triggers core dumps, and halts or resets the system.
- `coredump.h:coredump_initialize` (`coredump.c:coredump_initialize`, `CONFIG_COREDUMP`) - Initializes the core dump block/MTD storage device (`CONFIG_BOARD_COREDUMP_BLKDEV` / `CONFIG_BOARD_COREDUMP_MTDDEV`).
- `coredump.h:coredump_dump` (`coredump.c:coredump_dump`, `CONFIG_COREDUMP`) - Generates an ELF core dump for the specified PID (or all threads) to syslog or persistent storage.
- `coredump.c:coredump_add_memory_region` (`CONFIG_COREDUMP`) - Registers custom memory regions (`struct memory_region_s`) to include in core dumps.
- `coredump.c:coredump` (`CONFIG_COREDUMP`) - Streams ELF core notes and memory segments to a `lib_outstream_s` writer.
- `deadlock.c:nxsched_collect_deadlock` (`CONFIG_ARCH_DEADLOCKDUMP`) - Detects mutex wait cycles using Floyd's tortoise-and-hare algorithm and populates a PID array of deadlocked tasks.
- `panic_notifier.c:panic_notifier_chain_register` - Registers a callback block on `panic_notifier.c:g_panic_notifier_list`.
- `panic_notifier.c:panic_notifier_chain_unregister` - Unregisters a callback block from `panic_notifier.c:g_panic_notifier_list`.
- `panic_notifier.c:panic_notifier_call_chain` - Invokes registered panic callbacks (`PANIC_KERNEL`, `PANIC_TASK`, `PANIC_KERNEL_FINAL`).
- `reboot_notifier.c:register_reboot_notifier` - Registers a callback block on `reboot_notifier.c:g_reboot_notifier_list`.
- `reboot_notifier.c:unregister_reboot_notifier` - Unregisters a callback block from `reboot_notifier.c:g_reboot_notifier_list`.
- `reboot_notifier.c:reboot_notifier_call_chain` - Invokes registered reboot callbacks (`SYS_RESTART`, `SYS_HALT`, `SYS_POWER_OFF`).

## Invariants
- `assert.c:_assert` serializes panic execution via `assert.c:g_assert_lock` (`spin_lock_irqsave_nopreempt`) once `OSINIT_OS_READY()` is true, and immediately invokes `assert.c:reset_board` if a nested panic occurs while `OSINIT_IS_PANIC()` is already set.
- `coredump.c:coredump` executes inside `enter_critical_section()` to snapshot task registers and memory consistently.

## Side Effects
- Sets `g_nx_initstate` to `OSINIT_PANIC`, disables KASAN (`kasan_stop`), pauses secondary CPUs via SMP IPI (`assert.c:pause_all_cpu`), flushes syslog (`syslog_flush`), dumps CPU registers, stacks, task states, and deadlocks, and resets (`up_systemreset`) or halts (`up_mdelay`) the board in `assert.c:_assert`.
- Writes compressed (`lib_lzfoutstream`) or raw ELF core dump streams to syslog (`lib_syslograwstream_open`) or block/MTD devices (`ftl_initialize_by_path`) in `coredump.c:coredump_dump`.

## Verification
- Run: `make test`
