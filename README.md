EXP-3

Date:

                                 SIMULATION AND IMPLEMENTATION OF MULTIPLIER
AIM: 
 To simulate and synthesis multiplier using STEP:1 Launch the Vivado 2023.2. 

APPARATUS REQUIRED:

VIVADO 2023.2
  
PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

Logic Diagram
2 bit Multiplier

![301736574-7713750f-65e6-41c0-8082-5005eac4031c](https://github.com/Naradinakar/VLSI-LAB-EXP-3/assets/161109578/e7144aed-447b-4f6d-9c44-65d7b8625bae)


Verilog code
```
module ha(a,b,sum,c);
input a,b;
output sum,c;
xor g1(sum,a,b);
and g2(c,a,b);
endmodule
module bitmultiplier(a,b,c);
input [1:0]a,b;
output[3:0]c;
wire w1;
and g1(c[0],b[0],a[0]);
ha ha1(a[0]&b[1],a[1]&b[0],c[1],w1);
ha ha2(a[1] &b[1],w1,c[2],c[3]);
endmodule
```

Output

![328595208-e08ffd69-3dc5-432b-960f-05d8def8b7d1](https://github.com/Naradinakar/VLSI-LAB-EXP-3/assets/161109578/b0fda2b4-62f2-4889-863f-d0006466861c)



Logic Diagram
2 bit Multiplier

![328595392-8381c0eb-8694-43d1-a56d-ce2c8b813adc](https://github.com/Naradinakar/VLSI-LAB-EXP-3/assets/161109578/a2b48755-14f6-40bb-a90d-2b9236ab0002)



Verilog code
```
module ha(a,b,c,s);
input a,b;
output s,c;
xor g1(s,a,b);
and g2(c,a,b);
endmodule
module fa(a,b,c,s,carry);
input a,b,c;
output s,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(s,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
module bitmultiplier(x,y,z);
input[3:0]x,y;
output[7:0]z;
wire [17:1]w;
and g1(z[0],x[0],y[0]);
ha ha1(x[1]&y[0],x[0]&y[1],z[1],w[1]);
fa fa1(x[2]&y[0],x[1]&y[1],w[1],w[5],w[2]);
fa fa2(x[3]&y[0],x[2]&y[1],w[2],w[6],w[3]);
ha ha2(x[3]&y[1],w[3],w[7],w[4]);
ha ha3(w[5],x[0]&y[2],z[2],w[8]);
fa fa3(w[6],x[1]&y[2],w[8],w[12],w[9]);
fa fa4(w[7],x[2]&y[2],w[9],w[13],w[10]);
fa fa5(w[4],x[3]&y[2],w[10],w[14],w[11]);
ha ha4(w[12],x[0]&y[3],z[3],w[15]);
fa fa6(w[13],x[1]&y[3],w[15],z[4],w[16]);
fa fa7(w[14],x[2]&y[3],w[16],z[5],w[17]);
fa fa8(w[11],x[3]&y[3],w[17],z[6],z[7]);
endmodule
Output Waveform
```
OUTPUT

![323645333-12637e2a-c11f-4143-a475-e45bb29443a6](https://github.com/Naradinakar/VLSI-LAB-EXP-3/assets/161109578/d49e8c32-e18c-4f66-8bc8-85d74d36fe43)




Result:
       Hence the 2 bit multiplier and 4 bit multiplier are simulated and synthesised using Vivado 2023.2.



