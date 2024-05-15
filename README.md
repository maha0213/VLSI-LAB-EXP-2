# EXP NO 2

# Date:27/02/2024

# SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS

# AIM:
To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using vivado.

# APPARATUS REQUIRED:
vivado 2023.2.

# PROCEDURE: 
Open Vivado: Launch Xilinx Vivado software on your computer.

Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.
# LOGIC DIAGRAM

# ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)

VERILOG CODE

module encoder(a,y);
input [7:0]a;
output[2:0]y;
or(y[2],a[6],a[5],a[4],a[3]);
or(y[1],a[6],a[5],a[2],a[1]);
or(y[0],a[6],a[4],a[2],a[0]);
endmodule

# Output

![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/5a39f9ca-36e1-4b31-92a4-cf4bb035bc0b)



# DECODER
![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/cc3c9bcd-4f0b-4b88-b040-c4ad82f7c80c)

VERILOG CODE

module decoder1(a,y);
input [2:0]a;
output[7:0]y;
and(y[0],~a[2],~a[1],~a[0]);
and(y[1],~a[2],~a[1],a[0]);
and(y[2],~a[2],a[1],~a[0]);
and(y[3],~a[2],a[1],a[0]);
and(y[4],a[2],~a[1],~a[0]);
and(y[5],a[2],~a[1],a[0]);
and(y[6],a[2],a[1],~a[0]);
and(y[7],a[2],a[1],a[0]);
endmodule

 # Output 
 ![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/c4491a16-5832-4299-8fdb-44ad01bc0120)



# MULTIPLEXER
![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/37937914-f933-4538-9d0b-adc01b36e085)

VERILOG CODE

module mux(s,c,a);
input [2:0]s;
input [7:0]a;
wire [7:0]w;
output c;
and(w[0],a[0],~s[2],~s[1],~s[0]);
and(w[1],a[1],~s[2],~s[1],s[0]);
and(w[2],a[2],~s[2],s[1],~s[0]);
and(w[3],a[3],~s[2],s[1],s[0]);
and(w[4],a[4],s[2],~s[1],~s[0]);
and(w[5],a[5],s[2],~s[1],s[0]);
and(w[6],a[6],s[2],s[1],~s[0]);
and(w[7],a[7],s[2],s[1],s[0]);
or (c,w[0],w[1],w[2],w[3],w[4],w[5],w[6],w[7]);
endmodule

# Output

![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/90d9199f-2cc8-4dd7-a238-469187e829eb)

# DEMULTIPLEXER

![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/51935b6c-eecb-451f-9650-3c87cdb7987a)

VERILOG CODE

module demux_8(s,a,y);
input [2:0]s;
input a;
output [7:0]y;
and(y[0],a,~s[2],~s[1],~s[0]);
and(y[1],a,~s[2],~s[1],s[0]);
and(y[2],a,~s[2],s[1],~s[0]);
and(y[3],a,~s[2],s[1],s[0]);
and(y[4],a,s[2],~s[1],~s[0]);
and(y[5],a,s[2],~s[1],s[0]);
and(y[6],a,s[2],s[1],~s[0]);
and(y[7],a,s[2],s[1],s[0]);
endmodule

OUTPUT
![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/ad0d9fad-8767-470b-94c7-e97da6f00691)



# MAGNITUDE COMPARATOR

![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/fa5445fe-d7bb-4ff5-a95c-dc3ad0dc1bee)

VERILOG CODE

module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
 begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule

OUTPUT

![image](https://github.com/maha0213/VLSI-LAB-EXP-2/assets/159602131/7ded52ea-0d47-4879-b89c-567d9e35b1da)

# RESULT:
Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed





