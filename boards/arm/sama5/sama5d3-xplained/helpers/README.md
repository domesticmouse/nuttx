# `sama5d3-xplained/helpers` Component (`boards/arm/sama5/sama5d3-xplained/helpers`)

## Overview
Board support component `helpers` for `sama5d3-xplained` (`arm/sama5`), containing 1 source/script file(s) (`netusb-up.sh`).

## Interface
- `[netusb-up.sh]` Shell script entry point `netusb-up.sh`

## Invariants
- None

## Side Effects
- `[netusb-up.sh]` Executes shell commands on the host environment

## Verification
- Run: `./tools/configure.sh sama5d3-xplained:nsh && make`
