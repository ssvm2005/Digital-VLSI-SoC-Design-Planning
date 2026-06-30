# Digital VLSI SoC Design and Planning

## RTL to GDSII Physical Design Flow using OpenLANE and Sky130 PDK

A hands-on implementation of a complete ASIC physical design flow using open-source EDA tools.

This repository documents my learning, lab execution, and implementation work during the **VSD Digital VLSI SoC Design and Planning Workshop**, covering the complete journey from RTL design to final GDSII generation.

# Overview

Physical Design is the process of converting a synthesized RTL netlist into a manufacturable silicon layout.
The complete ASIC flow followed in this project:

```
RTL Design
    ↓
Logic Synthesis
    ↓
Floorplanning
    ↓
Placement
    ↓
Clock Tree Synthesis (CTS)
    ↓
Routing
    ↓
Static Timing Analysis
    ↓
GDSII Generation
```

This project uses:

- Google SkyWater 130nm Open PDK
- OpenLANE RTL-to-GDSII flow
- Open-source EDA tools


# Objectives

- Understand the complete ASIC design flow
- Learn RTL synthesis using Yosys
- Perform floorplanning and placement
- Understand standard cell design and characterization
- Perform timing analysis using OpenSTA
- Generate physical layout through routing
- Explore open-source ASIC design methodology

# Tools Used

| Tool | Purpose |
|---|---|
| OpenLANE | Complete RTL-to-GDSII automation flow |
| Yosys | RTL synthesis |
| OpenROAD | Floorplanning, Placement, CTS |
| TritonCTS | Clock Tree Synthesis |
| TritonRoute | Detailed Routing |
| Magic | Layout viewing, DRC and extraction |
| ngspice | SPICE simulation and characterization |
| OpenSTA | Static Timing Analysis |
| Netgen | LVS checking |
| Sky130 PDK | 130nm semiconductor process design kit |

# Design Used

## PicoRV32 RISC-V Core

The main design implemented through the physical design flow:

- PicoRV32 RISC-V processor core
- Sky130 standard cell library
- OpenLANE implementation flow

# ASIC Design Flow

## Day 1 - Introduction to OpenLANE, EDA Tools and Sky130 PDK

### Topics Covered

- ASIC design flow overview
- Chip architecture
- Open-source EDA ecosystem
- Sky130 PDK introduction
- RTL synthesis using OpenLANE

### OpenLANE Setup

Launch OpenLANE:

```bash
./flow.tcl -interactive
```

Prepare design:

```tcl
prep -design picorv32a
```

Run synthesis:

```tcl
run_synthesis
```

# Day 2 - Floorplanning and Placement

## Concepts Learned

- Die area
- Core area
- Utilization factor
- Aspect ratio
- Power planning
- Standard cell placement

### Running Floorplan

```tcl
run_floorplan
```

### Running Placement

```tcl
run_placement
```
The floorplan decides the physical organization of the chip, while placement determines the optimal location of standard cells to reduce congestion and timing issues.

# Day 3 - Standard Cell Characterization

## CMOS Inverter Characterization

A CMOS inverter cell was analysed using:

- Magic Layout Tool
- ngspice simulation

Flow:

```
Layout
   ↓
SPICE Extraction
   ↓
Circuit Simulation
   ↓
Timing Characterization
```

Measured parameters:

- Rise time
- Fall time
- Propagation delay

Commands:

Extract layout:

```bash
extract all
```

Generate SPICE:

```bash
ext2spice
```

Run simulation:

```bash
ngspice sky130_inv.spice
```

# Day 4 - Static Timing Analysis and Clock Tree Synthesis

## Topics Covered

- LEF generation
- Standard cell integration
- Timing libraries
- Static Timing Analysis
- Clock Tree Synthesis

### OpenSTA Timing Analysis

```bash
sta pre_sta.conf
```

### Clock Tree Synthesis

```tcl
run_cts
```
CTS balances clock distribution and reduces clock skew across the design.

# Day 5 - Final RTL to GDSII Flow

Final physical implementation stages:

- Power Distribution Network generation
- Routing
- Parasitic extraction
- Timing verification
- GDSII generation


Generate PDN:

```tcl
gen_pdn
```

Run routing:

```tcl
run_routing
```

Generate final layout:

```tcl
run_magic
```

# Key Learnings

- Complete RTL-to-GDSII ASIC implementation flow
- Importance of floorplanning in chip design
- Standard cell design and characterization
- Timing closure concepts
- Clock tree optimization
- Physical verification concepts
- Open-source ASIC design ecosystem

# Results

The following outputs were generated during the flow:
* Synthesized netlist  
* Floorplanned design  
* Placed design  
* Clock tree synthesized design  
* Routed layout  
* Timing reports  
* Final GDSII database  

# References

- VSD Digital VLSI SoC Design and Planning Workshop
- OpenLANE Documentation
- OpenROAD Project
- SkyWater Sky130 PDK

# Acknowledgement

Special thanks to the VSD team for providing a practical learning environment focused on open-source ASIC design and RTL-to-GDSII implementation.
