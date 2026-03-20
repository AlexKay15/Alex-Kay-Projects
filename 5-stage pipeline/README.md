# 5-Stage Pipeline Processor

Developing a multi-phase 5-stage pipelined processor in SystemVerilog for a computer organization course. The project focuses on building and extending pipeline stages, propagating control signals, and validating execution through simulation and waveform-based debugging.

## Overview

This project involves implementing a 5-stage pipelined processor step by step, with functionality added over multiple phases. My work has focused on extending the processor datapath and control logic so instructions move correctly through decode, execute, memory, and writeback stages.

A recent milestone added full support for `add` and `addi`, including decode-stage control generation, execute-stage ALU behavior, and writeback-stage register updates.

## Technical Highlights

- Implemented pipeline-stage logic in SystemVerilog
- Extended decode logic to generate ALU and register write control signals
- Implemented execute-stage operand selection and ALU behavior
- Passed destination register and control information through the pipeline
- Updated writeback behavior to correctly drive register file writes
- Used simulation, testbenches, and waveform inspection to debug and validate processor behavior

## Current Milestone

The current phase supports full implementation of:
- `add`
- `addi`

This work included:
- decoding instruction fields and control signals
- selecting between register and immediate ALU inputs
- performing ALU addition in the execute stage
- forwarding writeback information through memory and writeback stages
- preventing writes to register `x0`

## What I Learned

This project has strengthened my understanding of:
- pipelined processor organization
- stage-by-stage datapath design
- control signal generation
- register file interactions
- simulation-based hardware debugging
- verifying behavior using waveforms and test programs

## Tools and Topics

- SystemVerilog
- Computer architecture
- Pipelined processors
- Datapath and control design
- Testbenches
- Waveform debugging

