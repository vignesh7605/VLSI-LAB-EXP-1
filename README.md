**SIMULATION AND IMPLEMENTATION OF LOGIC GATES , ADDER AND SUBTRACTOR**

**AIM:**

To simulate and synthesis Logic Gates,Adders and Subtractor using Vivado 2023.2.

**APPARATUS REQUIRED:**

Vivado 2023.2

**PROCEDURE:**

STEP:1 Start the Vivado, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the Behavioural Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.


**LOGIC GATES:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

**VERILOG CODE:**

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
**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/b9ecb213-09ec-468a-943f-de9292bc859c)


**HALF ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

**VERILOG CODE:**

```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
**OUTPUT:**
![image](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/56d9a1ee-d590-47af-a204-133edf046f3f)

**FULL ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

**VERILOG CODE:**
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
**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/4136079e-f8ff-4891-86d8-0c8678860dba)


**HALF SUBTRACTOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

**VERILOG CODE:**

```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/4975f71a-f29d-45cf-af3f-141f53aedef2)


**FULL SUBTARCTOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

**VERILOG CODE:**

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

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/7e78b1ef-8bfb-4d86-b28a-1a4c28455bea)

**8 BIT RIPPLE CARRY ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

**VERILOG CODE:**

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

**OUTPUT:**

![image](https://github.com/vignesh7605/VLSI-LAB-EXP-1/assets/160568690/557f2e9e-2a87-461b-b15f-a72aae04bd06)



**RESULT:**

Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Vivado 2023.2


