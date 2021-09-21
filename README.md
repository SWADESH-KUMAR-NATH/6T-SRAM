# 6T-SRAM

## Table of Contents
- [SRAM ARCHITECTURE](#SRAM-ARCHITECTURE)
     - [6T 1 BIT SRAM CELL](#6T-1-BIT-SRAM-CELL)
     - [PRECHARGE CIRCUIT](#PRECHARGE-CIRCUIT)
     - [SENSE AMPLIFIER](#SENSE-AMPLIFIER)
     - [WRITE DRIVER](#WRITE-DRIVER)
- [PRE-LAYOUT SIMULATIONS](#PRE-LAYOUT-SIMULATIONS)
     - [STATIC NOISE MARGIN](#STATIC-NOISE-MARGIN)
     - [TRANSIENT ANALYSIS](#TRANSIENT-ANALYSIS)
- [LAYOUTS](#LAYOUTS)
- [ACKNOWLEDGEMENTS](#ACKNOWLEDGEMENTS)
- [CONTACT INFORMATION](#CONTACT-INFORMATION)

---

## Overview

![SRAM Block Diagram](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/sram_arc.jpg)

In this Project we have designed the various components of SRAM considering the below specifications
* Memory size    : *1K\*32bit*
* Supply voltage : *5.0V*
* Technology     : *scn4m_subm 0.5um*

Here according to the row and column address one of the wordline and one of the column will get selected, which will give access to one of the 6T-Bit cells in the respective column. For this 6T cell, we did the simulation and checked its functionality.

---

## SRAM ARCHITECTURE

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/6Tcell.jpg"
     align=right
     width="whatever" 
     height="400" />

### 6T 1 BIT SRAM CELL

*The sizing of all the 6 Transistors are done so that the internal node voltage at **Q1** should not exceed Threshold voltage **Vt** of Transistors*

The sizing of 6T 1 BIT SRAM is described [here](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/sizing.md).

Finally, the sizes of 6 Transistors are as follows :

| TRANSISTOR | WIDTH | LENGTH |
| --- | --- | --- |
| M1, M2 | 1.2um | 0.4um |
| M3, M4 | 0.6um | 0.8um |
| M5, M6 | 0.6um | 1.2um |


<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/pc.jpg"
     align=right
     width="whatever" 
     height="400" />

### PRECHARGE CIRCUIT

- Precharge Circuit acts like a switch which charges the bit-lines before read and write operations. The third PMOS transistor connects the two bit-lines together to equalize the voltage between them.
- This circuit is controlled by another enabling signal "PC" which turns on/off the PMOSes.
- It plays significant role when more number of 6T-bit cells are implemented with one set of bit lines i.e. BL & BLB.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/sa.jpg"
     align=right
     width="whatever" 
     height="400" />

### SENSE AMPLIFIER

- The Sense Amplifier is a differential circuit amplifier to sense the voltage difference between BL and BLB while a read operation is performed. It recovers the signals from the bit-lines as they do not experience full voltage swing because of large parasitic capacitance.
- Here we've used *Basic Latch Based Sense Amplifier* with pass transistors which effectively decouples the amplifier inputs and outputs from the bitlines. The whole circuit is controlled by "R_EN" signal.
- Because of the positive feedback due to the cross coupled inverters, the node voltages couldn't stay at the metastable state and the bias developed latches the output to stable states i.e. Logic 0 & 1.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/wd.jpg"
     align=right
     width="whatever" 
     height="400" />
     
### WRITE DRIVER

- Write Driver is used to write data into the 6t-Bit cells. During write operations when the "W_EN" signal is enabled, depending upon the signal of "DIN" it pulls down the voltage of a specific bitline to Logic 0 .

---

## PRE-LAYOUT SIMULATIONS

### STATIC NOISE MARGIN

Static Noise Margin helps to determine the stability of the SRAM. It can also be defined as the least noise voltage needed to change the cell state .One of the methods of calculating the Static Noise Margin (SNM) is by plotting the butterfly curve. Butterfly curve is plotted by drawing and mirroring the inverter characteristics and then finding the maximum possible square between them. The length of the side of the square gives SNM. Greater the SNM better is stability.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snmx.PNG"
     width="whatever" 
     height="whatever" />
     
<center>Examples of SNM for Hold , Read and Write mode respectively.</center>
     
1. HOLD SNM
In absence of word line voltage, the ability of SRAM to retain the stored data is defined as hold stability.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snm_hold.jpg" 
     width="whatever" 
     height="whatever" />

2. READ SNM
The read margin is used to find out read stability of the SRAM. Read Stability is the ability to prevent the SRAM cell to flip the stored value while the stored value is being read.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snm_read.jpg" 
     width="whatever" 
     height="whatever" />

3. WRITE SNM
The minimum voltage required to feed new value into the SRAM cell is known as write margin. Write stability is the ability of the SRAM to allow the changes in the stored value.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snm_write.JPG" 
     width="whatever" 
     height="whatever" />

---

### TRANSIENT ANALYSIS

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/trans1.JPG" 
     width="whatever" 
     height="whatever" />
     
<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/trans2.JPG" 
     width="whatever" 
     height="whatever" />
     
<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/trans3.JPG" 
     width="whatever" 
     height="whatever" />

---

## ACKNOWLEDGEMENTS

-   Dr.Saroj Rout,Associate Professor,Silicon Institute Of Technology,Bhubaneswar
-   Mr.Santunu Sarangi,Assistant Professor,Silicon Institute Of Technology,Bhubaneswar

---

## CONTACT INFORMATION

 - Swadesh Kumar Nath, Design Engineer, [Sevya Multimedia Technologies Pvt. Ltd.](https://sevyamultimedia.com/)
 
 ---
