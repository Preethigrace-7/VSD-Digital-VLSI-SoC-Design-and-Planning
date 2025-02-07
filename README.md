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
Below is a representation of how RISC-V code transforms into a physical layout:

![image](https://github.com/user-attachments/assets/b6f6d3f7-642c-42ea-951c-6f81e0a81a27)
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







