# 🏛️ MIPS32 5-Stage Pipelined Processor

A robust **Verilog** implementation of a 32-bit RISC processor. This design utilizes a **5-stage pipeline** to achieve high instruction throughput by processing multiple instructions simultaneously.

---

### 🚀 Core Features
* **5-Stage Pipeline:** Implemented via **IF, ID, EX, MEM, and WB** stages.
* **Dual-Phase Clocking:** Uses `clk1` and `clk2` to eliminate race conditions between pipeline stages.
* **Rich ISA:** Native support for arithmetic, logical, memory, and control flow instructions.
* **Performance:** Includes a dedicated **Multiplication (MUL)** unit and **Set-on-Less-Than (SLT)** logic.

---

### 📑 The 5-Stage Pipeline
The processor splits instruction execution into five distinct stages to increase efficiency:

* **IF (Instruction Fetch):** The PC provides the address to fetch the instruction from memory.
* **ID (Instruction Decode):** Decodes the 32-bit instruction and reads values from the Register File.
* **EX (Execute):** The ALU performs calculations or target address computation.
* **MEM (Memory Access):** Handles Data Memory communication for Load (`LW`) and Store (`SW`).
* **WB (Write Back):** Writes the final results back into the destination register.

---

### 📑 Instruction Set Architecture (ISA)


| Category | Instructions |
| :--- | :--- |
| **Arithmetic** | `ADD`, `SUB`, `MUL`, `ADDI`, `SUBI` |
| **Logical** | `AND`, `OR` |
| **Comparison** | `SLT`, `SLTI` |
| **Memory** | `LW` (Load Word), `SW` (Store Word) |
| **Control** | `BEQZ`, `BNEQZ`, `HLT` (Halt) |

---

### 🛠 Architecture at a Glance
* **Registers:** 32 General Purpose 32-bit Registers (`Reg[0-31]`).
* **Memory:** 1024 x 32-bit word-addressable memory space.
* **Pipelining:** Uses internal registers (IF/ID, ID/EX, EX/MEM, MEM/WB) to bridge stages.

---

### 🧪 Verifying with AMD Vivado
This project is designed to be simulated using the **Vivado Design Suite**.

**Steps to Run:**
1. **Create Project:** Create a new "RTL Project" in Vivado and target your FPGA (or choose a generic part).
2. **Add Sources:** Add `pipe_MIPS32.v` as a Design Source and `test_mips32.v` as a Simulation Source.
3. **Run Simulation:** Click **Run Simulation > Run Behavioral Simulation**.
4. **Analyze Waves:** 
   * The testbench automatically probes internal signals like `PC` and `ALUOut`.
   * Check the **Tcl Console** to see the register values ($R0-$R5) printed at the end of the simulation.

**Tcl Command (Alternative):**
```tcl
launch_simulation
run 300ns
```

---

### 🤝 Contributing
Feel free to fork and add:
* **Hazard Detection Units** to handle data dependencies.
* **Forwarding Paths** to minimize pipeline stalls.

**Author:** Chethan Aithal  
**Date:** April 2026
