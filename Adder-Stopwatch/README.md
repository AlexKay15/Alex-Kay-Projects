# Interrupt-Driven Stopwatch

Built a stopwatch in Nios II assembly for the DE10-Lite board using timer and pushbutton interrupts. The system tracks minutes, seconds, and hundredths of a second, and supports start, stop, lap, resume, and reset behavior with real-time seven-segment display output.

## Overview

This project replaced a polling-based design with an interrupt-driven stopwatch architecture. A hardware timer interrupt provides periodic time updates, while pushbutton interrupts handle user input and state transitions.

The stopwatch maintains time in minutes, seconds, and hundredths, and displays the current value on the board’s seven-segment displays. It also supports a lap mode that freezes the visible display while the internal time continues to advance.

## Technical Highlights

- Implemented timer interrupt-driven timekeeping in Nios II assembly
- Used pushbutton interrupts for user input and state transitions
- Designed stopwatch control logic for start, stop, lap, resume, and reset
- Stored and updated time as minutes, seconds, and hundredths
- Converted numeric values into seven-segment display output
- Managed interrupt context saving and restoring inside exception handlers

## System Behavior

The stopwatch supports:
- **Start / Stop** using pushbutton input
- **Lap** mode to freeze the displayed time while internal timing continues
- **Resume** to restore live display updates
- **Reset** to clear time back to `00:00.00` when stopped

The design uses:
- timer interrupts for fixed-rate time updates
- pushbutton interrupts for event-driven control
- memory-mapped I/O for hardware interaction
- seven-segment output formatting for live display

## What I Learned

This project gave me hands-on experience with:
- interrupt-driven embedded software design
- exception handling in Nios II assembly
- low-level state machine implementation
- timer-based scheduling
- hardware interfacing through memory-mapped I/O
- real-time display control on FPGA-based hardware

## Tools and Topics

- Nios II assembly
- DE10-Lite
- Timer interrupts
- Pushbutton interrupts
- Exception handling
- Memory-mapped I/O
- Seven-segment displays
- Embedded systems

---

# Interrupt-Driven JTAG Adder

Built a Nios II assembly program for the DE10-Lite board that receives signed integer input over JTAG UART, maintains a running sum, and displays the result on seven-segment displays. The design uses interrupts, supports negative values, and resets on overflow outside the displayable range.

## Overview

This project implemented an interrupt-driven integer adder using the JTAG UART interface as the primary input source. When a user enters a number through the terminal, the program reads the ASCII input, converts it into a signed integer, adds it to a running total, and displays the updated result on the board’s seven-segment displays.

The system supports both positive and negative input values and handles overflow by resetting the running total when the result exceeds the supported display range.

## Technical Highlights

- Implemented JTAG UART interrupt handling in Nios II assembly
- Read terminal input through memory-mapped JTAG UART registers
- Echoed user input back through the terminal interface
- Converted ASCII strings into signed integers
- Maintained a running signed sum across inputs
- Displayed positive and negative results on seven-segment displays
- Added overflow handling by resetting values outside the supported display range
- Managed exception handling and register preservation during interrupts

## System Behavior

The program:
- waits for terminal input through JTAG UART
- reads a signed integer entered by the user
- converts the input from ASCII into an integer value
- adds the value to a running total
- displays the result on seven-segment hardware output
- shows negative values with a minus sign
- resets the total to zero when overflow exceeds the displayable range

## What I Learned

This project strengthened my understanding of:
- interrupt-driven input handling
- low-level serial-style communication through JTAG UART
- string-to-integer conversion in assembly
- signed arithmetic in embedded systems
- seven-segment display encoding
- exception handling and ISR design in Nios II

## Tools and Topics

- Nios II assembly
- DE10-Lite
- JTAG UART
- Interrupts
- ASCII parsing
- Signed integer arithmetic
- Memory-mapped I/O
- Seven-segment displays
- Embedded systems

 
