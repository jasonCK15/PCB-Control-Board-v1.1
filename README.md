# FPGA-Control-Boaard

## Description
This PCB is used to amplify the digital signal, which is generated from the FPGA. Hence, controlling the patch antennas in the metasurface. 

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/dc01adc4-7358-4ef4-ae02-3903834554af)


## Design 

For the circuit design of the board, it consists of three parts: 
1. Power Conversion 
2. op-amp signal 
3. Traces routing

For the power Conversion, the system has a two stage of power conversion. 

First part is the stepdwon voltage from 12V to 5V. By doing that, we use the LM25116 for doing the power conversion. LM25116 is a power IC for doing the stepdown voltge, the IC supports wide range of the voltage input (9-42V), and perform differenet output voltage in different conffiguration. Here is the schematic of the LM25116 circuit using in this control baord, the converter supports maximum current rating of 5A, which is enough for the whole system operation, including the op-amp, IC and the FPGA Core Board's operations.

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/f3f20763-f181-4c54-b8e6-f3d5443e2d84)

Moreover, the board is also consist safety IC for preventing the short-circcuit, overvoltage or other problems that may harm the circuit's operation. 

![image](https://github.com/jasonCK15/PCB-Control-Board-v1.1/assets/86227836/41ed517f-0a94-4875-816a-413e0aecfdb3)


