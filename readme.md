**Contents:**

i)   [Day_0 : System/Tool Setup Check & GitHub ID creation](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#day_0)\
ii)  [Day_1 : Introduction to RTL verilog design and analysis](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#day_1)\
iii) [Day_2 : Timing libs, hierarchical vs flat synthesis and efficient flop coding styles](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#day_2)
 
### Day_0

**_Quick notes_**

chip --package

wirebond - solid phase welding process, where two metallic materials (wire and pad surface) are brought into intimate contact

design present inside the chip very small- 5nm/7nm
io pads - connect core( all gates, logic gates and all) (inside world) to outside world
io pads - a very huge domain
	- needs to be protected -from charges in not damaging the core  - esd


Core

ADC- Analog to convert to digital signal

only allow low frequencies signal to pass into the core

Foundry IP- high value 
if the (soc)design inside the core need higher frequency than can provide by the outside
eg: have a booster to boost the frequency - provided 50 MHz then needed 100Mhz
every foundry gives you different transistor 

Macros
-eg: rtl 
-prety easy code

CBB - custom building block

Snapshot\
![Note1](https://user-images.githubusercontent.com/118953929/205479029-dcfa21b3-52b0-4e38-a6e2-327f2d1de574.png)
![Notes2](https://user-images.githubusercontent.com/118953929/205479032-fcff4233-6313-4fe5-ab9d-5338e53bbb1f.png)


_**Lab:**_ \
![day-0](https://user-images.githubusercontent.com/118953929/205479043-0a05819e-ed14-4521-a34f-8da892d44c67.jpg)

### Day_1

_**Quick notes & Lecture Session**_

Part_1\
**Introduction to iverilog design test bench**

_Simulator_
- is a tool to check the design
	-iverilog - a compiler that translates Verilog source code into executable programs  

_Design_
- is the verilog codes that has the intended functionality to meet with required specification

_TestBench_
- is a setup tool to apply stimulus (to check whether the design is obey/align to required specifications) - by observing the outputs

**NOTES: testbench doesn't have a primary inputs/outputs, while Design may have one or more primary inputs/outputs

_**Lab_1:**_ 


i) Creating VLSI directory, do git clone [enter this full link path](https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop) to setup the lab with files. ( Make sure be in VLSI directory )
![lab1_1](https://user-images.githubusercontent.com/118953929/205483354-1448f2fa-a5f2-45ee-9b8b-e91e0249bc07.jpg)

ii) Checked if the git clone is cloning correctly. 
- made sure all the files stated is in the path directory, respectively.
![lab1_2](https://user-images.githubusercontent.com/118953929/205483355-a7722db1-d7f5-494a-80d4-1b6d640bf42d.jpg)
![lab1_3](https://user-images.githubusercontent.com/118953929/205483357-a4652328-69df-435b-87f0-2835cd645a55.jpg)
![lab1_4](https://user-images.githubusercontent.com/118953929/205483347-af26c122-cecf-4859-829b-3fdf39d6a439.jpg)

**in verilog_files, make sure all the verilog files, comes along with tb (testbench) files, respectively. 
Eg: rcs.v and tb_rca.v

**_Lab_2:_**

i) Load iverilog: do _iverilog good_mux.v tb_good_mux.v_ , 
After loaded, a.out file will be generated. Next, execute the a.out: do _./a.out_
Then, will see a _tb_good_mux.vcd_ file being generated
![lab2_1](https://user-images.githubusercontent.com/118953929/205483348-058652de-ccd4-49fc-ba64-14e0232c9937.jpg)

ii) Launch waveform: do gtkwave tb_good_mux.vcd
Observe the waveform pattern. 
![lab2_2](https://user-images.githubusercontent.com/118953929/205484160-e89c70db-3f5e-4741-872f-116be7ffa5e1.jpg)

iii) Design verilog code and the testbench of the verilog
![lab2_3](https://user-images.githubusercontent.com/118953929/205483351-457c63d4-79e2-468f-81e8-3eac230105df.jpg)
![lab2_4](https://user-images.githubusercontent.com/118953929/205483352-e18dcbec-a049-4c66-8ee6-879c6692b518.jpg)


Part_2\
**Introduction to yosys**

_Synthesizer_
- tool used to convert RTL to netlist, while _yosys_ is the synthesizer

_Yosys setup_
![day1_2_n1](https://user-images.githubusercontent.com/118953929/205484828-c5ea45ae-67f2-4cd4-9d23-f77894bf9747.jpeg)

How to verify the synthesis?
![day1_2_n2](https://user-images.githubusercontent.com/118953929/205484946-4d833972-1931-40ad-943a-95f80b379670.jpg)

Logic synthesis
- RTL Design
	-behavioral representation of the required spec
What is synthesis?
- RTL to gate level translation

What is .lib?
- Collection of logical modules, inc basic logic gates 

Why do need different flavours of gate?
- Combinational delay in logic path which determines the max speed of operation of the digital logic circuit

Tclk > TcQ_A + Tcombi + T setup_B

**we need cells that works fast to meet the required performance, and need cells that works slow to meet HOLD

_Faster cells vs Slower cells_

Faster the charging --> lesser the cell delay
**Propagation delay here is , the time for the input to be fill up the output. 

Transistors - charge/discharge the capacitance fast.
Wider transistors -> low delay (more area and power)
Narrow transistors -> More delay (less area and power)

**_Labs:_**

i) invoking yosys: terminal >_yosys_

![day1_2_lab1_1](https://user-images.githubusercontent.com/118953929/205486805-7e6d67cb-4ce7-43ae-aff2-03e9b553ea26.jpg)

ii) read the library file from my_lib/lib/sky*.lib

![day1_2_lab1_2](https://user-images.githubusercontent.com/118953929/205486804-35069d18-56b8-4370-a3b6-a4d8e7027de1.jpg)

iii) Read design --> read_verilog

![day1_2_lab1_3](https://user-images.githubusercontent.com/118953929/205486803-4d05e8bc-45a7-4145-8f0e-a1e4aa492351.jpg)

iv) to link, what is the module we are going to do synthesis: terminal > synth -top

![day1_2_lab1_4](https://user-images.githubusercontent.com/118953929/205486802-00587b9b-a30e-44f8-ab28-d691bde694a6.jpg)
![day1_2_lab1_5](https://user-images.githubusercontent.com/118953929/205486801-7a2c8b5a-09b7-4f4e-81fb-42472dfe7573.jpg)

v) command to generate the netlist ( convert the rtl file into a gate , and what gate will be link to): terminal > abc -liberty 

![day1_2_lab1_6](https://user-images.githubusercontent.com/118953929/205486800-399d8000-3ada-4e2b-b934-23f3c5e0417d.jpg)
![day1_2_lab1_7](https://user-images.githubusercontent.com/118953929/205486799-fff2516b-62fb-4d88-a454-f6165c4bee43.jpg)

vi) write the netlist --> do write _verilog_

![day1_2_lab3_1](https://user-images.githubusercontent.com/118953929/205486796-8612b623-8610-4387-84cd-0b59c0830303.jpg)
![day1_2_lab3_2](https://user-images.githubusercontent.com/118953929/205486795-2e749e0d-83f7-4802-b53c-5a89dc7909b2.jpg)

Simplifying:
![day1_2_lab3_3](https://user-images.githubusercontent.com/118953929/205486794-76e68f97-3790-448c-b511-3a11c30b517f.jpg)
![day1_2_lab3_4](https://user-images.githubusercontent.com/118953929/205486793-aaf9ccda-eb3a-47a8-ad57-802b23199490.jpg)

### Day_2

_**Lecture and notes**_

**_Labs:_**

_Lab 4: Introduction to dot lib _


