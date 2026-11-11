# DMA Buffer Sharing Framework (`drivers/dma-buf`)

## Overview
Implements the NuttX `dma-buf` and `dma-heap` buffer sharing subsystem, enabling cross-driver DMA buffer export, file descriptor wrapping, device attachment/mapping, CPU cache access synchronization, and `/dev/dma_heap/*` character device allocation (including the system heap).

## Interface
- `dma-buf.c:dma_buf_export`, `dma-buf.c:dma_buf_fd`, `dma-buf.c:dma_buf_get`, `dma-buf.c:dma_buf_put` - Exports a `dma_buf_s` backed by `dma_buf_ops_s`, binds it to an anonymous file descriptor, looks up a `dma_buf_s` from an `fd`, and releases references.
- `dma-buf.c:dma_buf_attach`, `dma-buf.c:dma_buf_detach`, `dma-buf.c:dma_buf_map_attachment`, `dma-buf.c:dma_buf_unmap_attachment` - Attaches/detaches target DMA devices (`dma_buf_attachment_s`) and maps/unmaps scatter-gather or contiguous DMA regions.
- `dma-buf.c:dma_buf_begin_cpu_access`, `dma-buf.c:dma_buf_end_cpu_access` - Synchronizes CPU cache coherency before and after CPU access to a shared DMA buffer.
- `dma-heap.c:dma_heap_add` - Registers a DMA heap character device at `/dev/dma_heap/<name>` supporting `DMA_HEAP_IOCTL_ALLOC`.
- `system_heap.c:dmabuf_system_heap_create`, `system_heap.c:system_heap_buffer`, `system_heap.c:dma_heap_attachment` - Creates the kernel `system` DMA heap backed by `kmm_zalloc` and `mm_map_add`.

## Invariants
- `dma-buf.c:dma_buf_export` requires `exp_info->priv != NULL`, `exp_info->ops != NULL`, `exp_info->ops->release != NULL`, and `exp_info->size > 0`.
- `dma-buf.c:dma_buf_put`, `dma-buf.c:dma_buf_attach`, and `dma-buf.c:dma_buf_detach` assert `dmabuf != NULL`.
- `dma-heap.c:dma_heap_add` requires a non-empty `exp_info->name` and `exp_info->ops->allocate != NULL`.

## Side Effects
- Allocates `dma_buf_s`, `dma_heap_s`, and backing system heap buffers via `kmm_zalloc` (`dma-buf.c:dma_buf_export`, `dma-heap.c:dma_heap_add`, `system_heap.c:dmabuf_system_heap_create`).
- Allocates file descriptors via `file_allocate_from_inode` and closes files via `file_put` (`dma-buf.c:dma_buf_fd`, `dma-buf.c:dma_buf_put`).
- Acquires `dmabuf->lock` and `buffer->lock` via `nxmutex_lock` during attachment, mapping, and `mmap` operations (`dma-buf.c:dma_buf_attach`, `system_heap.c:dmabuf_system_heap_create`) and registers `/dev/dma_heap/*` character devices via `register_driver` (`dma-heap.c:dma_heap_add`).

## Verification
- Run: `make test`
