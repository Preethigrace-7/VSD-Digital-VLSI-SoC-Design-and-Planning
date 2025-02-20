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

### *SkyWater 130nm Open-Source PDK*
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
### SKY_L2 - Design Preparation Step

### *Running OpenLANE in Interactive Mode*

To start OpenLANE in **interactive mode**, use the following command:

```sh
./flow.tcl -interactive
```

- The `-interactive` flag allows **manual control** over the flow.
- Running the command **without** `-interactive` executes the **entire flow automatically**.
- Once inside OpenLANE, the prompt will change to `%`.

### *Loading Required Packages*

Before proceeding, **load the required OpenLANE package**:

```tcl
% package require openlane 0.9
```

### *Navigating to the Design Folder*

We are working on the **picorv32a** design located in OpenLANE’s design directory.
![image](https://github.com/user-attachments/assets/0ee4895b-6a0b-4eae-8e88-cde22bd51668)

- The **RTL source files** and **SDC (netlist constraints)** are in the `src` folder.
- The **configuration file** `config.tcl` is also inside the `picorv32a` folder.

### *Editing the Configuration File*
![image](https://github.com/user-attachments/assets/f73d09a1-38fb-450c-a09a-34ce4e4080c5)

The `config.tcl` file allows **customizing design parameters**.
For example, to override the default clock period, set:

```tcl
set ::env(CLOCK_PERIOD) 5
```

This **overrides the default clock period** for **picorv32a**.

### *Preparing the Design*

To merge `.lef` and `.tlef` files into a single file and prepare the design:

```tcl
% prep -design picorv32a
```
![image](https://github.com/user-attachments/assets/d63ced44-a1dc-4c7b-893f-577bace3848e)

This step **initializes** the design and prepares it for **further processing**.

---

### SKY_L3 - Review Files After Design Prep and Run Synthesis

### *Review Files After Design Prep*
Once the design preparation is completed, a `runs` directory is created with the current date as its folder name.
![Image](https://github.com/user-attachments/assets/73f6d181-0923-4778-aacd-536836c0750e)
Inside the `runs` directory, we have:
- **Results folder**: Stores outputs for each stage of the design flow.
- **Reports folder**: Contains logs and reports generated during the process.
- **config.tcl file**: Found in the latest date folder, showing the parameters and details used for that design run.

### *Checking Configurations*
To verify if modifications are correctly reflected, we can inspect the `config.tcl` file:
```sh
less runs/<latest_date_folder>/config.tcl
```
Press `q` to exit the file viewer.

### *Running Synthesis*
To start the synthesis step, use the following command:
```sh
% run_synthesis
```
This step is handled by **Yosys** and **ABC**, which optimize and map the RTL into gate-level logic.

After synthesis, the generated reports can be found in the `runs/<latest_date_folder>/reports/synthesis/` directory.
![image](https://github.com/user-attachments/assets/52703060-7f40-4929-8aac-f196f0f30361)

---
### SKY_L5 - Steps to Characterize Synthesis Results

Once the **Static Timing Analysis (STA)** is done and synthesis has occurred, we need to characterize the synthesis results by calculating the **flop ratio**.

### *Flop Ratio Calculation:*
- **Formula:**
  ```
  Flop Ratio = (Number of Flip-Flops) / (Total Number of Cells)
  ```
  ![image](https://github.com/user-attachments/assets/750cb125-b595-440f-bc7b-2acbc8e3d4af)

- For our case:
  ```
  Flop Ratio = 1613 / 14876 = 0.108429685
  ```
- Convert to percentage:
  ```
  0.108429685 × 100 = 10.84%
  ```

### *Where to Find These Details:*
- Synthesis details are stored in the **runs/** folder.
- Navigate to the **latest date folder** inside the runs directory.
- we need to check the synthesis reports to validate the number of flip-flops and total cells.

---
## SKY130 Day 2 - Good Floorplan vs Bad Floorplan and Introduction to Library Cells

### SKY130_D2_SK1 - Chip Floor Planning Considerations

### SKY_L1 - Utilization Factor and Aspect Ratio

### *First Step of Physical Design*
The first step in physical design is to define the **width** and **height** of the **core** and **die**.

![image](https://github.com/user-attachments/assets/d08b344e-94bd-4890-a46c-26775e131f70)

### *Understanding the Netlist*
- The netlist represents the connectivity of standard cells.
- The most important components are **standard cells**.

![image](https://github.com/user-attachments/assets/ee9231b6-a01b-4dc1-92de-fa53c970bb4f)

![image](https://github.com/user-attachments/assets/d5363f73-43ab-408e-a908-7b85283c2751)


### *Core and Die Section of a Chip*
- The **core** is the active area where logic is placed.
- The **die** is the overall chip boundary.

![image](https://github.com/user-attachments/assets/12fc3d57-4b90-4452-97fa-5327a74842dd)

### *Utilization Factor*
- **Formula**: `Utilization Factor = (Area occupied by netlist) / (Total area of core)`
- Ideal utilization is **50% - 60%**, not 100%, to allow routing space.

### *Aspect Ratio*
- **Formula**: `Aspect Ratio = Height / Width`
- If **Aspect Ratio = 1**, the shape is a **square**.
- If **Aspect Ratio ≠ 1**, the shape is a **rectangle**.

![image](https://github.com/user-attachments/assets/fe8cab00-42bc-4002-8bdf-d137a6bb2cec)

---
### SKY_L2 - Concept of Pre-Placed Cells

### *Definition:*
Pre-placed cells are specific functional blocks in a design whose locations are fixed during the early stages of physical design. These cells are strategically positioned to optimize performance, reduce routing congestion, and ensure modular design implementation.

### *Purpose of Pre-Placed Cells:*
- Used in large circuits by dividing them into smaller, manageable modules.

  ![image](https://github.com/user-attachments/assets/0aa38eaf-b93c-4716-92c4-47ffd18d37ae)

- Each module is implemented separately and then integrated.
- Allows extending I/O pins and black-boxing modules (hiding internal details).

  ![image](https://github.com/user-attachments/assets/2d526182-7902-4b19-b464-d861f30f62b2)

- Enables design reuse by implementing functionality only once and integrating multiple times.
- Once placed, their locations remain unchanged to maintain design integrity.

  ![image](https://github.com/user-attachments/assets/eb6c7ec0-f5f0-4a3d-99af-fe4208d3dee7)

  - some IP's are Memory, mux, clock-gating cells, comparator, etc.

### *Benefits:*
- Simplifies integration of different IP blocks.
- Reduces overall design complexity and enhances scalability.
- Ensures consistent and predictable design performance.
---
### SKY_L3 - De-coupling Capacitors

### *Continuing with Pre-Placed Cells*

If we have blocks A, B, and C as pre-placed cells, they are usually positioned close to the input side for efficiency. These pre-placed cells need to be surrounded by decoupling capacitors to ensure stable power delivery.

![image](https://github.com/user-attachments/assets/8a49a382-66a3-47aa-a036-548eea074592)

### Why Do We Need Decoupling Capacitors?
- When power is supplied to a complex circuit, voltage drops occur due to the physical resistance of wires.
- The voltage received at the circuit might not equal the actual voltage source, potentially causing the circuit to fail to switch.
- According to noise margin considerations, if the voltage falls within the noise margin area, the circuit remains operational. However, if it enters the undefined or grey area, the circuit may not switch properly.

![image](https://github.com/user-attachments/assets/1bc1d219-847f-43f8-bbdd-b51eeb8719db)

### Role of Decoupling Capacitors
- A decoupling capacitor **charges** when the circuit is not switching.
- When the circuit requires a charge, the capacitor **discharges** to provide immediate power.
- This ensures voltage stability, preventing fluctuations that might lead to functional failures.

![image](https://github.com/user-attachments/assets/3f3e37fe-1aae-4b7b-b3ca-ce4d5ff01b0d)

### Ensuring Proper Local Communication
- Once decoupling capacitors are placed around pre-placed cells, we can efficiently manage local power distribution and communication within the circuit.

![image](https://github.com/user-attachments/assets/2dc1c1dd-e627-4bf7-b2ab-624b87a3d7f0)

---

### SKY_L4 - Power Planning

In complex circuits, multiple interconnected blocks exist within a chip. The signal transition from one circuit to another must be sustained until it reaches the connected circuit. To ensure this, **VDD** and **GND** are strategically placed between them.

![image](https://github.com/user-attachments/assets/d917d423-9a88-4e5a-b864-4a609eed8579)

### *Power Challenges in a Circuit*

1. **Signal Integrity**  
   - Consider a **16-bit bus** where logic transitions occur (charging for `1` and discharging for `0`) in between the circuits.

     ![image](https://github.com/user-attachments/assets/a6a338e7-2fc3-4c36-a157-bfe44e72eb37)

   - If capacitors discharge simultaneously to `0`, it causes **ground bounce**.

     ![image](https://github.com/user-attachments/assets/4ae2c5b0-7e91-47bc-a054-a5bf5236ebfd)

   - If capacitors request voltage simultaneously, it results in **voltage droop**.

     ![image](https://github.com/user-attachments/assets/c57b5759-e23a-4a9c-8374-4da7c0ea88c9)


2. **Ground Bounce**  
   - This occurs when multiple capacitors discharge at the same time, causing a temporary rise in ground potential.

3. **Voltage Droop**  
   - This happens when multiple capacitors demand voltage simultaneously, leading to a temporary drop in supply voltage.

## Solution: **Power Mesh Architecture**

To mitigate these issues:
- Multiple power supply connections are added instead of a single supply.
- The circuit draws power from the nearest supply.

  ![image](https://github.com/user-attachments/assets/ae87229e-ed50-4ee0-932b-4d3d687871c2)

- **VDD** and **VSS** are connected in a **vertical and horizontal power mesh** to distribute power efficiently.
![Image](https://github.com/user-attachments/assets/1aff0b22-7617-435d-baa8-74f742f78323)

---

### SKY_L5 - Pin Placement and Logical Cell Placement Blockage

### *Pin Placement Strategy*

Let's consider a design with:
- **2 Flip-Flops (FFs)**
- **1 NOT Gate**
- **1 AND Gate**
- **Preplaced Cells**: Block A, Block B, and Block C
  
![image](https://github.com/user-attachments/assets/a0b0169f-f677-4168-be80-c731be1cd21b)

![image](https://github.com/user-attachments/assets/8a126c2c-2acb-4f21-9999-f9618cfb8991)


### *Circuit Description:*
- **Block A** takes `Din1` and `Din2` as inputs and connects to the AND gates of both circuits.
- **Block B** takes inputs from two different clocks (`clk1`, `clk2`) and outputs `clkout`.
- **Block C** takes `Din3` and `Din4` and connects to the AND gates of the third and fourth circuits.

  ![image](https://github.com/user-attachments/assets/7de10588-c3fb-4e8f-aec4-14427aae0852)


### *Port Placement in the Chip:*
1. **Input Ports on the Left**  
   - All input signals (`Din1`, `Din2`, `Din3`, `Din4`, `Clk1`, `Clk2`) are placed on the left side.
   
2. **Output Ports on the Right**  
   - All outputs (`Dout1`, `Dout2`, `Dout3`, `Dout4`, `Clkout`) are placed on the right side.
     
![image](https://github.com/user-attachments/assets/48832fc6-583a-4b32-a973-3bd231585151)

3. **Preplaced Cells & Port Alignment**  
   - Ports are placed **close to preplaced cells** since their positions are fixed.
   - This ensures **shorter wire lengths** and **efficient routing**.

4. **Clock Ports Considerations**  
   - **Clock ports are larger** than data ports.
   - This reduces resistance, ensuring a stable clock signal throughout the chip.

### *Logical Cell Placement Blockage*
- The **reserved area** around ports ensures that no other standard cells are placed there.
- Only **ports** are allowed in these regions.
  
![image](https://github.com/user-attachments/assets/ac3d446c-1baa-4722-8731-7afb7944ca90)

This completes the **placement stage**, ensuring an optimized layout for further design steps.

---
 
### SKY_L6 - Steps to Run Floorplan Using OPENLANE  

We are covering floorplan.  

After the synthesis flow, the next stage is floorplanning.  
- Standard cell placement happens in the placement stage.  
- Macros are placed in the floorplanning stage.   

### *Checking Required Variables*
To check the variables required for each stage, navigate to the `README.md` file in the OpenLane configuration folder:  

```sh
cd $OPENLANE_ROOT/configuration
less README.md
```
![image](https://github.com/user-attachments/assets/7ccb5c8c-6d91-41c8-9f91-c8f3acaa2748)


For floorplan, we need to check the following variables:  

- `FP_IO_HMETAL`  
- `FP_IO_VMETAL`  
- `FP_CORE_UTIL`  

To check the definitions and default values of these variables, use:  

```sh
grep 'FP_IO_HMETAL' README.md
grep 'FP_IO_VMETAL' README.md
grep 'FP_CORE_UTIL' README.md
```  

### *Understanding the PnR Flow*

- Initially, the Place & Route (PnR) flow is iterative.  
- After congestion analysis, we need to meet timing constraints.  

### *Setting Configuration Variables*

Each stage has a default settings file in the OpenLane `configuration` folder.  
We can override these settings in `config.tcl` in the `design` folder.  

![image](https://github.com/user-attachments/assets/f83486eb-5082-4b20-9159-989ba108893c)


The priority order for configurations:  
1. **System default (lowest priority)**  
2. **config.tcl in the design folder**  
3. **sky130A_sky130_fd_sc_hd_config.tcl in the picorv32a folder (highest priority)**  

Once the configuration is set, we can run the floorplan using: 

### *Command to Run Floorplan*
To run floorplan, use the following command:  

```sh
run_floorplan
``` 
![image](https://github.com/user-attachments/assets/47b1e4c4-0eb8-4c58-b8e6-24be2b8c4868)

![image](https://github.com/user-attachments/assets/3945971b-eea9-40e2-b756-5946575d79a3)

---

### SKY_L7 - Review Floorplan Files and Steps to View Floorplan  

### *Checking Floorplan Changes*

1. Navigate to the `runs` folder to check if the changes have been applied:  

   ```sh
   cd runs/<latest_run>/logs/floorplan
   less io_placer.log
   ```
  ![image](https://github.com/user-attachments/assets/9e5d7128-e040-4217-b7d5-5fd6d1aef3f8)

   - This log file contains details of I/O placement using system defaults.  
   - Verify if the expected modifications are reflected.

  ![image](https://github.com/user-attachments/assets/23342568-a049-471e-a9c0-376db6a30cfb)


2. To check all parameters accepted by the current flow, inspect `config.tcl` in the `runs` folder:  

   ```sh
   less runs/<latest_run>/config.tcl
   ```
![image](https://github.com/user-attachments/assets/00922567-8da7-4d03-8496-ec5cbd0199c2)


### *Viewing Floorplan*

1. The floorplan results can be found in the `results/floorplan` directory.
   
   ![image](https://github.com/user-attachments/assets/b1890c3e-7885-4a08-97e9-a0982cc4a2e9)

2. The `.def` file (Design Exchange Format) contains placement orientation, placement details, and die area.

![image](https://github.com/user-attachments/assets/5a04408b-e5b7-417f-a7dd-3f2e5987be62)

### Opening Floorplan in Magic  

![image](https://github.com/user-attachments/assets/445ebf36-9731-4e63-ba37-d4a34b067ad7)

To visualize the floorplan using **Magic**, use the following commands:  

```sh
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

- `&` at the end frees up the terminal prompt, allowing further commands to be entered.  
- Ensure that the tech file path and `picorv32a.floorplan.def` are correctly set for your design.  

---

### SKY_L8 - Review Floorplan Layout in Magic  

### *Centering the Layout*
- Press **S** to select.  
- Press **V** to center the selected area.  

### *Navigating the Layout*
- **Selecting a region**:  
  - Left-click on one corner.  
  - Right-click on the opposite corner.  
- **Zooming**:  
  - Press **Z** to zoom in.  
  - Press **Shift + Z** to zoom out.  
![image](https://github.com/user-attachments/assets/6483a9ea-2292-4d59-9849-ef902e2898c8)

### *Observing Floorplan Components*
- Input and output pins are placed as per design.  
- **Tap cells** are arranged to avoid latch-up conditions by connecting **nwell to VDD**.  
- **Decoupling (DCAP) cells** are placed at the boundary for power stability.  
![image](https://github.com/user-attachments/assets/e9f4c0e1-7674-4330-b5c3-ef71c4a70be3)


### *Inspecting Cell Details in `tkcon`*
1. Move the cursor over a pin or cell.  
2. Press **S** to select it.  
3. Open the **tkcon** window and type:  

   ```sh
   what
   ```
![image](https://github.com/user-attachments/assets/a1807a7d-5921-48bd-9519-15659adf9c8c)

   - This command displays the **cell layer and name**.
   ![image](https://github.com/user-attachments/assets/f6c2d6ee-14de-4c8e-b5ba-167a428c0c57)


### *Placement of Standard Cells*
- Standard cells are present in the floorplan but are not yet placed in the designated area.  
- Initially, they appear in the **lower corner** of the layout.  
![image](https://github.com/user-attachments/assets/86a7ce9c-f0a9-473c-84d4-86404101d67c)

---

## SKY130_D2_SK2 - Library Binding and Placement  
### SKY1_L1 - Netlist Binding and Initial Place Design  

### *Placement and Routing*

### 1. Bind Netlist with Physical Cells  
- The **shape of gates** determines functionality, but in reality, everything is represented as **rectangular or square boxes**.  
- Each **flip-flop, NOT gate, AND gate**, etc., is assigned a proper **width and height**.  
- These **predefined shapes** are stored in the **library**, which also contains **timing information** for each cell.
  ![image](https://github.com/user-attachments/assets/714d4ca9-db97-480c-b715-35f914742f76)

- **Types of libraries**:  
  - One **library** stores **physical dimensions** (width & height).  
  - Another **library** stores **timing-related** information.  
- The same cell is available in **multiple sizes**:  
  - **Larger size** → **Faster operation** (Lower delay).  
  - **Smaller size** → **Higher delay**.  
- Cells are selected based on **timing constraints** in the design.
  ![image](https://github.com/user-attachments/assets/b68b272d-485b-4c89-a72c-4bba0997febd)


### 2. Placement  
- This step **places all the standard cells** onto the floorplan based on the netlist connectivity.  
- The **cells are positioned in the core area** while ensuring optimized **signal paths**.  
- Placement follows the **logical structure of the netlist** as illustrated in the design diagram.
  ![image](https://github.com/user-attachments/assets/cea8df12-faec-464b-bfab-0fdc7174c537)

---


### SKY_L2 - Optimize Placement Using Estimated Wire Length  

### *3. Optimize Placement*

### Signal Integrity Considerations  
- To maintain **signal integrity**, we **add repeaters (buffers)**.  
- Buffers help transmit signals across **long distances** (beyond a default threshold).  
- However, excessive buffer insertion **increases area usage**, so **optimization is necessary**.  
![image](https://github.com/user-attachments/assets/c68e0d17-8e89-4747-982d-e254f0eb72c2)

### **Wire Length and Capacitance Estimation**  
- **Wire length estimation** helps in determining **capacitance values**.  
- **Higher capacitance** requires **more charge** to drive, leading to **higher slew rates**.  
- Based on estimated capacitance, **repeaters are inserted** at strategic points.  

### **Buffer Functionality**  
- Buffers **regenerate the received signal** and **transmit it further** to either:  
  - Another **buffer** (if the distance is large).  
  - The **target cell** (if within range).  

This optimization step ensures **efficient signal transmission** while **minimizing area overhead**.  

---

### SKY_L3 - Final Placement Optimization  

### *Handling Wire Overlaps*
- **Wire overlapping** is resolved by **routing them on different metal layers**.  
- Different layers help in avoiding **short circuits** and **crosstalk** issues.  

### *Final Placement Considerations*
- **Legalization** ensures all cells are **placed properly** without violations.  
- **Optimization algorithms** refine placement for **better wire length, timing, and congestion reduction**.  
- The final placement stage ensures **minimal design rule violations (DRVs)** before routing.  

This step finalizes the **placement of standard cells** while ensuring **signal integrity and manufacturability**.  
---

### SKY_L4 - Need for Libraries and Characterization

### *Library Characterization and Modeling*
- **Characterization** is essential for defining the **behavior and timing** of standard cells.
- A **library** is a collection of gates/cells with **physical, electrical, and timing** attributes.
- Characterized libraries are used across **placement, clock tree synthesis (CTS), and routing**.

### *Clock Tree Synthesis (CTS)*
- Ensures the **clock signal reaches all sequential elements (flops)** at the **same time**.
- Minimizes **clock skew** for accurate timing.

### *Final Routing*
- **Maze routing** is used to establish **optimal interconnections** between components.
- Ensures **minimal delay, congestion, and DRV (Design Rule Violations)**.
![image](https://github.com/user-attachments/assets/450aadbb-8614-4508-8ee0-292ea837a9ca)

### *Static Timing Analysis (STA)*
- Involves analyzing **data arrival time** and **data required time** for **launch and capture flops**.
- Ensures timing constraints are met for functional correctness.
![image](https://github.com/user-attachments/assets/b6d4d496-0bb5-427e-b7d7-77a58fb280e1)

### *Why Library Characterization is Important?*
- Libraries define the **cells used in all design stages**.
- Each gate/cell in the library must be **modeled accurately** to ensure the design functions correctly.

### *Next Steps: Understanding Cell Design Flow*
- We will explore **how cells are designed and characterized** to be used in libraries.
---

### SKY_L5 - Congestion Aware Placement Using RePlAce

### *Stages of Placement*
Placement occurs in **two stages**:

1. **Global Placement (Post Placement)**
   - Reduces **wirelength** using **HPWL (Half-Perimeter Wire Length)**.
   - Converges design by reducing **overflow (congestion)**.

2. **Detailed Placement**
   - **Legalization** is performed to ensure:
     - **No overlaps** between standard cells.
     - **Timings constraints** are met.

### *Running Placement in OpenLane*
- Use the following command:
  ```sh
  run_placement
  ```
  ![image](https://github.com/user-attachments/assets/622636c9-3f3b-4ab1-ae34-5bc8e5e97766)

  ![image](https://github.com/user-attachments/assets/b125d3bc-49b8-46a8-a866-f6f87532f761)

  ![image](https://github.com/user-attachments/assets/f4d2a829-b0dc-47d6-b20f-e81c3ace6ab1)


- After running, a `.def` file is created at:
  ```
  runs/results/placement/
  ```

### *Viewing Placement in Magic*
- Open the placement **DEF file** in **Magic**:
  ```sh
  magic -T <tech_file> lef read ../../tmp/merged.lef def read <design>.placement.def &
  ```
- The **standard cells** are placed in the **core area**, initially located in the **lower-left corner** of the floorplan.
![image](https://github.com/user-attachments/assets/16da2801-4d03-407c-bf73-6d3e1ec93fbd)

![Image](https://github.com/user-attachments/assets/d89818b8-de6a-4e7f-9258-05f7ad9ea0d9)

### *Power Distribution Network (PDN)*
- **PDN creation** typically happens in **floorplanning**, but in OpenLane, the sequence differs.
- Before **routing**, generate the **PDN** using:
  ```sh
  gen_pdn
  ```
---

### D2 SK3 - Cell Design and Characterization Flows  
### **Cell Design Flow**  
The **cell design flow** involves designing, placing, and routing standard cells used in a digital design.  

### **Standard Cell Library**
- The **library** contains all standard cells with their **physical and electrical characteristics**.
- **Sizes** are referred to as **drive strengths**.
- **Threshold voltage (Vt)** varies for different cells.
![image](https://github.com/user-attachments/assets/84d84ca7-0d76-49fe-8035-728d7b15d365)

### **SKY_L1 - Inputs for Cell Design Flow**  
### **Example: Inverter Design**
An **inverter** has:
- **Single input**
- **One output**
- **Defined drive strength and threshold voltage variations**

### *Cell Design Flow Steps*
1. **Inputs**
   - Technology file (PDK)
   - Specifications (Voltage, Drive strength, Delay requirements)
   - Library constraints

2. **Design Steps**
   - **Schematic Design**
   - **Simulation** (SPICE, Spectre)
   - **Layout Design**
   - **DRC & LVS Checks** (Design Rule Check & Layout vs. Schematic)
   - **Characterization** (Timing, Power, Noise)

3. **Outputs**
   - Standard Cell Layout
   - Timing and Power Reports
   - Extracted Library Files (LEF, LIB, GDSII)
  
     ---
  
### SKY_L2 - Circuit Design Steps  

### *1. Inputs*
The inputs required for circuit design include:  
- **PDK (Process Design Kit)**  
- **DRC & LVS** (Design Rule Check & Layout vs. Schematic)
  ![image](https://github.com/user-attachments/assets/1a7e0f0a-35d8-462d-8a28-2b5ae7b905f0)

- **SPICE Models**
  ![image](https://github.com/user-attachments/assets/91de37c6-77d5-4371-a012-d3dd0e12d843)


### Library and User-Defined Specifications
- **Cell Height:** The height of a standard cell in the library, usually determined by the number of metal routing tracks available.
![image](https://github.com/user-attachments/assets/cfeb793c-e715-4fe3-a9ea-f7fb1ca2eb98)

- **Supply Voltage (VDD, VSS):** The voltage levels used for power and ground in the circuit, affect performance and power consumption.  
- **Metal Layers:** The number of metal interconnect layers available for routing signals and power within the design.
  ![image](https://github.com/user-attachments/assets/9a282fe0-501a-40b1-ad5b-2237d20daf3d)

- **Pin Location:** The fixed positions of input and output pins in the layout, affect routing complexity and signal integrity.
![image](https://github.com/user-attachments/assets/c8a71e04-df78-434c-8b35-e78bf9d3f82d)

- **Drawn Gate-Length:** The transistor gate's physical length impacts switching speed, leakage, and overall performance.  

### *2. Design Steps*
- **Circuit Design:**  
  - Choosing **W/L ratios**  
  - **Drain current analysis**  
  - Simulation using **SPICE models**  
  - Determining **final transistor sizes**  

- **Layout Design:**  
  - Based on the circuit specifications  
  - Ensuring compliance with **design rules**  

### *3. Outputs*
- **CDL (Circuit Description Language):** A netlist format used for circuit verification and integration with other tools.  

---

### SKY_L3 - Layout Design Step  

### *1. Layout Concepts*
- **Euler’s Path:** A method to determine the optimal transistor placement in a layout by ensuring that each node is visited only once, reducing diffusion breaks.
  ![image](https://github.com/user-attachments/assets/9ea8dfdc-a297-453a-ac3b-05f32839578e)
 
- **Stick Diagram:** A simplified representation of the circuit layout using colored lines to indicate different layers and connections.
  ![image](https://github.com/user-attachments/assets/0d186e4e-5b41-443d-be75-f6dc6f9929d3)


### *2. Layout Outputs*
- **GDSII (Graphic Data System II):** The standard file format used for storing IC layout data, required for fabrication.  
- **LEF (Library Exchange Format):** Contains abstracted cell information like height, width, and pin locations, essential for placement and routing.  
- **SPICE Netlist (.cir file):** Captures parasitic capacitance and other extracted parameters for post-layout simulation and verification.  

### *3. Layout Generation Process*
- Layout is created based on the **circuit design** and **foundry DRC & LVS rules** to ensure manufacturability and correctness.  
---

### SKY_L4 - Buffer Characterization using GUNA  

### **Overview**  
We have the following components for characterization:  
- **Layout of Buffer**  
- **Buffer Description**  
- **SPICE Extracted Netlist of Buffer**  
- **Subcircuit File (Contains NMOS and PMOS models)**  
- **Resistances and Capacitances**  

By combining these elements, we generate the necessary simulation setup for extracting key parameters such as **timing, noise, power, and functional characteristics** using **GUNA software**.  

---

### **Step-by-Step Process**  

### *Step 1: Load Models*
- Read **NMOS** and **PMOS** models from foundry:  
  ```spice
  .model nmos <parameters>
  .model pmos <parameters>
  ```

### *Step 2: Load Extracted SPICE Netlist*
- Read the **SPICE-extracted netlist** of the buffer, which includes parasitic resistances and capacitances.  
  ```spice
  .include buffer_extracted.spice
  ```
![image](https://github.com/user-attachments/assets/9c4acf6e-26b7-4371-8b57-1f3cf6fb4dde)

### *Step 3: Recognize Buffer Behavior*
- Identify how the buffer interacts with signals and power sources.  

### *Step 4: Read Subcircuit of Inverter*
- Attach the **my_inv** subcircuit for logic processing.  
  ```spice
  Xinv input output VDD VSS my_inv
  ```

### *Step 5: Attach Power Sources*
- Provide **VDD** and **GND** connections to ensure circuit operation.  
  ```spice
  VDD VDD 0 1.8V
  VGND 0 0 0V
  ```

### *Step 6: Apply Stimulus*
- Define input signals for analysis (e.g., step, pulse, or sinusoidal inputs).  
  ```spice
  Vin input 0 PULSE(0 1.8 0 1n 1n 5n 10n)
  ```

### *Step 7: Add Output Capacitances*
- Model load capacitances at the output.  
  ```spice
  Cload output 0 10f
  ```
![image](https://github.com/user-attachments/assets/a403291f-b734-4039-97a4-19ccb283dea4)

### *Step 8: Set Up Simulation Commands*
- Define the type of analysis to perform (e.g., **Transient, DC, or AC** analysis).  
  ```spice
  .tran 0.1n 10n
  .dc Vin 0 1.8 0.01
  ```

### *Step 9: Run GUNA Software for Characterization*
- Feed all **SPICE netlist files** into GUNA.  
- Extract parameters such as **timing, noise, power, and functional characteristics**.  
- Merge the extracted data with the **library characterization process** for final integration.  


### *Final Output*
After running all steps in **GUNA**, we obtain:  
- **Timing Parameters** (Delays, Transition Time)  
- **Noise Characteristics**  
- **Power Consumption**  
- **Functional Library (LIB) File for Further Use**

  ---
