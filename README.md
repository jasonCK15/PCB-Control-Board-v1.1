# FPGA-Control-Boaard

## Description
This PCB is used to amplify the digital signal, which is generated from the FPGA. Hence, controlling the patch antennas in the metasurface. 

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/dc01adc4-7358-4ef4-ae02-3903834554af)


## Design 

For the circuit design of the board, it consists of three parts: 
 1. Power Conversion 
 2. op-amp signal 


### Power Conversion

For the power Conversion, the system has a two stage of power conversion. 

First part is the stepdwon voltage from 12V to 5V. By doing that, we use the LM25116 for doing the power conversion. LM25116 is a power IC for doing the stepdown voltge, the IC supports wide range of the voltage input (9-42V), and perform differenet output voltage in different conffiguration. Here is the schematic of the LM25116 circuit using in this control baord, the converter supports maximum current rating of 5A, which is enough for the whole system operation, including the op-amp, IC and the FPGA Core Board's operations.

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/f3f20763-f181-4c54-b8e6-f3d5443e2d84)

Moreover, the board is also consists safety IC for preventing the short-circcuit, overvoltage or other problems that may harm the circuit's operation. The safety IC is placed into the 5V rail on the top and button isde of the PCB Board. 

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/41ed517f-0a94-4875-816a-413e0aecfdb3)

After having the 5V rail in the board, the op-amp requires a ±1.5V supply for normal operation, which can power the 5 op-amps with all being loaded. For doing this, the LM27762 Converter is used for doing the positive and negative power conversion. The LM27762 can supply up to 250mA in each rail, which is able to use 1 LM27762 LDO to power 5 op-amp simultaneously.

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/44f310d2-d21f-49b1-b0b7-1b2c236dff4a)

For the configuration of the circuit, the positive and negative voltage is determined by the output resistors. 

**Negative Output Voltage Setting**
$$VOUT=–1.22V×(R3+R4)/R4$$

**Positive Output Voltage Setting**
$$VOUT=1.2V×(R1+R2)/R2$$

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/a2a99f98-b9f9-46a3-ae95-649aaaac19d1)

***Reminder: As the previous testing, it is found that the C13 capacitance has to be 0.2uF or 0.1uF for normal operation. The reason is that the charge-pump cannot be reached to the 5V voltage when it is using the higher capacitance in the C13(cfly) capacitor.***


### op-amp signal

The op-amp circuit is used as a comparator circuit, which IO's output voltage is smaller than the 1V, the output voltage is zero on the output side. 

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/96ed053f-181c-4bcc-8847-9b61d34aed04)

The simplified signal diagram is shown below:

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/c5cde211-8cd8-43f8-8b5b-e304d7ccf828)



### Reference Links ###

1. LM27762 Datasheet
https://www.ti.com/lit/ds/symlink/lm27762.pdf?ts=1698800117651&ref_url=https%253A%252F%252Fwww.google.com%252F

