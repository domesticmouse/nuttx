# NuttX User Socket (usrsock) RPMsg Transport (`include/nuttx/usrsock`)

## Overview
Defines the RPMsg protocol extensions and server initialization entry point for forwarding NuttX user-space socket (`usrsock`) requests, fragmented responses, and DNS server configuration events across processor cores.

## Interface
- `usrsock_rpmsg.h:usrsock_rpmsg_dns_request_s`, `usrsock_rpmsg_dns_event_s`, `usrsock_rpmsg.h:usrsock_message_frag_ack_s` - Wire-format message structures for cross-core DNS server registration/events and fragmented payload acknowledgments.
- `usrsock_rpmsg.h:USRSOCK_RPMSG_EPT_NAME`, `usrsock_rpmsg.h:USRSOCK_RPMSG_DNS_REQUEST`, `usrsock_rpmsg.h:USRSOCK_RPMSG_DNS_EVENT`, `usrsock_rpmsg.h:USRSOCK_RPMSG_FRAG_RESPONSE` - RPMsg endpoint name (`"rpmsg-usrsock"`) and protocol message IDs.
- `usrsock_rpmsg.h:usrsock_rpmsg_server_initialize` - Initialization function for the RPMsg `usrsock` server daemon that proxies remote socket operations onto the local network stack.

## Invariants
- All `usrsock_rpmsg.h` protocol structures (`usrsock_rpmsg_dns_request_s`, `usrsock_rpmsg_dns_event_s`, `usrsock_message_frag_ack_s`) use `begin_packed_struct` / `end_packed_struct` to guarantee identical binary layout across heterogeneous CPU architectures.

## Side Effects
- `usrsock_rpmsg.h:usrsock_rpmsg_server_initialize` registers an RPMsg callback for the `"rpmsg-usrsock"` endpoint and opens local kernel sockets and DNS resolvers on behalf of remote processors.

## Verification
- Run: `make test`
