<p align="center">
  <img src="https://www.vlsisystemdesign.com/wp-content/uploads/2016/12/vsd_logo.jpg" alt="VSD Logo" width="250">
</p>

# Digital VLSI SoC Design and Planning 15 Days Learning Journey

This repository documents my learnings from the **Digital VLSI SoC Design and Planning** course by **VLSI System Design (VSD)**. Over 15 days, I hve explored key concepts, methodologies, and tools used in SoC design, documenting my progress and insights here.

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
### SKY130_D1_SK3 - Get familiar to open-source EDA tools

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
## Day 2 - Good Floorplan vs Bad Floorplan and Introduction to Library Cells

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

### D2_SK3 - Cell Design and Characterization Flows  
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

## SKY130_D2_SK4 - General Timing Characterization Parameters  

### **SKY_L1 - Timing Threshold Definitions**  

### *Overview*
In this section, we define key timing threshold parameters used in **timing.lib** and **power.lib** files. These parameters help in waveform analysis and delay characterization.  

### *Waveform Threshold Definitions*

1. **Slew Low Rise Threshold (`slew_low_rise_thr`)**  
   - Defines the **80% voltage point** of the rising edge.  
   - **Low** means the initial voltage is close to **0V**.  
![image](https://github.com/user-attachments/assets/44c42cbc-a7dd-4ed9-be5e-8969fbfd7d80)

2. **Slew High Rise Threshold (`slew_high_rise_thr`)**  
   - Defines the **20% voltage point** of the rising edge.  
   - Used to calculate the **rise time (slew rate)** by finding the time difference between **80% and 20% points**.  
![image](https://github.com/user-attachments/assets/ca43fafb-08c1-4efb-848e-f8e923335a11)

3. **Slew Low Fall Threshold (`slew_low_fall_thr`)**  
   - Defines the **80% voltage point** of the falling edge.  
   - The voltage decreases towards **0V**.  
![image](https://github.com/user-attachments/assets/10bbb110-e5c1-40a0-a770-1298978e3b82)

4. **Slew High Fall Threshold (`slew_high_fall_thr`)**  
   - Defines the **20% voltage point** of the falling edge.  
   - Used to calculate **fall time (slew rate)**.  
![image](https://github.com/user-attachments/assets/f4412d1f-03b8-4fa3-aac6-f196dacf4463)


### *Input and Output Threshold Definitions*

5. **Input Rise Threshold (`in_rise_thr`)**  
   - Defines the voltage point where the input signal is considered as **rising**.  
![image](https://github.com/user-attachments/assets/0d4984fa-1822-4b03-bdf4-f432a8b665b3)

6. **Input Fall Threshold (`in_fall_thr`)**  
   - Defines the voltage point where the input signal is considered as **falling**.  

7. **Output Rise Threshold (`out_rise_thr`)**  
   - Defines the voltage point where the output signal starts **rising**.  
![image](https://github.com/user-attachments/assets/c72adf22-572b-4a9e-8047-d525720bb89f)

8. **Output Fall Threshold (`out_fall_thr`)**  
   - Defines the voltage point where the output signal starts **falling**.  
![image](https://github.com/user-attachments/assets/c225738a-64ae-4a8a-a14e-cd3238749e39)

---

### **Timing Characterization in `.lib` Files**  
- These thresholds are used in **Liberty (.lib) timing models** to define **propagation delay, transition time, and setup/hold constraints**.  

---

### SKY_L2 - Propagation Delay and Transition Time  

### *1. Propagation Delay Definition*
Propagation delay (\(t_{pd}\)) is the time difference between the input signal and the corresponding output signal transition.  

### Formula for Delay Calculation
\[
t_{pd} = \text{time}(out\_thr) - \text{time}(in\_thr)
\]
where:  
- `out_thr` = Output threshold voltage (typically 50%)  
- `in_thr` = Input threshold voltage (typically 50%)
  ![image](https://github.com/user-attachments/assets/59c6c519-7cc2-4a5a-afd1-84bb1a8029b6)


A correct choice of threshold voltage ensures positive delay.  
If the threshold is incorrect, it may result in negative delay.  

### **Wire Delay Impact**  
If a wire introduces delay before the input signal reaches the logic gate, it can lead to a negative delay.  
Even with correct threshold selection, wire delays can distort timing.  
![image](https://github.com/user-attachments/assets/c3143e66-3a92-4efd-82d3-5cb40875fa5f)

---

### *2. Transition Time (Slew Rate)*
Transition time refers to the time taken for a signal to transition from **low to high** or **high to low**.  

### **Typical Threshold Values for Transition Calculation**  
- **Low Threshold (20%)**: 0.36V  
- **High Threshold (80%)**: 1.44V  
![image](https://github.com/user-attachments/assets/292db359-0882-4c52-becc-29daaeb6b452)

### **Formula for Slew Calculation**  
\[
t_{slew} = \text{time}(80\%) - \text{time}(20\%)
\]
- This gives the **rise time** or **fall time**.  
- Direct subtraction of threshold timing values provides **slew rate**.
---


## SKY130 DAY 3 - Design Library Cell using Magic Layout and NGSpice Characterization  

### *SKY130_D3_SK1 - CMOS Inverter NGSpice Simulations*
- Perform NGSpice simulations for CMOS inverter characterization.  
- Validate signal transitions, propagation delay, and power characteristics.  

---

### SKY_L0 - IO Placer Revision

### *Downloading and Integrating .mag File*
- Download the `.mag` file from GitHub.  
- Integrate the cell into `picorv32a` for verification.  

### **Modifying Configuration in OpenLane**  
- Update `config.tcl` file:  
  ```tcl
  set ::env(FP_IO_MODE) 2
  ```
- Run the floorplan again:  
  ```tcl
  run_floorplan
  ```
- Check the `.def` file to ensure pin placements are updated.

  ---

### SKY_L1 - SPICE Deck Creation for CMOS Inverter  

### *1. VTC - SPICE Simulations*
- Create a SPICE deck to define the connectivity of components.  
- Identify tap points and assign component values.  

### *2. Circuit Considerations*
- **Substrate Tuning:** Adjusts threshold voltage.  
- **Load Capacitor (Cload):** Depends on input capacitance and circuit parameters.  
- **Transistor Sizing:**  
  - PMOS is typically wider than NMOS (2x or 3x).  
  - Here, both transistors have the same size:  
    - \( W/L = 0.375\mu m / 0.25\mu m \)  
- **Operating Conditions:**  
  - \( V_{in} \) (Gate Voltage) = 2.5V  
  - \( V_{DD} \) (Drain Voltage) = 2.5V  

### *3. Node Identification*
- **Definition:** A node is a connection point between two or more components.  
![image](https://github.com/user-attachments/assets/a4284e89-574d-4b6c-b94f-894396213f47)

### **4. SPICE Deck Structure**  
1. **Component Connectivity**  
2. **Component Values**  
3. **Node Identification**  
4. **Node Naming**  

### **SPICE Deck Example**  

```spice
*** MODEL DESCRIPTION ***

*** NETLIST DESCRIPTION ***
M1 out in vdd vdd pmos W=0.375u L=0.25u  
M2 out in 0 0 nmos W=0.375u L=0.25u  
```

---

### **SKY_L2 - SPICE Simulation Lab for CMOS Inverter**  

#### **1. Transistor Description in SPICE**  
- Transistor connections: **Drain - Gate - Source - Substrate**  
- **NMOS (M2) and PMOS (M1) structure**  
- Load capacitor:  
  ```spice
  Cload out 0 10f
  ```
- Voltage sources:  
  ```spice
  Vdd vdd 0 2.5
  Vin in 0 2.5
  ```

#### **2. SPICE Simulation Commands**  
```spice
*** Simulation Commands ***
.op
.dc Vin 0 2.5 0.05  *Sweeps Vin from 0 to 2.5V in steps of 0.05V*
```
- **Operating Point Analysis (`.op`)**  
- **DC Sweep Analysis (`.dc`)**  
![image](https://github.com/user-attachments/assets/e94bb90f-cd03-48fd-bd20-6ec2429fc223)


#### **3. Model Inclusion**  
```spice
*** Include Model File ***
.include tsmc_025um_model.mod
.LIB "tsmc_025um_model.mod" CMOS_MODELS
.end
```
![image](https://github.com/user-attachments/assets/28c92f98-7470-4ed5-9b2b-dc58f117b87c)

- Defines transistor characteristics using **TSMC 0.25μm model**  


#### **4. Running Simulation in NGSPICE**  
1. Load the netlist:  
   ```sh
   source <filename>.cir
   ```
2. Run the simulation:  
   ```sh
   run
   ```
3. Set the plot:  
   ```sh
   setplot
   dc1
   ```
4. Plot Output vs. Input:  
   ```sh
   plot out vs in
   ```
![image](https://github.com/user-attachments/assets/bf9ba964-6275-427f-a3f1-2bd0d469566d)


#### **5. SPICE Simulation for Different W/L Ratios**  
- **Same W/L for NMOS & PMOS:** \( W/L = 1.5 \)  
- **Increased PMOS Size:**  
  - \( W/L \) for NMOS = 1.5  
  - \( W/L \) for PMOS = 2.5  
- Follow the same simulation steps as above for different transistor sizes.  

---

### **SKY_L3 - Switching Threshold (Vm) in CMOS Inverter**  
![image](https://github.com/user-attachments/assets/85a35357-7220-4498-8a08-856cc63c52e1)

- **Definition**: The switching threshold \( V_m \) is the input voltage at which the output voltage equals the input voltage (\( V_{out} = V_{in} \)).  
- **Importance**:  
  - Determines the noise margin and stability of the CMOS inverter.  
  - Ensures robust operation under variations in process, voltage, and temperature (PVT).  
- **Key Observations**:  
  - The transfer characteristic curve shifts based on transistor sizing and supply voltage.  
  - \( V_m \) is typically close to \( V_{DD}/2 \), making CMOS inverters highly reliable for digital logic.  
![image](https://github.com/user-attachments/assets/bae9962d-4f2e-4bd7-9771-d9d39ebb0d7f)

This property makes CMOS the preferred choice in industries due to its **high noise immunity and low power consumption**.

---

### **SKY_L4 - Static and Dynamic Analysis of CMOS Inverter**  

### *1. Determining the Switching Threshold (\( V_m \))*
- To find \( V_m \), draw a **45-degree line** from the origin on the Voltage Transfer Characteristic (VTC) curve.  
- The intersection of this line with the inverter’s transfer curve gives the switching threshold \( V_m \).  

### *2. Pulse Definition for Transient Analysis*
```spice
Vin in 0 0 pulse(0 2.5 0 10p 10p 1n 2n)
```
- This defines a **pulse waveform**:
  - Starts at **0V**.
  - **Rises to 2.5V**.
  - Rise time: **10 ps**, Fall time: **10 ps**.
  - Pulse width: **1 ns**.
  - Period: **2 ns**.  

### *3. Measuring Rise Delay in ngspice*
- Run transient analysis in ngspice.  
- Click on the rising edge in the waveform viewer to measure **rise delay**.  
- **Rise delay** is the time difference between **50% of input rise and 50% of output rise**.  

This helps in analyzing the **static and dynamic behavior** of the CMOS inverter.

---

### **SKY_L5 - Lab Steps to Clone and Open VSD Standard Cell Design**  

### *1. Clone the Repository*
Run the following command inside the **OpenLane** directory:  
```sh
wget https://github.com/nickson-jose/vsdstdcelldesign.git
```
or  
```sh
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```

### *2. Navigate to the Cloned Folder*
```sh
cd vsdstdcelldesign
```

### *3. Copy the Technology File*
Copy the necessary tech file into the folder using:  
go to where .tech file is located
/home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic
then 

```sh
cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/
```  

#### **4. Open the Layout in Magic**  
Launch **Magic** and open the `.mag` file:  
```sh
magic -T sky130A.tech sky130_inv.mag
```
This will load the **VSD Inverter (vsd_inv)** layout for further modifications or analysis.
![image](https://github.com/user-attachments/assets/308efc6c-d28b-45d3-a284-f331206174e8)

---

### SKY130_D3_SK2 - Inception of Layout: A CMOS Fabrication Process

### SKY_L1 - Create Active Region

### 1. Selecting a Substrate
- **Substrate Type**: P-type (most commonly used)
- **Resistivity**: 5-50 ohm-cm
- **Doping Level**: ~10¹⁵ cm⁻³
- **Doping Level Consideration**: Should be lower than well doping
- **Crystal Orientation**: 100
    ![image](https://github.com/user-attachments/assets/28e14713-9fdb-40c7-a756-355937870365)


### 2. Creating Active Region for Transistors
Active regions are where PMOS and NMOS transistors are formed.

#### Steps:
1. **Ensure Active Region Isolation**: The active region should not interfere with the P-substrate.
2. **Deposition Process**:
   - **Silicon Oxide (~40nm)**: Acts as an insulator.
   - **Silicon Nitride (~80nm)**: Acts as a mask layer.
3. **Photoresist Deposition (~1µm)**:
   - Apply a photoresist layer to define well regions.
4. **Photolithography Process**:
   - Use **UV light** to expose the mask-defined areas.
   - **No chemical reaction** occurs under masked regions.
    ![image](https://github.com/user-attachments/assets/d913389b-e616-4837-9227-05b67c9196f0)

5. **Etching Process**:
   - Wash off unexposed photoresist.
   - Remove silicon nitride from exposed areas.
   - Strip the remaining photoresist layer.
   
    ![image](https://github.com/user-attachments/assets/21e2997e-2de7-4d4a-b649-acadd8741a6f)

6. **Furnace Treatment**:
   - Formation of **isolation areas** to prevent communication between wells.
   - Growth of **Field Oxide (LOCOS - Local Oxidation of Silicon)**.
   
    ![image](https://github.com/user-attachments/assets/b8812184-170f-4cda-a9e6-1a7e21f11ef5)

7. **Final Furnace Treatment**:
   - Remove remaining **silicon nitride layer** completely.


- The isolation area forms a structure known as **Bird's Beak** due to oxide encroachment.
![image](https://github.com/user-attachments/assets/f0d6ff85-1892-406f-bfe1-b96e968f3ea7)

- These steps ensure that the transistors are electrically isolated before further processing.

---

### SKY_L2 - Formation of N-Well and P-Well

Both wells cannot be formed at the same time. The process involves multiple steps using different masks and ion implantation energies. This process can be related to the layout mask.
![image](https://github.com/user-attachments/assets/59c29b78-cac2-4421-a9c1-cfa84e91f15a)


### *3. N-Well and P-Well Formation*

1. **P-Well Formation**  
   - Apply photoresist and mask.
     
 ![image](https://github.com/user-attachments/assets/f20a6a2e-6863-44ce-a10d-1b6bb5df4e9e)

   - Remove the mask and perform ion implantation with **Boron (~200 keV)** to create the **P-Well**.
     
   ![image](https://github.com/user-attachments/assets/11d59600-5d7f-4b23-aea7-92526c806334)


2. **N-Well Formation**  
   - Apply a photoresist layer over the P-Well to protect it.
     
   ![image](https://github.com/user-attachments/assets/3018a3ff-578e-4f0d-87cf-be88941d26e6)

   - Add a mask and then remove it.  
   - Perform ion implantation with **Phosphorus (~400 keV)**
     
   ![image](https://github.com/user-attachments/assets/a3e1f38d-2b61-4bf5-bfd2-3216c0ade22c)

   - **Phosphorus requires higher energy than Boron** to create the **N-Well**.  
   - Remove the photoresist.  

3. **Diffusion Process**  
   - The wafer is placed in a **drive-in diffusion furnace**.
     
   ![image](https://github.com/user-attachments/assets/34a87094-6827-4d28-aff3-803e35709987)

   - The N-Well and P-Well diffuse further into the substrate.  
   - This is known as the **Twin-Tub Process**.
     
   ![image](https://github.com/user-attachments/assets/9adb5208-2b18-499b-bb57-7c2040baf02c)

   ---
  
### SKY_L2 - Formation of Gate Terminal

### *4. Formation of Gate*
The **gate terminal** is the **control** of the entire transistor.

### Steps:  
1. **N-Well Doping (P-Well Implantation)**  
   - Use **Mask 4** on the **N-Well** with photoresist under the mask.
   ![image](https://github.com/user-attachments/assets/77efeb4e-335e-410c-97a6-19236b2eeb17)

   - Perform **Boron implantation (~60 keV)** to set the doping concentration on the **P-Well**.
    ![image](https://github.com/user-attachments/assets/d9f88a09-60dc-42e6-b5be-da723d73e187)


2. **P-Well Doping (N-Well Implantation)**  
   - Apply **Mask 5** on the **P-Well**.
   ![image](https://github.com/user-attachments/assets/4b24053f-151b-48bb-8255-de66a469bad7)

   - Perform **Arsenic (N-doping) implantation** into the **N-Well** until the required **threshold voltage** is reached.
    ![image](https://github.com/user-attachments/assets/a6058fc4-7f16-41d6-9509-8ac3ff1dab9f)


3. **Oxide Etching and Re-implantation**  
   - **Etch the oxide layer** on both wells.  
   - **Re-implant a new oxide layer** of the same size.  

4. **Polysilicon Deposition**  
   - Deposit a **0.4 nm polysilicon layer** on the wafer.
   ![image](https://github.com/user-attachments/assets/1c8b22ae-de10-40d3-abd2-2e2c31b6c569)

   - Apply **Mask 6** to define the **gate regions**.
   ![image](https://github.com/user-attachments/assets/8e898367-17b3-4316-a295-c9fb28732828)
![image](https://github.com/user-attachments/assets/c84f43ae-7eb3-49f6-9f10-b7be878b2e37)


   - Remove the mask and **etch away unwanted polysilicon**.
![image](https://github.com/user-attachments/assets/f98db705-38f9-42df-84a2-c61c1315fb4b)

   - Remove the remaining **photoresist**, leaving the **gates** on both **N-Well and P-Well**.
   ![image](https://github.com/user-attachments/assets/dfefcf60-5e0c-4969-9707-670bb09ffe8a)


---

### SKY_L4 - Lightly Doped Drain (LDD) Formation

### 5. Lightly Doped Drain (LDD) Formation  

### *Purpose of LDD:*
1. **Hot Electron Effect** - Prevents damage due to high-energy electrons.  
2. **Short Channel Effect** - Reduces unwanted variations in transistor behavior.  

### Steps:  
1. **N-Type Implantation for P-Well**  
   - Apply **Mask 7** on the **N-Well**.
![image](https://github.com/user-attachments/assets/16128ccf-4a11-4d1c-8a91-c9046b6533e5)

   - Perform **Phosphorus implantation** for an **N-type LDD** on the **P-Well**.
  ![image](https://github.com/user-attachments/assets/4d3088b7-a7d3-4f55-bf50-64af1be9572e)


2. **P-Type Implantation for N-Well**  
   - Apply **Mask 8** on the **P-Well**.
![image](https://github.com/user-attachments/assets/db72eb52-12b7-4ba8-8af1-dab57840e0a9)

   - Perform **Boron implantation** for a **P-type LDD** on the **N-Well**.
    ![image](https://github.com/user-attachments/assets/0c784346-762b-4837-a704-1f9346e0138b)


3. **Sidewall Spacer Formation**  
   - Deposit a **thick (~0.1 µm) SiO₂ layer**.
   ![image](https://github.com/user-attachments/assets/5c8a00f5-c097-4f33-88a1-cd5658087f40)

   - Use **Plasma Anisotropic Etching** to remove unwanted oxide.  
   - The remaining **sidewall spacers** help control electric fields and reduce leakage.
   ![image](https://github.com/user-attachments/assets/0d3c9ffd-7225-48da-982a-d059e6d33539)
  - The screen oxide is to avoid channeling during implants.

---

### SKY_L5 - Source and Drain Formation  

### *6. Source and Drain Formation*

### Steps:  

1. **N+ Source/Drain Formation in P-Well**  
   - Apply **Mask 9** on the **N-Well**.
   ![image](https://github.com/user-attachments/assets/015089e1-98c6-4a67-a517-5a095244ed63)

   - Expose to **Arsenic (As) at 75 keV** for the **P-Well**.
   ![image](https://github.com/user-attachments/assets/c2ac6b1e-5192-43a5-94fd-69b37ce52466)
  
   - This helps form the **N+ source and drain regions**, with LDD already in place.  

2. **P+ Source/Drain Formation in N-Well**  
   - Apply **Mask 10** on the **P-Well**.
![image](https://github.com/user-attachments/assets/83fe41ca-0572-4eff-bf86-36365ef7b2e6)

   - Expose to **Boron (B) at 50 keV**.
   ![image](https://github.com/user-attachments/assets/3862c336-edd2-4008-a739-0b3be7bdf4e1)

   - The boron ions enter the open areas and settle down, forming the **P+ source and drain**.  

3. **Annealing Process**  
   - Expose the wafer to **high temperatures** to allow the dopants to diffuse properly.
   ![image](https://github.com/user-attachments/assets/68db8d1d-27ba-45ba-a68a-c5e84cbbea16)

   - The **N+ regions** penetrate deeper into the **P-Well**, ensuring a well-formed transistor structure.
   ![image](https://github.com/user-attachments/assets/3705af4e-10b8-45ac-a5e6-978a35594019)

   - A similar process occurs for the **N-Well** with **P+ regions**.  

---

### SKY_L6 - Local Interconnect Formation  

### *7. Steps to Form Contacts and Interconnects (Local)*

### Process Steps:  

1. **Etching Oxide**  
   - Thin oxide is etched in **HF (Hydrofluoric Acid) solution** to expose the silicon surface.  
![image](https://github.com/user-attachments/assets/929206c6-0a85-4152-89d2-ceea0e6fc79b)

2. **Titanium Deposition**  
   - **Titanium (Ti)** is deposited on the wafer surface using **sputtering**.  
   - **Sputtering**: A process where **Argon ions** hit the **Titanium target**, causing atoms to be ejected and deposited onto the wafer.  
![image](https://github.com/user-attachments/assets/e551ff50-c7bc-4c41-9e48-5b2b542f4e2c)
![image](https://github.com/user-attachments/assets/ae00f6c2-11d8-4787-b64d-7141f27fa4ae)


3. **Titanium Silicide (TiSi₂) Formation**  
   - **Titanium (Ti)** reacts with silicon when heated at **high temperatures**.
   ![image](https://github.com/user-attachments/assets/817057be-ffd9-4c1b-9851-75cba0c790c4)

   - This forms **Titanium Silicide (TiSi₂)**, which has **low resistance** and is used for **local interconnects**.  

4. **Contact Masking and Etching**  
   - A **mask 11** is used to define contact regions.
   ![image](https://github.com/user-attachments/assets/e95a7af1-582b-4e2d-9c1e-6dc0033ae4d1)

   - Excess **Titanium Nitride (TiN)** is etched off using **RCA cleaning**.
    ![image](https://github.com/user-attachments/assets/cc592ebb-01df-46ca-8095-4d70ab26b892)


5. **Photoresist Removal**  
   - The **photoresist is removed**, leaving behind the **local interconnects** for short-range connections.
   ![image](https://github.com/user-attachments/assets/e925c413-ba52-47e9-93a3-7d9cd0d50ee2)

---


# SKY_L7 - Higher Level Metal Formation  

## 8. Higher Level Metal Formation  

### Process Steps:  

1. **Planarization of the Surface**  
   - Since the surface is **non-planar**, we first **planarize** it.  
   - Deposit a thick **SiO₂ layer** doped with **Boron (BPSG) or Phosphorus (PSG)**.
   ![image](https://github.com/user-attachments/assets/9e4e663e-70e2-4bd8-a9d5-d9495f149fe6)
 
   - Polish using **Chemical Mechanical Polishing (CMP)** to achieve a flat surface.
    ![image](https://github.com/user-attachments/assets/6db5fa74-6bb4-499c-acc2-b38b5a75cd3b)


2. **Contact Hole Formation**  
   - Use **Mask 12** to define contact holes.
   ![image](https://github.com/user-attachments/assets/703144fc-37a5-45bb-8f0b-f51ede5e73ae)

   - Remove the mask and **etch SiO₂** to create the openings.  
   - Drill the contact holes and remove the **photoresist**.  

3. **Metal Deposition for Contacts**  
   - Deposit a thin **10nm TiN (Titanium Nitride) layer** as a barrier.  
   - Blanket deposit **Tungsten (W)** to fill the contact holes.
   ![image](https://github.com/user-attachments/assets/6af5d253-9798-4249-95c9-875866a6f4ca)

![image](https://github.com/user-attachments/assets/5e60b685-2d14-4f4d-bc4b-3b0bd12835bf)

![image](https://github.com/user-attachments/assets/d0720abe-0865-4122-8c3d-ff4334a67425)



   - Use **CMP** again for planarization, leaving **Tungsten in the contact holes**.
![image](https://github.com/user-attachments/assets/bcb8e7f6-5484-45e4-831e-1342b9c988be)


4. **First Metal Layer Formation**  
   - Deposit **Aluminum (Al)**.
   ![image](https://github.com/user-attachments/assets/bd142a88-5d09-4354-88dc-90258116fa15)

   - Use **Mask 13** to define interconnect patterns.
   ![image](https://github.com/user-attachments/assets/1d1d862a-bf91-4b82-aae8-bed4a44c6448)

   - Remove excess **Aluminum** using **Plasma Etching**.  
   - Remove the **photoresist** after etching.  

5. **Second Metal Layer & Via Formation**  
   - Deposit another **SiO₂ layer** for insulation.
   ![image](https://github.com/user-attachments/assets/ef5adc6a-45a9-464d-9f92-438e43b16400)

   - Planarize using **CMP**.  
   - Use **Mask 14** to drill via holes.  
   - Deposit **TiN** followed by **Tungsten (W)** for via formation.  
![image](https://github.com/user-attachments/assets/a33d0133-fad1-49f5-ada5-4c8e0afb39b7)


6. **Third Level of Interconnects**  
   - Use **Mask 15** to define **third-level metal** interconnects.  
   - Deposit another **Aluminum (Al)** layer for upper metal connections.
  ![image](https://github.com/user-attachments/assets/4ace4681-669c-479e-8515-abbd484b5619) 

7. **Final Protection Layer**  
   - Deposit a **Si₃N₄ (Silicon Nitride) passivation layer** to protect the chip.  
   - Use **Mask 16** for final connection openings.  
![image](https://github.com/user-attachments/assets/77551886-04fd-4e6d-8ecc-e1d348b308c5)

---

### SKY_L8 - Inverter Connections on Layout  

### Viewing Connections in **Magic Layout Editor**  

- To check the **connected layers and metals** in the layout:  
  - **Press `S` three times** while keeping the cursor on a port or layout.  
  - This will highlight the **entire connectivity** of the selected node.
  ![image](https://github.com/user-attachments/assets/7e1add8f-c533-4cce-a93f-1b585110e4f4)

  - If **`S` is pressed multiple times**, it will extend the selection further to **show all connected layers**.  
  -The layout differs from the actual layout we see in magic.
![Image](https://github.com/user-attachments/assets/a4da8402-7820-49e2-bee9-71b534bb9bbe) 

---

### SKY_L9 - Extracting SPICE Netlist from Layout  

3## Steps to Generate `.ext` and SPICE Netlist  

1. **Extract the layout** in **Magic**:  
   - Open the **Tkcon** window.  
   - Run the command:  
     ```tcl
     extract all
     ```
![image](https://github.com/user-attachments/assets/1d010925-8490-4ce7-82da-74344bedbf9e)

   - This generates the **extracted file** (`sky130_inv.ext`).  

1. **Convert `.ext` to SPICE netlist**:  
   - Run the following commands in the **Tkcon** window:  
     ```tcl
     ext2spice cthresh 0 rthresh 0
     ext2spice
     ```
   - This creates the **SPICE netlist file** (`sky130_inv.spice`).
   ![image](https://github.com/user-attachments/assets/32dbb9d3-b870-40ee-a806-c42138346fa8)

---

### SKY130_D3_SK3 - Sky130 Tech file Labs

### SKY_L1 - SPICE File Setup  

### 1. Opening and Editing the SPICE File  
- **Transistor terminal order**:  
  - **NMOS & PMOS format**: `Drain Source Substrate Gate`  
- **Steps**:  
  1. Open the **SPICE file** in a text editor.  
  2. Check the **dimensions** of the transistor boxes in the layout.  
  3. Update the **SPICE file** accordingly.  

### 2. Include NMOS & PMOS Model Files  
![image](https://github.com/user-attachments/assets/4ebe834d-115e-4caa-9de5-2698b22e6255)

Add the following `.include` statements to ensure correct device models are used:  
```spice
.include nmos_model.lib
.include pmos_model.lib
```
![image](https://github.com/user-attachments/assets/821190b4-fea2-4b73-8f8a-302a133f8ea7)


### 3. Before & After SPICE File (Refer to Images)  
- The **before** and **edited** SPICE files are attached in the repository.  
![image](https://github.com/user-attachments/assets/de46b4ab-e4ab-4975-a60a-f279dd5777be)
 
![image](https://github.com/user-attachments/assets/c4676d06-8ccd-4f92-b08b-02e3937cdbc5)

![image](https://github.com/user-attachments/assets/68bfdd48-9de1-46e3-a959-9be3598b3e6d)

---


### SKY_L2 - Characterizing an Inverter Using SKY130 Model Files  

### 1. Running SPICE Simulation  
- Open the **SPICE file** in NGSPICE using:  
  ```sh
  ngspice sky130_inv.spice
  ```
- If **spikes** appear in the output, modify the **capacitor load** in the SPICE file and rerun the simulation.
![image](https://github.com/user-attachments/assets/6a4af03e-3117-49e7-a594-c6deaced231a)

### 2. Plotting & Delay Calculation  
- Plot **V(out) vs. time** to observe the waveform.
![image](https://github.com/user-attachments/assets/1cead679-746a-47bc-8343-5c1a3edae575)

- **Rise transition calculation**:  
  - Check **voltage at 20%** (Vdd × 0.2).  
  - Check **voltage at 80%** (Vdd × 0.8).
  ![image](https://github.com/user-attachments/assets/f0624075-e0e4-44b4-8056-4aca1051b705)

  - Subtract the two time values to get **rise delay**.
  2.239−2.146=0.093ns
- **Cell rise delay**:  
  - Identify **50% voltage point (1.65V for 3.3V Vdd)** for both input and output.  
  - Measure delay at **room temperature**.
    2.20−2.14=0.06ns
![image](https://github.com/user-attachments/assets/94e7b48e-d413-4279-ae9b-fa6c84d6c674)

### 3. Magic Tool Commands  
- Use **`Shift + Z`** to zoom out in Magic.  

---

### SK3_D3 - Lab: Introduction to Magic Tool Options and DRC Rules  

### 1. Overview  
This lab focuses on using **Magic VLSI Layout Tool** to understand **Design Rule Checking (DRC)** and fixing errors based on **SkyWater 130nm PDK**.  

### 2. Topics Covered  
- **Magic DRC Commands**  
- **Google/SkyWater DRC Rules**  
- **Fixing a Sample DRC Error**  
- **Magic Technology File Definition**  

### 3. Useful Documentation  
- **Magic Tool Reference:**  
  [Magic VLSI Tool Documentation](http://opencircuitdesign.com/magic/)  
- **SkyWater 130nm DRC Rules:**  
  [SkyWater PDK DRC Rules](https://skywater-pdk--136.org.readthedocs.build/en/136/)  

### 4. Magic Commands for DRC  
- **Run DRC Check:**  
  ```sh
  drc check
  ```
- **Highlight DRC Errors:**  
  ```sh
  drc why
  ```
- **Fixing DRC Errors:**  
  - Identify the error location  
  - Modify the layout to meet spacing/size rules  
  - Rerun `drc check` to verify the fix  

---


### SKY_L4 - Lab: Introduction to Sky130 PDKs and Steps to Download Labs

### 1. Overview  
This lab covers the **SkyWater 130nm PDK (Process Design Kit)** and the necessary steps to **download and set up the DRC test labs**.

### 2. Lab Content URL  
The required lab files can be downloaded from:  
[DRC Test Labs](http://opencircuitdesign.com/open_pdks/archiev/drc_tests.tgz)  

### 3. Steps to Download and Extract Labs  
Use the following **commands** to download and extract the lab files:  

```sh
# Step 1: Download the DRC test labs
wget http://opencircuitdesign.com/open_pdks/archiev/drc_tests.tgz
# Step 2: Extract the downloaded file
tar xfz drc_tests.tgz
# Step 3: Navigate into the extracted directory
cd drc
cd drc_tests
# Step 4: List all files to verify extraction
ls -al
# Step 5: Print the current working directory
pwd
# Step 6: Open .magicrc file for configuration
vi .magicrc
```
![image](https://github.com/user-attachments/assets/8d258b44-9069-429c-a4bd-98b8d345603a)
```
# Step 7: Launch Magic in XR mode
magic -d XR
```
![image](https://github.com/user-attachments/assets/1464ed6b-f297-4796-aaa3-dcc6f066e698)

---

### SKY_L5 - Lab: Introduction to Magic & Steps to Load Sky130 Tech Rules

### 1. Overview  
This lab introduces the **Magic VLSI Tool** and covers the steps to **load Sky130 technology rules**, create metal contacts, and measure distances.

### 2. Steps to Load Sky130 Tech Rules & Work with Magic  

### 2.1 Open the `.mag` File  
Run the following command to open the `met3.mag` file in **Magic**:  
```sh
magic met3.mag
```
![image](https://github.com/user-attachments/assets/b0f4626a-e6f2-4a0a-8b59-3c5059e48846)

### 2.2 Create a Metal Contact and Add Contact Cuts  
Inside the Magic terminal, execute:  
```sh
%cif see VIA2  # View the VIA2 layer  
%what          # Display information about the selected object  
```
![image](https://github.com/user-attachments/assets/b2354b8b-2d01-42f6-ad49-65de70cdff87)

### 2.3 Measure Distance in Magic  
To measure distances using the mouse:  
1. Select the area using the **mouse pointer**.  
2. Use the command:  
   ```sh
   %box
   ```
   ![image](https://github.com/user-attachments/assets/4235607f-951d-4c5a-b048-5bf8e1609675)

3. Snap the box to the nearest grid intersection using:  
   ```sh
   snap int
   ```
4. Clear the box after measuring:  
   ```sh
   feed clear
   ```
![image](https://github.com/user-attachments/assets/f4c0e4ad-bfb7-4fe0-80c3-bfc8ed0d85e3)

---

### SKY_L6 - Lab: Fixing `poly.9` Error in Sky130 Tech-File  

### 1. Overview  
This lab guides you through **identifying and fixing a `poly.9` error** in the Sky130 technology file using **Magic VLSI**.

### 2. Steps to Fix `poly.9` Error  

### 2.1 Load the `poly.mag` File  
Open the file in **Magic** using:  
```sh
load poly
```
![image](https://github.com/user-attachments/assets/65c020f8-abeb-4632-b0e3-fd569286624a)

### 2.2 Identify the `poly.9` Error  
- Look for **design rule violation (DRC) errors** in `poly.9`.
  ![image](https://github.com/user-attachments/assets/41a3f684-b65b-4884-ab1d-e232ee012568)

- Run:  
  ```sh
  drc check
  drc why
  ```
  This will display the specific **design rule violation** and its **cause**.

### 2.3 Edit the Sky130 Tech File  
- Open the **Sky130 technology file** in a text editor (e.g., `vi`):  
  ```sh
  vi sky130.tech
  ```
  ![image](https://github.com/user-attachments/assets/d2d2fec1-76b9-4b55-90dd-ac00abaf4866)
  ![image](https://github.com/user-attachments/assets/473b4836-54e4-4bfa-9bad-5ad413194837)


- Locate the **poly.9** rule and modify it based on the correct design specifications (refer to images for the correct parameters).  
- Save the file and exit.

### 2.4 Reload the Sky130 Tech File in Magic  
After making changes, reload the tech file:  
```sh
tech load sky130A.tech
```
![image](https://github.com/user-attachments/assets/e92f22f1-2413-4e89-986c-8d223d6871e2)

### 2.5 Verify the Fix  
- Run `drc check` again in Magic.  
- If no errors appear, the issue is resolved.  
![image](https://github.com/user-attachments/assets/bf4f6be4-ef95-47d6-9aa9-5c75c9b5e45f)

---

### SKY_L7 - Lab: Implementing Poly Resistor Spacing to Diffusion and Tap  

### 1. Overview  
This lab focuses on **setting the correct spacing** between a **poly resistor** and **diffusion (n-type and p-type)** using **Magic VLSI** and Sky130 design rules.

### 2. Understanding Diffusion Types  
- **N-type diffusion** → **Green color** in Magic  
- **P-type diffusion** → **Tan color** in Magic

---

### SKY_L8 - Lab Challenge: Describing DRC Errors as Geometrical Constructs  

### 1. Overview  
This lab focuses on **understanding, analyzing, and fixing DRC errors** in Magic by modifying the **Sky130A.tech file** and verifying geometrical constraints.

### 2. Editing DNWELL Section in Sky130A.tech  

### 2.1 Open the Technology File  
```sh
vi sky130A.tech
```
![image](https://github.com/user-attachments/assets/e628bf5b-dc27-4362-89aa-69fad0680e5c)

### 2.2 Locate the DNWELL Section  
- Search for **DNWELL** in the **.tech file**.  
- Check for constraints such as **cifmaxwidth** and **geometrical rules**.
![image](https://github.com/user-attachments/assets/ba5f7c4a-9935-4ea4-8352-50f51c470299)

### 2.3 Modify DRC Constraints  
- Adjust the **cifmaxwidth** value as per the **image reference**.  
- Ensure it aligns with **Sky130 design rules**.

### 3. Finding and Analyzing DRC Styles  

### 3.1 Identifying the DRC Rule  
- Use the following command to check the **style**:
  ```sh
  grep "drc" sky130A.tech
  ```

### 3.2 Checking for Missing Layers  
- Locate **temporary layers** and verify **nwell_missing dnwell** rule:
  ```sh
  grep "templayer nwell_missing dnwell" sky130A.tech
  ```
![image](https://github.com/user-attachments/assets/8f85a9ad-fe9d-46b8-8180-d8674caeda88)
![image](https://github.com/user-attachments/assets/d221a08d-c593-4b72-8bcc-b4989848da03)

![image](https://github.com/user-attachments/assets/1e73d0f4-7a40-4b0a-b65b-c9cbe9832a9d)
![image](https://github.com/user-attachments/assets/ee8760ef-45e0-4f16-94a7-877b7cf7a836)

### 3.3 Running DRC in Magic  
- Load the layout and run:
  ```sh
  drc check
  drc why
  ```
  ![image](https://github.com/user-attachments/assets/191163f1-2de4-4a80-b45b-7d8be2585faf)

- Identify the **geometrical issue** causing the DRC violation.


---
## SKY130 Day 4 - Pre-Layout Timing Analysis & Clock Tree Importance  

### SKY_L1 - Lab Steps to Convert Grid Info to Track Info  

### 1. Navigating to the Required Directory  
```sh
cd vsdstdcelldesign
```
- This directory contains the **standard cell design files**.

### 2. Opening the Layout in Magic  
```sh
magic -T sky130A.tech sky130_inv.mag
```
- Loads the **inverter layout** in Magic using **Sky130A.tech**.

### 3. Viewing Track Information  
Navigate to the **Sky130 PDK directory** where track definitions exist:  
```sh
cd pdks/sky130/libs.tech/openlane/sky130_fd_sc_hd/
less tracks.info
```
![image](https://github.com/user-attachments/assets/9a818042-5944-4c50-bf5e-0a24e0f8b525)

- **Tracks.info** defines **metal layers, spacing, and pitch**.  
- Example from `tracks.info`:
  ```
  li1 x 0.23 0.46
  ```
  - **0.23um spacing**
  - **0.46um pitch**

### 4. Activating Grid in Magic  
- Press **'g'** in Magic to **activate grid view**.  

### 5. Converting Grid to Track Information  
Use the following **grid command** in Magic to match the track definition:  
```sh
grid 0.46um 0.34um 0.23um 0.17um
```
![image](https://github.com/user-attachments/assets/b051eb89-7fec-4b0d-b150-9e68a60da3c1)
before the cmd 
![image](https://github.com/user-attachments/assets/b326ccd3-61c9-4fbc-81cd-cc16cfbff4fa)

after the cmd 
![image](https://github.com/user-attachments/assets/d167ff67-718d-4df2-af90-6f88a76298b2)

  - **Aligns ports to track intersections**.
  - Ensures **routing follows defined tracks**.
  ![image](https://github.com/user-attachments/assets/46eca2d2-e359-4b59-bdd3-4c9ef5ee0bbf)

  - Helps in **timing closure & better layout optimization**.

---

### SKY_L2 - Lab Steps to Convert Magic Layout to Standard Cell LEF  

### 1. Standard Cell Dimension Requirements  
- **Width** should be in **odd multiples of the metal pitch (zx pitch)**.  
- **Height** should also follow the same rule.

### 2. Navigating to the Standard Cell Design Folder  
```sh
cd vsdstdcelldesign
```
- This folder contains the **custom standard cell layouts**.

### 3. Opening and Saving Layout in Magic  
Launch Magic and open the **inverter layout**:  
```sh
magic -T sky130A.tech sky130_vsdinv.mag
```
Save the updated `.mag` file:  
```sh
save sky130_vsdinv.mag
```
- **Ensures the latest changes are stored**.

### 4. Writing the LEF File  
Run the following command in Magic to generate the **LEF (Library Exchange Format) file**:  
```sh
lef write
```
![image](https://github.com/user-attachments/assets/2eb93679-3f14-4de8-8970-85aae17c337b)

- This command **extracts** the standard cell information needed for PnR tools.

### 5. Verifying the LEF File  
Check the generated **LEF file**:  
```sh
less sky130_vsdinv.lef
```
- **Ensures the file contains correct standard cell dimensions and pin placements**.

### 6. Integrating LEF into PicoRV32a  
- Before using the **LEF file** in **PicoRV32a**, move the **design files** into the `src` folder:  
```sh
mv sky130_vsdinv.lef /path/to/picorv32a/src/
```
- The **LEF file** is now ready for integration into the **PicoRV32a RISC-V core**.

---

### SKY_L3 - Introduction to Timing Libraries & Steps to Include a New Cell in Synthesis  

### 1. Timing Libraries Overview  
For **PVT (Process-Voltage-Temperature) variation**, we need three **timing libraries**:
- **Typical Corner:** `sky130_fd_sc_hd__typical.lib`
- **Fast Corner:** `sky130_fd_sc_hd__fast.lib`
- **Slow Corner:** `sky130_fd_sc_hd__slow.lib`
These vary with slew and temperature parameters

### 2. Copy Libraries into PicoRV32a  
Move the **timing libraries** into the **src folder** of `picorv32a`:  
```sh
cp sky130_fd_sc_hd__typical.lib sky130_fd_sc_hd__fast.lib sky130_fd_sc_hd__slow.lib /path/to/picorv32a/src/
```
This ensures OpenLane can access the required **liberty (.lib) files** during synthesis.

### 3. Modify the Configuration File  
Update the **config.tcl** in `picorv32a`:
```tcl
set ::env(LIB_SYNTH) "sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "sky130_fd_sc_hd__slow.lib"
```
![image](https://github.com/user-attachments/assets/2e8d78b7-2164-4bff-bfc1-b69edbe3b085)

- This **includes** the custom standard cell in synthesis.

### 4. Running OpenLane for Synthesis  
### **Start OpenLane Docker**  
```sh
./flow.tcl -interactive
```
### **Load OpenLane Package**  
```tcl
package require openlane 0.9
```
### **Prepare the Design for Synthesis**  
```tcl
prep -design picorv32a -tag 12-02_06-52 -overwrite
```
![image](https://github.com/user-attachments/assets/64931c99-6e70-4fef-a4e5-f8093296dbbf)

- `-tag 12`: Identifies the run instance.  
- `-overwrite`: **Erases previous runs** to start fresh.

### **Run Synthesis**  
```tcl
run_synthesis
```
![image](https://github.com/user-attachments/assets/01b2dfd0-fbe5-4a05-b68d-99c92e2234e1)

---

### SKY_L4 - Introduction to Delay Tables & Power-Aware CTS  

### *1. Basics of Delay Tables*
Delay tables help model the delay of a gate based on:  
- **Input transition time**  
- **Output load capacitance**  

### **Example - Clock Gating in AND/OR Gates**
- **AND Gate:** If **enable = 1**, output follows input.  
- **OR Gate:** If **enable = 0**, output follows input.  
![image](https://github.com/user-attachments/assets/a5d5d11f-1a29-4430-bcd2-96cf3612ae4b)

### *2. Clock Tree & Buffering Observations*
Consider a **Clock Tree** with **buffered stages**:  
| Buffer | Node | Capacitance (fF) |
|--------|------|------------------|
| Buffer 1 | A | 60 fF |
| Buffer 2 | B | 50 fF |
| Buffer 3 | C | 50 fF |
![image](https://github.com/user-attachments/assets/f98ddd28-d114-40f4-882b-ed3a38388e31)

### **Key Observations:**
- Each node drives the **same load**.  
- Identical buffers exist at the **same level**.  
- **Load variation affects input transition**, impacting delay.  

### *3. Capturing Delay Tables*
- **Vary Input Transition Time**  
- **Vary Output Load Capacitance**  
- Measure **Delay for each condition**  
- Generate **lookup delay tables**    

---

### SKY_L5 - Delay Table Using Part 1  

### *1. Understanding Delay Tables*
Delay tables help in estimating gate delays based on:  
- **Input transition time (ps)**  
- **Output load capacitance (fF)**  

### *2. Example: Delay Calculation for Buffers*
We analyze two buffers **CBUF1** and **CBUF2**.  
![image](https://github.com/user-attachments/assets/1b15c987-a226-4c7f-b694-bfed21296f79)

### Given Conditions:  
- **Input Transition Time** = 40 ps  
- **Output Load Capacitance** = 50 fF to 70 fF  
![image](https://github.com/user-attachments/assets/ddeee369-77dd-4b49-8be8-4d14980f73ef)

- The delay value falls **between the interpolated values** in the provided figure.  
- This helps determine the actual delay during STA (Static Timing Analysis).  
- Provides accurate **timing estimates** before physical implementation.  

---
### SKY_L6 - Delay Table Using Part 2  

### 1. Understanding Buffer Delays  
We analyze the delay propagation between buffers **BUF1** and **BUF2** using delay tables.  

### 2. Given Conditions for BUF2:  
- **Transition Time** = 60 ps  
- **Output Load Capacitance** = 50 fF  
![image](https://github.com/user-attachments/assets/926a17b6-b62e-4e7e-ae36-492dcf512fed)
 
- Let **x9** be the delay for buf 1.
- **y15** be the delay for buf 2.  
- Using delay tables, we extract the delay value corresponding to the given input transition and output load.  
- Next, we compute **delay from BUF1 to BUF2** based on these values.  

### 3. Key Observations  
- Delay depends on **input transition and load capacitance**.  
- Accurate delay calculation helps in **timing closure and clock tree optimization**.  
- This step ensures correct **buffer insertion and CTS refinement** for low-skew clock distribution.  

---

### **SKY_L7-Lab Steps to Configure Synthesis Settings and Reduce Delay**
1. **Modify Synthesis Strategy**
   - Set the synthesis strategy to **1**:
     ```
     set ::env(SYNTH_STRATEGY) 1
     ```
   - Verify if synthesis buffering is enabled:
     ```
     echo $::env(SYNTH_BUFFERING)
     ```
   - Enable synthesis sizing:
     ```
     set ::env(SYNTH_SIZING) 1
     ```
   - Check the default **synth_driving_cell**:
     ```
     echo $::env(SYNTH_DRIVING_CELL)
     ```

2. **Run Synthesis**
   ```
   run_synthesis
   ```

3. **Run Floorplan**
   ```
   run_floorplan
   ```
![image](https://github.com/user-attachments/assets/3f9cec47-3984-44bd-827b-9af8ff7addba)

4. **Handling Errors During Floorplan**
   If you encounter errors, try running the following commands step by step:
   ```
   init_floorplan
   place_io
   tap_decap_or
   ```
   ![image](https://github.com/user-attachments/assets/c616eaff-fa62-4cf1-ae8e-27ac09c7e218)
   ![image](https://github.com/user-attachments/assets/ed7393e1-d0b8-45a3-8cc2-b710867b7c7a)
   ![image](https://github.com/user-attachments/assets/d6e07600-2e6c-4f63-ac12-83586a9e4127)
   

6. **Verify Merged LEF File**
   - Navigate to the `runs/current/` directory:
     ```
     cd runs/12-02_06-52/merged.lef
     ```
   - Open `merged.lef` to check if the custom design (including `vsd_inv`) is included.
     ```
     run_placement
     ```
    ![image](https://github.com/user-attachments/assets/f0c2dacb-e4e4-491a-aeed-2ff41c81bb7a)

7. **Legality Check & Verification**
   ![image](https://github.com/user-attachments/assets/3bfdd52c-5e9b-4a02-9775-86e629c563a2)

   - Open the **LEF** and **DEF** files in **Magic** (after placement):
     ```
     magic -T sky130A.tech lef read merged.lef def read picorv32a.placement.def
     ```
   - Check if `sky130vsd_inv` is present and verify placement.

---

### **SKY130_D4_SK2-Timing Analysis with Ideal Clocks using OpenSTA**  

### **SKY_L1-Setup Timing Analysis & Flip-Flop Setup Time**  
- In **Static Timing Analysis (STA)**, the setup time is the minimum time before the clock edge that data must be stable at the input of a **D Flip-Flop (DFF)**.
  ![image](https://github.com/user-attachments/assets/bce28873-04f1-4079-88a1-ba436d63e510)

- If the clock period is **T**, the **combinational delay** must satisfy:
  Combinational delay < Time period(T)
  As the capture flop needs some time to capture the input from the launch flop that is the setup time of the capture flop that instance
  \[
  \text{Combinational Delay} < T - \text{Setup Time of Capture Flop}
  \]
  ![image](https://github.com/user-attachments/assets/692d732b-11d3-4394-8a66-83cf0fe6cfde)

- The **internal delay of MUX1** is equivalent to the **setup time of the capture flip-flop**.  
---

### SKY_L2 - Introduction to Clock Jitter and Uncertainty  

### Clock Jitter  
- The clock is expected to transition at fixed intervals, starting from time **t = 0**.  
- However, due to connections with other source clocks and wires, the actual clock signal **does not always arrive exactly at the expected edge**.  
- The next clock edge also experiences similar variations.  
- These **temporary variations in the clock period** are called **jitter**.  

### Clock Uncertainty  
- **Clock uncertainty** refers to the difference between the **expected clock arrival time** and the **actual arrival time**.  
- It is influenced by jitter, clock skew, and variations in routing delays.  
- A more stable clock has **lower uncertainty**.  

### Impact on Timing  
- Previously, the condition for setup timing was:  
  ```
  Combinational Delay < Clock Period - Setup Time
  ```
- Now, considering **clock uncertainty due to jitter**:  
  ```
  Combinational Delay < Clock Period - Setup Time - Clock Uncertainty
  ```
  ![image](https://github.com/user-attachments/assets/f3abce8d-d4eb-41db-8903-d7374416b663)

- This means **less available time for data propagation**, making timing closure more challenging.  

Let's check our **core design** for timing violations due to jitter and uncertainty.  
![image](https://github.com/user-attachments/assets/6b25e888-f054-4be3-b699-64d106baffed)
![image](https://github.com/user-attachments/assets/f04f6ada-ddfe-457f-89e0-618ef263c7c3)

---

### SKY_L3-lab steps to configure OpenSTA for post-synth timing analysis

We have to do timing analysis in OpenSTA.

### Steps:

1. **Navigate to the OpenLane folder:**
   ```sh
   cd /path/to/openlane
   ```

2. **Create a file named `pre_sta.conf`:**
   ```sh
   touch pre_sta.conf
   ```

3. **Open the file in a text editor (e.g., `vi`):**
   ```sh
   vi pre_sta.conf
   ```

4. **Before this, create `my_base.sdc` in**  
   `openlane/designs/picorv32a/src/`  
   - Take reference from `openlane/scripts/base.sdc`.  
   - For `cap_load`, check in the `libs` directory.  

5. **Content of `my_base.sdc`** (Refer to the given image for exact details).  
![image](https://github.com/user-attachments/assets/5cd1c8d2-a3df-4ffc-9459-84383a26a089)

6. **Write the `pre_sta.conf` file** (Refer to the given figure for content).  
![image](https://github.com/user-attachments/assets/0a0fd878-5d08-41bb-9cb5-9ce03b2ac09f)

7. **Run OpenSTA with the configuration file:**
   ```sh
   sta pre_sta.conf
   ```
![image](https://github.com/user-attachments/assets/cc47be3d-dff8-4676-a9d0-8f25f4dedbd4)

![image](https://github.com/user-attachments/assets/b1e77fe1-0fbf-48cc-b70c-a58c11444e59)

slack is violated so we need to make changes to make slack met.

---

### SKY_L4-lab steps to optimize synthesis to reduce setup violation

### Steps:

1. **Navigate to the OpenLane :**

2. **Set the maximum fanout value:**
   ```sh
   set ::env(SYNTH_MAX_FANOUT) 4
   ```
   ![image](https://github.com/user-attachments/assets/619b635b-7b82-4c94-8527-96af449a6ef4)

   - Higher fanout increases slew due to circuit connections.
   - If buffers are placed side by side, slew propagation worsens.
![image](https://github.com/user-attachments/assets/a8f776f3-bb9e-4bdf-a479-1793017042a6)

3. **Check net connections (example for `_7899_`):**
   ```sh
   report_net connections _7899_
   ```

4. **Replace a cell with a different size to optimize timing:**
   ```sh
   replace_cell _14365_ sky130_fd_sc_hd__buf_1
   ```

5. **Run timing analysis and check setup violations:**
   ```sh
   report_checks -format -digits 4
   ```

   ![image](https://github.com/user-attachments/assets/414b9c41-4b72-4417-ae69-1d3a649fc2d2)
   ![image](https://github.com/user-attachments/assets/5945d3ea-fcd8-4858-8488-9c18d38b6ec4)

   ![image](https://github.com/user-attachments/assets/51ce58a1-c228-4590-8a2c-7a67ad68e30f)

   decreased slack but much less
   so do replace the cells again for other delays

   ![image](https://github.com/user-attachments/assets/3670e7a6-0f46-4fcd-966e-f025e15d4644)

   ![image](https://github.com/user-attachments/assets/cedb1480-1c65-4a0a-9caf-ea7c1178c9f3)

   ![image](https://github.com/user-attachments/assets/3b81bdfe-dbed-4ec8-843f-c49aa25a9a4c)

   ![image](https://github.com/user-attachments/assets/f89c6e94-36f5-43a3-9de6-1385914ab1f3)


  ![image](https://github.com/user-attachments/assets/b7409732-ac10-476d-bf65-0290efe282ed)

   ![image](https://github.com/user-attachments/assets/eca07193-c9a0-4b76-91bc-85b6ce557613)
---
### SKY_L5-Lab steps to do basic timing ECO

  now after making slack a bit less 
  ```
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-02_06-52/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls

# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-02_06-52/results/synthesis/picorv32a.synthesis.v
```

---

### SKY130_D4_SK3 - Clock Tree Synthesis TitronCTS and Signal Integrity

### SKY_L1 - Setup timing analysis using real clocks

### Steps:

1. **Connect `clk1` to flip-flops (FFs).**  
   The time required to reach `FF1` and `FF2` is `t1` and `t2`, respectively (as shown in the image).
![image](https://github.com/user-attachments/assets/3ab93a01-e2fe-4031-a226-32a8efb1b3f8)
![image](https://github.com/user-attachments/assets/ae5963a5-c88d-4288-9d3f-9962fe45ad60)

2. **Use an H-tree for clock distribution.**  
   - Take midpoints of flip-flops so that the clock reaches every FF at the same time.
![image](https://github.com/user-attachments/assets/829d8b62-ce5c-47d6-8e04-f0ef37a20976)

3. **Clock tree buffering:**  
   - To maintain signal integrity, add repeaters (buffers).
   - Without buffers, the clock signal may degrade due to high delay.
   ![image](https://github.com/user-attachments/assets/8d5fbf98-8c7d-44ef-adac-4aff9fc50e60)


4. **Adding repeaters (red buffers):**  
   - This ensures that the clock signal at the output is relatively the same as the input, maintaining signal quality.
![image](https://github.com/user-attachments/assets/24739bef-f437-46da-a1d0-1674a43331a1)

---

### SKY_L2 - Crosstalk and Clock Net Shielding

### Clock Net Shielding

- **Clock tree aims for 0 skew.**
- **Latency**: Time required for the clock signal to reach a flip-flop.
- **Skew**: Difference in latency between different flip-flops.

### Why Shield Clock Nets?

- **Crosstalk can collapse the entire clock design.**
- To prevent this, we shield clock nets/wires.

### Two Problems Caused by Crosstalk:

1. **Glitch:**  
   - Unintended switching due to noise from adjacent signals (refer to the image).  
   - Solution: Add shielding by connecting one shield to `VDD` and another to `GND`, ensuring they do not switch.
![image](https://github.com/user-attachments/assets/f0f702ce-383a-45b1-801e-4096faf7eef4)

![image](https://github.com/user-attachments/assets/e342a033-f2de-49d7-b819-66f9831a7297)


2. **Delta Delay:**  
   - Crosstalk introduces **delta delay**, causing unintended timing shifts.  
   - This can affect logic transitions (e.g., `1 → 0`) due to delay accumulation.  
   - As a result, clock skew may not remain zero and could be affected by delta delay (refer to the figure).
![image](https://github.com/user-attachments/assets/409e5f0d-8e7d-40c2-b67e-fc4476f34c2f)

### Practical Considerations:

- Ideally, only **critical nets** are shielded.
- Shielding all clock nets is **not feasible** as it would cause congestion in routing the design.
![image](https://github.com/user-attachments/assets/d1d347cc-3776-4adf-b48c-f824bb62c80d)

---

### SKY_L3 - Lab Steps to Run CTS Using TritonCTS

### Steps:

1. **Modify the slack value as needed.**  
2. **Re-run synthesis:**
   ```sh
   run_synthesis
   ```
   ![image](https://github.com/user-attachments/assets/cded471d-6a57-4d74-bccb-2320697758d4)

3. **Run floorplanning:**
   ```sh
   run_floorplan
   ```
   ![image](https://github.com/user-attachments/assets/f8c96ac2-6a61-4973-934c-b6ba54cf0835)

4. **Run Clock Tree Synthesis (CTS):**
   ```sh
   run_cts
   ```

### Output:

- This process generates **`picorv32a.synthesis_cts.v`**,  
  - This file contains clock buffers added during CTS.
  ---
  
### SKY_L4 - Lab Steps to Verify CTS Runs

### Steps:

1. **Navigate to OpenROAD in OpenLane:**  
   ```sh
   cd openlane/scripts/openroad
   ```
   - OpenROAD tool is available here.

2. **Verify the following design stages in OpenROAD:**
   - **Floorplan**
   - **Placement**
   - **Clock Tree Synthesis (CTS)**
   - **Optimization**
   - **Global Routing**
![image](https://github.com/user-attachments/assets/140424c5-58ac-4460-9589-85b57b990522)

---

### SKY130_D4_SK4- Timing analysis with real clocks using openSTA
### SKY_L1 - Timing Analysis with Real Clock

### Setup Timing Analysis:

- In a real clock, **buffers are added** to maintain signal integrity.
- The **combinational delay** must be **less than** (time period + buffer delay).
![image](https://github.com/user-attachments/assets/7ab88a2f-4312-41e2-97a7-81a33323ee8b)

### Key Parameters:
- **Δ1**: Time required for the clock to reach the **launch flip-flop**.
- **Δ2**: Time required for the clock to reach the **capture flip-flop**.
![image](https://github.com/user-attachments/assets/0fe956ae-d64f-4ba9-84f5-a00338dbfe90)

### Setup Timing Equation:
\[
|Δ1 - Δ2| = \text{Skew}
\]
- **Jitter** is also considered.
- **Slack** is calculated as:
  \[
  \text{Slack} = \text{Data Arrival Time} - \text{Data Required Time}
  \]
- **Slack should be 0 or positive** for a valid design.
![image](https://github.com/user-attachments/assets/b249d606-abd5-40ff-8fc2-8cbe85bc2bb0)
![image](https://github.com/user-attachments/assets/e6124c1e-f0ab-4e81-8fe4-d76239188e96)

---

## Hold Timing Analysis:

- The **combinational delay** must be **greater than** the hold time of the capture flip-flop.

### Hold Timing Considerations:
- The capture flop sends data out with **MUX2 delay**, which equals the hold time of the flop.
- It will not receive new data during the **hold time**.
- Therefore, the data must **arrive after** the hold time.
![image](https://github.com/user-attachments/assets/f7105aa2-baeb-4988-995e-60d760828c6e)

### Hold Timing Equation:
\[
\text{Combinational Delay} + Δ1 > \text{Hold Time} + Δ2
\]

---

### SKY_L2 - Timing Analysis with Real Clock and Single Clock

### Considerations:

- **Uncertainty** is added to the **data required time** for more accurate analysis.
- With a **single clock**, we must consider:
  - **Real wire RC delay**
  - **Buffer delays**
![image](https://github.com/user-attachments/assets/f9c7a690-79f5-493b-a182-59a28bb9a58e)

### Key Parameters:
- **Δ1**: Time required for the clock to reach the **launch flip-flop** (includes RC + buffer delays).
- **Δ2**: Time required for the clock to reach the **capture flip-flop** (same RC delay applies).
![image](https://github.com/user-attachments/assets/16e8d5f6-2f48-4b7c-bfe4-c81e4447dfa0)
![image](https://github.com/user-attachments/assets/39de8842-2c19-445b-95e0-25386250a65c)

### Skew Calculation:

![image](https://github.com/user-attachments/assets/46fd8d15-1931-4a20-8844-76d7733f71cc)


### Setup Timing Equation:

![image](https://github.com/user-attachments/assets/bf13d3f8-7c97-4310-b2a0-1cfed8e164ba)


### Hold Timing Equation:

![image](https://github.com/user-attachments/assets/dd678f0b-726d-4102-9aa2-49c66e5c3a2f)

---

### SKY_L3 - Lab Steps to Analyze Timing with Real Clocks Using OpenSTA

### Steps:

1. **Open OpenROAD:**
   ```sh
   openroad
   ```

2. **Read the LEF file:**
   ```sh
   read_lef /openLANE_flow/designs/picorv32a/runs/12-02_06-52/tmp/merged.lef
   ```

3. **Read the DEF file (post-CTS):**
   ```sh
   read_def /openLANE_flow/designs/picorv32a/runs/12-02_06-52/results/cts/picorv32a.cts.def
   ```

4. **Create and load an OpenROAD database:**
   ```sh
   write_db pico_cts.db
   read_db pico_cts.db
   ```

5. **Read the post-CTS netlist:**
   ```sh
   read_verilog /openLANE_flow/designs/picorv32a/runs/12-02_06-52/results/synthesis/picorv32a.synthesis_cts.v
   ```

6. **Read the design library:**
   ```sh
   read_liberty $::env(LIB_SYNTH_COMPLETE)
   ```
![image](https://github.com/user-attachments/assets/9ba4e094-2bed-4fc3-8ae9-db49e9146f12)

7. **Link the design and library:**
   ```sh
   link_design picorv32a
   ```

8. **Read the custom SDC file:**
   ```sh
   read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
   ```

9. **Set propagated clocks:**
   ```sh
   set_propagated_clock [all_clocks]
   ```

10. **Generate a custom timing report:**
    ```sh
    report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
    ```
![image](https://github.com/user-attachments/assets/6e542555-7d73-47a0-be5f-84b2c467dc13)

11. **Report hold skew:**
    ```sh
    report_clock_skew -hold
    ```

12. **Report setup skew:**
    ```sh
    report_clock_skew -setup
    ```
![image](https://github.com/user-attachments/assets/1b73f9f4-72e8-4808-a45e-aa35e2103458)

13. **Exit OpenROAD:**
    ```sh
    exit
    ```
---
### SKY_L4 - Lab Steps to Execute OpenSTA with Right Timing Libraries and CTS Assignment

### Steps:

1. **Check the current value of `CTS_CLK_BUFFER_LIST`:**
   ```sh
   echo $::env(CTS_CLK_BUFFER_LIST)
   ```

2. **Set and replace CTS clock buffer list:**
   ```sh
   set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]
   ```

3. **Verify the updated `CTS_CLK_BUFFER_LIST`:**
   ```sh
   echo $::env(CTS_CLK_BUFFER_LIST)
   ```

4. **Navigate to the directory containing the generated PDN DEF file:**
   ```sh
   cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-02_06-52/tmp/floorplan/
   ```
   ![image](https://github.com/user-attachments/assets/c49a806e-e906-41f9-9f26-ca8c7fc43525)

---
### SKY_L5 - Lab Steps to Observe Impact of Bigger CTS Buffers on Setup and Hold

### Steps:

1. **Check the current value of `CURRENT_DEF`:**
   ```sh
   echo $::env(CURRENT_DEF)
   ```
   ![image](https://github.com/user-attachments/assets/02785758-05aa-4fef-bdbd-4f6240b417c6)


2. **Set the DEF file to placement DEF:**
   ```sh
   set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/12-02_06-52/results/placement/picorv32a.placement.def
   ```

3. **Run CTS again:**
   ```sh
   run_cts
   ```

4. **Check and verify `CTS_CLK_BUFFER_LIST`:**
   ```sh
   echo $::env(CTS_CLK_BUFFER_LIST)
   ```

5. **Run CTS again to observe the impact:**
   ```sh
   run_cts
   ```

6. **Launch OpenROAD:**
   ```sh
   openroad
   ```

7. **Read required files into OpenROAD:**
   ```sh
   # Read LEF file
   read_lef /openLANE_flow/designs/picorv32a/runs/12-02_06-52/tmp/merged.lef

   # Read DEF file post CTS
   read_def /openLANE_flow/designs/picorv32a/runs/12-02_06-52/results/cts/picorv32a.cts.def

   # Create and load OpenROAD database
   write_db pico_cts1.db
   read_db pico_cts1.db

   # Read netlist post CTS
   read_verilog /openLANE_flow/designs/picorv32a/runs/12-02_06-52/results/synthesis/picorv32a.synthesis_cts.v

   # Read library for design
   read_liberty $::env(LIB_SYNTH_COMPLETE)

   # Link design and library
   link_design picorv32a

   # Read custom SDC file
   read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

   # Set propagated clocks
   set_propagated_clock [all_clocks]
   ```

8. **Generate timing reports:**
   ```sh
   # Report timing with detailed fields
   report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

   # Report hold skew
   report_clock_skew -hold

   # Report setup skew
   report_clock_skew -setup
   ```

9. **Exit OpenROAD:**
   ```sh
   exit
   ```

- After changing `clk_buf1` to `clk_buf2`, the slack improved, but area consumption increased.
- To balance performance and area, reinsert `clk_buf1`.
---

## D5 - Routing

### SKY130_D5_SK1 - Routing Algorithms

### SK1_L1 - Routing and DRC Stage

We need to connect the wires `din1` and `ff1`.

### 1. Maze Routing - Lee's Algorithm [Lee 1961]

- Uses minimal zig-zag, L-shape, or similar path patterns.
- The algorithm first creates a **grid-based representation** of the routing area.
- Defines **source** and **target** points on the grid.
- Each grid cell has **four adjacent neighbors** (left, right, top, bottom).
- The process follows these steps:
![image](https://github.com/user-attachments/assets/97191966-68bf-469c-ba3a-9ea0575ac96f)

  1. Mark the **source** grid as `1`.
  2. Expand outward to **adjacent grids**, labeling them incrementally (`2`, `3`, `4`…).
  ![image](https://github.com/user-attachments/assets/5f9d1d96-2293-4275-bfd9-3e4023580ce6)

  4. Continue labeling until the **target** grid is reached.
  5. Once the target is found, **backtrack** along the smallest numbered path to create an **optimal connection**.

- This method ensures:
  - **Guaranteed routing completion** (if a path exists).
  - **Shortest path in terms of grid steps**.
  - **No overlaps or violations** in a simple routing scenario.

---

### SKY5_L2 - Maze Algorithm

- We **cannot** use pre-placed cells for routing.
  ![image](https://github.com/user-attachments/assets/12af6b93-5b2e-4537-8c05-9f03cd0354e9)
  ![image](https://github.com/user-attachments/assets/60ffeff0-4813-4476-a544-58e60ec0823b)


- After reaching a certain point in the grid, there are **multiple possible paths** to the target.

### Optimizing the Route
- Instead of blindly choosing a path, we **evaluate different routing options**.
- **Bend Minimization**:  
  - A **single-bend route** is generally preferred as it reduces signal integrity issues.
  - **Less bending → Less delay & better manufacturability**.
![image](https://github.com/user-attachments/assets/10eb2b74-b6b5-4793-894e-bf190e601287)
![image](https://github.com/user-attachments/assets/11bc4928-8017-47c1-bcd9-7be2802cd19a)

  - Routed paths are **highlighted in green**.
    ![image](https://github.com/user-attachments/assets/59d2e39e-2ae4-4695-aba7-79f5b89ccbf9)

  - Ensures proper connectivity without **violating design rules**.
---

### SKY_L3 - DRC Check

### Design Rule Checks (DRC)
When routing two wires, **minimum spacing and width constraints** must be followed to avoid **DRC violations**.

### Key Parameters:
1. **Wire Width**  
   - The wire width should meet the minimum **manufacturing constraints**.
   - Built using **optical lithography**, which is dependent on **wavelength limitations**.
   - After lithography, the width can be **larger**, but **never smaller** than the defined limit.
![image](https://github.com/user-attachments/assets/c4b1c10a-942c-4f71-b144-7e12f6f76a92)

2. **Wire Pitch**  
   - The **center-to-center distance** between two adjacent wires.
![image](https://github.com/user-attachments/assets/7f97ff33-a58b-4862-b14d-4ada93445305)

3. **Wire Spacing**  
   - The **minimum allowable distance** between two wires to avoid short circuits.
![image](https://github.com/user-attachments/assets/998f0924-f594-452f-86bd-854067b57bf6)

### DRC Violation Type: **Signal Short**
- Can cause **functionality failures**.
  ![image](https://github.com/user-attachments/assets/fe1e6927-7006-404e-aa1d-ec24630ae08c)

- **Solution:**  
  - **Route signals on different metal layers** to reduce congestion.
  - **Higher metal layers** are generally **wider** than lower ones.
![image](https://github.com/user-attachments/assets/ce42cdf1-210f-4bfc-8921-b0cb2c22dbec)

### Via Constraints:
1. **Via Width**  
   - When switching between layers, via dimensions must comply with DRC rules.
   ![image](https://github.com/user-attachments/assets/754e18be-fcf3-4225-aa19-f7420f6ca871)

2. **Via Spacing**  
   - Minimum distance between adjacent vias to prevent **electrical and reliability issues**.
![image](https://github.com/user-attachments/assets/4bf20e17-3902-44be-9f9b-f213ff0337a7)

### Next Step: **Parasitic Extraction**
- After resolving DRC violations, parasitic elements (capacitance, resistance) are extracted for **timing and signal integrity analysis**.
  ![image](https://github.com/user-attachments/assets/f6d36d07-178f-4647-ac52-dbf2a8b26cd5)

---

### SKY_L1 - Design Preparation and Updates

### Step 1: Preparing the Design
To update variables and ensure the design reflects the latest changes, run:
```tcl
prep -design picorv32a -tag 12-02_06-52 -overwrite
```

### Step 2: Updating LEF Files in OpenLane
If new LEF files were added, include them in the OpenLane flow:
```tcl
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```

### Step 3: Setting Synthesis Parameters
Modify synthesis strategy and sizing:
```tcl
set ::env(SYNTH_STRATEGY) "DELAY 3"
set ::env(SYNTH_SIZING) 1
```
I have set these in config.tcl , for not repeating every time I don't need to set.
### Step 4: Running Synthesis
Once the design is prepped, execute synthesis:
```tcl
run_synthesis
```

### Step 5: Floorplanning Steps
The following commands are included in `run_floorplan`:
```tcl
init_floorplan
place_io
tap_decap_or
```

### Step 6: Placement
To perform placement, use either:
```tcl
run_placement
```

or execute individual placement steps:
```tcl
global_placement_or
detailed_placement
```
![image](https://github.com/user-attachments/assets/1f47ddd5-8da8-48ae-95ce-dfdec8f535b6)
![image](https://github.com/user-attachments/assets/6eacdba6-927e-4579-b14b-cce9ea5916ac)

```
run_pdn
```
After running **Power Distribution Network (PDN)**, we obtain **standard power rails**.
![image](https://github.com/user-attachments/assets/f59c5554-5ae8-40bd-bb45-842024991936)

![image](https://github.com/user-attachments/assets/9fc39c44-2963-440f-b2b4-296038c0a4e8)
we can see the width, and pitch here of metal layers

---

### SKY_L2 - Routing Explanation
![image](https://github.com/user-attachments/assets/5e179b9c-3cb7-49ab-a2bf-3806cd26a098)

### Power and Ground Pads
- **Red pad** → Represents the **Power pad**.
- **Blue pad** → Represents the **Ground pad**.

### Power Distribution Network (PDN)
- **Red and blue lines** → Represent **power and ground straps**.
- **Power flow**:
  1. Power is delivered to the **power ring**.
  2. The power ring distributes it to **straps**.
  3. Straps then transfer power to **rails**.
  4. Finally, power reaches individual **cells**.

### Checking Current DEF Before Routing
Before running routing, verify the current DEF file:
```tcl
echo $::env(CURRENT_DEF)
```
This ensures the correct placement data is used before proceeding with routing.
![image](https://github.com/user-attachments/assets/731ad56b-d245-40f7-b455-5b138548fb3e)
after pdn the def files created

---

### SKY2_L3 - Routing in Magic and TritonRoute

### Loading PDN DEF in Magic Tool
To visualize and verify the Power Distribution Network (PDN) in Magic:
```tcl
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech \
      lef read ../../tmp/merged.lef \
      def read 14-pdn.def &
```
![image](https://github.com/user-attachments/assets/a34ca4d8-9f46-497e-abe5-a195b05ba30d)
![image](https://github.com/user-attachments/assets/8da58b5b-901e-46db-a74e-7830ab9b842f)



### Running Routing
```tcl
run_routing
```
Routing is performed using **TritonRoute**, which consists of two phases:
![image](https://github.com/user-attachments/assets/95da15e8-5288-4948-aedb-f16f1da595ba)

1. **Fast Route**
   - Generates an initial set of **routing guides**.
   - Helps direct the **detailed routing** process.

2. **Detailed Route**
   - Uses **routing algorithms** to optimize wire connections.
   - Ensures minimal **wire length, congestion, and DRC violations**.

The detailed routing phase produces the final routed design with **optimized** connections.
---


### SKY3_L1 - TritonRoute and Routing Schemes

### **TritonRoute for Detailed Routing**
TritonRoute performs **detailed routing** using a structured approach to ensure efficient and optimized wire connections.

### **Routing Scheme**
TritonRoute follows a **pane routing scheme** with:
1. **Intra-layer parallel routing**:
   - Routes wires in the same metal layer parallel to each other.
   - Optimizes for minimal congestion and short paths.

2. **Inter-layer sequential routing**:
   - Routes wires sequentially across multiple metal layers.
   - Ensures proper **via placement** and **signal integrity**.

### **Routing Guides**
- Routing guides are pre-generated to **direct detailed routing**.
- They help **avoid congestion** and ensure **Design Rule Compliance (DRC)**.
![image](https://github.com/user-attachments/assets/77a4cefe-287d-47aa-843e-f49e2a372f80)

---

### SKY3_L2 - Intra-Layer Parallel and Inter-Layer Sequential Panel Routing

### **Panel Routing Concept**
Panel routing is a structured approach used in **detailed routing** to efficiently connect wires while optimizing space and reducing congestion.

### **1. Intra-Layer Parallel Routing**
- Wires within the **same metal layer** are routed in a **parallel fashion**.
- This ensures **minimal interference** and **efficient track utilization**.
- Helps in **reducing delays** and **minimizing RC parasitics**.

### **2. Inter-Layer Sequential Routing**
- Wires moving across **different metal layers** are routed **sequentially**.
- **Vias** are used to transition between layers.
- Higher metal layers are **wider** for power and clock signals, while lower layers are **denser** for local connections.

### **Panel Representation**
- **Dashed lines** represent **routing panels**.
- Each panel contains a **set of tracks** for intra-layer routing.
- Routing progresses **panel by panel**, optimizing for **design rule compliance (DRC)** and **timing constraints**.
![image](https://github.com/user-attachments/assets/65a22aaa-13c6-4fe6-a06f-8bf199f74423)

---

### SKY_L3 - TritonRoute Handling Connectivity

### **TritonRoute Overview**
TritonRoute is an **open-source detailed router** used in OpenROAD to ensure correct connectivity and design rule compliance (DRC) in physical design.

### **Handling Connectivity in TritonRoute**
1. **Input Preparation**
   - Takes **global routing guides** from FastRoute.
   - Reads **DEF, LEF, and design constraints**.
   - Ensures correct **netlist connectivity** before detailed routing.
   ![image](https://github.com/user-attachments/assets/a38ca915-9e3e-44d3-b107-f61debb5d717)
---

## SKY_L4 - Routing Topology Algorithm

### **Routing Topology Overview**

![image](https://github.com/user-attachments/assets/928eeaa8-1132-4d27-9f59-89f6946adb06)

Routing topology defines how wires connect different components in a chip while optimizing performance, area, and power. 
![image](https://github.com/user-attachments/assets/91e55fae-1f30-47ce-aec8-8f42ab8b3bc4)

![image](https://github.com/user-attachments/assets/8e7ef354-01f0-4fb5-8b9e-4ce048716ddb)

for me it took 0h31m41s
```
  magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read final-routed.def &
```

![image](https://github.com/user-attachments/assets/5651457c-b7b4-4f5a-8de6-3db5d493e31f)
with no DRC errors

![image](https://github.com/user-attachments/assets/70678216-035f-424d-aa7f-93a179811691)


![image](https://github.com/user-attachments/assets/cda5bfbf-9939-4ef4-ae1b-65ec53098e80)
---

