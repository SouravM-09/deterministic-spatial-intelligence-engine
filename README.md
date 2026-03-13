# deterministic-spatial-intelligence-engine
# Description
Digital hardware design that reads up to 7 coordinate points from ROM, stores them in registers, selects point pairs using counters and multiplexers, computes distance and a custom metric, and continuously updates the minimum value using comparator-controlled registers.'
# Coordinate Metric Evaluation Using Digital Logic
# Overview
This project implements a hardware-based coordinate processing system using discrete digital logic components. The design reads up to seven coordinate points (xi, yi) from ROM, stores them in registers, and systematically evaluates all valid pairs of points. For each pair, the circuit computes mathematical expressions such as Euclidean distance squared and a custom metric function, while continuously tracking the minimum result using comparator-based logic.

The goal of this project is to demonstrate how algorithmic computation typically performed in software can be implemented using pure hardware datapath and control logic.

# System Architecture
The system consists of several functional blocks working together:
ROM
 ↓
Decoder
 ↓
Register Bank (Store X and Y coordinates)
 ↓
Multiplexer Network
 ↓
Arithmetic Processing Unit
 ↓
Comparator
 ↓
Minimum Value Register
Each block performs a specific task in the coordinate processing pipeline.

# Key Features
1.Supports up to 7 coordinate points
2.Stores coordinate data using dedicated X and Y registers
3.Uses hardware counters to generate valid point pairs
4.Implements multiplexer-based point selection
5.Computes:
  Euclidean distance squared
  Custom metric function
6.Tracks the minimum value automatically
7.Fully clock-synchronized digital system

# Hardware Components Used
The design uses commonly available digital ICs such as:
1.ROM – Stores coordinate values
2.74LS139 – Address decoder for register selection
3.74179 Registers – Coordinate storage
4.74151 Multiplexers – Select coordinates
5.74161 Counters – Generate point indices
6.74283 Adders – Arithmetic operations
7.4585 Comparator – Minimum value detection
These components collectively implement the system's datapath and control logic.

# Working Principle
# 1.Coordinate Storage
Coordinate values are stored in ROM. A decoder enables specific registers to load the data, allowing the system to store multiple coordinate pairs simultaneously.
# 2. Point Selection
Two hardware counters generate indices i and j, representing the selected points. These indices drive multiplexers that choose the corresponding xi, yi, xj, yj values from the register bank
# 3. Pair Evaluation
The counters operate similarly to a nested loop structure, ensuring that all valid pairs of points are processed without redundancy.
# 4.Arithmetic Computation
For each selected pair, the system computes:
Distance:
$$d^2 = (x_i - x_j)^2 + (y_i - y_j)^2$$

Metric:
$$Metric = (x_i y_i + x_j y_j) \pmod{i \times j}$$
These calculations are implemented using adders, subtractors, and multipliers

# 5. Minimum Value Tracking
Each computed result is compared with the current minimum value stored in a register. If the new value is smaller, a comparator triggers the load signal to update the minimum register

# 6. Clock and Synchronization
All registers, counters, and control logic operate using a single system clock. This ensures synchronized updates and prevents timing mismatches between arithmetic computations and register updates.

# 7. Applications
Although implemented as a learning project, the architecture demonstrates concepts used in:
1. Hardware accelerators
2. Signal processing circuits
3. Embedded datapath design
4. FPGA and ASIC digital systems
5. Algorithm implementation in hardware

# 8. Learning Outcomes
Through this project, the following digital design concepts are explored:
1. Datapath and control architecture
2. Hardware implementation of nested loops
3. Multiplexer-based data selection
4. Register-based storage systems
5. Comparator-driven decision logic
6. Clock-synchronized digital systems

# 9. Possible Improvements
Future improvements could include:
1. Implementing the design on an FPGA
2. Increasing the number of supported points
3. Adding a hardware square-root unit for actual Euclidean distance
4. Optimizing the metric computation unit
5. Introducing a finite state machine (FSM) for better control logic

# Author
Sourav Mandal
Electronics Engineering
IIT (BHU)
