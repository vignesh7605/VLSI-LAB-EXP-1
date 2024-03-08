# VLSI-LAB-EXPERIMENTS
## AIM:
To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

## APPARATUS REQUIRED:
Xilinx 14.7 Spartan6 FPGA

## PROCEDURE:
STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## Logic Diagram :

### Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


### Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


### Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


### Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



### Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



### 8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



## VERILOG CODE:

### Logic Gates:
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
### Half Adder:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
### Half Subtractor:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
### Full Adder:
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
### Full Subtractor:
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
### 8 Bit Ripple Carry Adder:
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```
## OUTPUT:
### Logic Gates:
### AND GATE
![311276783-23d9c1be-7b74-4d07-9f78-9e972e84c57e](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/c31d736b-bfc7-4b3b-89b3-1ed540b0836f)

### OR GATE
![311276818-ebce9760-5470-4f0c-ab01-922ffab827af](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/61171432-0d3c-4bf0-a67b-bccf23aad72d)


### NAND GATE
![311277019-32fe8101-f152-48c9-a862-e59300657686](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/a6a07628-0ddc-474b-a58d-70c83eb5aec7)


### NOR GATE

![311277322-fdc2d528-f76f-483f-bf99-5dbf59d24763](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/ec349283-ef74-4009-bf52-835894f723c7)

### XOR GATE
![311277118-7081bd26-9775-4af2-8944-0ac4edfc8a71](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/94ca2621-976b-46b6-b64e-58f14d35680d)


### XNOR GATE
![311277187-f14caf8c-34fc-4057-83f1-713dbaf232fc](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/127a26bc-2762-41f7-af21-a9eb0d9791bd)


### NOT GATE
![311277275-181f5b38-f922-4eb6-a97c-07be176b8d82](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/a64a66e8-eefd-45b1-bf00-1d0edfc5b956)


### Half Adder:
![311277374-980162fb-8e62-410e-a47f-ded465d68394](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/cb67697a-0561-4c36-a7d4-99c0b889e710)


### Half Subtractor:
![311277475-2b635509-2702-40ca-9fb6-11e381d97f7e](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/c8054638-67f1-4f2f-9109-eaa10bdbb750)


### Full Adder:
![311277526-4dea3a4a-09b9-47a2-80ff-a351d84e636c](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/73ecbae5-418a-474b-8c86-fe92088a9be0)


### Full Subtractor:
![311277758-20d650b4-0c31-45b5-a16c-b176d00dc041](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/29805ff8-d275-4daa-85a7-185769df03ae)


### 8 Bit Ripple Carry Adder:

## RESULT:
