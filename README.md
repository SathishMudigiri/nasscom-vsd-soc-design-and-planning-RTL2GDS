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
<br>
We will be using RTL IP's, EDA tools, and PDK data to form an ASIC Design. All these components will be taken from open-source sites as it makes it easier to design the flow.

For the RTL IP's, we will be using librecores.org, opencores.org, github.com and many other open-source websites. For EDA tools, we will be using OpenLANE, and OpenRoad. OpenROAD will be used for static timing analysis.

For the PDKS, we will be using Skywater 130nm PDK. SkyWater 130nm PDK is an open source PDK developed by SkyWater and Google in collaboration. PDKs include Process Design Rules like DRC,LVS etc., Device models, Digital Standard Libraries, I/O Libraries and many other things.

The EDA tools can perform the following processes.

 ![Image](https://github.com/user-attachments/assets/4c258d68-313e-4b27-a5b0-2f910a41007d)

## RTL to GDSII Flow

The transformation from RTL to GDSII encompasses

- **RTL Design**: Defining the desired functionality using a hardware description language

    ![Image](https://github.com/user-attachments/assets/e53d1391-c2c8-4938-bebe-788e0731e034)
  
- **Synthesis**:
Converting RTL code into a gate-level netlist  <br>
The synthesis converts the RTL to a circuit out of components from the standard cell library. There are multiple different standard cells. Standard cells of the 
same component can have different areas based on the use case.

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
<br>It is used to implement interconnect using available metal layers. Metal tracks form a routing grid which is huge as it covers the entire chip.

  ![Image](https://github.com/user-attachments/assets/839357ea-0eb7-4e56-acd1-19784a149e2f)

  - **Sign-Off**: Verifying the design meets all specifications before fabrication
<br>The Sign Off contains the Physical Verifications like Design Rule Check(DRC) and Layout Vs. Schematic(LVS).

    It also does the timing verification using Static Timing Analysis.

## OpenLANE

  OpenLANE started as an Open-Source Flow for true Open Source Tape-Out Experiment. They use the striVe family of open everythings.

  The ASIC flow's main goal is to produce a clean GDSII with no human intervention. The operation has 2 modes namely autonomous and interactive.

 ![Image](https://github.com/user-attachments/assets/d740fa84-be02-4ef1-b04f-ab3f04c236bb)

The above image is the OpenLANE ASIC Design Flow.

OpenLANE flow is based in OpenROAD Magic VLSI Layout Tool Fault Yosys QFlow and ABC. OpenLANE uses Regression Testing in which it runs OpenLANE on 70-75 designs and compares the results to the best known ones.

It has Design for Test(DFT) which performs the tasks of Scan Insertion, Automatic Test Pattern Generation, Test Patterns Compaction, Fault Coverage, and Fault Simulation.

In Physical Implementation, it does the Placement and Routing of the cells along with floor/powerplanning, Clock Tree Synthesis and much more

Logic Equivalence Check(LEC) is used to formally confirm that the function did not change after modifying the netlist.

In the flow, we also have to deal with antenna rules violation which can be solved using Bridging or adding an antenna diode cell to leak away the charges.

In the last step, we do Timing verification and Physical verification of the chip.
  

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

![Image](https://github.com/user-attachments/assets/7c2c59a4-0e4c-48c2-926d-b9e75089501e)

## Workshop Breakdown

### Day 1: Exploring Open-Source EDA OpenLANE and Sky130 PDK

### How to talk to computers


- **Introduction to QFN-48 package**
   The QFN-48 is a Quad flat No-leads 48 pin package. It is a 7mmx7mm package with a height of 0.9mm.
  ![Image](https://github.com/user-attachments/assets/acce49eb-d9c1-4170-931a-4f005120ad12)

  ![Image](https://github.com/user-attachments/assets/36a559ea-b646-4fd2-849f-a9a31bd2fd05)

 The QFN-48 has PADS, Core, and Die. Pads are mechanism used to send signal through the chip. The signal can be sent from inside to outside and vice versa. The core is a place allocated for the placement of logic gates. The Die is the size of the entire chip.

Inside the Core, multiple IP's(Intellectual Property) as well as Macros can be placed.

Intellectual properties are pre designed macros provided by different entities for different purposes.
  ![Image](https://github.com/user-attachments/assets/5a789e1b-d057-4dfb-b426-ed40027f3b34)
  ![Image](https://github.com/user-attachments/assets/74d2ceb4-e6c9-48ab-af91-b5eae98451d3)
  
 ## RISC-V Overview: 
   Introduction to the RISC-V architecture and its significance in modern SoC designs
    ![Image](https://github.com/user-attachments/assets/03031d37-129c-4498-ab3a-2ff8cafb8b19)
    ![Image](https://github.com/user-attachments/assets/3f750465-d126-49f9-8864-9a74281ae490)
  
 RISC-V is an open-standard Instruc on Set Architecture (ISA) rooted in established Reduced Instruc on Set 
 Compu ng (RISC) principles. Its open-source nature allows for extensive customiza on and adaptability, making it a 
 preferred choice for modern System on Chip (SoC) designs. In this workshop, par cipants will learn to u lize the 
 OpenLANE flow to transform a high-level C program into a hardware layout, encompassing steps from logic synthesis 
 to physical design, culmina ng in a ready-for-fabrica on GDSII file.

 ## Get familiar to open-source EDA tools

 Getting to know the various commands:

  pwd: It shows the current directory the user is present.
  
  cd: This command helps the user move from one directory to another.
  
  ls-ltr: It lists all the sub- directories and files that the directory contains.
  
  help: This command helps the user with the information for any command the user wants to gain knowledge about.
  
  clear: This command clears the terminal.
  
  mkdir: This command creates a new directory.
  
  There are few key file like libs.ref which contains information about standard cells, IO cells, etc. and libs.tech which contains all the information regarding the 
  EDA tools.

  To get into OpenLANE flow we have to set our directory to

  cd /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane

  To invoke the OpenLANE flow, we have to give the following commands

   docker # this command enters us into the OpenLANE flow

  ./flow.tcl -interactive

  #We need to open the necessary packages
   package require openlane 0.9

  #To run any design, we have to prepare it
  prep -design picorv32a

  #Now, to run the synthesis, give the command
  run_synthesis

  Once you run the synthesis an new file will be created under the runs directory in the picorv32a directory.

  Screenshots of running the code:
  ![Image](https://github.com/user-attachments/assets/d47be14c-0086-48e8-b4b1-f8cc56841456)
  ![Image](https://github.com/user-attachments/assets/79d5ee54-5bf0-4345-8b64-e75c7415afb3)
  ![Image](https://github.com/user-attachments/assets/12019cef-c5b3-4ee0-b95f-cb48d43fb2d4)

 # Calculate the flop ratio
 After running the synthesis, we get the following data

  ![Image](https://github.com/user-attachments/assets/1dc4d72e-fece-4574-8ca2-d967d1f8c459)
  ![Image](https://github.com/user-attachments/assets/cb1d57b8-2bd2-473f-b936-fbe59bd1ff96)

  Using this we have to find the flop ratio
  
                Flop Ratio = Number of D Flip Flop/Totall number of cells

                Percentage of DFF's = Flop Ratio* 100 
                
 Therefour flop ratio will be
 
                Flop Ratio = 1613/14876
                           = 0.108429685 %
 
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


