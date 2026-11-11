# vpnkit (`nuttx/arch/sim/src/sim/posix/vpnkit`)

## Overview
Hardware abstraction and architecture package for `vpnkit` under `nuttx/arch/sim/src/sim/posix/vpnkit`, providing 1 header file(s) and 2 source file(s) (including `sim_protocol.h`, `sim_negotiate.c`, `sim_protocol.c`).

## Interface
- `[sim_protocol.h:negotiate]`
- `[sim_protocol.h:create_init_message]`
- `[sim_protocol.h:read_init_message]`
- `[sim_protocol.h:write_init_message]`
- `[sim_protocol.h:print_init_message]`
- `[sim_protocol.h:write_command]`
- `[sim_protocol.h:write_ethernet_args]`
- `[sim_protocol.h:read_vif_response]`
- `[sim_protocol.h:really_read]`
- `[sim_protocol.h:really_write]`
- `[sim_protocol.h:init_message]`
- `[sim_protocol.h:command]`
- `[sim_protocol.h:response_type]`
- `[sim_protocol.h:ethernet_args]`
- `[sim_protocol.h:vif_info]`
- `[sim_protocol.h:disconnect_reason]`
- `[sim_protocol.h:msg_response]`
- `[sim_protocol.h:CURRENT_VERSION]`
- `[sim_negotiate.c:negotiate]`
- `[sim_protocol.c:really_read]`
- `[sim_protocol.c:really_write]`
- `[sim_protocol.c:create_init_message]`
- `[sim_protocol.c:print_init_message]`
- `[sim_protocol.c:read_init_message]`
- `[sim_protocol.c:write_init_message]`
- `[sim_protocol.c:read_vif_response]`
- `[sim_protocol.c:write_command]`
- `[sim_protocol.c:write_ethernet_args]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
