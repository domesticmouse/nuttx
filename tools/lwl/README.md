# lwl

## Overview
Host-side Lightweight Link (LWL) debug console client (`tools/lwl`) that communicates with a target running NuttX over an OpenOCD TCL RPC socket (`127.0.0.1:6666`) without requiring UART hardware or halting the CPU.

## Interface
- `ocdconsole.py:oocd` - OpenOCD TCL RPC client class providing `send`, `readVariable`, `writeVariable`, and `testInterface` over TCP port `6666`.
- `ocdconsole.py:LWL_SIG` (`0x7216A318`), `ocdconsole.py:LWL_PORT_CONSOLE` (`1`) - Magic signature and console port number used to locate and multiplex the LWL shared-memory link in target RAM.
- `ocdconsole.py:kbhit`, `ocdconsole.py:dooutput` - Non-blocking terminal input polling (`select.select`) and raw console output writer.

## Invariants
- Target RAM between `baseaddr` (`0x20000000`) and `baseaddr + length` (`0x8000`) must contain a valid `LWL_SIG` word (`0x7216A318`) immediately preceding the `downwordaddr` and `upwordaddr` 32-bit mailbox words.
- Downlink and uplink 32-bit transfer words encode valid-bit (`1 << 31`), port ID (`bits 27..30`), byte count (`bits 24..26`), and up to 3 payload bytes (`bits 0..23`).

## Side Effects
- Connects to OpenOCD via TCP socket on `127.0.0.1:6666` (`ocdconsole.py:oocd.__init__`) and issues `mdw`/`ocd_mdw` and `mww` memory read/write commands to target RAM.
- Switches standard input into raw terminal mode via `tty.setraw` and restores saved `termios` attributes on exit.

## Verification
- Run: `make test`
