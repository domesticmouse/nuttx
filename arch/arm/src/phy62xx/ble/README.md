# ble (`nuttx/arch/arm/src/phy62xx/ble`)

## Overview
Hardware abstraction and architecture package for `ble` under `nuttx/arch/arm/src/phy62xx/ble`, providing 1 header file(s) and 0 source file(s) (including `ble_controller.h`).

## Interface
- `[ble_controller.h:phy62xx_ble_init]`
- `[ble_controller.h:Sleep_Mode]`
- `[ble_controller.h:l2capPacket_t]`
- `[ble_controller.h:segmentBuff_t]`
- `[ble_controller.h:l2capSegmentBuff_t]`
- `[ble_controller.h:osal_event_hdr_t]`
- `[ble_controller.h:hciEvt_DisconnComplete_t]`
- `[ble_controller.h:connParam_t]`
- `[ble_controller.h:chanMap_t]`
- `[ble_controller.h:preChanMapUpdate_t]`
- `[ble_controller.h:txData_t]`
- `[ble_controller.h:llDataQ_t]`
- `[ble_controller.h:ctrlPktInfo_t]`
- `[ble_controller.h:encInfo_t]`
- `[ble_controller.h:featureSet_t]`
- `[ble_controller.h:verExchange_t]`
- `[ble_controller.h:verInfo_t]`
- `[ble_controller.h:termInfo_t]`
- `[ble_controller.h:perInfo_t]`
- `[ble_controller.h:ll_phy_update_ind_t]`
- `[ble_controller.h:ll_pdu_length_ctrl_t]`
- `[ble_controller.h:llPduLenManagment_t]`
- `[ble_controller.h:ll_phy_ctrl_t]`
- `[ble_controller.h:llPhyModeManagment_t]`
- `[ble_controller.h:ll_pkt_desc]`
- `[ble_controller.h:llLinkBuf_t]`
- `[ble_controller.h:llLinkStatistics_t]`
- `[ble_controller.h:llCTEModeManagement_t]`
- `[ble_controller.h:CTEInfo_t]`
- `[ble_controller.h:llConnState_t]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
