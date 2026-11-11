# NuttX Graphics Subsystem (`graphics`)

## Overview
Root directory for the NuttX Graphics (`NX`) windowing and rasterization subsystem. Organizes the low-level pixel-depth-templated rasterizer library (`nxglib`), the Z-ordered window clipping and compositing back-end (`nxbe`), the multi-user message-queue display server (`nxmu`), and the VT100-capable character console driver (`nxterm`).

## Subdirectories & Boundaries
- **NX Graphics Library (`nxglib`)**: [./nxglib/README.md](./nxglib/README.md) - Low-level 1/2/4/8/16/24/32-bpp rasterizers for linear framebuffers (`fb`), indirect LCDs (`lcd`), per-window RAM framebuffers (`pwfb`), and software cursors (`cursor`).
- **NX Window Manager Back-End (`nxbe`)**: [./nxbe/README.md](./nxbe/README.md) - Window Z-order hierarchy, rectangular occlusion clipper (`nxbe_clipper`), per-window framebuffer synchronization, software cursor management, and device plane configuration.
- **NX Multi-User Server (`nxmu`)**: [./nxmu/README.md](./nxmu/README.md) - Multi-client NX server daemon (`nx_runinstance`, `nxmu_start`), POSIX message queue IPC dispatcher, background window ownership, and mouse/keyboard input routing.
- **NX Terminal Driver (`nxterm`)**: [./nxterm/README.md](./nxterm/README.md) - Character console driver (`/dev/nxtermN`) rendering cached font glyphs, VT100 escape sequences, scrolling text, and keyboard input onto NX/NXTK windows and toolbars.
