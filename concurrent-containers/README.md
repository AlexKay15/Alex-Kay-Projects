# Concurrent Containers

Implemented several concurrent stack and queue data structures in C++, with a focus on synchronization, correctness under concurrency, and performance as thread counts increased.

This project explored both lock-based and lock-free approaches to concurrent container design. In addition to single-lock implementations, I worked with classic non-blocking algorithms such as the Treiber stack and the Michael & Scott queue, and also implemented flat-combining variants to compare different synchronization strategies.

## Overview

The goal of this project was to study how concurrent data structures behave under contention and how different synchronization techniques affect throughput and scalability.

I implemented:
- Single-lock stack
- Single-lock queue
- Treiber stack
- Michael & Scott queue
- Flat-combining stack
- Flat-combining queue

## Technical Highlights

- Implemented both lock-based and lock-free concurrent containers
- Worked with compare-and-swap style synchronization in non-blocking data structures
- Explored tradeoffs between simplicity, scalability, and contention behavior
- Evaluated throughput across varying thread counts
- Compared performance behavior under different concurrency levels

## What I Learned

This project gave me hands-on experience with:
- concurrent algorithm design
- synchronization under multithreaded execution
- lock-free data structures
- flat combining as an alternative to traditional locking
- experimental performance evaluation of systems code

## Tools and Topics

- C++
- Multithreading
- Concurrent programming
- Lock-based synchronization
- Lock-free algorithms
- Performance benchmarking

