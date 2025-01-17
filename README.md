# Maze-Solving Robot using HCS12 Microcontroller

## Overview

This project implements a maze-solving robot that uses the "right-hand rule" to navigate through a maze. The robot is powered by the HCS12 microcontroller and programmed in assembly language. It leverages sensor data for real-time decision-making and efficient pathfinding.

## Features

- **Right-Hand Rule Navigation**: Ensures consistent maze traversal by keeping one side of the robot aligned with the maze walls.
- **State Machine Design**: Includes distinct states like `START`, `FORWARD`, `RIGHT TURN`, `LEFT TURN`, `REVERSE`, and `STOP` for seamless transitions.
- **Real-Time Sensor Integration**: Uses multiple sensors to detect walls, junctions, and dead ends.
- **Error Detection and Correction**: Implements mechanisms to identify and recover from incorrect paths or obstacles.
- **LCD Feedback**: Displays current status and sensor readings for debugging and user feedback.

## Technical Specifications

- **Microcontroller**: HCS12
- **Programming Language**: Assembly
- **Sensors**: Infrared and bump sensors for obstacle detection and line tracking
- **Actuators**: Motor control via PWM signals
- **Display**: 16x2 LCD for debugging and status updates

## Algorithm

### Right-Hand Rule
1. Always keep the right side of the robot touching the wall.
2. At junctions:
   - Turn right if possible.
   - If blocked, move forward.
   - If unable to move forward, turn left.
   - If all directions are blocked, reverse.
3. Use a backtracking mechanism to remember visited paths.

### State Machine
- **START**: Initialize sensors and motors.
- **FORWARD**: Move straight until a junction or obstacle is detected.
- **RIGHT TURN**: Execute a right turn if possible.
- **LEFT TURN**: Take a left turn when right and forward are blocked.
- **REVERSE**: Backtrack to the last junction if dead ends are encountered.
- **STOP**: Halt the robot upon completion or on user command.

## Code Structure

- **main.asm**: Main program initializing the robot's states and hardware.
- **sensors.asm**: Functions for reading sensor data and determining thresholds.
- **motor_control.asm**: Subroutines for precise motor operations.
- **lcd_display.asm**: Code for updating the LCD with sensor readings and status.
- **state_machine.asm**: Core logic for state transitions based on sensor input.

## Challenges and Solutions

### Sensor Calibration
- **Problem**: Variations in surface texture and lighting affected sensor accuracy.
- **Solution**: Calibrated thresholds dynamically based on environmental readings.

### Real-Time Decision Making
- **Problem**: Delays in processing caused erratic movements.
- **Solution**: Optimized assembly code for faster sensor data interpretation and decision-making.

### Debugging
- **Problem**: Difficulties in identifying faulty logic.
- **Solution**: Utilized LCD feedback to display real-time state transitions and sensor values.

## Getting Started

### Requirements
- HCS12 microcontroller development board
- Assembly IDE (e.g., CodeWarrior)
- Infrared and bump sensors
- Motor driver and DC motors
- LCD module
