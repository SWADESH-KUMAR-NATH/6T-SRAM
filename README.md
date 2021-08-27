# 6T-SRAM

## Table of Contents
* 6T-SRAM CELL DESIGN
* PRE-LAYOUT SIMULATIONS
* LAYOUTS

## 6T-SRAM CELL DESIGN
In this Project we designed the various components of SRAM considering the below
constraints
* Memory size : *32kb*
* Supply voltage : *5.0V*
* Technology : *scn4m_subm 0.5um*

*The sizing of all the 6 Transistors are done so that the internal node voltage at `Q1` should not exceed Threshold voltage `Vt`*

---
> READ OPERATION

![SRAM-read](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/SRAM_READ.JPG)

![READ EQ](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/read_eq.PNG)

---
> WRITE OPERATION

![SRAM-write](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/SRAM_WRITE.JPG)

![WRITE EQ](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/write_eq.PNG)

---
> SIZING OF 6T-SRAM CELL

![Final SRAM Sizing](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/6T-SRAM_CELL.JPG)

Finally, the sizes of 6 Transistors are as follows :

| TRANSISTOR | WIDTH | LENGTH |
| --- | --- | --- |
| M1, M2 | 1.2um | 0.4um |
| M3, M4 | 0.6um | 0.8um |
| M5, M6 | 0.6um | 1.2um |

## PRE-LAYOUT SIMULATIONS

### DC ANALYSIS

Voltage Transfer Characteristic (VTC) of individual inverter :
![DC ANALYSIS](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/simulations/sram_dc.PNG)
Here for `Vdd = 5V` we got the `Inversion Threshold` or `Switching Threshold` as `1.2V`.

---
### SNM

The stability and writability of the SRAM cell depends upon `Hold margin`,`Read margin` and `Write margin`, which are determined by `Static Noise Margin(SNM)`of the two cross coupled inverters

1. HOLD SNM
![SNM HOLD](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/simulations/sram_hold.PNG)
2. READ SNM
![SNM READ](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/simulations/sram_read.PNG)

---
### TRANSIENT ANALYSIS
Here the effect of parasitic capacitors`(gate capacitance)` at BL, BLB and WL are demonstrated 
![TRANSISENT ANALYSIS](https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/simulations/sram_trans1.PNG)


