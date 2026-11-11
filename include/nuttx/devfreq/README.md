# Device Frequency Scaling (Devfreq) Headers (`include/nuttx/devfreq`)

## Overview
Provides the Quality of Service (QoS) frequency constraint aggregation interface for the NuttX dynamic device frequency scaling (`devfreq`) subsystem.

## Interface
- `devfreq_qos.h:qos_req_type_e` - QoS constraint bound selector (`QOS_REQ_MIN`, `QOS_REQ_MAX`).
- `devfreq_qos.h:qos_request_s`, `devfreq_qos.h:qos_constraints_s` - Priority-list (`plist_node` / `plist_head`) request node and aggregated min/max constraint container.
- `devfreq_qos.h:qos_constraints_init`, `devfreq_qos.h:qos_add_request`, `devfreq_qos.h:qos_remove_request`, `devfreq_qos.h:qos_update_request`, `devfreq_qos.h:qos_get_value` - Lifecycle and query functions for adding, updating, removing, and evaluating min/max QoS frequency requests.

## Invariants
- `devfreq_qos.h:qos_constraints_init` must be called on a `qos_constraints_s` instance before adding or querying requests.
- `devfreq_qos.h:qos_constraints_s` orders `min_requests` and `max_requests` via priority lists (`plist_head`) so `qos_get_value` returns the effective extreme constraint in O(1) time.

## Side Effects
- `devfreq_qos.h:qos_add_request` allocates a `qos_request_s` structure (and records a caller backtrace when `CONFIG_DEVFREQ_PROCFS_QOS` is enabled) and inserts it into `constraints`.
- `devfreq_qos.h:qos_remove_request` unlinks and frees the `qos_request_s` instance.

## Verification
- Run: `make test`
