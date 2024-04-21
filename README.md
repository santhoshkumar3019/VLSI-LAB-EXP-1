# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.
logic gates:
Logic Diagram :
![image](https://github.com/santhoshkumar3019/VLSI-LAB-EXP-1/assets/161813818/34e2ac0b-31d9-4aac-a837-b2c0dc4a8cf5)

verilog code:
module logicgate(a,b,andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate);
input a,b;
output andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
nand(nandgate,a,b);
nor(norgate,a,b);
xor(xorgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule

output waveform :
![image](https://github.com/santhoshkumar3019/VLSI-LAB-EXP-1/assets/161813818/98c14edc-cc9b-4a0c-acdb-a21014deec27)

Half Adder:
logic diagram :
![image](https://github.com/santhoshkumar3019/VLSI-LAB-EXP-1/assets/161813818/a93ff77f-ac6a-4e07-ba0d-18e55d8298d7)
verilog code :
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule 
output waveform :
![image](https://github.com/santhoshkumar3019/VLSI-LAB-EXP-1/assets/161813818/b2831abf-d7aa-4959-ac9e-ecc59b3a99f5)

Full adder:
logic diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)
verilog code:
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule

output waveform:
![image](https://github.com/santhoshkumar3019/VLSI-LAB-EXP-1/assets/161813818/95900fda-8422-4beb-a541-ba7eb6c5b687)



Half Subtractor:
logic diagram :

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)
verilog code:
module halfsub(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor(diff,a,b);
and(borrow,~a,b);
endmodule
output waveform:
![image](https://github.com/santhoshkumar3019/VLSI-LAB-EXP-1/assets/161813818/0f4840b8-5e5d-44dd-a3d8-862fe08e098e)

Full Subtractor:
logic diagram :

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)
verilog code:
module fs(a,b,bin,d,bout);
input a,b,bin;
output d,bout;
wire w1,w2,w3;
xor(w1,a,b);
xor(d,w1,bin);
and(w2,~a,b);
and(w3,~w1,bin);
or(bout,w3,w2);
endmodule
output waveform:
![image](https://github.com/santhoshkumar3019/VLSI-LAB-EXP-1/assets/161813818/86423ef0-0898-41f1-9fe4-dd1e620d24a6)

8 Bit Ripple Carry Adder
logic diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)
verilog code:
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule

module rca_8bit(a,b,cin,s,cout);
input [7:0]a,b;
input cin;
output [7:0]s;
output cout;
wire [7:1]w;
fulladder f1(a[0], b[0], cin, s[0], w[1]);
fulladder f2(a[1], b[1], w[1], s[1], w[2]);
fulladder f3(a[2], b[2], w[2], s[2], w[3]);
fulladder f4(a[3], b[3], w[3], s[3], w[4]);
fulladder f5(a[4], b[4], w[4], s[4], w[5]);
fulladder f6(a[5], b[5], w[5], s[5], w[6]);
fulladder f7(a[6], b[6], w[6], s[6], w[7]);
fulladder f8(a[7], b[7], w[7], s[7], cout);
endmodule
output waveform :
![image](https://github.com/santhoshkumar3019/VLSI-LAB-EXP-1/assets/161813818/30c439b1-8f80-4600-acbc-501dd20a91d1)

VERILOG CODE:

----Type Verilog Code

OUTPUT:

-----Place a Waveform Generated from Xilinx ISE

RESULT:

