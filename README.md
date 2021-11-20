# 6T-SRAM

## Table of Contents
- [OVERVIEW](#OVERVIEW)
- [SRAM ARCHITECTURE](#SRAM-ARCHITECTURE)
     - [6T 1 BIT SRAM CELL](#6T-1-BIT-SRAM-CELL)
     - [PRECHARGE CIRCUIT](#PRECHARGE-CIRCUIT)
     - [SENSE AMPLIFIER](#SENSE-AMPLIFIER)
     - [WRITE DRIVER](#WRITE-DRIVER)
- [PRE-LAYOUT SIMULATIONS](#PRE-LAYOUT-SIMULATIONS)
     - [STATIC NOISE MARGIN](#STATIC-NOISE-MARGIN)
     - [TIMING ANALYSIS](#TIMING-ANALYSIS)
- [LAYOUTS](#LAYOUTS)
- [ACKNOWLEDGEMENTS](#ACKNOWLEDGEMENTS)
- [CONTACT INFORMATION](#CONTACT-INFORMATION)

---

## OVERVIEW

![SRAM Block Diagram](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/sram_arc.jpg)

In this Project we have designed the various components of SRAM considering the 
below specifications
* Memory size    : *1K\*32bit*
* Supply voltage : *5.0V*
* Technology     : *scn4m_subm 0.5um*

Here according to the row and column address one of the wordline and one of the 
column will get selected, which will give access to one of the 6T-Bit cells in 
the respective column. For this 6T cell, we did the simulation and checked its 
functionality.

---

## SRAM ARCHITECTURE

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/6Tcell.jpg"
     align=right
     width=400
     height="whatever" />

### 6T 1 BIT SRAM CELL

*The sizing of all the 6 Transistors are done so that the internal node voltage 
at **Q1** should not exceed Threshold voltage **Vt** of M2 Transistors*

The sizing of 6T 1 BIT SRAM is described [here](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/sizing.md).

Finally, the sizes of 6 Transistors are as follows :

| TRANSISTOR | WIDTH | LENGTH |
| --- | --- | --- |
| M1, M2 | 1.2um | 0.4um |
| M3, M4 | 0.6um | 0.8um |
| M5, M6 | 0.6um | 1.2um |


<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/pc.jpg"
     align=right
     width=400 
     height="whatever"  />

### PRECHARGE CIRCUIT

- Precharge Circuit acts like a switch which charges the bit-lines before read and 
write operations. The third PMOS transistor connects the two bit-lines together to 
equalize the voltage between them.
- This circuit is controlled by another enabling signal "PC" which turns on/off 
the PMOSes.
- It plays significant role when more number of 6T-bit cells are implemented with 
one set of bit lines i.e. BL & BLB.
- We should make the pmoses strong enough to pull up the bitline voltages to avoid delay.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/sa.jpg"
     align=right
     width=400
     height="whatever"  />

### SENSE AMPLIFIER

- The Sense Amplifier is a differential circuit amplifier to sense the voltage dif-
ference between BL and BLB while a read operation is performed. It recovers the 
signals from the bit-lines as they do not experience full voltage swing because 
of large parasitic capacitance.
- Here we've used *Basic Latch Based Sense Amplifier* with pass transistors which 
effectively decouples the amplifier inputs and outputs from the bitlines. The 
whole circuit is controlled by "R_EN" signal.
- Because of the positive feedback due to the cross coupled inverters, the node 
voltages couldn't stay at the metastable state and the bias developed latches 
the output to stable states i.e. Logic 0 & 1.
- Read operatiion is negative edge triggered i.e. when "R_EN" is at Logic 0 it can read.

     
### WRITE DRIVER

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/wd.jpg"
     align=right
     width=400 
     height="whatever"  />
     
- Write Driver is used to write data into the 6t-Bit cells. During write operations when the "W_EN" signal is enabled (at Logic 1), depending upon the signal of "DIN" it pulls down the voltage of a specific bitline to Logic 0 .

- If "DIN" is Logic 1 the nmos connectig to the BLB bitline gets turned on thereby pulling its voltage to ground (Logic 0) and updates the _Q1_ and _Q2_ node voltage as Logic 1 and 0 . Similarly when "DIN" is Logic 0, the nmos connectig to the BL bitline gets turned on thereby pulling its voltage to ground (Logic 0), which eventually leads to updating the _Q1_ and _Q2_ node voltage as Logic 0 and 1 respectfully. 
- The stronger the nmoses the quicker the bitlines get pulled down to Logic 0.

---

## PRE-LAYOUT SIMULATIONS

### STATIC NOISE MARGIN

Static Noise Margin helps to determine the stability of the SRAM. It can also be defined as the least noise voltage needed to change the cell state .One of the methods of calculating the Static Noise Margin (SNM) is by plotting the butterfly curve. Butterfly curve is plotted by drawing and mirroring the inverter characteristics and then finding the maximum possible square between them. The length of the side of the square gives SNM. Greater the SNM better is stability.

<!-- <img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snmx.PNG"
     width="whatever" 
     height="whatever" />
     
<center>Examples of SNM for Hold , Read and Write mode respectively.</center> -->
     
1. HOLD SNM

- In absence of word line voltage, the ability of SRAM to retain the stored data is defined as hold stability.
- Hold SNM is the side of the largest square nested inside the butterfly curve, which is found to be 1V.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snm_hold.jpg" 
     width="whatever" 
     height="whatever" />

2. READ SNM

- The read margin is used to find out read stability of the SRAM. Read Stability is the ability to prevent the SRAM cell to flip the stored value while the stored value is being read.
- Here the read margin is 0.4V.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snm_read.jpg" 
     width="whatever" 
     height="whatever" />

3. WRITE SNM

- The minimum voltage required to feed new value into the SRAM cell is known as write margin. Write stability is the ability of the SRAM to allow the changes in the stored value.
- The write margin is found to be 1.7V.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/snm_write.JPG" 
     width="whatever" 
     height="whatever" />

---

### TIMING ANALYSIS

- In this Project we have performed read and write operation over one 6T-bit cell in a 1K\*32 bit SRAM havig 128 rows and 256 columns. So during the operation there are some paracitic effects of remaining 127 bit cells in the specific column and 255 bit cells in the specific row over the operating bit cell.
- As the size of the SRAM increases it becomes hard to read data from or write data into a specific bit cell as junction capacitance of each bit cell get added. Therefore we need some reading and writing circuitaries to operate properly.

#### Timing Analysis with Precharge Circuit

- Before reading data, the bit lines are charged upto Vdd and the supply is cut-off before the access transistors are turned on (by **WL** signal). Accordingly we must give the clock enabling signal **PC** to the Precharge circuit.
- The NMOSes connected to the bit lines are responsible for writing data into to bit cell by pulling down the bit lines and these are controlled by 2 signals **W0** and **W1**.
- When WL and PC both are at Logic 1 if W0 is set to Logic 1 the voltage at BL node pulled down to 0V which writes 0 at into the bit cell. Similarly W1 pulls down BLB node to 0V and writes 1 into the bit cell.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/trans1.JPG" 
     width="whatever" 
     height="whatever" />

#### Timing Analysis with Sense Amplifier

- When the **R_EN** enable signal is at Logic 0 it allows the access transistors to update the input of the Sense amplifier with the bit line voltages. Then when the signal gets high again it turns on the NMOS connecting to the ground which helps in latching the voltages at the 2 nodes of the Sense Amplifier (SA and SAB) from metastable state to stable states.
- It's necessary to keep the R_EN at logic 0 for minimum time possible i.e. time to update the inputs with latest bit line voltages.

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/trans2.JPG" 
     width="whatever" 
     height="whatever" />

#### Timing Analysis with Write Driver

- Write driver is controlled by **W_EN** signal which needs to be at logic 1 to write data. WE should keep the voltage of the **DIN** constant at logic 1 or 0. We must not change the DIN value while WL is high to avoid errors because of parasitics.
- For one column one Write driver is there so there are 128 number of write drivers from which one gets selected by the column decoder.
 
<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/trans3.JPG" 
     width="whatever" 
     height="whatever" />

---

## LAYOUTS

### 6T 1 BIT SRAM CELL

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/l6Tcell.PNG" 
     width="whatever" 
     height="whatever" />
     
### PRECHARGE CIRCUIT

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/lpc.PNG" 
     width="whatever" 
     height="whatever" />
     
### SENSE AMPLIFIER

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/lsa.PNG" 
     width="whatever" 
     height="whatever" />
     
### WRITE DRIVER

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/lwd.PNG" 
     width="whatever" 
     height="whatever" />
     
## ACKNOWLEDGEMENTS

-   Dr. Saroj Rout, Associate Professor, Silicon Institute Of Technology, Bhubaneswar
-   Mr. Santunu Sarangi, Assistant Professor, Silicon Institute Of Technology, Bhubaneswar

---

## CONTACT INFORMATION

 - Swadesh Kumar Nath, Design Engineer, [Sevya Multimedia Technologies Pvt. Ltd.](https://sevyamultimedia.com/)
 - [Linked in](https://www.linkedin.com/in/swadesh-kumar-nath-b394a1194/) 
 
 ---
