# 6T-SRAM

## Table of Contents
- [SRAM BLOCKS](#SRAM-BLOCKS)
     - [6T 1 BIT SRAM CELL](#6T-1-BIT-SRAM-CELL)
     - [PRECHARGE CIRCUIT](#PRECHARGE-CIRCUIT)
     - [SENSE AMPLIFIER](#SENSE-AMPLIFIER)
     - [WRITE DRIVER](#WRITE-DRIVER)
- [PRE-LAYOUT SIMULATIONS](#PRE-LAYOUT-SIMULATIONS)
     - [STATIC NOISE MARGIN](#STATIC-NOISE-MARGIN)
     - [TRANSIENT ANALYSIS](#TRANSIENT-ANALYSIS)
- [LAYOUTS](#LAYOUTS)
- [CONTACT INFORMATION](#CONTACT-INFORMATION)
- [ACKNOWLEDGEMENTS](#ACKNOWLEDGEMENTS)

## Overview

![SRAM Block Diagram](https://github.com/gautam19499/6T-SRAM_cell_design/blob/main/images/block_diagram_new.jpeg)

In this Project we designed the various components of SRAM considering the below
constraints
* Memory size    : *1K\*32bit*
* Supply voltage : *5.0V*
* Technology     : *scn4m_subm 0.5um*
Here according to the row and column address one of the wordline and one of the column will get selected, which will give access to one of the 6T cell in the respective column. For this 6T cell, we did the simulation and checked its functionality.

---

## SRAM BLOCKS
### 6T 1 BIT SRAM CELL

*The sizing of all the 6 Transistors are done so that the internal node voltage at **Q1** should not exceed Threshold voltage **Vt** of Transistors*
[sizing in detail](#https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/sizing.md)

Finally, the sizes of 6 Transistors are as follows :

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/6T-SRAM_CELL.png"
     align=right
     width="whatever" 
     height="250" />

| TRANSISTOR | WIDTH | LENGTH |
| --- | --- | --- |
| M1, M2 | 1.2um | 0.4um |
| M3, M4 | 0.6um | 0.8um |
| M5, M6 | 0.6um | 1.2um |

<center>[ fig - 6T-SRAM Cell ]</center>

## PRE-LAYOUT SIMULATIONS

### STATIC NOISE MARGIN

Static Noise Margin helps to determine the stability of the SRAM. It can also be defined as the least noise voltage needed to change the cell state .One of the methods of calculating the Static Noise Margin (SNM) is by plotting the butterfly curve. Butterfly curve is plotted by drawing and mirroring the inverter characteristics and then finding the maximum possible square between them. The length of the side of the square gives SNM. Greater the SNM better is stability.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snmx.PNG"
     width="whatever" 
     height="whatever" />
<center>Examples of SNM for Hold , Read and Write mode respectively.</center>
     
1. HOLD SNM

Inabsence of word line voltage, the ability of SRAM to retain the stored data is defined as hold stability.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snm_hold.jpg" 
     width="whatever" 
     height="whatever" />

2. READ SNM

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snm_read.jpg" 
     width="whatever" 
     height="whatever" />

3. WRITE SNM

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

## ACKNOWLEDGEMENTS

-   Dr.Saroj Rout,Associate Professor,Silicon Institute Of Technology,Bhubaneswar
-   Mr.Santunu Sarangi,Assistant Professor,Silicon Institute Of Technology,Bhubaneswar

---
## CONTACT INFORMATION

 - Swadesh Kumar Nath, Design Engineer, [Sevya Multimedia Technologies Pvt. Ltd.](https://sevyamultimedia.com/)
