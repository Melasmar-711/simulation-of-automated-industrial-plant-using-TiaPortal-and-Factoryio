# Factory Automation Production Line

Automated production line simulation using Factory I/O and Siemens TIA Portal for MTC 313 course.

## Table of Contents

- [Overview](#overview)
- [System Architecture](#system-architecture)
- [Technical Stack](#technical-stack)
- [Features](#features)
- [Installation & Setup](#installation--setup)
- [PLC Configuration](#plc-configuration)
- [HMI Interface](#hmi-interface)
- [Results](#results)
- [Team](#team)

## Overview

This project implements a comprehensive PLC-based automated manufacturing system with four coordinated stations: feeding, sorting, machining, and assembly. The system demonstrates real-time automation control using Ladder Diagram programming on a Siemens S7-314C PLC with TP_700 HMI interface.

A production line is a series of sequential operations set up in a factory where components are assembled to make a finished product. The production line consists of multiple components:

- **Sensors:** Vision sensor, IR sensors, Limit switches
- **Actuators:** Pick & place robots, Conveyors, CNC machines
- **Control:** Manual control panels (Start, Stop, Emergency Stop)
- **PLC:** Siemens S7-314C PN/DP

## System Architecture

### Stations

#### 1. Feeding Unit
The entry point of the production line where raw materials are generated and distributed. Features include random material generation with color differentiation (green and blue) and a pick-and-place robot that feeds materials into the system.

#### 2. Sorting Unit
Sortation process where raw materials are identified on the conveyor and separated based on their color. The sorting is done with a vision sensor configured to detect green raw materials. When a green material is detected, the clamp raises to allow the product to get to the machining center. If the product is blue, the clamp stays in place and the pick-and-place machine transports it to its conveyors.

#### 3. Machine Centre
The Machining Center is used to manufacture lids and bases from raw materials. An articulated robot waits for raw material at the entry bay. When material is detected, it is loaded into the CNC machine. Processing times vary by product type:
- Lids: 6 seconds
- Bases: 3 seconds

Once complete, the robot places the item on the exit bay.

#### 4. Assembly Unit
The final production stage where bases and lids are assembled into finished products. The station uses:
- Two pick-and-place machines
- Three clamps
- Positioning bars for alignment

The first pick-and-place transfers the base to the next conveyor where it is held with the positioner waiting for the lid. The second pick-and-place assembles the lid over the base. After assembly, the positioner raises so products can be moved from the line.

## Technical Stack

- **Simulation Tool:** Factory I/O
- **PLC Hardware:** Siemens S7-314C PN/DP
- **Programming Language:** Ladder Diagram (IEC 61131-3)
- **HMI Device:** TP_700 Touchscreen
- **Driver:** Siemens S7-PLCSIM
- **Sensors:** Vision (color detection), IR, Limit switches
- **Actuators:** Pick-and-place robots, Conveyors, CNC machines, Clamps

## Features

- **Modular Station Design** - Four independent yet coordinated stations
- **Color-Based Routing** - Automatic sorting and processing of different product types
- **Real-Time Monitoring** - HMI displays production status, component activity, and product counts
- **Safety Controls** - Start, Stop, and Emergency Stop buttons
- **Production Tracking** - Counters for finished products by color type
- **Comprehensive PLC Tags** - 100+ defined tags for I/O and logic management

## Installation & Setup

### Configuration

The scene is connected to Siemens S7-PLCSIM driver. The addresses of inputs and outputs are adjusted from the configuration tab to match the addresses in TIA Portal.

### HMI Monitoring

The HMI window provides visual feedback on:
- Station operational status (Feeding, Sorting, Machining, Assembly)
- Product counts for green and blue production lines
- Machine busy states (MC_Blue_on, MC_Green_on)
- Station activity status

## PLC Configuration

### PLC Tags Overview

The system includes comprehensive PLC tagging with 100+ tags managing:

- **Control Signals:** Start, Stop, Emergency buttons
- **Sensor Inputs:** IR sensors, Position feedback, Vision sensor (Color_sensor)
- **Actuator Outputs:** Conveyors, Grippers, Clamps, Suction systems
- **Status Flags:** Station on/off, Machine busy states
- **Product Counters:** Green_Count, Blue_Count

### Sample Tag Structure

**Feeding Station Tags:**
- Feeding_ir_sensor, Feeding_clamp, Feeding_gripper_Z, Feeding_gripper_X
- Feeding_conv1 through Feeding_conv6

**Sorting Station Tags:**
- Color_sensor, Sorting_clamp, Sorting_clamp_raise
- Sorting_gripper_Z, Sorting_gripper_X

**Machining Center Tags:**
- Mc_centre_green_start, Mc_centre_blue_start
- Green_conv_1, Green_conv_2, Green_conv_3
- Blue_conv_1, Blue_conv_2, Blue_conv_3

**Assembly Station Tags:**
- GreenAsm_ir_sensor, BlueAsm_ir_sensor
- GreenAsm_clamp, BlueAsm_clamp
- Green_Product_Finished, Blue_Product_Finished

## HMI Interface

| HMI Tag | Connection | PLC Tag | Data Type |
|---------|-----------|---------|-----------|
| Sorting_on | HMI_Connection_2 | Sorting_Station_On | Bool |
| Feeding_on | HMI_Connection_2 | Feeding_Station_On | Bool |
| MC_Blue_on | HMI_Connection_2 | MC_Blue_Busy | Bool |
| MC_Green_on | HMI_Connection_2 | MC_Green_Busy | Bool |
| Assembly_Blue_on | HMI_Connection_2 | Asm_Station_Blue_On | Bool |
| Assembly_Green_on | HMI_Connection_2 | Asm_Station_Green_On | Bool |
| Blue_Count | HMI_Connection_2 | Blue_Count | Int |
| Green_Count | HMI_Connection_2 | Green_Count | Int |

## Results

### Key Findings

- Simulation tools significantly reduce design complexity and prototyping risks
- Costs are reduced due to lower probability of failure in testing
- Similar outputs can be achieved with different logic diagrams, but optimization depends on requirements
- Proper coordination between stations ensures efficient material flow and product completion

### Performance

- The system successfully separates and processes both green and blue products through the production line
- Real-time monitoring via HMI provides clear visibility into production status
- Counters accurately track finished products for both production lines

## Team

- **Ahmed Ossama El-Sayed** (18P8506) - Factory I/O setup, Programming
- **Haidy Emad Samir Abouelnasr** (18P4188) - HMI, Blue product assembly/machining
- **Tasneem Mohamed Mansour** (18P5892) - HMI, Blue product assembly/machining
- **Arwa Ashraf Mahmoud Farag** (1805479) - Feeding/sorting, Green product programming, HMI
- **Mahmoud Magdy El-Asmar** (18P8983) - Blue product programming, HMI

## Course

**MTC 313** - Automation Major Task
