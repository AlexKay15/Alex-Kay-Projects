# Alex Kay – Computer Engineering Projects

Electrical and Computer Engineering student at the University of Colorado Boulder with experience in concurrent programming, real-time operating systems, embedded systems, computer organization, interrupt-driven systems, and low-level software development.
## Featured Projects

### Concurrent Containers
Implemented several concurrent stack and queue algorithms, including coarse-grained and lock-free data structures. This project focused on synchronization, correctness under concurrency, and performance across varying thread counts.

**Description:**
- Implemented concurrent stack and queue data structures
- Worked with lock-free designs such as the Treiber stack and Michael & Scott queue
- Explored throughput across different thread counts
- Focused on concurrent algorithm behavior and systems-level performance

**Code:** Private course repository  


---

### RTOS Labyrinth Game (In Progress)
Developing a real-time embedded labyrinth game on the STM32F429I-DISC1 for a Real-Time Operating Systems course. The project uses gyroscope input, LCD graphics, LEDs, button input, and randomized maze generation to create a physics-based maze game.

**Description:**
- Developing a real-time game loop with fixed-rate physics updates
- Using gyroscope input to control movement through a virtual maze
- Generating randomized maze layouts with walls, holes, and waypoints
- Designing embedded feedback with LEDs, LCD graphics, and button input
- Implementing energy-based disruptor behavior as part of the game mechanics
- Applying RTOS and embedded systems concepts to a multi-component interactive project

**Code:** Private course repository  


---

### 5-Stage Pipeline Processor (In Progress)
Developing a multi-phase 5-stage pipelined processor in SystemVerilog for a computer organization course. The current phase adds support for `add` and `addi` by extending decode, execute, memory, and writeback behavior across the pipeline.

**Description:**
- Implemented pipeline-stage logic in SystemVerilog
- Added ALU control and source-selection signals in the decode stage
- Implemented execute-stage ALU behavior for `add` and `addi`
- Passed register writeback information through memory and writeback stages
- Used testbenches and waveform-based debugging to validate functionality

**Code:** Private course repository  


---

### Interrupt-Driven JTAG Adder
Built a Nios II assembly program for the DE10-Lite that receives signed integer input over JTAG UART, maintains a running sum, and displays the result on seven-segment displays. The design uses interrupts, supports negative values, and resets when the running total exceeds the supported display range.

**Description:**
- Implemented JTAG UART interrupt handling in Nios II assembly
- Converted ASCII terminal input into signed integers
- Maintained a running signed sum with overflow wrap handling
- Displayed positive and negative values on seven-segment displays

**Code:** Private course repository  


---

### Interrupt-Driven Stopwatch
Built a stopwatch in Nios II assembly using timer and pushbutton interrupts. The stopwatch tracks minutes, seconds, and hundredths of a second, and supports start, stop, lap, resume, and reset functionality with real-time seven-segment display output.

**Description:**
- Implemented timer interrupt-driven timekeeping
- Used pushbutton interrupts for state changes and user input
- Supported start, stop, lap, resume, and reset behavior
- Displayed formatted real-time timing data on seven-segment displays

**Code:** Private course repository  



