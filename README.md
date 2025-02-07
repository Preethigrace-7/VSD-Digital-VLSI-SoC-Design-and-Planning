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
### **1.Internal Structure of the Processor**
- The processor includes key components such as **VDD/GND, JTAG, Flash, ADC, SRAM (external SoC), etc.**
![image](https://github.com/user-attachments/assets/288cf337-f5d1-48f1-ac6f-ca1e87c9ff98)

### **2.QFN-48 Package**
- **QFN (Quad Flat No-Leads)** is a chip package with **48 pins**.
- This package allows **efficient signal transmission** with minimal resistance.
![image](https://github.com/user-attachments/assets/5e52acee-f050-4a9f-a445-cc85cc5c0cc2)

### **3. Chip and Wire Bonding**
- The **chip is placed inside the package** and connected to the **package pins** using **wire bonds**.
![image](https://github.com/user-attachments/assets/a66058f5-82bb-47ac-b522-56131cbaac0c)

### **4. Chip Structure**
- The **chip** consists of three major components:
  - **Pads:** Located at the chip's boundary, these enable communication of signals between the **chip** and the **outside world**.
  - **Core:** Contains the fundamental digital logic elements such as **gates, multiplexers, encoders, decoders, etc.**
  - **Die:** The silicon part of the chip where transistors and circuits are fabricated.
![image](https://github.com/user-attachments/assets/e111b90e-424c-4052-9ec8-b1a814d03bda)

### **5. Foundry IPs and Macros**
- **Foundry IPs (Intellectual Property):** These are **pre-designed components** provided by the foundry.
  - Examples: **PLL, ADC, DAC, SRAM**
- **Macros:** These are **pre-verified functional blocks** used within the SoC.
  - Examples: **SPI, RISC-V/SoC**
![image](https://github.com/user-attachments/assets/15ac34e5-9f61-4c63-9bd9-d393efb30b65)



