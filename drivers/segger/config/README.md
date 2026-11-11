# SEGGER RTT and SystemView Configuration (`drivers/segger/config`)

## Overview
Configuration headers that adapt the external SEGGER Real-Time Transfer (RTT) and SystemView libraries to NuttX's Kconfig parameters, spinlock primitives, cache alignment settings, and high-resolution performance counter APIs.

## Interface
- `[Global.h:U8]`, `[Global.h:I8]`, `[Global.h:U16]`, `[Global.h:I16]`, `[Global.h:U32]`, `[Global.h:I32]`, `[Global.h:U64]`, `[Global.h:I64]` - Fixed-width integer type macros required by SEGGER RTT and SystemView sources.
- `[SEGGER_RTT_Conf.h:g_segger_lock]`, `[SEGGER_RTT_Conf.h:g_segger_offset]` - External declarations for the global recursive spinlock and optional uncached memory offset variable.
- `[SEGGER_RTT_Conf.h:SEGGER_RTT_LOCK]`, `[SEGGER_RTT_Conf.h:SEGGER_RTT_UNLOCK]` - Critical section macros backed by `rspin_lock_irqsave_nopreempt` and `rspin_unlock_irqrestore_nopreempt`.
- `[SEGGER_RTT_Conf.h:SEGGER_RTT_BLOCK_IF_FIFO_FULL]`, `[SEGGER_RTT_Conf.h:SEGGER_RTT_IS_CONNECTED]`, `[SEGGER_RTT_Conf.h:SEGGER_RTT_IS_FIFO_MODE]` - Channel state inspection and dynamic FIFO blocking mode switch helpers.
- `[SEGGER_SYSVIEW_Conf.h:note_sysview_get_interrupt_id]`, `[SEGGER_SYSVIEW_Conf.h:note_sysview_get_timestamp]`, `[SEGGER_SYSVIEW_Conf.h:note_sysview_timestamp_freq]` - Interrupt ID and performance timer hooks mapped to `SEGGER_SYSVIEW_GET_INTERRUPT_ID`, `SEGGER_SYSVIEW_GET_TIMESTAMP`, and `SEGGER_SYSVIEW_TIMESTAMP_FREQ`.

## Invariants
- `[SEGGER_RTT_Conf.h:SEGGER_RTT_LOCK]` and `[SEGGER_RTT_Conf.h:SEGGER_RTT_UNLOCK]` must be invoked within the same lexical scope because `SEGGER_RTT_LOCK()` declares local variable `irqstate_t __flags`.
- `[SEGGER_RTT_Conf.h:SEGGER_RTT_UNCACHED_OFF]` must point to a valid uncached memory alias offset on architectures with data caches when accessing `_SEGGER_RTT.aUp`.

## Side Effects
- `[SEGGER_RTT_Conf.h:SEGGER_RTT_LOCK]` disables local interrupts and preemption while acquiring the recursive spinlock `g_segger_lock`.
- `[SEGGER_RTT_Conf.h:SEGGER_RTT_BLOCK_IF_FIFO_FULL]` mutates the up/down buffer flags via `SEGGER_RTT_SetFlagsUpBuffer` and `SEGGER_RTT_SetFlagsDownBuffer` once a host debugger connection is detected (`RdOff != 0`).

## Verification
- Run: `make test`
