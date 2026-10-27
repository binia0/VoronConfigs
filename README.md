Voron 2.4 R2 350 StealthChanger 6 Tool Build
Overview
This repository contains the complete Klipper configuration for my custom-built Voron 2.4 R2 350 equipped with a StealthChanger toolchanger system.

The goal of this machine is to combine:

High-speed CoreXY motion
Multi-tool printing
Multi-material capability
Multi-color capability
Reliable ABS / ASA production
Fully enclosed heated chamber
Industrial-style automatic tool changing
The printer is designed around six independent toolheads and a fully CAN-based architecture.

Printer Specifications
Base Machine
Voron 2.4 R2
350mm build volume
Fully enclosed
CoreXY motion system
Quad Gantry Leveling
Klipper Firmware
Mainsail Interface
Build Volume:

350 x 350 x 310 mm
Motion System
Hardware
LDO Voron 2.4 R2 Motor Kit
0.9° LDO Stepper Motors (XY)
4 Independent Z Motors
Gates Belt Drive
Quad Gantry Level
Performance Targets
Current conservative settings:

max_velocity: 900
max_accel: 7000
square_corner_velocity: 5
Planned production settings:

max_velocity: 900
max_accel: 12000-15000
square_corner_velocity: 8
Future tuning will be based on tool-specific resonance measurements.

StealthChanger System
Configuration
StealthChanger
6 Tool Docks
Automatic Tool Pickup
Automatic Tool Dropoff
Fully integrated into PRINT_START and PRINT_END
Installed Tool Positions:

T0
T1
T2
T3
T4
T5
Toolheads
AntHead
Every toolhead is based on AntHead.

Reasons:

Lightweight
Compact design
Excellent cooling options
Optimized for StealthChanger
Excellent serviceability
Extruder
Galileo 2 Extruder (G2E)
All tools are planned around the Galileo 2 Extruder.

Benefits:

Lightweight design
Very short filament path
Excellent extrusion consistency
Outstanding compatibility with Voron ecosystem
Ideal for toolchanger applications
Advantages:

Lower moving mass
Better pressure advance consistency
Better dynamic performance
Excellent compatibility with Rapido hotends
Hotends
Phaetus Rapido UHF
Each toolhead uses:

Phaetus Rapido UHF
Volcano style nozzle system
Current setup:

Rapido UHF
+
Adapter Nut
+
Volcano Nozzle
Current measured flow:

~30 mm³/s
Future testing:

Volcano CHT Nozzles
Rapido UHF native nozzle system
Alternative high-flow nozzles
Expected performance:

Configuration	Expected Flow
Standard Volcano	30-40 mm³/s
Volcano CHT	40-55 mm³/s
Rapido UHF Native	50-70 mm³/s
Rapido UHF + CHT	60-80+ mm³/s
Electronics
Mainboard
BigTreeTech Octopus
Firmware
Klipper
Mainsail
Toolhead Electronics
Each toolhead contains:

Nitehawk 36 CAN Toolboard
System backbone:

Nitehawk Hexa CAN Hub
Benefits:

Fully CAN based
Reduced wiring complexity
Faster maintenance
Simplified tool changes
Resonance Measurement
Nitehawk Accelerometers
The printer does not use an external ADXL345.

Resonance measurements are performed using the onboard accelerometers integrated into the Nitehawk 36 toolboards.

This allows:

Tool-specific resonance analysis
Tool-specific Input Shaper profiles
More accurate measurements
Easier maintenance
Workflow:

Pickup Tool
↓
Measure Resonances
↓
Generate Input Shaper
↓
Store Tool Profile
Example:

T0 -> Profile T0
T1 -> Profile T1
T2 -> Profile T2
T3 -> Profile T3
T4 -> Profile T4
T5 -> Profile T5
Input Shaper
Input Shaper values are planned individually for every tool.

Reasons:

Different toolhead mass
Different fan configurations
Different resonance characteristics
Maximum print quality
Future implementation:

T0 = Individual Shaper
T1 = Individual Shaper
T2 = Individual Shaper
T3 = Individual Shaper
T4 = Individual Shaper
T5 = Individual Shaper
Bed Leveling
Quad Gantry Level
The machine uses:

[quad_gantry_level]
Features:

Independent Z correction
Fully automatic gantry alignment
Integrated into print startup workflow
Workflow:

Home
↓
QGL
↓
Z Home
↓
Mesh
↓
Print
Bed Mesh
Current Configuration:

mesh_min: 40,40
mesh_max: 310,310
probe_count: 7,5
algorithm: bicubic
Adaptive Mesh:

BED_MESH_CALIBRATE ADAPTIVE=1
Probe System
Current
Virtual Probe Endstop
QGL Based Workflow
Planned
Each toolhead will receive:

Cartographer Probe
Benefits:

Fast probing
Tool-specific offsets
Accurate first layer
Reduced setup time
Planned configuration:

6x Cartographer
6x Toolheads
Toolhead LEDs
Integrated RGB status system.

States:

Heating
Homing
Mesh
QGL
Tool Change
Prime
Printing
Complete
Error
Macros:

TOOLHEAD_LED_HEATING
TOOLHEAD_LED_HOMING
TOOLHEAD_LED_QGL
TOOLHEAD_LED_MESH
TOOLHEAD_LED_TOOLCHANGE
TOOLHEAD_LED_PRIME
TOOLHEAD_LED_PRINTING
TOOLHEAD_LED_DONE
TOOLHEAD_LED_ERROR
Chamber System
Carbon Filter
Automatic filter control based on bed temperature.

Starts:

Bed >= 100°C
Stops:

Bed < 50°C
Designed for:

ABS
ASA
Engineering materials
Cooling
Electronics Cooling
Automatic controller fan control.

Monitors:

Steppers
Heated bed activity
Raspberry Pi Cooling
Temperature controlled cooling.

Target:

50°C
Monitoring
Available Sensors:

MCU Temperature
Raspberry Pi Temperature
Toolboard Sensors
Nitehawk Accelerometers
Future:

Chamber Temperature Monitoring
Cartographer Thermal Compensation
Planned Mechanical Upgrades
Anti-Vibration Platform
The printer is planned to be installed on:

Voron 2.4
↓
Hula Feet
↓
60x60 cm Concrete Slab
↓
Anti-Vibration Mat
↓
Floor
Purpose:

Reduce floor resonance
Improve Input Shaper accuracy
Improve print quality
Improve high-speed performance
Software Stack
Current Software:

Klipper
Mainsail
Spoolman
AxisScope
Klipper Timelapse
StealthChanger
KNOMI Display
Toolhead LED System
Project Goals
Production
Reliable ABS printing
Reliable ASA printing
Multi-color prints
Multi-material prints
Performance
Target acceleration:

12000 - 15000 mm/s²
Potential after tuning:

15000+ mm/s²
Flow Rate
Target:

50+ mm³/s
on all six toolheads.

Current Status
✅ Voron 2.4 R2 350 Operational

✅ Quad Gantry Level

✅ StealthChanger Installed

✅ KNOMI Integration

✅ Toolhead LED System

✅ Nitehawk CAN Architecture

✅ Nitehawk Hexa Backbone

✅ Galileo 2 Design Planned

✅ Rapido UHF Toolheads

🟡 Cartographer Integration

🟡 Tool Specific Input Shaper

🟡 High Flow Optimization

🟡 Full Production Tuning

Mission
Build a reliable, high-speed, six-tool Voron platform capable of:

Multi-material printing
Multi-color printing
ABS / ASA production
Rapid prototyping
Advanced tool-changing workflows
while maintaining the flexibility and open-source philosophy of the Voron ecosystem.
