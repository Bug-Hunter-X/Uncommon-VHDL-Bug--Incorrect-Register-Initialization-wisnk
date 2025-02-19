# Uncommon VHDL Bug: Incorrect Register Initialization

This repository demonstrates a subtle bug in VHDL related to the initialization of an internal signal.  The problem arises from the way the initial value is assigned and how it interacts with the rest of the code.

## Bug Description

The `internal_reg` signal in the provided VHDL code is initialized to `x"00"`.  This value, while seemingly harmless, can cause problems if the synthesis tool does not properly handle undefined or high-impedance states during simulation or synthesis.

## How to Reproduce

1. Synthesize and simulate the provided `bug.vhdl` code using a VHDL simulator (e.g., ModelSim, GHDL).
2. Observe the behavior of `data_out` during simulation, paying close attention to the first few clock cycles. 
3. You may notice unexpected or undefined outputs, depending on your simulator's handling of uninitialized signals.

## Solution

The solution involves initializing `internal_reg` to a known, well-defined value, such as all zeros (`"00000000"`) or all ones (`"11111111"`). This makes the code more robust and predictable.
