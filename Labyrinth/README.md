# RTOS Labyrinth Game

Developing a real-time embedded labyrinth game on the STM32F429I board using gyroscope input, LCD graphics, LEDs, button input, random maze generation, and game-state logic.

This project reimagines the classic tabletop marble maze as an interactive embedded system. The player controls movement by tilting the board, while the game uses onboard peripherals and real-time update logic to manage motion, hazards, and feedback.

## Overview

The system uses the board’s 2D tilt as input to control motion through a virtual maze. The maze contains randomly generated walls and traps, and the player must navigate while avoiding hazards.

A special disruptor mechanic adds an additional gameplay element: when activated with the user button, it temporarily allows movement through walls or over traps.

## Technical Highlights

- Built a real-time game loop with fixed-rate physics updates
- Used gyroscope input to control motion through a virtual maze
- Generated randomized maze layouts with walls, holes, and navigation goals
- Integrated LCD graphics for game visualization
- Used LEDs and button input for embedded feedback and control
- Implemented temporary disruptor behavior as part of the gameplay system
- Applied real-time embedded design concepts to a multi-component interactive project

## System Features

- Tilt-based movement using onboard sensors
- Randomized game environments
- Trap and collision handling
- Temporary power-up / disruptor behavior
- Embedded visual and hardware feedback
- Real-time response to player input

## What I Learned

This project has involved:
- real-time embedded software design
- sensor-driven input handling
- game-state and physics update logic
- hardware/software integration
- working with multiple peripherals in a single embedded system

## Tools and Topics

- STM32F429I-DISC1
- Embedded C / low-level embedded development
- RTOS concepts
- Gyroscope input
- LCD graphics
- RNG / randomized generation
- Real-time control loops


