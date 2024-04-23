![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/32a31fb1-0b28-4f4e-8a20-0f89f8a315e1)![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/946c6f19-9cd0-4788-b3bb-dd89ecd9d4c0)SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS
# AIM:
To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using vivado.

# APPARATUS REQUIRED:
vivado 2023.2.
# LOGIC DIAGRAM

# ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


# DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


# MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


# DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


# MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
# PROCEDURE:
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table

# VERILOG CODE
# 8-3 ENCODER:
module encoder(d,a,b,c);

input [7:0]d; output a,b,c;

or (a,d[4],d[5],d[6],d[7]);

or (b,d[2],d[3],d[6],d[7]);

or (c,d[1],d[3],d[5],d[7]);

endmodule

# 3-8 DECODER:
module decoder(A,E,Y);

input [1:0]A;

input E;

output [3:0]Y;

assign Y[0]=~A[1]&~A[0]&E;

assign Y[1]=~A[1]&A[0]&E;

assign Y[2]=A[1]&~A[0]&E;

assign Y[3]=A[1]&A[0]&E;

endmodule

module decoder(A,Y);

input[2:0]A;

output[7:0]Y;

decoder_2_4 d1(A[1:0],~A[2],Y[3:0]);

decoder_2_4 d2(A[1:0],~A[2],Y[7:4]);

endmodule

# 8-1 MULTIPLEXER:
module multi(i,s,y);

input[7:0]i;

input[2:0]s;

output reg y;

always@(*)

begin

case({s[2],s[1],s[0]})

3'b000:y=i[0];

3'b001:y=i[1];

3'b010:y=i[2];

3'b011:y=i[3];

3'b100:y=i[4];

3'b101:y=i[5];

3'b110:y=i[6];

3'b111:y=i[7];

endcase

end

endmodule

# 1-8 DEMULTIPLEXER:
module demultiplexer(d1,d2,d3,d4,d5,d6,d7,d8,i,s0,s1,s2);

input i,s0,s1,s2;

output d1,d2,d3,d4,d5,d6,d7,d8;

wire w1,w2,w3;

not g1(w1,s0);

not g2(w2,s1);

not g3(w3,s2);

and g4(d1,w1,w2,w3,i);

and g5(d2,w1,w2,s2,i);

and g6(d3,w1,s1,w3,i);

and g7(d4,w1,s1,s2,i);

and g8(d5,s0,w2,w3,i);

and g9(d6,s0,w2,s2,i);

and g10(d7,s0,s1,w3,i);

and g11(d8,s0,s1,s2,i);

endmodule

# 2 BIT MAGNITUDE COMPARATOR :
module mag_com(a,b,gt,it,eq);

input [3:0]a,b;

output reg gt,it,eq;

always @(a,b)

begin

if(a>b)

begin

gt = 1'b1;

it = 1'b0;

eq = 1'b0;

end

else if(a<b)

begin

gt = 1'b0;

it = 1'b1;

eq = 1'b0;

end

else

begin

gt = 1'b0;

it = 1'b0;

eq = 1'b1;

end

end

endmodule

OUTPUT WAVEFORM
 # ENCODER:
 ![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/b125766a-9786-41c3-943e-1b04f32388ce)
 # DECODER:
 ![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/9ac8d2e8-9828-4d74-8a9a-2c12bbb98a26)
# MULTIPLEXER:
![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/cf94d652-473d-42be-b452-642b7dcc117d)
# DEMULTIPLEXER:
![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/bf5fab46-7ea5-437f-bd1a-65e0a010d541)
# 2 BIT MAGNITUDE COMPARATOR:
![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/392bfe5e-d003-45c1-bc37-c789f2e360db)

# RESULT:
Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.





