# EXPERIMENT:1   SIMULATION AND IMPLEMENTATION OF LOGIC GATES, ADDERS & SUBTRACTOR
# DATE:

# AIM:

To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

# APPARATUS REQUIRED:

vivado 14.7 Spartan6 FPGA

# PROCEDURE: 

STEP:1 Start the vivado navigator, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type. 

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. 

STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained.

STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. 

STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.

STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

STEP:12 Load the Bit file into the SPARTAN 6 FPGA


```
DEVELOPED BY: SANDEEP KUMAR A

REGISTERED NUMBER: 212222060215
```

Logic Diagram :

Logic Gates:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

VERILOG CODE:
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
OUTPUT:

 ![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-1/assets/160619092/b80cc1bf-406a-4ccb-b9b7-3f4132080a0b)
 
LOGIC DIAGRAM:

Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

VERILOG CODE:
```
module half_adder(Sum,carry,a,b);
input a,b;
output Sum,carry;
assign Sum = a ^ b;
assign carry = a & b;
endmodule
```
OUTPUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-1/assets/160619092/798ac1d4-e353-43e8-81bb-ac7d51a3103e)

LOGIC DIAGRAM:

Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

VERILOG CODE:
```
module fulladder(sum,cout,a,b,c);
input a,b,c;
output sum,cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and a1(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,c1,c2);
or o2(cout,w5,c3);
endmodule
```
OUTPUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-1/assets/160619092/cfcd7a2e-ad44-471f-a165-82e77e807d4a)

LOGIC DIAGRAM:

Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

VERILOG CODE:
```
module half_sub(Diff,Borrow,a,b);
input a,b;
output Diff,Borrow;
wire w1;
not(w1,a);
xor(Diff,a,b);
and(Borrow,b,w1);
endmodule
```
OUTPUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-1/assets/160619092/27f0eeb9-2391-44cf-bb65-02c4d4f1828d)


LOGIC DIAGRAM:

Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

VERILOG CODE:
```
module full_sub(borrow,diff,a,b,c);
output borrow,diff;
input a,b,c;
wire w1,w4,w5,w6;
xor (diff,a,b,c);
not n1(w1,a);
and a1(w4,w1,b);
and a2(w5,w1,c);
and a3(w6,b,c);
or o1(borrow,w4,w5,w6);
endmodule
```
OUTPUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-1/assets/160619092/fb5db538-ad22-4aed-b0f3-9bba16adf158)


LOGIC DIAGRAM:

8 Bit Ripple Carry Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

VERILOG CODE:
```
module fulladder(S, Co, X, Y, Ci);
  input X, Y, Ci;
  output S, Co;
  wire w1,w2,w3;
  //Structural code for one bit full adder
  xor G1(w1, X, Y);
  xor G2(S, w1, Ci);
  and G3(w2, w1, Ci);
  and G4(w3, X, Y);
  or G5(Co, w2, w3);
endmodule
module rippe_adder(S, Cout, X, Y,Cin);
 input [7:0] X, Y;// Two 4-bit inputs
 input Cin;
 output [7:0] S;
 output Cout;
 wire w1, w2, w3, w4, w5, w6, w7;
 // instantiating 8 1-bit full adders in Verilog
 fulladder u1(S[0], w1,X[0], Y[0], Cin);
 fulladder u2(S[1], w2,X[1], Y[1], w1);
 fulladder u3(S[2], w3,X[2], Y[2], w2);
 fulladder u4(S[3], w4,X[3], Y[3], w3);
 fulladder u5(S[4], w5,X[4], Y[4], w4);
 fulladder u6(S[5], w6,X[5], Y[5], w5);
 fulladder u7(S[6], w7,X[6], Y[6], w6);
 fulladder u8(S[7], Cout,X[7], Y[7], w7);
endmodule
```
OUTPUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-1/assets/160619092/3751c841-967e-4c20-937a-d2909244214b)



RESULT:

Hence, the stimulation and synthesis of a Logic Gates,Adders and Subtractor was run successfully by using vivado ISE.
