# `giant-board/helpers` Component (`boards/arm/sama5/giant-board/helpers`)

## Overview
Board support component `helpers` for `giant-board` (`arm/sama5`), containing 1 source/script file(s) (`netusb-up.sh`).

## Interface
- `[netusb-up.sh]` Shell script entry point `netusb-up.sh`

## Invariants
- None

## Side Effects
- `[netusb-up.sh]` Executes shell commands on the host environment

## Verification
- Run: `./tools/configure.sh giant-board:nsh && make`
