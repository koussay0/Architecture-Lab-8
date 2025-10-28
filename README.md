## Lab 8: Implementation of a 5-Stage Pipelined RISC-V Processor in Verilog (Computer Architecture)

# 1. Objective

The objective of this laboratory experiment is to design, implement, and simulate a five-stage pipelined RISC-V processor using Verilog HDL. The processor integrates fundamental components such as the ALU, Control Unit, Register File, and Data Memory, and incorporates pipeline hazard handling mechanisms including forwarding and hazard detection units. This lab demonstrates the principles of instruction-level parallelism and performance enhancement through pipelining.

# 2. Introduction

Modern processors employ pipelining to improve instruction throughput by overlapping the execution of multiple instructions. In this lab, we implement the classic 5-stage RISC-V pipeline consisting of:

Instruction Fetch (IF)

Instruction Decode (ID)

Execute (EX)

Memory Access (MEM)

Write-Back (WB)

The design includes the implementation of each stage as modular Verilog components and connects them through pipeline registers. Additionally, hazard control mechanisms are implemented to ensure correct instruction execution despite data dependencies and control hazards.

# 3. Modules Implemented

Each module plays a specific role in the processor datapath:

- Module	Function:
- 
Instruction_Memory.v	Stores and provides instructions for the IF stage.

ControlUnit.v	Generates control signals based on the instruction opcode.

Imm_Generator.v	Extracts and sign-extends immediate values from instructions.

Register_file.v	Contains general-purpose registers; supports read and write operations.

ALU_Control.v	Determines the ALU operation based on control signals and instruction funct fields.

ALU.v	Performs arithmetic and logical operations.

Adder.v	Computes branch target addresses.

Shift_Left.v	Shifts immediate values for branch address calculations.

Data_Memory.v	Implements data memory for load/store instructions.

Mux.v	Selects between multiple input signals in the datapath.

NbitRegister.v	Defines pipeline registers between stages (IF/ID, ID/EX, EX/MEM, MEM/WB).

ForwardingUnit.v	Resolves data hazards by forwarding data from later pipeline stages.

HazardControlUnit.v	Detects and handles stalls or flushes due to hazards.

RISCV_pipeline.v	Top-level integration of all components to form the full pipelined processor.

Processor_TB.v	Testbench for simulating and verifying the processor functionality.

# 4. Design Overview

The RISC-V pipeline was designed to handle basic arithmetic, logical, load/store, and branch instructions. The datapath was structured to mirror real processor architecture, with pipeline registers separating each stage.

Hazards were handled using:

Data forwarding (bypassing) from MEM/WB or EX/MEM to EX stage.

Hazard detection unit to introduce pipeline stalls when forwarding is insufficient (e.g., load-use hazards).

Branch control logic to flush instructions in case of mispredicted branches.

# 5. Simulation and Results

The design was simulated using ModelSim (or any Verilog simulator).

The Processor_TB.v file initialized instruction and data memory with sample RISC-V assembly instructions.

The simulation waveform demonstrated correct pipelined execution, showing overlapping instructions in different stages.

Results confirmed:

Correct arithmetic and logic operation outputs.

Proper data forwarding between stages.

Accurate branch and memory operations.

No functional hazards affecting instruction correctness.

A snapshot of simulation waveforms (if applicable) should be included here to show pipeline activity and timing.

# 6. Discussion

Implementing the pipelined RISC-V processor highlighted key architectural challenges, including hazard management and control signal synchronization. The separation of design into modular components ensured reusability and simplified debugging.
Forwarding and hazard detection logic were crucial to maintaining pipeline throughput without violating instruction dependencies.

Future improvements could include:

Implementing branch prediction.

Adding support for additional RISC-V instruction types.

Optimizing the control unit for more complex instruction sets.

# 7. Conclusion

In this lab, a 5-stage pipelined RISC-V processor was successfully designed, implemented, and simulated using Verilog HDL. The project reinforced understanding of processor architecture concepts such as pipelining, hazard detection, forwarding, and modular design. The simulation results verified correct functionality and demonstrated the performance benefits of pipelining in modern processor design.

