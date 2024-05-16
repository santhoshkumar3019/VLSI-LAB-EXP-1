# VLSI-LAB-EXPERIMENTS

# AIM:

To simulate Logic Gates ,Adders and Subtractors using Vivado 2023.1.

# APPARATUS REQUIRED: 

VIVADO 2023.1

# PROCEDURE:

1.Open Vivado: Launch Xilinx Vivado software on your computer.

2.Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3.Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4.Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add        Sources". Choose your Verilog files from the file browser.

5.Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado             Simulator).

6.Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7.Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8.Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9.View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.


# Logic Diagram :

# Logic Gates:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


# Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


# Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


# Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



# Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



# 8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



# VERILOG CODE: 

# Full Adder:
```
module fulladder (sum, cout, a,b,c);
input a,b,c;
output sum, cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and al(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,w2,w3); or o2(cout,w5,w4);
endmodule
```
# Full Subractor:
```
module full_subtractor(a, b, c,D, Bout);
input a, b, c;
output D, Bout;
assign D = a^b^c;
assign Bout = (a & b) | ((a^ b) & c);
endmodule
```
# Half Adder:
```
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry;
or(sum,a,b);
and(carry,a,b);
endmodule
```
# Half Subractor:
```
module half_subtractor(D,Bo,A,B);
input A,B;
output D,Bo;
assign D=A^B;
assign Bo=(~A)&B;
endmodule
```
# Logic Gates:
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
# Ripple Carry Adder 4Bit:
```
module rippe_adder(S, Cout, X, Y,Cin);
input [3:0] X, Y;// Two 4-bit inputs
input Cin;
output [3:0] S;
output Cout;
wire w1, w2, w3;fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
```
# OUTPUT:
# Full Adder
![8a1e1d4a-63d8-445a-9cf6-5c10cbeec61b](https://github.com/yogiyazh/VLSI-LAB-EXP-1/assets/159939338/b78ddb91-86ae-4433-801a-bc81b442b972)

# Full Subractor
![97cb94f7-6bf9-4824-8864-a800a053d9ac](https://github.com/yogiyazh/VLSI-LAB-EXP-1/assets/159939338/b82af11b-a92a-4024-88b2-28b5d48475d9)

# Half Adder
![3361d2e4-b9f2-4c5a-b49b-93cd935de652](https://github.com/yogiyazh/VLSI-LAB-EXP-1/assets/159939338/faed5e73-e920-47b5-9868-e06cc6aad3c7)

# Half Subractor
![5aeaf4af-cc29-4f6e-9f8b-e8ed1e6d09c8](https://github.com/yogiyazh/VLSI-LAB-EXP-1/assets/159939338/96a61fd0-4ca6-43e3-b821-a0b3287d8cea)

# Logic Gates
![f680e0f1-07a7-4efb-9487-04563c0cd2c3](https://github.com/yogiyazh/VLSI-LAB-EXP-1/assets/159939338/31139d4d-8586-4291-9169-483fe8162ffb)

# Ripple Carry Adder
![bca16bba-34f5-4c59-8525-349c503f5634](https://github.com/yogiyazh/VLSI-LAB-EXP-1/assets/159939338/dd24d2de-9c84-4f05-92d9-d58145b85bb8)


# RESULT:
Thus the Simulation of Logic Gates ,Adders and Subtractors is done and verified.
