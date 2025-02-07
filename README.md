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
#### **SKY_L1 - Introduction to QFN-48 Package, Chip, Pads, Core, Die, and IPs**

In this module, we explored how to design a System-on-Chip (SoC) on a **VSDSquadran Board** and got familiar with the **QFN-48 package**.

### **1. QFN-48 Package**
- **QFN (Quad Flat No-Leads)** is a chip package with **48 pins**.
- This package allows **efficient signal transmission** with minimal resistance.
- **Image 1:** QFN-48 Package (to be uploaded)

### **2. Internal Structure of the Processor**
- The processor includes key components such as **VDD/GND, JTAG, Flash, ADC, SRAM (external SoC), etc.**
- **Image 1.1:** Processor Block Diagram (to be uploaded)

### **3. Chip and Wire Bonding**
- The **chip is placed inside the package** and connected to the **package pins** using **wire bonds**.
- **Image 2:** Chip Interconnection with Wire Bonds (to be uploaded)

### **4. Chip Structure**
- The **chip** consists of three major components:
  - **Pads:** Located at the chip's boundary, these enable communication of signals between the **chip** and the **outside world**.
  - **Core:** Contains the fundamental digital logic elements such as **gates, multiplexers, encoders, decoders, etc.**
  - **Die:** The silicon part of the chip where transistors and circuits are fabricated.
- **Image 3:** Chip Structure Showing Pads, Core, and Die (to be uploaded)

### **5. Foundry IPs and Macros**
- **Foundry IPs (Intellectual Property):** These are **pre-designed components** provided by the foundry.
  - Examples: **PLL, ADC, DAC, SRAM**
- **Macros:** These are **pre-verified functional blocks** used within the SoC.
  - Examples: **SPI, RISC-V/SoC**
- **Image 4:** Foundry IPs and Macros in the Chip (to be uploaded)


