# VLSI-LAB-EXPERIMENTS
## AIM:
To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

## APPARATUS REQUIRED:
Xilinx 14.7 Spartan6 FPGA

## PROCEDURE:
STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## LOGIC GATES :
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)
### Verilog code:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
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
### Output:
![logic gates](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/5516f676-6f51-4b67-8d46-77570c1b3d2a)

## HALF ADDER:
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

### Verilog Code:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
### Output:
![311277374-980162fb-8e62-410e-a47f-ded465d68394](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/cb67697a-0561-4c36-a7d4-99c0b889e710)

## HALF SUBTRACTOR:
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

### Verilog Code:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
### Output:
![311277475-2b635509-2702-40ca-9fb6-11e381d97f7e](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/c8054638-67f1-4f2f-9109-eaa10bdbb750)

## FULL ADDER:
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

### Verilog Code:
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
### Output:
![311277526-4dea3a4a-09b9-47a2-80ff-a351d84e636c](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/73ecbae5-418a-474b-8c86-fe92088a9be0)

## FULL SUBTRACTOR:
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

### Verilog Code:
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
### Output:
![311277758-20d650b4-0c31-45b5-a16c-b176d00dc041](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/29805ff8-d275-4daa-85a7-185769df03ae)

## 8 BIT RIPPLE CARRY ADDER:
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

### Verilog Code:
```
module rca(a,b,c,sum,cout) ;
 input a,b,c;
 output sum,cout;
 wire w1,w2,w3;
 xor g1(w1,a,b);
 xor g2(sum,w1,c);
 and g3(w2,a,b);
 and g4(w3,w1,c);
 or g5(cout,w3,w2);
 endmodule
 
 module rca1(a,b,cin,sum,cout);
 input [7:0]a,b;
 input cin;
 output [7:0]sum;
 output cout;
 wire w1,w2,w3;
 rca RC1(a[0],b[0],cin,sum[0],w1);
 rca RC2(a[1],b[1],w1,sum[1],w2);
 rca RC3(a[2],b[2],w2,sum[2],w3);
 rca RC4(a[3],b[3],w3,sum[3],w4);
 rca RC5(a[4],b[4],w4,sum[4],w5);
 rca RC6(a[5],b[5],w5,sum[5],w6);
 rca RC7(a[6],b[6],w6,sum[6],w7);
 rca RC8(a[7],b[7],w7,sum[7],cout);
 endmodule
```
### Output:
![RCA](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/a199172f-9f8b-4fda-af52-53372798ebd3)

## RESULT:
Thus all the Logic Gates,Adders and Subtractor are Simulated using Xilinx ISE.
