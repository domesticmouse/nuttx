# 6LoWPAN (`net/sixlowpan`)

## Overview
The `net/sixlowpan` component implements IPv6 over Low-Power Wireless Personal Area Networks (6LoWPAN, RFC 4944 and RFC 6282) for IEEE 802.15.4 and generic packet radio drivers (`struct radio_driver_s`). It provides IPHC (`HC06`) and `HC1` IPv6/UDP header compression and decompression, 6LoWPAN fragmentation (`FRAG1`/`FRAGN`) and reassembly (`struct sixlowpan_reassbuf_s`), MAC-to-IID address derivation, and TCP/UDP/ICMPv6 transmission hooks over radio interfaces.

## Interface
- `[sixlowpan_initialize.c:sixlowpan_initialize]` - Initializes the 6LoWPAN subsystem, HC06 context table, and reassembly buffer pool.
- `[sixlowpan_tcpsend.c:psock_6lowpan_tcp_send]` - Sends a TCP packet from a socket over a 6LoWPAN radio (`[sixlowpan_tcpsend.c:sixlowpan_tcp_send]` sends internal TCP protocol frames).
- `[sixlowpan_udpsend.c:psock_6lowpan_udp_send]` - Sends a connected UDP datagram over 6LoWPAN (`[sixlowpan_udpsend.c:psock_6lowpan_udp_sendto]` and `[sixlowpan_udpsend.c:sixlowpan_udp_send]` handle unconnected and internal UDP transmissions).
- `[sixlowpan_icmpv6send.c:sixlowpan_icmpv6_send]` - Transmits an ICMPv6 packet over a 6LoWPAN radio interface.
- `[sixlowpan_send.c:sixlowpan_send]` - Compresses, fragments, and queues an IPv6 packet + upper-layer payload for transmission via `radio`.
- `[sixlowpan_input.c:sixlowpan_input]` - Processes incoming 6LoWPAN radio frames (`FRAG1`, `FRAGN`, `IPHC`, `HC1`, uncompressed `IPv6`), reassembling and decompressing them into `radio->r_dev.d_iob` before dispatching to `ipv6_input`.
- `[sixlowpan_framelist.c:sixlowpan_queue_frames]` - Compresses and slices an outbound IPv6 packet into a queue of radio frames.
- `[sixlowpan_framer.c:sixlowpan_meta_data]` - Populates link-layer frame metadata (`[sixlowpan_framer.c:sixlowpan_frame_hdrlen]` computes L2 header length; `[sixlowpan_framer.c:sixlowpan_frame_submit]` submits a frame to `radio->r_req_data`).
- `[sixlowpan_hc06.c:sixlowpan_hc06_initialize]` - Initializes RFC 6282 IPHC address contexts (`[sixlowpan_hc06.c:sixlowpan_compresshdr_hc06]` and `[sixlowpan_hc06.c:sixlowpan_uncompresshdr_hc06]` compress and decompress IPHC headers).
- `[sixlowpan_hc1.c:sixlowpan_compresshdr_hc1]` - Compresses IPv6/UDP headers using RFC 4944 HC1 (`[sixlowpan_hc1.c:sixlowpan_uncompresshdr_hc1]` decompresses HC1 headers).
- `[sixlowpan_reassbuf.c:sixlowpan_reass_initialize]` - Initializes the reassembly buffer pool (`[sixlowpan_reassbuf.c:sixlowpan_reass_allocate]`, `[sixlowpan_reassbuf.c:sixlowpan_reass_find]`, and `[sixlowpan_reassbuf.c:sixlowpan_reass_free]` manage `struct sixlowpan_reassbuf_s` buffers).
- `[sixlowpan_utils.c:sixlowpan_nexthopaddr]` - Resolves the next-hop link-layer address for a destination IPv6 address (`[sixlowpan_utils.c:sixlowpan_destaddrfromip]`, `[sixlowpan_utils.c:sixlowpan_ipfromaddr]`, and `[sixlowpan_utils.c:sixlowpan_ismacbased]` convert between IPv6 IIDs and short/extended MAC addresses).
- `[sixlowpan_globals.c:g_uncomp_hdrlen]` - Shared global tracking uncompressed IPv6 header offset during compression/decompression (`[sixlowpan_globals.c:g_frame_hdrlen]` tracks current frame header length).

## Invariants
- All 6LoWPAN compression, decompression, framing, and reassembly functions must execute with the global network lock held because `[sixlowpan_globals.c:g_uncomp_hdrlen]` and `[sixlowpan_globals.c:g_frame_hdrlen]` are shared across all radio interfaces.

## Side Effects
- Allocates and frees IOB frames and `struct sixlowpan_reassbuf_s` reassembly buffers, mutates `radio->r_dev.d_iob`, and submits outbound frames to the radio driver via `radio->r_req_data`.

## Verification
- Run: `make test`
