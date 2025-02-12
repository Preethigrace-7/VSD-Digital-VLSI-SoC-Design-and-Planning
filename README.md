<p align="center">
  <img src="https://www.vlsisystemdesign.com/wp-content/uploads/2016/12/vsd_logo.jpg" alt="VSD Logo" width="250">
</p>

# Digital VLSI SoC Design and Planning 15 Days Learning Journey

This repository documents my learnings from the **Digital VLSI SoC Design and Planning** course by **VLSI System Design (VSD)**. Over 15 days, I will explore key concepts, methodologies, and tools used in SoC design, documenting my progress and insights here.

## *Course Details*
- **Program:** NASSCOM-VSD Digital VLSI SoC Design and Planning  
- **Duration:** 2 Weeks (15 Days)  
- **Platform:** VLSI System Design (VSD)

## **Day 1 - Inception of Open-Source EDA, OpenLANE, and Sky130 PDK**
### **SKY130_D1_SK1 - How to Talk to Computers**
### **SKY_L1 - Introduction to QFN-48 Package, Chip, Pads, Core, Die, and IPs**

In this module, we explored how to design a System-on-Chip (SoC) on a **VSDSquadran Board** and got familiar with the **QFN-48 package**.
### *1.Internal Structure of the Processor*
- The processor includes key components such as **VDD/GND, JTAG, Flash, ADC, SRAM (external SoC), etc.**
![image](https://github.com/user-attachments/assets/288cf337-f5d1-48f1-ac6f-ca1e87c9ff98)

### *2.QFN-48 Package*
- **QFN (Quad Flat No-Leads)** is a chip package with **48 pins**.
- This package allows **efficient signal transmission** with minimal resistance.
![image](https://github.com/user-attachments/assets/5e52acee-f050-4a9f-a445-cc85cc5c0cc2)

### *3. Chip and Wire Bonding*
- The **chip is placed inside the package** and connected to the **package pins** using **wire bonds**.
![image](https://github.com/user-attachments/assets/a66058f5-82bb-47ac-b522-56131cbaac0c)

### *4. Chip Structure*
- The **chip** consists of three major components:
  - **Pads:** Located at the chip's boundary, these enable communication of signals between the **chip** and the **outside world**.
  - **Core:** Contains the fundamental digital logic elements such as **gates, multiplexers, encoders, decoders, etc.**
  - **Die:** The silicon part of the chip where transistors and circuits are fabricated.
![image](https://github.com/user-attachments/assets/e111b90e-424c-4052-9ec8-b1a814d03bda)

### *5. Foundry IPs and Macros*
- **Foundry IPs (Intellectual Property):** These are **pre-designed components** provided by the foundry.
  - Examples: **PLL, ADC, DAC, SRAM**
- **Macros:** These are **pre-verified functional blocks** used within the SoC.
  - Examples: **SPI, RISC-V/SoC**
![image](https://github.com/user-attachments/assets/15ac34e5-9f61-4c63-9bd9-d393efb30b65)

---

### **SKY_L2 - Introduction to RISC-V**
### *What is RISC-V?*
RISC-V is an **open-source Instruction Set Architecture (ISA)** that follows the **Reduced Instruction Set Computing (RISC)** principles. It provides a simple and flexible instruction set, making it widely used for hardware design and implementation.

### *How RISC-V Code is Converted for Hardware*
In software compilation, a **C program** is converted into **assembly language** and then into **machine code** for execution. Similarly, in hardware design:

1. **RISC-V C code** is written for the desired functionality.
2. It is compiled and translated into **HDL (Hardware Description Language)**.
3. HDL is the interface for the RISC-V to Layout process.
4. The HDL design undergoes **synthesis, placement, and routing (PnR)** to generate the final layout.
5. This layout is used for **fabricating the physical chip**.

This process enables the direct implementation of RISC-V-based designs into **hardware chips**, optimizing performance and power efficiency.

### *RISC-V Flow Overview*
RTL implements the RISC-V specification and then RTL to layout(standard RTL to GDS flow)


---
### **SKY_L3 - From Software Applications to Hardware**

### *How Software Translates into Hardware*
When we run an application, it undergoes multiple stages before reaching the hardware. The process follows this hierarchy:

1. **Application Software** → Executed by users (ex: MS Office, excel, etc).
2. **System Software** → Converts the application into machine-executable format(assembly language).
3. **Hardware** → Executes the binary instructions and performs the desired operations.

### *Major Components of System Software*
#### **1. Operating System (OS)**
- Handles **I/O operations, memory allocation, and low-level system functions**.
- Acts as a bridge between the user and hardware.

#### **2. Compiler**
- Takes the **application program from the OS** and converts it into **instructions**.
- Generates a **.exe (executable) file** that contains machine-level instructions.
- The syntax of instructions depends on the **hardware architecture** (e.g., x86, ARM, RISC-V).

#### **3. Assembler**
- Converts the compiler's instructions into **assembly language (machine code)**.
- This **binary format** is understandable by the **hardware** and can be executed directly.

### *Software-to-Hardware Flow*
The diagram below illustrates the **entire flow from application software to hardware**:

![image](https://github.com/user-attachments/assets/552bd626-ae77-4258-ad13-0a8a631246c6)

---

### **Example: Stopwatch Application**
Let’s take the **Stopwatch App** as an example. The process follows these steps:
![image](https://github.com/user-attachments/assets/bc2e1e4d-d3a0-47a1-a250-e68e70b9403e)

1. The **C code** of the stopwatch app is written.
2. The **compiler** translates it into **RISC-V assembly instructions**.
3. The **assembler** converts these instructions into **machine language** (binary).
4. The **hardware executes** the binary and the stopwatch behaves as programmed.
![image](https://github.com/user-attachments/assets/9339c0fe-c05d-491a-98a9-9a78db5e2b8a)

---

### **Abstract Interface: Instruction Set Architecture (ISA)**
Instructions act as an **abstract interface** between **software and hardware**. This interface is known as the **Instruction Set Architecture (ISA)**. 

- In our case, we focus on **RISC-V ISA**.
- Instructions are converted into **RTL (Register Transfer Level) code**.
- The RTL is synthesized into a **netlist**, which is used for **physical design**.
![image](https://github.com/user-attachments/assets/102b5378-2667-453e-8723-9457bdfdc5ae)

#### **RTL to Physical Design Flow**
1. **RISC-V Instructions → RTL Snippet (Hardware Description)**
2. **RTL → Synthesized Netlist**
3. **Netlist → Physical Design (Placement & Routing)**
4. **Final layout → Fabrication**

Below is the **flow from RTL to the final physical design**:

![image](https://github.com/user-attachments/assets/19f041dc-229b-417b-99e3-8c2c0346d333)

---
## **SKY130_D1_SK2 - SoC Design and OpenLANE**

### **SKY_L1 - Introduction to All Components of Open-Source Digital ASIC Design**

### *What is Digital ASIC Design?*
An **Application-Specific Integrated Circuit (ASIC)** is a chip designed for a specific function. The key components required for digital ASIC design are:

- **RTL IPs** – Pre-designed intellectual property blocks (e.g., processors, memory).
- **EDA Tools** – Software or CAD tools for design, verification, and implementation.
- **PDK Data** – Process Design Kit, containing foundry-specific design rules and libraries.
![image](https://github.com/user-attachments/assets/56aac8d6-d2a3-4cd0-9f8f-1757b17a0bd3)

### *Key Elements of Open-Source Digital ASIC Design*
![image](https://github.com/user-attachments/assets/bebef6e7-ecbf-4b1d-9ac9-f5907c665b52)
#### **1. RTL IPs (Register Transfer Level Intellectual Property)**
RTL defines the hardware behavior using **HDL (Hardware Description Language)**. Open-source RTL resources include:
- [LibreCores](https://www.librecores.org/)
- [OpenCores](https://www.opencores.org/)
- [GitHub](https://www.github.com/)

#### **2. EDA Tools (Electronic Design Automation)**
EDA tools are used for designing, simulating, and verifying ASICs. Some key open-source tools:
- **Qflow** – Complete RTL to GDSII flow.
- **OpenROAD** – Automated RTL to GDS flow.
- **OpenLane** – Open-source ASIC design flow.
- **SPICE Simulator** – Circuit simulation tool.
- **Magic** – Layout editor.

#### **3. PDK (Process Design Kit)**
##### **What is a PDK?**
A **Process Design Kit (PDK)** serves as the **interface between the foundry and designers**, providing essential data for ASIC fabrication.

A PDK includes:
- **Process Design Rules** – **DRC (Design Rule Check), LVS (Layout vs. Schematic), PEX (Parasitic Extraction)**
- **Device Models** – Defines transistor behavior.
- **Digital Standard Cell Libraries** – Includes **NAND, NOR, Flip-flops, etc.**
- **I/O Libraries** – Interfaces for external connections.

##### *SkyWater 130nm Open-Source PDK*
On **June 30, 2020**, **Google** released the **SkyWater 130nm Open-Source PDK**, making it the **first FOSS (Free and Open-Source Software) 130nm production PDK**.
---

### **ASIC Flow Objective: RTL to GDSII**
The main goal of the ASIC design process is to convert **RTL (Register Transfer Level) code** into **GDSII format**, which is used for fabrication.

This process is also known as:
- **Automated Place-and-Route (PnR)**
- **Physical Implementation**
---
### **SKY_L2 - Simplified RTL2GDS Flow**

### *Overview*
The **RTL-to-GDSII flow** converts an RTL design into a layout(tape-out) ready for fabrication. This involves multiple steps, from synthesis to final verification before tape-out.
    ![image](https://github.com/user-attachments/assets/7bd47bcf-2c5f-4c2e-a18d-48751d2af305)

---

### *Step-by-Step RTL to GDSII Flow*
1. *Synthesis*
   - Converts **RTL (Verilog/VHDL)** into a **gate-level netlist** using **Standard Cell Libraries (SCL)**.
   - The resultant circuit is described in **HDL**, representing logic gates and interconnections.
      ![image](https://github.com/user-attachments/assets/9f2e02ed-9176-46a1-a871-a3178043ab2d)

   #### *What are Standard Cells?*
   - **Regular Layout:** Standard cells have a uniform height and fit in predefined rows.
   - **Multiple Views:**  
     - **Electrical Models** (Delay, Power, etc.)
     - **HDL (Verilog, VHDL)**
     - **SPICE Models** (Circuit behavior)
     - **Layout Views** (Abstract and Detailed)

      ![image](https://github.com/user-attachments/assets/e7d49749-0f03-4c9f-bd38-1511fa1969cd)


2. *Floorplanning + Power Planning*

      ![image](https://github.com/user-attachments/assets/0453ca33-eefe-428e-9721-a43e8bd027c9)

   - Defines **chip dimensions**, **macro placement**, and **pin locations**.
      ![image](https://github.com/user-attachments/assets/79ade60e-4532-401c-befa-0e1524daf565)

   - **Micro-floorplanning** includes:

      ![image](https://github.com/user-attachments/assets/fffcc6a0-191c-46e9-8eea-d8dd7ce843e0)

     - Defining **rows** for standard cells.
     - **Pin and macro placement**.
   #### **Power Planning**
   - **Constructs the power network** using:
     - **Power Pads**
     - **Power Straps**
     - **Power Rings**
   - Helps address **Electromigration issues** and **reduce resistance** by using **higher metal layers**.

       ![image](https://github.com/user-attachments/assets/e7071e53-b242-4ecf-8191-76e0688af673)

4. *Placement*
   - **Standard cells and macros** are placed to enable successful routing.
   - Two-step process:
     - **Global Placement** – Roughly positions the cells.
     - **Detailed Placement** – Precisely adjusts cells(manually).
     
      ![image](https://github.com/user-attachments/assets/85ae1b01-9199-433d-b97b-076600c257c2)

5. *Clock Tree Synthesis (CTS)*
   - Distributes the clock signal efficiently.
   - Minimizes **clock skew** and **latency**.
   - Uses **tree structures** like **H-tree, X-tree**, etc.
   
    ![image](https://github.com/user-attachments/assets/bea19d4b-4a1b-4216-a2be-ed6134774fd8)

6. *Routing*
   - **Interconnects the standard cells** using metal layers.
   - **PDK defines metal layers** (Sky130 has **6 aluminum layers** and **9 total metal layers**).
   - Routing is done in **two steps**:
     - **Global Routing** – Estimates routing paths.
     - **Detailed Routing** – Final metal track connections.
     
    ![image](https://github.com/user-attachments/assets/406a93d2-8a7d-4e91-9bf4-0890510de1a6)

7. *Signoff (Final Verification)*
   - **Physical Verification**
     - **DRC (Design Rule Check):** Ensures layout follows foundry rules.
     - **LVS (Layout vs. Schematic):** Checks if the final layout matches the netlist.
   - **Timing Verification**
     - **STA (Static Timing Analysis):** Ensures timing constraints are met.
---
### **SKY_L3 - Introduction to OpenLANE and Strive Chipsets**

### *What is OpenLANE?*
- **Developed by Efabless**, OpenLANE is an **open-source RTL-to-GDSII flow** for ASIC design.  
- It integrates **open-source RTL, PDKs, and EDA tools** to automate the design flow.  
- **Goal:** To generate a **clean GDSII** with **no human intervention** (fully automated).  
- **"Clean" GDSII** means:
  - **No LVS (Layout vs. Schematic) errors**
  - **No DRC (Design Rule Check) violations**
  - **No timing violations**
- OpenLANE can be used to **harden macros** and **design complete chips**.  

---

### *Modes of Operation*
OpenLANE offers **two modes of operation**:
1. **Autonomous Mode**  
   - Runs the full **RTL-to-GDSII** flow automatically.  
   - No manual intervention is required.  
2. **Interactive Mode**  
   - Allows users to run specific steps of the flow manually.  
   - Useful for debugging and optimizing specific stages.  

### *Design Space Exploration (DSE)*
- OpenLANE helps **optimize design parameters** by exploring different flow configurations.  
- It searches for the **best setup** based on power, performance, and area (PPA).  

---
### **SKY_L4 - Introduction to OpenLANE Detailed ASIC Design Flow**
  ![image](https://github.com/user-attachments/assets/557e5247-d29c-4c25-994d-b020a5932c73)

### *Overview of OpenLANE ASIC Flow*
- The **OpenLANE flow** starts from **RTL to GDSII**.
- Built on multiple open-source projects:
  - **Yosys** (Synthesis)
  - **Fault** (DFT - Design for Test)
  - **KLayout** (Layout visualization)
  - **OpenROAD** (Physical design)
- **Objective:** Fully automated RTL-to-GDSII process for ASIC design.
  ![image](https://github.com/user-attachments/assets/3cd002bb-6ac9-4a7e-9cfc-426a53968581)

---

### *Step 1: RTL Synthesis*
- Converts RTL to **optimized logic circuits**.
- Uses **Yosys** to translate RTL into logic and optimize it.
- **ABC Mapping**: Optimizes delay and area.
- **Synthesis Exploration Utility**:
  - Shows delay and area impact of different synthesis strategies.
  - Helps select the **best synthesis strategy**.
  - **Generates reports** on violations for better design tuning.  
   ![image](https://github.com/user-attachments/assets/2bcc03e0-d80e-4ee5-8890-cd91d94af2aa)

---

### *Step 2: Design Exploration Utility for Regression Testing (CI)*
- OpenLANE provides a **Design Exploration Utility** for:
  - **Evaluating different configurations** to find the best design settings.
    ![image](https://github.com/user-attachments/assets/5d729458-3e1e-4afc-8c0a-f71181ab9aef)
  - **Performing regression testing (Continuous Integration - CI)**.
- **Regression Testing (CI) ensures:**
  - **No new violations** are introduced during iterative improvements.
  - The design remains **clean** throughout development.
     ![image](https://github.com/user-attachments/assets/85091c1e-017b-4ff2-9ce9-1ecc5e7c5909)

- **Automatically generates reports** on:
  - **Number of DRC, LVS, and timing violations**.
  - **Effect of design parameter changes on performance**.  


---

### *Step 3: Design for Test (DFT)*
- Uses **Fault**, an open-source DFT tool.
- **Scan Insertion**: Adds scan chains for testability.
- **Automatic Test Pattern Generation (ATPG)**: Generates test patterns.
- **Fault Coverage & Simulation**:
  - Ensures defects can be detected in silicon.
  - Reduces the number of test vectors needed.
  ![image](https://github.com/user-attachments/assets/333b5495-667a-4137-a788-69de0f090947)


---

### *Step 4: Physical Implementation*
Uses **OpenROAD** for automated **PnR (Place & Route)**.
- **Floorplanning & Power Planning**:
  - Defines **silicon area, power straps, and decoupling capacitors**.
- **Placement**:
  - **Global and detailed placement** of standard cells and macros.
- **Clock Tree Synthesis (CTS)**:
  - **Optimizes clock distribution** (H-tree, X-tree structures).
- **Routing**:
  - **Global and detailed routing** using PDK-defined metal layers.
- **Post-Placement Optimizations**:
  - **Logic Equivalence Check (LEC)** ensures netlist modifications don't change logic.  

---

### *Step 5: Antenna Rule Violation Fixing*
### **Antenna Effect**
  ![image](https://github.com/user-attachments/assets/e68fc83f-120a-4109-9370-66fa42c19849)

- During fabrication, **charge accumulation on metal wires** can damage transistors.
- **Reactive ion etching (RIE)** can cause charge buildup.
- **Fixes for Antenna Violations**:
  1. **Bridging**: Uses **top metal layers** to discharge.

      ![image](https://github.com/user-attachments/assets/c90c78ac-7a72-4eb7-9796-403bd4cd73d3)

  3. **Antenna Diode Insertion**: Adds **antenna diodes** to dissipate excess charge.
    ![image](https://github.com/user-attachments/assets/6f487980-64da-4b37-87f1-d2d6a57beac8)

- **Preventive Approach in OpenLANE**:
  - **Fake antenna diodes** added next to every cell input after placement.
  - **Antenna Checker (Magic)** detects violations.
  - If violations exist, **fake diodes are replaced with real ones**.
  ![image](https://github.com/user-attachments/assets/24a3dc2a-1705-4526-b8de-3185a7c97040)

---

### *Step 6: Sign-Off in OpenLANE*
- **STA (Static Timing Analysis)**:
  - Performed using **OpenROAD**.
  - **Timing violations and setup/hold checks**.
  ![image](https://github.com/user-attachments/assets/09f6be11-6392-4ba7-9a71-dfdb440e663f)

- **DRC (Design Rule Check)**:
  - Uses **Magic** for design rule verification.
  - Extracts **SPICE netlist from layout** for final validation.
- **LVS (Layout vs. Schematic)**
  - **Magic + Netgen** compare extracted SPICE netlist vs. synthesized Verilog netlist.
  - Ensures **physical layout matches logical design**.

---
### GSKY130_D1_SK3 - Get familiar to open-source EDA tools

### *SKY_L1 - OpenLANE Directory structure in detail*
OpenLANE is a **complete RTL-to-GDSII flow** for ASIC design, integrating multiple open-source EDA tools:

- **Yosys** - Logic Synthesis  
- **ABC** - Technology Mapping  
- **OpenROAD** - Place & Route (PnR)  
- **Magic** - DRC & LVS Verification  
- **Netgen** - LVS (Layout vs. Schematic)  

---

### *Basic Linux Commands for OpenLANE*

| **Command** | **Description** |
|------------|----------------|
| `cd ../` | Move to the parent directory |
| `ls -ltr` | List files in long format (sorted by modification time) |
| `command --help` | Get help for a command |
| `clear` | Clear the terminal screen |
| `less filename` | Open a file in read mode (Press `q` to exit) |
| `vi filename` | Open a file for editing in **vi/vim** |

---

### *Setting Up OpenLANE*
```sh
cd /work/tools/openlane_working_dir/openlane
```
![image](https://github.com/user-attachments/assets/06629ece-306a-4524-a105-cd5bbf57c11c)

- OpenLANE uses the **SkyWater 130nm PDK (SKY130)** for standard cells and routing rules.  
- We are working on the **PicoRV32a** core in OpenLANE.  

---

### *Understanding Open_PDKs*
- **Open_PDKs** is an open-source **PDK (Process Design Kit) manager** that sets up **SkyWater 130nm (SKY130)** for various EDA tools.

---

### *Understanding SKY130A*
- **SKY130A** is the **open-source process node** from **SkyWater**.
- It includes:
  - **Standard cells, I/O cells, and analog libraries**
  - **DRC, LVS, and routing rules**

---

### *Library Directories in OpenLANE*

#### 1. `libs.ref`
```sh
cd /work/tools/openlane_working_dir/pdks/sky130/libs.ref
```
- **Technology-specific** libraries (standard cells, I/O cells, SRAMs).  
- Contains **characterization data, timing models, and layouts**.

#### 2. `libs.tech`
```sh
cd /work/tools/openlane_working_dir/pdks/sky130/libs.tech
```
- **Tool-specific** libraries (for synthesis, placement, routing, and verification).  
![image](https://github.com/user-attachments/assets/3a9fccd1-3e02-4fb8-a1ac-5b90431b7c81)

---

### *Understanding SKY130 Naming Convention*
Example: `sky130_fd_sc_hd`

| **Part**  | **Meaning** |
|-----------|------------|
| `sky130`  | SkyWater 130nm node |
| `fd`      | Foundry |
| `sc`      | Standard Cells |
| `hd`      | High-Density variant |

Other variants:  
- **`sky130_fd_sc_hs`** → High-Speed  
- **`sky130_fd_sc_lp`** → Low-Power  

---

### *Tech LEF vs. LEF*

#### 1. LEF (Library Exchange Format)
- Defines **abstract views** of standard cells (for placement & routing).  
- Contains only **bounding box, pin locations, and blockage info**.  

#### 2. Tech LEF
- Defines **PDK-specific technology rules** for routing, via definitions, etc.  
- Includes **metal layers, via resistance, and design rules**.  

---

