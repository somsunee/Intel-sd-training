**Contents:**

i)  [Day_0 : System/Tool Setup Check & GitHub ID creation](https://github.com/somsunee/Intel-sd-training/edit/main/readme.md#day_0)\
ii) [Day_1 : Introduction to RTL verilog design and analysis](https://github.com/somsunee/Intel-sd-training/edit/main/readme.md#day_1)
 
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

Part_1 

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


Part_2 

Synthesizer
