## NAME: MALENI.M
## REGISTER NUMBER: 212223040110
# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 3 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
## PROCEDURE:
1.Create a New Project: Open Quartus and create a new project by selecting "File" > "New Project Wizard." Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA).

2.Create a New Design File: Once the project is created, right-click on the project name in the Project Navigator and select "Add New File." Choose "Verilog HDL File".

3.Write the Combinational Logic Code: Open the newly created Verilog or VHDL file and write the code for your combinational logic.

4.Compile the Project: To compile the project, click on "Processing" > "Start Compilation" in the menu. Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device.

5.Analyze and Fix Errors:* If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window. Review and fix any issues in your code if necessary. View the RTL diagram.

6.Verification: Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF". Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All. Give the Input Combinations according to the Truth Table amd then simulate the Output waveform

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final.
## PROGRAM:
```
module up_counter(clk,q1,q2,q3);
input clk;
output reg q1,q2,q3;
always@(posedge clk)
begin
q3=(q1&q2)^q3;
q2=q1^q2;
q1=1^q1;
end
endmodule
```
## RTL LOGIC FOR UP COUNTER:
![image](https://github.com/MALENIMURUGAN/Exp-7-Synchornous-counters-/assets/144870675/aae9b0be-59da-496d-bc65-26bfeaa9d85d)

## TRUTH TABLE:
![image](https://github.com/MALENIMURUGAN/Exp-7-Synchornous-counters-/assets/144870675/9c9173b4-0699-4d61-a41b-959ab1257ee2)

## TIMING DIAGRAM FOR UP COUNTER:
![image](https://github.com/MALENIMURUGAN/Exp-7-Synchornous-counters-/assets/144870675/45494cbf-ee79-4f2c-a3a8-1b768dbbffe0)

## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.

## PROGRAM:
```
module COUNTER(clk,q1,q2,q3);
input clk;
output reg q1,q2,q3;
always@(posedge clk)
begin
q3=((~q2)&(~q1))^q3;
q2=(~q1)^q2;
q1=1^q1;
end
endmodule
```

## RTL LOGIC DOWN COUNTER:
![image](https://github.com/MALENIMURUGAN/Exp-7-Synchornous-counters-/assets/144870675/ff3fcc05-76c9-445d-bb8f-7da8186c2ce4)

## TRUTH TABLE:
![image](https://github.com/MALENIMURUGAN/Exp-7-Synchornous-counters-/assets/144870675/9ce5f16a-1c67-443b-a2ab-090b69166eb4)

## TIMING DIAGRAM FOR DOWN COUNTER:
![image](https://github.com/MALENIMURUGAN/Exp-7-Synchornous-counters-/assets/144870675/d41418d4-a969-4cf8-bdbe-88901015372b)

## RESULT:
Thus synchornous counters up counter and down counter circuit are studied and the truth table for different logic gates are verified.




