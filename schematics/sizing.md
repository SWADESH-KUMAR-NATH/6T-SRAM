## Sizing of 6T-SRAM Cell

*The sizing of all the 6 Transistors are done so that the internal node voltage at **Q1** should not exceed Threshold voltage **Vt** of Transistors*

> READ OPERATION

[*For reading the data when node Q1 has logic 0 voltage*]

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/SRAM_READ.JPG" 
     width="whatever" 
     height="whatever" />

$$(\frac w l)_3 (V _gs -V_T)^2 = (\frac w l)_1 (2(V _gs -V_T)V_ds - V_ds^2) $$
$$\frac {(w/l) _3} {(w/l)_1} = \frac{(2(V _gs -V_T)V_ds-V_ds^2)}{(V _gs -V_T)^2} =0.265625$$
$$\frac {(w/l) _3} {(w/l)_1}\le\frac 1 4 $$


> WRITE OPERATION

[*For writing logic o at node Q1 when it has a previous value of logic 1*]

<img src="https://github.com/SWADESH-KUMAR-NATH/6T-SRAM/blob/main/schematics/SRAM_WRITE.JPG" 
     width="whatever" 
     height="whatever" />

$$ \mu_n(\frac w l)_3 (2(V _gs -V_T)V_ds - V_ds^2) = \mu_p(\frac w l)_5 (V _gs -V_T)^2 $$
$$ \frac {(w/l) _5} {(w/l)_3} = \frac {\mu_n} {\mu_p} \frac{2(V _gs -V_T)V_ds-V_ds^2}{(V _gs -V_T)^2} = 0.6665 $$
$$ \frac {(w/l) _5} {(w/l)_3} = \frac 2 3 $$


