# nasscom-vsd-soc-design-and-planning-RTL2GDS
VLSI SoC Design and Planning Workshop: Complete RTL-to-GDSII Flow, organized by VSD in collaboration with NASSCOM focusing on Advanced Physical Design using OpenLANE and Sky130# Digital VLSI SoC Design and Planning

## Overview

This repository chronicles the exploration of digital VLSI System on Chip (SoC) design and planning emphasizing the transformation from Register Transfer Level (RTL) designs to fabrication-ready GDSII files using open-source tools and the SkyWater 130nm Process Design Kit (PDK)

## Table of Contents

1. [Introduction to ASIC Design](#introduction-to-asic-design)
2. [RTL to GDSII Flow](#rtl-to-gdsii-flow)
3. [Open-Source Tools Utilized](#open-source-tools-utilized)
4. [SkyWater 130nm PDK](#skywater-130nm-pdk)
5. [Workshop Breakdown](#workshop-breakdown)
   - [Day 1: Exploring Open-Source EDA OpenLANE and Sky130 PDK](#day-1-exploring-open-source-eda-openlane-and-sky130-pdk)
   - [Day 2: Floorplanning Essentials and Library Cell Introduction](#day-2-floorplanning-essentials-and-library-cell-introduction)
   - [Day 3: Crafting Library Cells with Magic Layout and Ngspice Characterization](#day-3-crafting-library-cells-with-magic-layout-and-ngspice-characterization)
   - [Day 4: Pre-Layout Timing Analysis and Clock Tree Significance](#day-4-pre-layout-timing-analysis-and-clock-tree-significance)
   - [Day 5: Finalizing RTL to GDSII with TritonRoute and OpenSTA](#day-5-finalizing-rtl-to-gdsii-with-tritonroute-and-opensta)
6. [Acknowledgments](#acknowledgments)

## Introduction to ASIC Design

Application-Specific Integrated Circuits (ASICs) are custom-designed chips tailored for specific applications offering optimized performance and efficiency The design process involves several stages from conceptualization to the final layout ready for fabrication

## RTL to GDSII Flow

The transformation from RTL to GDSII encompasses

- **RTL Design**: Defining the desired functionality using a hardware description language
- **Synthesis**:
  Converting RTL code into a gate-level netlist  <br>
  The synthesis converts the RTL to a circuit out of components from the standard cell library. There are multiple different standard cells. Standard cells of the same component can have different areas based on the use case.

  ![Image](https://github.com/user-attachments/assets/b45c7be9-30b3-46be-a596-1a359870ee67)

  
- **Floorplanning/Powerplaning**: Determining the physical placement of components on the chip.
  <br>There are 2 types of Floorplanning namely Chip Foorplanning and Macro Floorplanning. Power planning works on the placement of power sources such as Vdd and ground.

  ![Image](https://github.com/user-attachments/assets/a186b3a8-f907-4e81-84cc-8435ebe8cdf2)

  ![Image](https://github.com/user-attachments/assets/4394b974-0b16-4c8f-a386-d162f05b3431)

  

- **Placement**:  Positioning standard cells within the floorplan
<br>Placement is used to place the cells on the floorplan rows, alogned with the sites. It is done in 2 steps.

  The first step is Global placement in which the flow places the standard cells in optimal position even when they overlap with each other.

  Then, Detailed placement takes place which alters the position of the global placement so they do not overlap.

  ![Image](https://github.com/user-attachments/assets/98c993a1-786b-4f30-925d-aa934a41e2bc)

- **Clock Tree Synthesis (CTS)**: Designing the clock distribution network.

   ![Image](https://github.com/user-attachments/assets/e8939ec5-2879-4374-a9b7-b7e25339e4a2)


- **Routing**: Establishing interconnections between components.
<br>
    It is used to implement interconnect using available metal layers. Metal tracks form a routing grid which is huge as it covers the entire chip.
    ![Image](https://github.com/user-attachments/assets/7bbf5fc0-3ae7-4c0c-aa57-cd832938288b)
  
- **Sign-Off**: Verifying the design meets all specifications before fabrication

## Open-Source Tools Utilized

The workshop leverages several open-source tools

- **Yosys**: For RTL synthesis
- **OpenLANE**: An end-to-end flow for ASIC design
- **Magic**: For layout visualization and editing
- **Ngspice**: For circuit simulation and characterization
- **OpenSTA**: For static timing analysis
- **TritonRoute**: For detailed routing

## SkyWater 130nm PDK

The SkyWater 130nm PDK is an open-source process design kit providing the necessary files and guidelines to design and fabricate integrated circuits at the 130nm technology node ([github.com](https://github.com/VLSIDesignByRahul/Digital-VLSI-SOC-DESIGN-AND-PLANNING?utm_source=chatgpt.com))

## Workshop Breakdown

### Day 1: Exploring Open-Source EDA OpenLANE and Sky130 PDK

- **Introduction**
- ![Image](https://github.com/user-attachments/assets/79d5ee54-5bf0-4345-8b64-e75c7415afb3)

- ![Image](https://github.com/user-attachments/assets/1dc4d72e-fece-4574-8ca2-d967d1f8c459)

- ![Image](https://github.com/user-attachments/assets/cb1d57b8-2bd2-473f-b936-fbe59bd1ff96)
  
- **RISC-V Overview**: Introduction to the RISC-V architecture and its significance in modern SoC designs

### Day 2: Floorplanning Essentials and Library Cell Introduction

- **Good vs. Bad Floorplans**: Identifying characteristics of effective floorplanning
- **Library Cells**: Introduction to standard cells and their role in design

### Day 3: Crafting Library Cells with Magic Layout and Ngspice Characterization

- **Magic Layout Tool**: Designing and editing layout geometries
- **Ngspice**: Characterizing the designed cells through simulation

### Day 4: Pre-Layout Timing Analysis and Clock Tree Significance

- **Static Timing Analysis (STA)**: Ensuring the design meets timing requirements
- **Clock Tree Design**: Importance of a well-structured clock distribution network

### Day 5: Finalizing RTL to GDSII with TritonRoute and OpenSTA

- **Detailed Routing**: Completing the interconnections using TritonRoute.
- **Final Sign-Off**: Verifying the design with OpenSTA before generating the GDSII file

## Acknowledgments

Special thanks to the organizers and contributors of the workshop for providing valuable insights into digital VLSI SoC design and planning


