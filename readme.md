
**Contents:**

- [Day 0 : System/Tool Setup Check & GitHub ID creation](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_0)
- [Day 1 : Introduction to RTL verilog design and analysis](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_1)
- [Day 2 : Timing libs, hierarchical vs flat synthesis and efficient flop coding styles](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_2)
- [Day 3 : Combinational and sequential optimizations](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_3)
- [Day 4 : GLS,blocking vs non-blocking and synthesis-simulation mismtach](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_4)
- [Day 5 : DFT](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_5)
- [Day 6 : Introduction to Logic Synthesis](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_6)
- [Day 7 : Basic of STA](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_7)
- [Day 8 : Advanced Constraints](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_8)
- [Day 9 : Optimization](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_9)
- [Day 10 : QOR](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_10)
- [Day 11 : Introduction to BabySoC](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_11)
- [Day 12 : BabySoC Modelling](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_12)
- [Day 13 : Post-synthesis simulation](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_13)
- [Day 14 : Synopsys DC and timing analysis](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_14)
- [Day 15 : Inception of EDA and PDK](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_15)
- [Day 16 : Good Floorplan vs Bad Floorplan and Introduction to library cells](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_16)
- [Day 17 : Design library cell using Magic layout and ngspice characterization](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_17)
- [Day 18 : Pre-layout timing analysis and importance of good clock tree](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_18)
- [Day 19 : Final steps for RTL2GDS](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_19)
- [Day 20 : Floorplanning and power planning labs](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_20)
- [Day 21 : Placement and CTS](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_21)
- [Day 22 : CTS Analysis labs](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_22)
- [Day 23 : Clock gating techniqueS](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_23)
- [Day 24 : Timing Violations and ECO](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_24)
- [Day 25 : RISC-V core RTL2GDS flow](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_25)
- [Day 26 : Introduction to mixed-signal flow](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_26)
- [Day 27 : Introduction to crosstalk -Glitch and delta delay](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_27)
- [Day 28 : Introduction to DRC/LVS](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_28)


# &#x1F537; Day_0


<details><summary><b>Lecture Notes</b></summary>
	
chip --package

wirebond - solid phase welding process, where two metallic materials (wire and pad surface) are brought into intimate contact

design present inside the chip very small- 5nm/7nm
io pads - connect core( all gates, logic gates and all) (inside world) to outside world
io pads - a very huge domain
	- needs to be protected -from charges in not damaging the core  - esd


$\Large{Core}$

ADC- Analog to convert to digital signal

only allow low frequencies signal to pass into the core

Foundry IP- high value 
if the (soc)design inside the core need higher frequency than can provide by the outside
eg: have a booster to boost the frequency - provided 50 MHz then needed 100Mhz
every foundry gives you different transistor 

$\Large{Macro}$
	
-eg: rtl 
-prety easy code

$\Large{CBB}$
- stands for custom building block

Snapshot\
![Note1](https://user-images.githubusercontent.com/118953929/205479029-dcfa21b3-52b0-4e38-a6e2-327f2d1de574.png)
![Notes2](https://user-images.githubusercontent.com/118953929/205479032-fcff4233-6313-4fe5-ab9d-5338e53bbb1f.png)


</details>

<details><summary><b>Labs</b></summary>

_**Lab:**_ \
![day-0](https://user-images.githubusercontent.com/118953929/205479043-0a05819e-ed14-4521-a34f-8da892d44c67.jpg)

</details>
	
# &#x1F537; Day_1

<details><summary><b>Lecture Notes</s></summary>

Part_1\
**Introduction to iverilog design test bench**

$\Large{Simulator}$
- is a tool to check the design
	-iverilog - a compiler that translates Verilog source code into executable programs  

$\Large{Design}$
- is the verilog codes that has the intended functionality to meet with required specification

$\Large{TestBench}$
- is a setup tool to apply stimulus (to check whether the design is obey/align to required specifications) - by observing the outputs

**NOTES: testbench doesn't have a primary inputs/outputs, while Design may have one or more primary inputs/outputs
	

Part_2\
**Introduction to yosys**

$\Large{Synthesizer}$
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

</details>

<details><summary><b>Labs</b></summary>	

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

</details>
	
# &#x1F537; Day_2

<details><summary><b>Lecture Notes</s></summary>
	
	

$\Large{CMOS - complementary metal-oxide-semiconductor}$
- has enabled massive scaling in a variety of semiconductor devices. Combining the CMOS process with VLSI has helped push packages to smaller levels while keeping costs reasonable

$\Large{Flops}$
-Propagation delay - the time required for the input to be propagated to the output

$\Large{Glitch}$
A glitch can be an issue if it propagates to the resultant logic or gets captured by a flip-flop. There can be two cases here:
**Synchronous timing paths:** (even has glitch) it will be within the limits of minimum and maximum delays permissible from one flip-flop to another
**Asynchronous timing paths:** if there is a glitch in the data path, it can get captured, hence, can cause issue. To prevent this, synchronizers are used and there are certain rules to be followed for asynchronous paths. 
![Screenshot 2022-12-07 201315](https://user-images.githubusercontent.com/118953929/206177613-9c92c340-9dd3-48f5-89bf-469067c00b85.jpg)

</details>

<details><summary><b>Labs</b></summary>

**_Labs:_**

_Lab 4:Introduction to dot lib_ 

a)
i) Open up sky*.lib file from lib 
![day2_lab4_1](https://user-images.githubusercontent.com/118953929/206072693-479941d2-ef25-4fb5-93ab-661817051570.jpg)
ii) Observe and understand the lib file.
- tt - typical
- 025C - tempertature\
***3 important things inside library, for the design to work\
$\Large{PVT}$
Process - variation due to fabrication\
Voltage\
Temperature

![day2_lab4_2](https://user-images.githubusercontent.com/118953929/206072690-9294af66-a21f-49ea-a8fc-4b2cc89ae32d.jpg)
![day2_lab4_3](https://user-images.githubusercontent.com/118953929/206072689-c8dc990e-9483-47a5-b6e0-6f96551ba3ca.jpg)

iii) Inside .lib, there will be a bucket of cells. Observe below:
![day2_lab4_5](https://user-images.githubusercontent.com/118953929/206072688-17e07a26-f5b9-49f4-a890-486905d7f843.jpg)
![day2_lab4_6](https://user-images.githubusercontent.com/118953929/206072685-5f2e27d9-8153-4e0c-81f6-38179ee0e5ae.jpg)
![day2_lab4_7](https://user-images.githubusercontent.com/118953929/206072678-59662277-664d-4f2b-b81e-cbe9ab0534ff.jpg)
Below you can see, as the area is wider, the power consume also higher.
![day2_lab4_8](https://user-images.githubusercontent.com/118953929/206072695-15e657b1-bf42-4f32-8c0d-7c7357c7038e.jpg)

_Lab5: Hierarchical vs Flat synthesis_

i) Invoke yosys, and read the lib file with the command as below:
![day2_lab5_1](https://user-images.githubusercontent.com/118953929/206074907-d5102e67-2230-4c7f-b637-30169d63b05c.jpg)

ii) View the multiple_modules.v file, there is a simple verilog code on the module. Observe and try to understand it by drawing out the circuit.
![day2_lab5_1_1](https://user-images.githubusercontent.com/118953929/206074905-389eb76e-39f6-4f23-b8fa-65591de827c2.jpg)

iii) do synth -top multiple_modules
![day2_lab5_2](https://user-images.githubusercontent.com/118953929/206074899-0aa1ab2f-109d-455e-bb4d-aa909b46fc86.jpg)
Observe, see if it matches how the module supposed to be ( multiple_modules.v )
![day2_lab5_3](https://user-images.githubusercontent.com/118953929/206074897-5fc2fb33-97a1-4269-8dee-93b5993d234a.jpg)
![day2_lab5_4](https://user-images.githubusercontent.com/118953929/206074894-634f758d-d905-425a-a183-4c857fa373a7.jpg)
![day2_lab5_5](https://user-images.githubusercontent.com/118953929/206074890-02abee98-f60e-487e-85a7-8bc82b6e4438.jpg)

iv) Show and observe the hierarchical design as below:
![day2_lab5_6](https://user-images.githubusercontent.com/118953929/206074918-c7c58973-9d94-4e71-a218-2ccc838250ea.jpg)

v) write_verilog multiple_modules.v and vim to view the code:
![day2_lab5_7](https://user-images.githubusercontent.com/118953929/206074916-e2e7c041-4d71-4300-99f2-1691b220fe30.jpg)

The full code for multiple_modules: ![View here](https://github.com/somsunee/Intel-sd-training/blob/main/multiple_modules)

vi) write_verilog -noattr multiple_modules.v for a simplifier code and vim to view it:

The full code for simplified multiple_modules: ![View here](https://github.com/somsunee/Intel-sd-training/blob/main/multiple_modules_simplified)

![day2_lab5_9_2](https://user-images.githubusercontent.com/118953929/206074913-62e200f5-5178-4830-86d8-63419b139aa9.jpg)

vii) flatten the design and write_verilog the flatten design to see the result:
![day2_lab5 2__1](https://user-images.githubusercontent.com/118953929/206177605-a595e5e6-6a92-4c08-80cc-52f16ba42011.jpg)
![day2_lab5 2__2](https://user-images.githubusercontent.com/118953929/206177508-cb9ce9f7-6d87-49ec-98c9-f80c968a834b.jpg)
![day2_lab5 2__3](https://user-images.githubusercontent.com/118953929/206177503-49730d6a-c4e1-4c51-9453-59018c6d083d.jpg)

View the simplified version of the flatten design:

![day2_lab5 2__4](https://user-images.githubusercontent.com/118953929/206177502-35fb4b37-1fe7-4f17-9a05-6eb630466f10.jpg)
![day2_lab5 2__5](https://user-images.githubusercontent.com/118953929/206177493-c3104bca-4c40-414a-90bf-28ae88bbe65c.jpg)

Show the design:

![day2_lab5 2__6](https://user-images.githubusercontent.com/118953929/206177490-cb8912d9-b7a3-4d35-b2e9-1599ba2580f2.jpg)

Repeat again the steps to read the lib and design, but dor submodule1:
![day2_lab5 2__7](https://user-images.githubusercontent.com/118953929/206177486-789813bd-cb34-43bf-ab32-a9dd5d2b1662.jpg)

***no more seeing hierarchy - only one single netlist
- no more submodule seeing

![day2_lab5 2__8](https://user-images.githubusercontent.com/118953929/206177480-3896b78a-03fb-44c7-9fe4-61d2ac72489d.jpg)
![day2_lab5 2__9](https://user-images.githubusercontent.com/118953929/206177461-4a09cb1a-4295-42c3-a450-4a30d196f929.jpg)

b)

![1](https://user-images.githubusercontent.com/118953929/206195575-3ba38c3f-0399-4981-bbdf-03710ecb6e1d.jpg)

![2](https://user-images.githubusercontent.com/118953929/206195570-d50b5ade-a993-4a77-a226-77de97b9af8b.jpg)

![3](https://user-images.githubusercontent.com/118953929/206195569-c874fe96-f4e0-4ec4-9593-e561c42c60c0.jpg)

![4](https://user-images.githubusercontent.com/118953929/206195564-9737308d-c5b1-4f7c-82ca-19af4e47bcaf.jpg)

![5](https://user-images.githubusercontent.com/118953929/206195561-c521e667-7bce-4153-985a-73c07411a359.jpg)

![6](https://user-images.githubusercontent.com/118953929/206195555-001a3145-c194-4a30-a8b9-602dffde790d.jpg)

![7](https://user-images.githubusercontent.com/118953929/206195548-ab7db8ae-31b6-436c-8680-a03859d8d99c.jpg)

![8](https://user-images.githubusercontent.com/118953929/206195545-c41a6914-5d14-45fc-ae19-8bae93d6b343.jpg)

![9](https://user-images.githubusercontent.com/118953929/206195542-5909d47b-6fd7-458a-bb31-dfca7577678d.jpg)

![10](https://user-images.githubusercontent.com/118953929/206195539-6d49e227-2b62-49b1-8e61-d33235742a37.jpg)
![11](https://user-images.githubusercontent.com/118953929/206195536-ceaf3c74-e82b-41ae-8af7-676059850bda.jpg)

do synth -top dff_async_set
![12_synth -top dff_async_set](https://user-images.githubusercontent.com/118953929/206195534-e7d45459-9302-4f3f-a914-9a02c3f8de64.jpg)

![13](https://user-images.githubusercontent.com/118953929/206195531-e982791c-4c11-40af-99b6-52c6c5fcd1a7.jpg)

![14](https://user-images.githubusercontent.com/118953929/206195525-86ae299d-ebb3-4c59-adcf-7ae6fecd6f82.jpg)

![15](https://user-images.githubusercontent.com/118953929/206195518-0e02e25e-258d-49c0-a464-2a23d095d0ed.jpg)

![16](https://user-images.githubusercontent.com/118953929/206195513-c130bbf2-1dd1-4097-ac48-75f6016b4dc8.jpg)

![17](https://user-images.githubusercontent.com/118953929/206195509-8ef5eddc-ad0b-46fa-98be-c96f0a34a5fa.jpg)
As can see, no cells is getting map during synthesis

![18](https://user-images.githubusercontent.com/118953929/206195498-73e34384-8fe6-47c4-ad0a-f96118463c10.jpg)
![19](https://user-images.githubusercontent.com/118953929/206198789-fa85ae76-bbef-4406-bb62-bf6d76ec0d54.jpg)
![20](https://user-images.githubusercontent.com/118953929/206198783-aa7c9318-02a6-4479-9b55-656a02994a5b.jpg)
![21](https://user-images.githubusercontent.com/118953929/206198780-115a0060-29c8-4f6b-8715-c2df955ad0c1.jpg)
![22](https://user-images.githubusercontent.com/118953929/206198777-636ac5f4-c732-4f8f-92a1-3ae7c6e0c812.jpg)
![23](https://user-images.githubusercontent.com/118953929/206198796-a9909427-873b-4fed-99c7-1583413c029d.jpg)
![24](https://user-images.githubusercontent.com/118953929/206198794-8a5931df-d29c-4f87-a0fc-1727e80b6c84.jpg)
![25](https://user-images.githubusercontent.com/118953929/206198792-7303b4c3-686e-41fd-b0bd-09d84d295829.jpg)

</details>	

# &#x1F537; Day_3
	
	
<details><summary><b>Lecture Notes</s></summary>



_**Combinational Logic Optimization**_
- squeez the logic in order to get most optimised design ( in term of _area_ and _power_ )

**techniques used in combinational logic optimization
- _Constant Propagation_ - which is direct optimization
- _Boolean Logic Optimization_ - eg: KMap


**CONSTANT PROPAGATION**
Eg:
![photo1670590644](https://user-images.githubusercontent.com/118953929/206707796-e4d76742-cea1-47b7-98fc-1b2c79534ff9.jpeg)
![photo1670590644 (1)](https://user-images.githubusercontent.com/118953929/206707795-d327e207-4803-4611-a2b4-6e2397cbd6b2.jpeg)

**BOOLEAN LOGIC OPTIMIZATION**
![photo1670590644 (2)](https://user-images.githubusercontent.com/118953929/206707789-5d2a239e-d3c7-40a3-8eae-ecfa23c0fe09.jpeg)

**_Sequential Logic Optimizations_**

- Basic
	- Sequential Constant propagation
- Advanced 
	- State optimisation
	- Retiming
	- Sequential Logic Cloning(FloorPlan Aware Synthesis)
	


**SEQUENTIAL CONSTANT**

![photo1670590644 (3)](https://user-images.githubusercontent.com/118953929/206707788-c3a11f60-e003-4e6a-a66a-b1a2b0947df9.jpeg)
![photo1670590644 (4)](https://user-images.githubusercontent.com/118953929/206707783-005d1b87-bb49-41a6-8994-d9ec84d5448f.jpeg)


</details>

<details><summary><b>Labs</b></summary>
	
_**Labs:**_

**Lab 6: **

First, open verilog_files and make sure opt_check files are there, open up the opt_check files and observe the differences:
![photo1670592095](https://user-images.githubusercontent.com/118953929/206712325-f818f5d6-2708-4418-a03e-c842e509d7c9.jpeg)

Steps for\
i)opt_check.v

yosys\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog opt_check.v\
synth -top opt_check\
opt_clean -purge (command to run optimization)\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show (expecting and and gate here)

![1](https://user-images.githubusercontent.com/118953929/206885179-b7c87be7-eb31-4238-88ab-c5f8327bd9c6.jpg)
![2](https://user-images.githubusercontent.com/118953929/206885180-acb69671-d5e6-4524-9704-00adbc42e1d9.jpg)
![3](https://user-images.githubusercontent.com/118953929/206885182-75f4f4e2-a4d9-4f4b-ae69-3b68441c4e15.jpg)
![4](https://user-images.githubusercontent.com/118953929/206885183-dfb2d2f5-f80b-4b4e-beec-b97b936fa0de.jpg)
![5](https://user-images.githubusercontent.com/118953929/206885156-c564f749-28c3-4580-99f0-885ed7acf1cd.jpg)
![6](https://user-images.githubusercontent.com/118953929/206885157-d6c03a4a-280d-4e10-a403-995aea689f5f.jpg)
![7](https://user-images.githubusercontent.com/118953929/206885158-621f64f2-945c-48da-b405-bb4be4bca7ae.jpg)

ii)opt_check2.v

Repeating same steps:\
do for opt_check2\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog opt_check2.v\
synth -top opt_check2\
opt_clean -purge\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![8](https://user-images.githubusercontent.com/118953929/206885160-a55ae685-0afe-4066-8cf0-a78218f72abc.jpg)
![9](https://user-images.githubusercontent.com/118953929/206885161-33dc7de0-149b-4e92-ab1b-693bc4391c0d.jpg)


iii)opt_check3.v

do for opt_check3\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.libread_verilog\
read_verilog opt_check3.v\
synth -top opt_check3\
opt_clean -purge\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![10](https://user-images.githubusercontent.com/118953929/206885163-c2f49b6c-87fe-4e0e-93ab-492f1d0f45de.jpg)
![11](https://user-images.githubusercontent.com/118953929/206885164-626cb87c-e627-4a6c-b0d9-c836ee3390b6.jpg)
![12](https://user-images.githubusercontent.com/118953929/206885165-01edaf4b-5788-42a0-b000-ffdc495c57a2.jpg)

iv)opt_check4.v

do for opt_check4\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog opt_check4.v\
synth -top opt_check4\
opt_clean -purge\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![13](https://user-images.githubusercontent.com/118953929/206885166-9812cf63-3a71-4121-bd97-139e72a642e1.jpg)
![14](https://user-images.githubusercontent.com/118953929/206885167-abedf50f-36da-4924-972e-9491bc8ed0fa.jpg)
![15](https://user-images.githubusercontent.com/118953929/206885168-6da4c733-b160-4b75-89c8-5601fc63ba8f.jpg)
![16](https://user-images.githubusercontent.com/118953929/206885169-5c972ebd-3996-4551-9884-a4dbf396f17e.jpg)

v)multiple_module_opt.v\
**do flatten before do the optimization

Steps:

do for multiple_module_opt\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog multiple_module_opt.v\
synth -top multiple_module_opt\
flatten\
opt_clean -purge\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![17](https://user-images.githubusercontent.com/118953929/206885170-97de8254-987c-4f74-8ee1-aa09285efd8f.jpg)
![18](https://user-images.githubusercontent.com/118953929/206885172-199a62fb-48ae-46d9-b33a-32e3abf03398.jpg)
![19](https://user-images.githubusercontent.com/118953929/206885173-79eed031-7122-4f2e-a8d4-6ee63b8dc036.jpg)
![20](https://user-images.githubusercontent.com/118953929/206885174-8b75499b-2f70-4a9d-aeac-a3f8cdca7b8a.jpg)

vi)multiple_module_opt2.v\
**do flatten before do the optimization

Steps:
do for multiple_module_opt2\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog multiple_module_opt2.v\
synth -top multiple_module_opt2\
flatten\
opt_clean -purge\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![21](https://user-images.githubusercontent.com/118953929/206885175-4a6ee305-3988-4d5d-9ca7-d98b3e95303d.jpg)
![22](https://user-images.githubusercontent.com/118953929/206885176-335b9ee0-be24-4d26-994c-ad2c774b3470.jpg)
![23](https://user-images.githubusercontent.com/118953929/206885177-24ba600c-a14d-4680-a505-4465a462b5d0.jpg)
![24](https://user-images.githubusercontent.com/118953929/206885178-fe052566-7fa6-46aa-94b2-e28054f9a40a.jpg)


**Lab 7:**

gvim the dff_const file to observe the code and see how the pattern will be:

![photo1670730967](https://user-images.githubusercontent.com/118953929/206885608-d6caec17-a07f-41d1-a9d5-d0962ce8c276.jpeg)

view the waveform pattern and observe:

a)iverilog dff_const1.v tb_dff_const1.v\
./a.out\
gtkwave *.vcd 

![1](https://user-images.githubusercontent.com/118953929/206887032-0b6f5949-e66e-446f-935c-cc5438f92a96.jpg)
![2](https://user-images.githubusercontent.com/118953929/206887033-0c0ea095-04dc-4e63-921f-ce4ec33d7150.jpg)

do the same and observe for dff_const2.v:

b)iverilog dff_const2.v tb_dff_const2.v\
./a.out\
gtkwave *.vcd

![3](https://user-images.githubusercontent.com/118953929/206887036-8a59ed42-70ef-4e69-a99a-c6b9313a759b.jpg)
![4](https://user-images.githubusercontent.com/118953929/206887038-ad0a9f12-a223-498f-848d-96ebaabd8529.jpg)

Synthesis:

dff_const1.v

i)do for dff_const1.v\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog dff_const1.v\
synth -top dff_const1\
dfflibmap -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![5](https://user-images.githubusercontent.com/118953929/206887039-c49d633d-f4e4-4b7c-8d2d-8ab7016f2d2d.jpg)
![6](https://user-images.githubusercontent.com/118953929/206886993-f055661d-c1f9-492d-9dbf-c9f745b9c35b.jpg)
![7](https://user-images.githubusercontent.com/118953929/206886994-2746c220-5be7-4fbd-bd52-2b403e296fd9.jpg)
![8](https://user-images.githubusercontent.com/118953929/206886995-761c8ed2-f7b5-48df-ab21-15fa3ab00d9c.jpg)
![9](https://user-images.githubusercontent.com/118953929/206886996-c653e3fb-aeed-43c0-8a90-b0a1156c738c.jpg)

ii)do for dff_const2.v\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog dff_const2.v\
synth -top dff_const2\
dfflibmap -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib ( no need map again )\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![10](https://user-images.githubusercontent.com/118953929/206886997-7cbd56ee-44bd-4df8-931f-753d536f1c54.jpg)
![11](https://user-images.githubusercontent.com/118953929/206886999-aca76b1a-2c49-49ef-8f4e-8a789d65cb32.jpg)
![12](https://user-images.githubusercontent.com/118953929/206887000-c7092cc2-053c-494f-ad09-3394373fe2a7.jpg)


- gvim for dff_const3.v ,dff_const4.v, dff_const5.v
![13](https://user-images.githubusercontent.com/118953929/206887001-c15bb11c-9f2d-4f51-8866-fe8a501a6acc.jpg)

view the waveform pattern and observe:

c)iverilog dff_const3.v tb_dff_const3.v\
./a.out\
gtkwave *.vcd

![14](https://user-images.githubusercontent.com/118953929/206887002-7b2c4b2d-d044-43ce-b54a-ea515241c674.jpg)
![15](https://user-images.githubusercontent.com/118953929/206887004-87c0b5af-2912-4fa5-9577-21bb3fe1d8ba.jpg)

iii)dff_const3.v

do for dff_const3.v\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog dff_const3.v\
synth -top dff_const3\
dfflibmap -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![16](https://user-images.githubusercontent.com/118953929/206887007-67e86d60-75a1-4498-9f4e-bc1e6d97ee0c.jpg)
![17](https://user-images.githubusercontent.com/118953929/206887008-657db25b-263f-4c64-a424-bef3646e5aa9.jpg)
![18](https://user-images.githubusercontent.com/118953929/206887009-0ebf01fe-f371-4837-9914-441cbf693e35.jpg)
![19](https://user-images.githubusercontent.com/118953929/206887011-0969477c-77d3-4d14-b836-5830171cdd38.jpg)
![20](https://user-images.githubusercontent.com/118953929/206887012-9702bd21-7e16-47ca-8f4b-d9e58e87b96d.jpg)
![21](https://user-images.githubusercontent.com/118953929/206887014-1714c7a7-5251-4c82-8d1d-b04484f6080a.jpg)


d)view the waveform pattern and observe:

iverilog dff_const4.v tb_dff_const4.v\
./a.out\
gtkwave *.vcd 

![22](https://user-images.githubusercontent.com/118953929/206887016-fa50d266-5fb9-4f01-8cae-2388dbee9816.jpg)
![23](https://user-images.githubusercontent.com/118953929/206887021-9065fcd0-c2f9-4316-8267-41ea0bfe45a3.jpg)

iv)dff_const4.v

do for dff_const4.v\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog dff_const4.v\
synth -top dff_const4\
dfflibmap -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show


![23 1](https://user-images.githubusercontent.com/118953929/206887017-b7c69fcd-8b5b-44a1-a895-775c1701a51e.jpg)
![23 2](https://user-images.githubusercontent.com/118953929/206887018-572dfe52-622d-43d8-ab70-a838f081aa16.jpg)
![23 3](https://user-images.githubusercontent.com/118953929/206887020-3b65ccff-324c-4b80-9ca5-12a52a1dd649.jpg)


e)iverilog dff_const5.v tb_dff_const5.v\
./a.out\
gtkwave *.vcd

![24](https://user-images.githubusercontent.com/118953929/206887022-c1080e93-eb94-41bf-a821-8d22f62fae4a.jpg)
![25](https://user-images.githubusercontent.com/118953929/206887029-30a60475-f668-4ae9-9f8d-0db05df852c2.jpg)

v)dff_const5.v

do for dff_const5.v\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog dff_const5.v\
synth -top dff_const5\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![25 1](https://user-images.githubusercontent.com/118953929/206887024-c099ccfe-aa91-4d43-96ee-fb48bca61b98.jpg)
![25 2](https://user-images.githubusercontent.com/118953929/206887027-b4a8f9af-39d0-404a-926b-e87dbea169df.jpg)
![25 3](https://user-images.githubusercontent.com/118953929/206887028-1d258dd7-af69-456c-a022-0faf537b3f6f.jpg)


_**Seq Optimisation unused outputs**_

![photo1670735469](https://user-images.githubusercontent.com/118953929/206887612-c714c172-2fb4-44c1-ac4e-be3b6ef1b841.jpeg)

a)counter_opt.v

yosys\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog counter_opt.v\
synth -top counter_opt\
dfflibmap -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![1](https://user-images.githubusercontent.com/118953929/206888002-b5e881c6-de87-4f53-bfd9-7fba2da8e795.jpg)
![2](https://user-images.githubusercontent.com/118953929/206888004-ebbca002-d42a-41d4-9710-9e94de6f2f64.jpg)
![3](https://user-images.githubusercontent.com/118953929/206888005-6664888e-819b-4f1a-b7cb-622e09d47723.jpg)
![4](https://user-images.githubusercontent.com/118953929/206888007-c6ab221a-4b7d-4eea-8fe2-477e555a94c9.jpg)
![5](https://user-images.githubusercontent.com/118953929/206887992-de0e6335-4230-4333-a97f-c07f7758413a.jpg)

copy over counter_opt.v to counter_opt2.v and do the changes
![6](https://user-images.githubusercontent.com/118953929/206887993-27fb396b-e06a-49e9-bbd3-c29516d5e5d2.jpg)

b)counter_opt2.v

yosys\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog counter_opt2.v\
synth -top counter_opt\
dfflibmap -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
show

![7](https://user-images.githubusercontent.com/118953929/206887994-4ee2a3f5-032d-449f-8582-9653e5e4a981.jpg)
![8](https://user-images.githubusercontent.com/118953929/206887996-90d0bd2d-d88c-4bce-a66d-4772a0923a30.jpg)
![9](https://user-images.githubusercontent.com/118953929/206887997-ac53542c-54d2-4694-8f48-79a9dbdab0fe.jpg)
![10](https://user-images.githubusercontent.com/118953929/206887998-c76aa5e4-ce8f-43bc-a5dc-536faa1d4b3a.jpg)
![11](https://user-images.githubusercontent.com/118953929/206888000-bac922c0-302c-46e5-8c9c-6d4d34f8fbdf.jpg)

</details>

# &#x1F537; Day_4

<details><summary><b> Lecture notes </b></summary>
	

$\Large{\ WHAT\ IS \ GLS?}$
- GLS stands for (Gate Level Simulation) 
	- used to boost the confidence regarding implementation of a design and can help verify dynamic circuit behaviour, which cannot be verified accurately by static methods.
	- running test bench with netlist (same as RTL code) as DUT 

GLS using iVERILOG

![photo1670737566 (2)](https://user-images.githubusercontent.com/118953929/206888465-87726af8-afac-46c4-aa10-f5f71ebdd252.jpeg)
![photo1670737566 (1)](https://user-images.githubusercontent.com/118953929/206888466-d53a252e-bc0d-455a-a349-f043ab4b79f3.jpeg)

***why need to validate the functionality of the netlist?

_Synthesis Simulation Mismatch_

- missing sensivity list
- blocking vs non-blocking asssignments
- non standard verilog coding


**Missing Sensivity list**

![photo1670738375](https://user-images.githubusercontent.com/118953929/206888819-04036770-9559-44a3-b5c6-1dee24458e35.jpeg)

changes: do _always @(*)_

**snapshot from lecture's video:
![photo1670738503](https://user-images.githubusercontent.com/118953929/206888896-dce12271-d0d8-4530-966d-5952a0e06a24.jpeg)

_**Blocking vs Non-blocking statements in verilog**_

Inside the always block
- if the "=" is used to make assignments --> that is called blocking statements
	- it executes in the order is written
	- the first statement is evaluated before the second statement

- if the "<=" ---> non-blocking statements
	- it executes all the RHS when always block is entered and assigns to LHS
	- parallel evaluation ( order doesn't matter )

Caveats with Blocking Statements:

![photo1670741002](https://user-images.githubusercontent.com/118953929/206890178-58738b0b-b8b0-4f9d-8c71-60c4ab90b5d0.jpeg)

![photo1670741384](https://user-images.githubusercontent.com/118953929/206890323-c31013ce-7194-458f-ab93-765669edbce1.jpeg)

</details>

<details><summary><b> Labs </b></summary>


_Lab GLS Synth Sim Mismatch_


open up the ternary_operator_mux.v good_mux.v and bad_mux.v to observe the pattern
![1](https://user-images.githubusercontent.com/118953929/206893035-e4eba467-2bf3-4199-a4fd-addf686a9114.jpg)

a)

iverilog ternary_operator_mux.v tb_ternary_operator_mux.v\
./a.out\
gtkwave *.vcd

![2](https://user-images.githubusercontent.com/118953929/206893037-0ad0a85e-ece4-423b-9b66-9ac63f389a66.jpg)

Synthesis:
yosys\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog ternary_operator_mux.v\
synth -top ternary_operator_mux\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
write_verilog -noattr ternary_operator_mux_net.v\
show

![3](https://user-images.githubusercontent.com/118953929/206893007-63f908df-33ff-4a23-97a2-ceb240e5d485.jpg)
![4](https://user-images.githubusercontent.com/118953929/206893011-395f61e5-027b-4857-bd95-af6b8272f5c2.jpg)
![5](https://user-images.githubusercontent.com/118953929/206893012-1cf46118-d631-40dd-868d-30b95d9a805e.jpg)

Explaination details from lecture's video:
![6](https://user-images.githubusercontent.com/118953929/206893013-c244fe21-7fd5-49d1-9778-b283f6307e79.jpg)


iverilog ../my_lib/verilog_model/primitives.v iver../my_lib/verilog_models/sky*.v ternary_operator_mux.v tb_ternary_operator_mux.v\
./a.out\
gtkwave *.vcd

![7](https://user-images.githubusercontent.com/118953929/206893014-d69d857e-84b1-4c80-90d8-95933dd5b4ed.jpg)
![8](https://user-images.githubusercontent.com/118953929/206893016-e93f2ded-22e3-44b7-8059-8fd0ee8bf7cb.jpg)

b)

iverilog bad_mux.v tb_bad_mux.v\
./a.out\
gtkwave *.vcd


![9](https://user-images.githubusercontent.com/118953929/206893018-9419c03c-18dd-423a-b150-b18803a4e249.jpg)
![10](https://user-images.githubusercontent.com/118953929/206893020-70f1e4c5-40c2-456a-b401-f3ed005fc754.jpg)

Synthesis:

yosys\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog bad_mux.v\
synth -top bad_mux\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
write_verilog -noattr bad_mux.v\
show

![11](https://user-images.githubusercontent.com/118953929/206893021-b6afe7f0-74e1-4be8-9e7a-8002b7230b78.jpg)
![12](https://user-images.githubusercontent.com/118953929/206893022-0aa3837d-75ca-4b2d-8a9f-87c9a5a1f7b2.jpg)
![13](https://user-images.githubusercontent.com/118953929/206893023-d44e5316-8099-4116-8209-60ee025b110a.jpg)

iverilog ../my_lib/verilog_model/primitives.v iver../my_lib/verilog_models/sky*.v bad_mux.v tb_bad_mux.v\
./a.out\
gtkwave *.vcd

![14](https://user-images.githubusercontent.com/118953929/206893024-00d195cd-803e-444b-8b38-d116d6ff6a01.jpg)
![15](https://user-images.githubusercontent.com/118953929/206893025-e37edafe-57ae-43a3-820b-e8bdf2fc1c52.jpg)

_Lab Synth sim mismatch blocking statement_ 

gvim to view blocking_caveat.v

![16](https://user-images.githubusercontent.com/118953929/206893027-cb157a18-e4bc-4aaf-8902-da9287c9ccbc.jpg)


a)blocking_caveat.v


iverilog blocking_caveat.v tb_blocking_caveat.v\
./a.out\
gtkwave *.vcd

![17](https://user-images.githubusercontent.com/118953929/206893029-a1ab11f0-0e8b-4d6c-89df-b73825963214.jpg)
![18](https://user-images.githubusercontent.com/118953929/206893030-aa1bd20c-8fd7-49cf-8649-a81049055662.jpg)


yosys\
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
read_verilog blocking_caveat.v\
synth -top blocking_caveat\
abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib\
write_verilog -noattr blocking_caveat.v\
show

![19](https://user-images.githubusercontent.com/118953929/206893031-d0207c9b-2c8b-469a-86f8-e415f713522d.jpg)
![20](https://user-images.githubusercontent.com/118953929/206893032-a6433d53-04d7-4967-b904-b83fb9a2e850.jpg)
![21](https://user-images.githubusercontent.com/118953929/206893033-e18dd1cf-a2c9-441b-8c3b-afe508094c86.jpg)

iverilog ../my_lib/verilog_model/primitives.v iver../my_lib/verilog_models/sky*.v blocking_caveat.v tb_blocking_caveat.v\
./a.out\
gtkwave *.vcd


![22](https://user-images.githubusercontent.com/118953929/206893034-00440c6d-13a1-4723-8294-4400548cae78.jpg)

</details>

# &#x1F537; Day_5

<details><summary><b> Lecture notes </b></summary> 
	
	
$\Large{DFT}$

$\fbox{W H A T  is dft?}$	

- DFT stands for Design For Testability 
- is a innovative design technique which makes the testing the chip cost-effective by adding circuitry to the chip.
- it improves the $\mathcal{\textcolor{purple}{observability} \}$ and $\mathcal{\textcolor{purple}{controllability} \}$ of internal nodes to increase the testability of all logic in the chip
	
$\fbox{W H Y  do we need dft?}$

- it makes the testing easy at the post-production process.
- helps to thorough testing of chips and to avoid the chances of any faults.
- we have 3 levels after a chip is being fabricated:
	- **Chip-level**: DFT at this stage helps to test the overall shipped-product quality. To ensure the smooth working of the product, chips are thoroughly checked and tested.
	- **Board-level**: DFT at this stage helps to test the operational life of chips with a temperature test.
	- **System-level**: to ensure that the replaceable parts are working smoothly, the application of DFT is important here.
		
> __Note__  : DFT also done due to economical and market needs.
	
$\fbox{W H E R E  do we need dft?}$

- during the "Synthesis"
	
$\fbox{W H E N  do we need dft?}$

- at the beginning of design flow
	

**ASIC DDESIGN FLOW chart:**

![photo1671021186](https://user-images.githubusercontent.com/118953929/207596500-9440f83f-0b5f-4ed6-8c34-2c38f57f9f03.jpg)

**Pros and Cons of DFT:**
	
Pros | Cons |
--- | --- | 
Reduces tester complexity |adds complication to the design flow | 
Reduces tester time |increase power, area, timing and package pins | 
Reduces the chances of going into loss |increases design time | 
	

**Basic Termonologies:**
	
$\mathcal{\textcolor{purple}{CONTROLLABILITY:} \}$ ability to establish a specific signal value at each node in a circuit from setting values at the circuit’s inputs.

$\mathcal{\textcolor{purple}{OBSERVABILITY:} \}$: ability to determine the signal value at any node in a circuit by controlling the circuit’s inputs and observing its outputs.

Controllability:
Lets take an example for this:

Let's say there are a lot more Registers here, all has been fabricated and do not have time to change the whole design, what do we do? 
- Assume only one node that can be control and let others be black box only, by this way, we can easily contorl the only one node. 
- An ad-hoc technique to increase controllability is adding a test point- adding a signal that you can control externally.

![photo1671022514](https://user-images.githubusercontent.com/118953929/207601104-851bb170-d2cb-4b63-a077-225523555246.jpeg)

Observability:

What do we add to observe at the node 1 ? 
- by adding a flip flop (only observe without effecting the results/process)

![photo1671023466](https://user-images.githubusercontent.com/118953929/207604465-595531a3-3302-4b7a-93c9-09a1d7a8a512.jpeg)
> __Note__  : Scan Based design increases both controllability and observability. You are able to set internal states and observe internal states. 

$\mathcal{\textcolor{purple}{FAULT:} \}$ physical damage/defect

$\mathcal{\textcolor{purple}{ERROR:} \}$ error caused by a fault

$\mathcal{\textcolor{purple}{FAILURE:} \}$ when system not working 


**DFT Techniques:**
	
i) Ad-hoc technique
	
	- avoid combinational feedback
	- all flip flops must be initialize
	- partition a large circuit into small blocks.
	- provide test control for the signals which are not controllable
	- consider ATE requirements while designing test logic
	
ii) Structured technique
	
	- Scan flip flop
	- Boundary Scan
	- Built-in self-test 
	     - MBist ( Memory Built-in self test ) - macro
	     - LBist ( Logic Built-in self test )

	
MBIST vs LBIST:

Types | Advantages | Disadvantages |
--- | --- | --- |
MBIST |It allows for robust testing of memories, Reduced test time, All the memories of the design can be tested in parallel, Lesser test cost |causes increase in area |
LBIST | provides self-test capability to logic inside chip, provides the ability to be tested at higher frequencies reducing test time considerably, can run while the chip is on field running functionally | the cost of chip increases, causing impact on timing |

Figure shows the built-in self-test architecture ![Reference](https://www.sciencedirect.com/topics/computer-science/scan-chain)
![Screenshot 2022-12-15 193122](https://user-images.githubusercontent.com/118953929/207850112-5240f120-2256-412a-a90b-470873a00e69.jpg)



Scan-chain technique ( scan-chains)

- the elements in scan-based designs that are used in scan in/out the data
- A scan chain is formed by a number of flops connected back to back in a chain with the output of one flop connected to another
- The input of first flop is connected to the input pin of the chip (called scan-in) from where scan data is fed. 
- The output of the last flop is connected to the output pin of the chip (called scan-out) which is used to take the shifted data out. 

_Purpose of scan chains_: As said above, scan chains are inserted into designs to shift the test data into the chip and out of the chip. 

	**The figure below shows a scan chain.
![photo1671026029](https://user-images.githubusercontent.com/118953929/207613675-79c2b972-7cc1-4b3c-99f0-173982f64ad2.jpeg)


_Scan configuration:_
	
	- initial step in scan chain planning ( where the general structure of the scan design is determined )
	- main decisions that made during this stage is:
		(1) the number of scan chains used;
		(2) the types of scan cells used to implement these scan chains; 
		(3) storage elements to be excluded from the scan synthesis process; 
	        (4) the way the scan cells are arranged within the scan chains
	
	- The number of scan chains used is typically determined by analyzing the input and output pins of the circuit to determine how many pins can be allo-cated for the scan use.



_How normal flop is transformed into a scan flop?_
	
-The flops in the design have to be modified in order to be put in the scan chains. To do so, the normal input (D) of the flip-flop has to be multiplexed with the scan input. A signal called **scan-enable** is used to control which input will propagate to the output.

> __Note__  :
If scan-enable = 0, data at D pin of the flop will propagate to Q at the next active edge;
If scan-enable= 1, data present at scan-in input will propagate to Q at the next active edge

_Scan terminology:_
	
Scan-in: Input to the flop/scan-chain that is used to provide scan data into it\
Scan-out: Output from flop/scan-chain that provides the scanned data to the next flop/output\
Scan-enable: Input to the flop that controls whether scan_in data or functional data will propagate to output

_How a scan chain functions:_ 

	Steps:
	Assert scan_enable (make it high) so as to enable (SI -> Q) path for each flop
	Keep shifting in the scan data until the intended values at intended nodes are reached
	De-assert scan_enable (for one pulse of clock in case of stuck-at testing and two or more cycles in case of transition testing) to enable D->Q path so that the combinational cloud output can be captured at the next clock edge.
	Again assert scan_enable and shift out the data through scan_out

	
_How Chain length is decided?_
	
	Number of ports required = 2 X Number of scan chains

Since for each scan chain, scan_in and scan_out port is needed. Also,
	
	 Number of cycles required to run a pattern = Length of largest scan chain in design
	
> __Note__  : Scan-chain balancing is keeping almost equal number of flops in each scan chain	
	
 ![photo1671027130](https://user-images.githubusercontent.com/118953929/207618179-1b2f43f7-67a5-409b-9037-d0a7c09956ad.jpeg)
	
	- Scan chain operation involves three stages: Scan-in, Scan-capture and Scan-out. 
	- Scan-in involves shifting in and loading all the flip-flops with an input vector. 
	- During scan-in, the data flows from the output of one flop to the scan-input of the next flop not unlike a shift register. 
	- Once the sequence is loaded, one clock pulse (also called the capture pulse) is allowed to excite the combinatorial logic block and the output is captured at the second flop. 
	- The data is then shifted out and the signature is compared with the expected signature. Modern ATPG tools can use the captured sequence as the next input vector for the next shift-in cycle. Moreover, in case of any mismatch, they can point the nodes where one can possibly find any manufacturing fault.
	

	
Figure below shows the sequence events that takes place: ![Reference](https://anysilicon.com/overview-and-dynamics-of-scan-testing)
	
![photo1671101685](https://user-images.githubusercontent.com/118953929/207841630-1a4d24d6-0174-4ef9-94bf-f9091df43eb4.jpeg)


	
> __Conclusion__  :Insertion of scan chains in the design leads to additional cost in terms of area, speed, power, design- cycle, complexity. Scan chains are inserted to serially shift in the test patterns and serially shift out the test pattern responses.
	
	
**Basic ATE functionality**
	
-scan-in phase\
-parallel measure\
-parallel capture\
-first scan-out phase\
-scan-out Phase


How is ATE useful and beneficial ?

- if faults or defects are detected during testing, ATE helps to diagnose why.
- helps cut down testing time 
- saves money by digitizing and automating traditionallu manual testing equipment, procedures and processes
	
Benefits of ATE:\
	- reduce test and cycle time\
	- reduction or prevention of data input errors\
	- more efficient and effective use of available engineering resources\
	- faster and more accurate tests

Automatic Test Pattern Generation (ATPG)
- an electronic design automation (EDA) method used to find an input sequence which, when it applied to a digital circuit, it enables testers to distinguish between the correct circuit behavior and the faulty circuit behavior caused by defects. 

- The effectiveness of ATPG is measured by the amount of modeled defects, or fault models, that are detected and the number of generated patterns.

- influenced by the fault model under consideration, the type of circuit under test (combinational, synchronous sequential, or asynchronous sequential), the level of ab-straction used to represent the circuit under test (register, gate, transistor), and the required test quality

Basic ATPG flow ![Reference](https://reader.elsevier.com/reader/sd/pii/B9780128124772000083?token=3CE44CC7CA29B54B4A43CC24F6819451EFE4F4C8F8587A00A8EA924CF8B653C4AA14648E6E123A7B8FB307A456A19429&originRegion=eu-west-1&originCreation=20221215111428)

![Screenshot 2022-12-15 194703](https://user-images.githubusercontent.com/118953929/207852221-c1f089e5-7ac0-4ac0-b848-9c9a912c91f4.jpg)


</details>

	
# &#x1F537; Day_6

<details><summary><b> Lecture 1: Introduction to the course </b></summary>

$\fbox{BASIC of Digital Logic Design and Synthesis}$
	
- Digital Logic
	- Switching Function
	- Automation and Decision making
- Behavioral Model of the design written in HDL
	- VDHL
	- verilog

![photo1671431897](https://user-images.githubusercontent.com/118953929/208363710-a66ff672-995c-4c90-bdae-848795ff4652.jpeg)

$\fbox{WHAT is .lib ?}$
	

![photo1671431897 (1)](https://user-images.githubusercontent.com/118953929/208363706-26b57ea0-b701-4ad9-b4bf-b7c441d74c8d.jpeg)
	
**Faster cells vs slower cells**
	
	- load in Digital logic circuit -> Capacitance
	- Faster the charging or discharging of cap -> lesser the cell delay
		- Wider transistors -> LOW delay (more AREA and POWER)
		- narrow transistors -> MORE delay (Less AREA and POWER)
	

![photo1671431897 (2)](https://user-images.githubusercontent.com/118953929/208363703-c5e208ed-1e8e-4051-b10c-ed02cb2010b2.jpeg)
![photo1671431897 (3)](https://user-images.githubusercontent.com/118953929/208363698-6086474a-df25-4d58-9bdd-d6dad5716cfa.jpeg)
	
> __Keep in mind ^^__  : Wider transistors, increased capacitance ; faster cells, more power
	
	
Cells selection
	
**How do we select the cells ?**
	
	- need to guide the Synthesizer tool to select the flavours of cells.
	- more use of faster cells 
		- bad circuit ( in term of POWER and AREA )
	- more use of slower cells 
		- may not meet the performance need
	- The guidance use is ---> the CONSTRAINTS


**Synthesis illustration**

![photo1671431897 (4)](https://user-images.githubusercontent.com/118953929/208363693-15248534-1e9a-4ed7-8d13-d273b55ba071.jpeg)

	
**Logic synthesis basics**

![photo1671431897 (5)](https://user-images.githubusercontent.com/118953929/208363689-953b8fcb-4de4-4dae-9cc7-a26085118c9b.jpeg)
	
_Standard cell details:_
	
![photo1671431897 (6)](https://user-images.githubusercontent.com/118953929/208363678-6912c17c-6f52-42b9-9593-577e31df4593.jpeg)
	
	
**by seeing at the briefly calculation; we can see that implementation 3 is a good choice. _(but it may not always be the choice, it depends)_
*let's say the logic is present in hold: additional buffers added to meet the hold, so we will need additional area, Right? 

A working digital logic circuit:
	- logically correct
	- electrically correct
	- timing met
		
</details>

<details><summary><b> Lecture 2: Introduction to DC </b></summary>

$\fbox{WHAT is DC ?}$

- Design Compiler (DC) 
	- synthesis tool targeted for ASIC design flow from synopsys
	- Features of DC
		- premium synthesis tool
		- interoperability with various backend tools
		- has the ability to perform DFT scan stitch
		- can handle huge designs (with complexity) and provide very good QoR
	
Common Terminologies:
	

$\mathbb{\color{magenta}{SDC}}$ : Synopsys Design Constraints\
	- supplied to DC to _enable appropriate optimization_ suitable to archieve the best implementation\
	- design intent in terms of **timing, power** (upf file) and **area** constraints.\
	- supported by differemt EDA tools\
	- based in TCL programming language\
$\mathbb{\color{magenta}{.LIB}}$ : Design library (contains stamdard cells)\
$\mathbb{\color{magenta}{DB}}$ : same as .lib, but different format, in DC, we use .db\
$\mathbb{\color{magenta}{DDC}}$ : storing the design information. DC can write out and read in DDC\
$\mathbb{\color{magenta}{DESIGN}}$ : RTL files which has the behavioral model of the design
	

**DC setup:**
	
	 RTL files + .lib + SDC constraints --> outputs verilog netlist and DDC
	

Implementation Flow of ASIC

![photo1671436358](https://user-images.githubusercontent.com/118953929/208374668-6547ffb0-3a50-408e-b943-fad07eb0544a.jpeg)
![photo1671436358 (1)](https://user-images.githubusercontent.com/118953929/208374654-f35b05d6-be85-4c64-9bca-df04a82139ad.jpeg)
	

</details>

<details><summary><b> Lab 1: Invoking DC basic setup </b></summary>

i) Create a directory at the home area and git clone the website:\
	- do git clone ![https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop](https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop)

![photo1671438641](https://user-images.githubusercontent.com/118953929/208381694-9b404594-ead6-4a70-9eea-d61f718a2259.jpeg)
**sepin = my unix id 
> __Warning !__  :Check that all the files needed are there before proceed. 

ii) information of the .lib content:\
	- do gvim sky*.lib

![photo1671439783 (1)](https://user-images.githubusercontent.com/118953929/208385257-74f29be8-8352-461b-8688-6e895cd4e851.jpeg)
![photo1671439783](https://user-images.githubusercontent.com/118953929/208385266-fede7754-cbcf-4f0e-82a1-e77c82a2eced.jpeg)

iii) invoke csh - enable the cshell, then invoke dc_shell

![1](https://user-images.githubusercontent.com/118953929/208390505-45a9fe8b-91a5-43c3-8a57-bde37ea9c7e9.jpg)
![photo1671441268](https://user-images.githubusercontent.com/118953929/208390305-e02a7d7c-fbd2-45e0-811f-c8a334b6e96f.jpeg)
![photo1671441268 (1)](https://user-images.githubusercontent.com/118953929/208390300-2637233d-ff93-4519-abd8-1b286b53cb61.jpeg)
** exec gvim - to execute the gvim command inside the tool without exitting the dc_shell

iv) read_verilog the lab1 verilog file

![photo1671443693](https://user-images.githubusercontent.com/118953929/208398625-8ba432f9-0943-4b73-8f4f-122108ab3770.jpeg)


v) read_db of the sky130 db file (do not want the dummy gtech), but it still not read in in this case. WHY ? 
![photo1671443693 (2)](https://user-images.githubusercontent.com/118953929/208398592-c3684e3e-8e34-437f-ac04-3a2a3f2b5801.jpeg)
![photo1671443693 (3)](https://user-images.githubusercontent.com/118953929/208398586-d72fb8d4-a4aa-4a66-a7a1-39097ba46a59.jpeg)

vi) need to set the link_library and target library to what we targeted. And do make sure the link file is correct

![photo1671443693 (4)](https://user-images.githubusercontent.com/118953929/208398581-dd6ce789-d919-49e9-bd2f-18a144d0c2db.jpeg)
![photo1671443693 (5)](https://user-images.githubusercontent.com/118953929/208398575-9c364c16-3ad6-4100-b858-d2b89c93827c.jpeg)

vii) compile

![photo1671443693 (6)](https://user-images.githubusercontent.com/118953929/208398570-ac152ecf-9ea6-4127-9d22-a312f48daac5.jpeg)
![photo1671443693 (7)](https://user-images.githubusercontent.com/118953929/208398566-b7f655ee-453f-442d-b013-6f551700899c.jpeg)

viii) There we go! the standard cells should be read in! 
![photo1671443693 (8)](https://user-images.githubusercontent.com/118953929/208398554-26cc10ee-6a2c-408a-8ceb-b98834e89781.jpeg)

</details>

<details><summary><b> Lab 2: Intro to DDC GUI with design_vision </b></summary>

Invoke the design_vision:

![photo1671453569](https://user-images.githubusercontent.com/118953929/208428299-7f4e972e-9737-4a67-bba9-24c3a1a76164.jpeg)

write the ddc file:
![photo1671453569 (1)](https://user-images.githubusercontent.com/118953929/208428292-40b1a116-250f-470f-81b4-c37232397bc2.jpeg)

Do read_ddc inside the gui, to read the ddc
![photo1671453569 (2)](https://user-images.githubusercontent.com/118953929/208428284-650808ac-4f25-45c2-9b60-ffeccbfcdf47.jpeg)

Observe the difference between read_verilog and read_ddc ! 
![photo1671453569 (3)](https://user-images.githubusercontent.com/118953929/208428275-c6a82425-37b1-40a0-a23c-21a8b8d1412d.jpeg)

> __Notes__  :ddc will save all information in the tool memory in the particular session. It only understood by synopsys tool.

Open up the schematic view:
![photo1671454097](https://user-images.githubusercontent.com/118953929/208429887-ef137045-5a02-42aa-bd35-0b09b4cf3213.jpeg)

Observe the schematic view, get as what we expected, as drawn expectedly:
![photo1671454097 (1)](https://user-images.githubusercontent.com/118953929/208429896-54c37ecf-2392-48ab-b5b0-68ade0668a0f.jpeg)


</details>

<details><summary><b> Lab 3: DC synopsys DC setup </b></summary>

If you notice, each and everytime we invoke dc_shell, we will need to repeatatively set target_library and link_library to the lib file, if not, it will keep pointing back to your_library.db. So HOW ? 
![photo1671454547](https://user-images.githubusercontent.com/118953929/208431075-d84a97fd-569c-4a79-95cc-0e5f26e1a1a7.jpeg)

**by creating the sysnopsys.dc_setup ^^

![photo1671455560 (1)](https://user-images.githubusercontent.com/118953929/208434088-96c1e630-eeef-4cfb-a236-6913448794ed.jpeg)
![photo1671455560](https://user-images.githubusercontent.com/118953929/208434096-4a324ad3-ce28-42f4-8cf3-5570255e008c.jpeg)

</details>
	
<details><summary><b> Lecture 3: TCL(Tool Command Language) quick refresher </b></summary>
	
Quick refresher:
	
- set
	- keyword use for setting any variables in tcl
	- eg: set a 5 , which is a = 5
	- for a nested command, use square brackets: 
		- eg: set a [expr $a + $b] --> a = a+b
	
- conditional statements;
	if{condition} {
		statements if true
	}else{
		statements if false
	}
	
> __Keep in mind ^^__  : make sure use only curly brackets, and take note of the spacing, it does matters!

- while loops:
	while{condition} {
	statements
	}

> __Keep in mind ^^__  : use the correct variables ! else it might lead to infinite loops.

- for loop:
	for{looping var} {condition} {looping var modification} {
		statements
	}
	
- foreach var list {
	statements
	}
	
> __Keep in mind ^^__  : this is very useful in DC, to loop lists
	
- foreach_in_collection var collection {
	statements
	}

> __Keep in mind ^^__  : nesting of tcl commands is very useful in tcl
	
</details>
	
<details><summary><b> Lab 4: TCL scripting </b></summary>

$\mathbb{\color{blue}{Let \ play \ around \ with \ tcl}}$

![photo1671458055](https://user-images.githubusercontent.com/118953929/208441615-126acd35-0c48-41f3-baaa-f01e33d78fc3.jpeg)
![photo1671458056](https://user-images.githubusercontent.com/118953929/208441613-bf7c0350-7722-4546-847c-5721d932c182.jpeg)
![photo1671458056 (1)](https://user-images.githubusercontent.com/118953929/208441606-12f9ddf0-5d09-4cd4-9fe9-86398969906c.jpeg)
![photo1671458056 (2)](https://user-images.githubusercontent.com/118953929/208441608-7368691d-bd73-4df3-8e23-12a6c03bf1fe.jpeg)
![photo1671458056 (3)](https://user-images.githubusercontent.com/118953929/208441602-b62ac05e-5864-45d5-82b2-978df67dd2e8.jpeg)
![photo1671458056 (4)](https://user-images.githubusercontent.com/118953929/208441597-1da2cdba-6ed0-4828-9265-8158b5cce6bb.jpeg)
![photo1671458056 (5)](https://user-images.githubusercontent.com/118953929/208441591-ee7bbbeb-642f-412a-83a8-f68b949c1322.jpeg)

</details>
	
	
# &#x1F537; Day_7

<details><summary><b> Lecture 4 - Intro to STA </b></summary>

_**Introduction to STA**_

![photo1671619579](https://user-images.githubusercontent.com/118953929/208887282-db208f6a-7566-4d8c-bd64-f91f360124f5.jpeg)
![photo1671619579 (1)](https://user-images.githubusercontent.com/118953929/208887278-50708554-dccf-4818-8c05-02952d24a36a.jpeg)
![photo1671619579 (2)](https://user-images.githubusercontent.com/118953929/208887275-499446b4-12ab-4e8b-9b1a-e72597767dd9.jpeg)
![photo1671619579 (3)](https://user-images.githubusercontent.com/118953929/208887265-c5472951-8dfe-4277-9e51-cdd8ae55e080.jpeg)
![photo1671619579 (4)](https://user-images.githubusercontent.com/118953929/208887263-15369060-7e9f-4da1-84c2-bfaf34507f23.jpeg)

The patterns:

Device | CLK to Q | D to Q | Setup | Hold
--- | --- | --- | --- |--- |
PosEdge DFF |from PosEdge Clk | NA | to PosEdge clk |from PosEdge clk 
NegEdge DFF |from NegEdge Clk | NA | to NegEdge clk |from NegEdge clk
PosLevel DLAT |from PosEdge Clk | From D to Q when clk is high | to NegEdge clk |from NegEdge clk
NegLevel DLAT |from NegEdge Clk | From D to Q when clk is low | to PosEdge clk |from PosEdge clk


</details>

<details><summary><b> Lecture 5 - What are constraints ? </b></summary>

![photo1671622625](https://user-images.githubusercontent.com/118953929/208896636-7e7f87fc-638b-45de-92af-5a8bd036499c.jpeg)
![photo1671622625 (1)](https://user-images.githubusercontent.com/118953929/208896641-eb3cab74-9bef-4d5f-95a3-ad9da5b3e30c.jpeg)
![photo1671622625 (2)](https://user-images.githubusercontent.com/118953929/208896646-a550e743-f7fa-4fa8-aff5-8fc6d2ea5b69.jpeg)	
![photo1671622625 (3)](https://user-images.githubusercontent.com/118953929/208896632-76b66324-70b5-47e0-af5a-99f3071af9b2.jpeg)
	
	
</details>
	
	
<details><summary><b> Lecture 6 - Input Trans Output Load ? </b></summary>

![photo1671625548](https://user-images.githubusercontent.com/118953929/208904696-e2d8dd77-d8be-4a3f-bfd7-24bf6a3d61d4.jpeg)
![photo1671625548 (1)](https://user-images.githubusercontent.com/118953929/208904701-702c4da7-38b8-4850-bc6c-5f5f895a63e8.jpeg)

</details>

<details><summary><b> Lab 5 - Timing dot libs </b></summary>

![photo1671594240 (1)](https://user-images.githubusercontent.com/118953929/208911519-06122118-a568-44e4-9f67-207264534c2a.jpeg)
![photo1671627454](https://user-images.githubusercontent.com/118953929/208911071-f229ebc8-ad6e-4f74-beed-38cd34a0c721.jpeg)
![photo1671627454 (1)](https://user-images.githubusercontent.com/118953929/208911060-576b923e-0bc0-4065-bb6a-973dc5c5c6e9.jpeg)
![photo1671627454 (2)](https://user-images.githubusercontent.com/118953929/208911064-322f22ef-6ffd-4d51-bfc9-8daec2bbbb64.jpeg)
![photo1671627454 (3)](https://user-images.githubusercontent.com/118953929/208911059-cd9135cc-72e8-4ea1-922b-db9ae39cda6b.jpeg)
![photo1671627454 (4)](https://user-images.githubusercontent.com/118953929/208911053-c729139b-3e92-421b-bee9-15a6101fa2f5.jpeg)
![photo1671627454 (5)](https://user-images.githubusercontent.com/118953929/208911048-0e8d6948-ebb7-4b37-902c-39c3c634a7eb.jpeg)
![photo1671627454 (6)](https://user-images.githubusercontent.com/118953929/208911043-b0d66aae-9aeb-409d-aacf-dfed2d281c84.jpeg)
![photo1671627454 (8)](https://user-images.githubusercontent.com/118953929/208911020-b3a6f645-ced3-41b3-b0f3-daada7a486f2.jpeg)
</details>


<details><summary><b> Lab 6 - Exploring dotlibs part 1 </b></summary>

![photo1671630456](https://user-images.githubusercontent.com/118953929/208920467-16b985ec-84e7-4705-a662-7c55559c279c.jpeg)
![photo1671630456 (1)](https://user-images.githubusercontent.com/118953929/208920475-df6b35b4-31b7-454e-845e-efc948f9489d.jpeg)
![photo1671630456 (2)](https://user-images.githubusercontent.com/118953929/208920553-e96d9bd1-3eb3-467c-8124-ccc08da88396.jpeg)
![photo1671630456 (3)](https://user-images.githubusercontent.com/118953929/208920546-68ae46bc-a24b-401b-953f-3ccdcac1d881.jpeg)
![photo1671630456 (4)](https://user-images.githubusercontent.com/118953929/208920542-6652d066-735e-4b97-b57a-0ec7841848fd.jpeg)
![photo1671630456 (5)](https://user-images.githubusercontent.com/118953929/208920532-54f36f4d-864e-43a0-a106-458a37dbd0eb.jpeg)
![photo1671630456 (6)](https://user-images.githubusercontent.com/118953929/208920557-af15c4ca-b009-42e2-96d5-99c6152af62e.jpeg)

</details>
	
<details><summary><b> Lab 6 - Exploring dotlibs part 2 </b></summary>


![photo1671633446](https://user-images.githubusercontent.com/118953929/208931084-29b1fa4f-e48c-4960-827a-96d2bafbedcb.jpeg)
![photo1671633446 (1)](https://user-images.githubusercontent.com/118953929/208931079-96b193d5-d885-4c88-8c2f-6cffe1eb14c5.jpeg)
![photo1671633446 (2)](https://user-images.githubusercontent.com/118953929/208931073-26ae12d9-e5d4-4d70-a69f-449086443532.jpeg)
![photo1671633446 (3)](https://user-images.githubusercontent.com/118953929/208931063-c3f580e6-cf68-4e55-9b72-b4135f7a300b.jpeg)
![photo1671633446 (4)](https://user-images.githubusercontent.com/118953929/208931070-33a71b25-d9c5-4909-8fad-2e3a211405de.jpeg)
![photo1671633577](https://user-images.githubusercontent.com/118953929/208931051-4726a83c-154b-4fb2-84b7-3b1557972707.jpeg)


	
</details>

	
# &#x1F537; Day_8

<details><summary><b> Lecture 7 - SDC Part1 Clock - Clock Tree Modelling </b></summary>

	
Small recap from previous: 

![1](https://user-images.githubusercontent.com/118953929/209536618-4da86ee8-c343-4fcc-aec6-eb9c2ee0f973.jpg)

Q: What needs to be constrained for clocks ?
-	CLOCK PERIOD

![2](https://user-images.githubusercontent.com/118953929/209536616-9bfd1b57-f8c4-4d9a-b5f6-732923857e9d.jpg)

Looking back at the Implementation flow of ASIC, pay attention at the CTS stage.
CTS (Clock Tree Synthesis)
-	Clock is built during CTS ONLY !
-	Clock is an IDEAL Network. 
	
	
Theoretically explained:
	
	- The concept of Clock Tree Synthesis (CTS ) is the automatic insertion of buffers/inverters along the clock paths of the ASIC design in order to balance the clock delay to all clock inputs.
	- In order to balance clock skew and minimize insertion delay, CTS is performed. Naturally, before CTS, all clock pins are driven by a single clock source and considered as an ideal net.
	
	

Ideal Network:

![3](https://user-images.githubusercontent.com/118953929/209536605-5afcfee5-d9f0-47c5-91c3-a31315b3a7fe.jpg)

> __NOTE !__  : But practically this is not possible

![5_1](https://user-images.githubusercontent.com/118953929/209536614-61c7f7ae-cc74-4852-bd4a-e8469caab32b.jpg)

> __NOTE !__  : ALL flops sees the edge at same time 
	
Pratically:
	
![4](https://user-images.githubusercontent.com/118953929/209536608-5d647e36-6f6c-4b0f-a6bd-56de58ba1eeb.jpg)

Clock needs to be routed, the CTS is basically to ensure to reduce the delay between these two flops.
> __NOTE !__  : These delays will not be seen at the synthesis tool ( refer the flow of ASIC )

![5_2](https://user-images.githubusercontent.com/118953929/209536610-941ce990-eadf-4eff-9533-01097010899e.jpg)


> __NOTE !__  : Edges arrive within a window, the location of edge varies from cycle to cycle within this window

> __NOTE !__  : Pratical Network after CTS, ALL flops may not see the clock edge at same instance---> which this is called CLOCK SKEW

Clock Generation:\
	- Oscillator\
	- PLL\
	- External clock source

> __NOTE !__  : All these clock sources have inherent variations in the clock period due to stochastic effects

Clock Distribution:

![6](https://user-images.githubusercontent.com/118953929/209536603-4050cbb4-5e52-4d72-a4a0-bf808aa6a556.jpg)
	
Clock Skew:\
	- Clock Tree built during CTS --> Practical Clock Tree\
	- Logic optimization happens in synthesis --> Ideal Clock Tree\
	- Timing Clean paths in synthesis may fail after STA 

![7](https://user-images.githubusercontent.com/118953929/209536598-1373eaf9-7144-45f0-bdb5-bc5fc40d1c88.jpg)
	
** Available timing window shrinks, path is timing clean before CTS, but fails after CTS
	
Clock Modelling

- Model the clock:
	- Period
	- Source Latency --> Time taken by the clock source to generate clock
	- Clock network latency --> Time taken by CLOCK DISTRIBUTION network
	- Clock Skew --> Clock path delay mismatches ( causes difference in the arrival of clock )
		- CTS will balance the clock, but the skew CANNOT be reduced to 0
	- Jitter --> Stochastic variations in the arrival of clock edge
		- Duty cycle jitter
		- Period Jitter
	- Collctively clock skew, Jitter is CLOCK UNCERTAINTY
- Post CTS
	- the clock NW is real, hence these modelled clock skew and clock network latency must be removed! 

> __NOTE !__  :Synthesis --> Jitter + Skew ; Post CTS --> Only Jitter
	
</details>


<details><summary><b> Lecture 8 - SDC Part2 IO delays </b></summary>

H O W  to constraint the design in DC ?


![8](https://user-images.githubusercontent.com/118953929/209544443-13e6b651-1e03-4136-8d1a-9808233db7b3.jpg)

** NETS - 2 or more pin that are connected to ports


Commands to getting ports in DC

- get_ports clk;
- get_ports * clk *; --> * gets all ports with "clk" in within
- get_ports *; --> gets all ports name for the design
- get_ports * -filter "direction == in"; --> get all ports, pins that are input
- get_ports * -filter "direction == out"; --> get all ports, pins that are output

> __NOTE !__  : all ports, pins , clk are case sensitive !

Commands to getting clocks in DC

- get_clocks *
- get_clocks * clk *
- get_clocks * -filter "period > 10"
- get_attribute [get_clocks my_clk] period --> my_clk is the clock variable that we set
- get_attribute [get_clocks my_clk] is_generated
- report_clocks my_clk

Querying the cells in the Design\
Inside the combo logic:

![9](https://user-images.githubusercontent.com/118953929/209544445-7f56f7a0-2d17-44e4-8034-2c00ef3c2af7.jpg)


Clock Distribution:

H O W do we create clock?

Command: 

![10](https://user-images.githubusercontent.com/118953929/209544447-f4b3fc8a-61c7-4f03-8847-912c2784b0f2.jpg)


> __NOTE !__  : Clock must be created on the clock generators (PLL, OSCILLATORS) or Primary IO pins (for EXTERNAL CLOCKS). Clock should not be created on hierarchical pins which are not clock generators. 

P R A C T I C A L I T I E S  of clock network

![11](https://user-images.githubusercontent.com/118953929/209544449-631fbc68-c681-4dea-8de0-240ec866c7a0.jpg)


Clocks - Waveform

![12](https://user-images.githubusercontent.com/118953929/209544438-831bb21d-9765-445b-8941-e4d3803ab8b4.jpg)


H O W do we constraint the IO paths ?

Looking inside the input ports:

![13](https://user-images.githubusercontent.com/118953929/209544441-b34f2e86-1b27-4642-a047-7dfafc5f6e0a.jpg)


</details>
	
	
<details><summary><b> Lab8 - Loading design get_cells, get_ports, get_nets </b></summary>
	
![14](https://user-images.githubusercontent.com/118953929/209548837-871391d9-f499-415c-9c44-1a3380dc0d5d.jpg)
![15_1](https://user-images.githubusercontent.com/118953929/209548840-d66e78a7-38fa-40ad-a1a9-25fae4de5a1f.jpg)
![15_2](https://user-images.githubusercontent.com/118953929/209548841-c01482ac-ec3c-4a30-9d6a-a8ff209ac4cb.jpg)
![16](https://user-images.githubusercontent.com/118953929/209548844-d85e0f17-f1ec-4ed8-9afe-c0963b26e004.jpg)
![17](https://user-images.githubusercontent.com/118953929/209548846-c0c6774b-5954-46a3-8b21-8b5133a01293.jpg)
![18](https://user-images.githubusercontent.com/118953929/209548849-124a1dea-835e-4ae1-8b5b-72c91d3558a1.jpg)
![20](https://user-images.githubusercontent.com/118953929/209548853-a9ee4d30-7c10-4ffa-8e69-051b167d19e3.jpg)
![21](https://user-images.githubusercontent.com/118953929/209549497-2a067b5a-95ac-4905-bff7-2bece6b4561a.jpg)
	
Clear picture of the schematic shown:
![19](https://user-images.githubusercontent.com/118953929/209548851-447f914b-f9b5-4904-be8a-621294e2250c.jpg)

	
</details>


<details><summary><b> Lab9 - get_pins, get_clocks, querying_clocks </b></summary>
	
![22](https://user-images.githubusercontent.com/118953929/209552228-2c0430c6-d249-4e71-9512-4991ae96cb0b.jpg)
![23](https://user-images.githubusercontent.com/118953929/209552233-6f98f67f-4df4-4f1d-b8cf-28d581c5bc71.jpg)
![24](https://user-images.githubusercontent.com/118953929/209552235-96a480c5-a28d-40a0-bb51-77a72ac68f94.jpg)
![25](https://user-images.githubusercontent.com/118953929/209552238-3e248aaa-977f-45c0-bfa9-1fc6f7e5770c.jpg)
![26](https://user-images.githubusercontent.com/118953929/209552240-78aa9309-1375-4a89-bd62-c19d3331f074.jpg)
![27](https://user-images.githubusercontent.com/118953929/209552241-5aa9ce78-c92d-4c69-8bf1-46ab3e3c1468.jpg)
	
</details>
	
<details><summary><b> Lab10 - create_clock waveform </b></summary>

![28](https://user-images.githubusercontent.com/118953929/209554372-3afdee57-d20a-4db7-b8f0-de0c87133d7c.jpg)
![29](https://user-images.githubusercontent.com/118953929/209554364-dc7c1373-eb85-48fd-9546-c823e891f260.jpg)
![30](https://user-images.githubusercontent.com/118953929/209554367-8e462ad8-c76f-4955-a808-91094b63fb39.jpg)
![31](https://user-images.githubusercontent.com/118953929/209554368-8ac7b54b-9f1a-4dcd-9033-a0ad238c7890.jpg)
![32](https://user-images.githubusercontent.com/118953929/209554369-f6bd844b-7a82-4ccf-8de6-cf7efc4743c5.jpg)

	
</details>
	
<details><summary><b> Lab11 -Clock Network Modelling -Uncertainty, report_timing </b></summary>

![33](https://user-images.githubusercontent.com/118953929/209559774-dd7647c5-63fc-41f8-ac87-93525c977e36.jpg)
![34](https://user-images.githubusercontent.com/118953929/209559776-39eeced7-5bb1-4e50-9315-fa9d5d8b3e55.jpg)
![35](https://user-images.githubusercontent.com/118953929/209559777-f26a0e48-5390-4c1d-af17-19d35c3f1377.jpg)
![36](https://user-images.githubusercontent.com/118953929/209559781-71be7931-9a4a-4de4-9ba5-aef44243cd18.jpg)	
![37](https://user-images.githubusercontent.com/118953929/209559768-ec06328f-29b0-4724-a684-c8b5349a68c4.jpg)
	
</details>

<details><summary><b> Lab12 -IO Delays </b></summary>


![38](https://user-images.githubusercontent.com/118953929/209562271-31756623-c7d8-4abe-a4b1-4696ba7fb1e0.jpg)
![39](https://user-images.githubusercontent.com/118953929/209562272-674d6cf8-0dc4-414a-bb1f-93897355696b.jpg)
![40](https://user-images.githubusercontent.com/118953929/209562274-d592bc6d-3242-4638-90f8-9c1156b5bbf9.jpg)
![41](https://user-images.githubusercontent.com/118953929/209562277-64c704d6-c904-4e37-9e80-76f7ff6c51b9.jpg)
![42](https://user-images.githubusercontent.com/118953929/209562278-4df95deb-23b4-4a5f-9f6f-9ee400f7ba0c.jpg)
![43](https://user-images.githubusercontent.com/118953929/209562280-68361239-85e6-4260-b909-1dece45e76a4.jpg)
![44](https://user-images.githubusercontent.com/118953929/209562283-b8842d3f-7cd4-4316-85f0-eac61937d96e.jpg)

</details>

<details><summary><b> Lecture9 - SDC Part3 generated_clk </b></summary>

Looking at the output path:

![45](https://user-images.githubusercontent.com/118953929/209565327-b783e813-9196-4096-a51e-2ad0f4c60d5f.jpg)


Command to generate clocks:


![46](https://user-images.githubusercontent.com/118953929/209565321-72c544da-6ef0-4ef2-91cf-6b5e8c653c53.jpg)


H O W  do we constraints the design?

![47](https://user-images.githubusercontent.com/118953929/209565324-e05d0160-a10e-4d7f-a524-2c297e88f4a8.jpg)

H O W the clocks are propagated:

- once a clock is created on a pin/port, DC will propogate that clock downstream based on the timing arcs. 
- all the timing arcs from the definition point will see the clock propogate by default.

</details>

<details><summary><b> Lab13 - Generated_clocks </b></summary>

![48](https://user-images.githubusercontent.com/118953929/209567986-0dba1601-3dbf-4d03-a990-ca56e145dfd4.jpg)
![49](https://user-images.githubusercontent.com/118953929/209567987-4e4b751e-1836-41f1-bcb6-56a5ba8ea5e4.jpg)
![50](https://user-images.githubusercontent.com/118953929/209567989-6dcdacc0-2668-4cba-89d8-ab1e61b69db3.jpg)
![51](https://user-images.githubusercontent.com/118953929/209567991-1f3cae2d-0d98-4805-9aca-ccda3ff11080.jpg)
![52](https://user-images.githubusercontent.com/118953929/209567992-c04a99eb-5567-496f-83f3-9a31c58a95f6.jpg)
![53](https://user-images.githubusercontent.com/118953929/209567997-f9f1e7d1-15bd-473c-916b-371a7186fffd.jpg)
![54](https://user-images.githubusercontent.com/118953929/209567984-cdc713e9-dd99-4d16-a981-fec7223cc02b.jpg)

</details>

<details><summary><b> Lecture 10: SDC Part4 vclk, max_latency, rise_fall IO delays </b></summary>

I N P U T   D E L A Y


![55](https://user-images.githubusercontent.com/118953929/209570802-2f0133e1-e6ef-4ced-ac6c-c407a9845f91.jpg)
![56](https://user-images.githubusercontent.com/118953929/209570803-04f4d94d-cdd0-4e8c-a84a-e0fb61eacdbe.jpg)
![57](https://user-images.githubusercontent.com/118953929/209570804-f989be6e-347a-475d-bc97-8bfcb164b94d.jpg)
![58](https://user-images.githubusercontent.com/118953929/209570805-65a11c6b-701f-4d98-9704-ef1fa1ea0acf.jpg)


O U T P U T   D E L A Y 

![59](https://user-images.githubusercontent.com/118953929/209570806-7091866e-bd7d-48b3-8047-8b1e641346d0.jpg)
![60](https://user-images.githubusercontent.com/118953929/209570798-b6d78138-7c01-4040-9c7c-578e4a9bd461.jpg)

IO CONSTRAINTS REVISITED:
	
	***No clock definition point -> virtual clock inferred

eg:

Diagram from Lecture's:
![image](https://user-images.githubusercontent.com/118953929/209571224-58a56d8a-3644-4e4d-b0ce-aebc27a324d7.png)
	
create_clock -name MY_VCLK -period 5
	
set_output_delay -max 2.5 -clock MY_VCLK [get_ports OUT_Z]\
set_input_delay -max 1.5 -clock MY_VCLK [get_ports IN_C]\
set_input_delay -max 1.5 -clock MY_VCLK [get_ports IN_D]
	
> __NOTE !__  : for virtual clock, there is no latency , no clock definition point	

	
set_driving_cell --> will be discussed more on lab

	set_input_transition -max 0.15 [get_ports IN_A]
	
**more accurate for all internal paths
	
eg of usage:
	
	set_driving cell -lib_cell <lib_cell_name> <ports>
	set_driving_cell -lib_cell sky130_fd_sc_hd_buf_1 [all_inputs]
	

</details>

<details><summary><b> Lab 15: part1 - set_max_delay </b></summary>
	
![61](https://user-images.githubusercontent.com/118953929/209574357-bab1ff23-5a4a-46a5-a724-e5151e32a529.jpg)
![62](https://user-images.githubusercontent.com/118953929/209574363-3cc2511c-1cb6-43d0-af25-9152c461b2dc.jpg)
![63](https://user-images.githubusercontent.com/118953929/209574365-5769a00c-45b6-4e08-ada6-7901ba36d0f2.jpg)
![64](https://user-images.githubusercontent.com/118953929/209574366-22203df3-19c1-434e-b8fc-164dd6b0fa7a.jpg)
![65](https://user-images.githubusercontent.com/118953929/209574367-28bd22a4-5b11-496b-a3fa-bb70d0662631.jpg)
![66](https://user-images.githubusercontent.com/118953929/209574368-af43ff58-e953-4b67-960a-2bb3debe7e44.jpg)
![67](https://user-images.githubusercontent.com/118953929/209574369-25507ad9-5d2a-428b-b7e1-dd9a64bf9cbb.jpg)
![68](https://user-images.githubusercontent.com/118953929/209574372-a91bbf21-8a77-4137-a606-0cc10330f6b3.jpg)
![69](https://user-images.githubusercontent.com/118953929/209574375-116a02da-b813-4bba-aaa7-812b80a81f95.jpg)
![70](https://user-images.githubusercontent.com/118953929/209574377-cc65303e-6883-431e-a28f-19b98098afc4.jpg)
![71](https://user-images.githubusercontent.com/118953929/209574378-88f6640a-c796-40de-ad08-604dcf278f68.jpg)
	
</details>
	
<details><summary><b> Lab 15: part2 - VCLK </b></summary>
	
**virtual clock: a clock that is created WITHOUT a definition point



![72](https://user-images.githubusercontent.com/118953929/209575557-35cf47fb-d1ba-4b89-9ec9-ad0770fc50f5.jpg)
![73](https://user-images.githubusercontent.com/118953929/209575558-e9c362a3-e9e3-4550-8d1d-5d2f163cda4e.jpg)
![74](https://user-images.githubusercontent.com/118953929/209575560-028f8c3d-8f34-4429-aac9-58bd370cfd29.jpg)
![75](https://user-images.githubusercontent.com/118953929/209575561-7902521b-f699-493f-a6c1-9c2938d9d95b.jpg)
![76](https://user-images.githubusercontent.com/118953929/209575563-58cb415b-e87c-4c5b-b84d-88bbf6601301.jpg)	
![77](https://user-images.githubusercontent.com/118953929/209575552-0e94edf1-bac7-45fe-8ec1-899a42d69087.jpg)

	
</details>

# &#x1F537; Day_9
	
<details><summary><b> Lecture 11 - Optimizations Combinational Opt </b></summary>

$\fbox{OPTIMIZATION GOALS}$

- Cost function based optimizations
	- Optimization till the cost is met
	- Over optimization of one goal will/might harm the other
	- Goals for synthesis 
		- Meeting Timing --> $\colorbox{blue}{{\color{white}{FASTER}}}$ cells, $\colorbox{red}{{\color{white}{BAD}}}$ power and area 
		- Meet Area --> $\colorbox{blue}{{\color{white}{SMALLER}}}$ cells, $\colorbox{blue}{{\color{white}{GOOD}}}$ power and area, $\colorbox{red}{{\color{white}{BAD}}}$ timing
		- Meet Power 
	
$\fbox{Combinational Logic Optimisation}$
	
- Squeezing logic to get $\colorbox{violet}{{\color{white}{most optimized}}}$ design
	- area and power savings
	
- Constant Propagation
	- $\colorbox{violet}{{\color{white}{Direct}}}$ Optimisation

![image](https://user-images.githubusercontent.com/118953929/209784103-3e8db6cb-3c61-4d53-baf5-d9c5c880e9a3.png)


- Boolean Logic Optimisation
	- KMap
	- Quine McKluskey
	
 ![image](https://user-images.githubusercontent.com/118953929/210214118-dc4f7cf5-642f-46e3-99df-b3b669da053f.png)

	
$\fbox{Resource sharing}$
	
![image](https://user-images.githubusercontent.com/118953929/210215647-798f19b2-974e-4372-9d99-e314bf3923b3.png)

	
$\fbox{Logic sharing}$	

![image](https://user-images.githubusercontent.com/118953929/210217890-8f904a95-9241-4681-8d5f-57cf0bbd0594.png)
	
$\fbox{Balanced vs Preferential Implementation}$
	
Assuming 5 i/p,
	
	assign y = a & b & c & d & e ;

![image](https://user-images.githubusercontent.com/118953929/210227906-610588c7-59c7-4ecb-8795-c46c863b227f.png)
	
</details>	
	

<details><summary><b> Lecture 12 - Sequential Optimizations </b></summary>

$\fbox{Sequential Logic Optimisations}$
	
- Basic 
	- Sequential Constant propagation
	- Retiming
	- Unused flop removal
	- Clock gating
	
- Advanced 
	- State Optimization
	- Sequential Logic Cloning ( Floor Plan Aware Synthesis )
	

EG:
	
SEQUENTIAL CONST
i) q is grounded;  Q is always D (1'b0)

![image](https://user-images.githubusercontent.com/118953929/210234695-0e5a2631-2d25-4253-bce8-2fa4787c4813.png)

ii) q = VDD ; Q is always 1'b1
	
![image](https://user-images.githubusercontent.com/118953929/210234528-a5be02b4-dd55-45f8-aed1-c4d5d51f898d.png)


NOT A SEQUENTIAL CONST ( cannot be optimized )

iii) 

![image](https://user-images.githubusercontent.com/118953929/210239040-6653fae1-d63c-45ce-9109-0341e7738aa9.png)

Another example:
	
Seq Const:
	
B'.1 + B.1' = B' + 0 
	    = B' --> out 
	
![image](https://user-images.githubusercontent.com/118953929/210243392-b7a1e855-a59a-4bbc-984f-603c0c44e7ab.png)

	

$\fbox{Optimization of uloaded outputs}$

input --> clk , en, res
output --> q
reg of 4 bit count --> cnt
	
	**condition(s): if there is enable, it will toggle, if not, will not toggle --> be the value of 4 bit counter
	
![image](https://user-images.githubusercontent.com/118953929/210246643-e2b5dec1-68d5-4b22-861a-ed7ad159672e.png)

	
$\fbox{Controlling sequential optimizations in DC}$
	
- compile_seqmap_porpagate_constants
- compile_delete_unloaded_sequential_cells
- compile_register_replication

	
</details>

<details><summary><b> Lab 16 - part1 Combinational_optimizations </b></summary>	

read_verilog --> can observe the comments --> nothing is report out, means nothing is present in the design
	
![image](https://user-images.githubusercontent.com/118953929/210250103-7fc7cec1-f02a-413e-abbb-7acddfcafdb0.png)
do link, and compile, and then report_timing again, then you will see the and gate reported out
	
![image](https://user-images.githubusercontent.com/118953929/210250421-7ac0241c-5b1d-463b-a751-8501b5e8040a.png)
	
load up the desion_vision and write ddc the op_check.v file:
	
![image](https://user-images.githubusercontent.com/118953929/210253237-5ae57d2e-6589-4da3-ab62-02205c1f5c34.png)

for others: 
	
do read_verilog opt_check*.v , link and compile, write ddc file and observe the schematic

opt_check2.v
![image](https://user-images.githubusercontent.com/118953929/210253493-1f73e905-036b-4f63-b150-63a486578132.png)

opt_check3.v
![image](https://user-images.githubusercontent.com/118953929/210253610-da3c0732-c412-40e1-95b8-a007d973db38.png)
	
opt_check4.v 
![image](https://user-images.githubusercontent.com/118953929/210254092-3faab2d5-5d1f-4455-8f7a-261b07963adf.png)
	
report_timing: will see the path is unconstrained, as nothing is being link here

![image](https://user-images.githubusercontent.com/118953929/210289837-27bf3cc5-fbed-456d-ba8b-fbff0fec3db2.png)

do set_max_delay; observe the violated time
	
![image](https://user-images.githubusercontent.com/118953929/210289904-8c18122d-d1ac-4ca1-bdf7-79b4a65a0b0e.png)

compile_ultra, and report_timing again to see differs;
so as observed, nothing actually happens any changes here.
	
![image](https://user-images.githubusercontent.com/118953929/210289953-0322ddaa-2c88-4846-a811-353fd04c2a5a.png)

do a set_max_delay for a 6 ps,

![image](https://user-images.githubusercontent.com/118953929/210292233-fbba4550-1073-4d64-aad6-03b38fee31a5.png)

report_timing, observed:
	
![image](https://user-images.githubusercontent.com/118953929/210292271-269c9c9f-4c24-4b12-a352-58b341249bae.png)

compile_ultra for the optimization, and observe the differs:

![image](https://user-images.githubusercontent.com/118953929/210292437-c39ea3a0-701a-4d2f-8e35-f79d601401c9.png)
	
	
</details>	

<details><summary><b> Lab 16 - part2 Resource sharing optimizations </b></summary>	

open up resource_sharing_mult_check.v
- looking back at the notes, the code is write out as what we drawn theoretically:
	
![image](https://user-images.githubusercontent.com/118953929/210292787-4b4f6336-488f-43c0-953c-f1bd8f822bc1.png)
	
read_verilog resource_sharing_mult_check.v\
link\
compile_ultra

![image](https://user-images.githubusercontent.com/118953929/210294460-2a537e69-b0ca-4625-b6b2-1e5005e93b6f.png)

![image](https://user-images.githubusercontent.com/118953929/210293879-895d4c8f-df66-436a-81e7-ce7a7f252f2b.png)

FOR RUN1:

report_area, viewing from the .v file and the diagram, we observed: 
- input [3:0] a , input [3:0] b, input [3:0] c , input [3:0] d, output [7:0] y  , input sel --> 25 ports
	
![image](https://user-images.githubusercontent.com/118953929/210294926-e7584450-cdc7-43cb-a428-000aeddd3f82.png)
	
![image](https://user-images.githubusercontent.com/118953929/210295382-aba19538-b3dc-4b33-8580-d83a4eb42ea2.png)

set_max_delay:
	
![image](https://user-images.githubusercontent.com/118953929/210295531-03df338b-85f3-4e0a-bd0f-88ecb3ba0ee1.png)
	

report_timing: 

![image](https://user-images.githubusercontent.com/118953929/210295587-f67f1be3-df45-4f9d-bf9d-7ff3c41a4397.png)

after compile_ultra:

![image](https://user-images.githubusercontent.com/118953929/210296217-2117afcb-6f5d-436c-9d30-d05775cf0476.png)

set_max_delay from sel:
	
![image](https://user-images.githubusercontent.com/118953929/210296391-9a05ff01-3336-4379-8df5-56e44e2b9142.png)

report_timing:

![image](https://user-images.githubusercontent.com/118953929/210296453-28dbbf57-afdf-4290-ae0f-499ef8079ec4.png)

after compile_ultra:

![image](https://user-images.githubusercontent.com/118953929/210296493-7bac0e9b-3709-40b0-bcd5-343b390ca1e0.png)


FOR RUN2:

report_area:

![image](https://user-images.githubusercontent.com/118953929/210296548-c47d1a11-a52b-400b-a13b-41ead6917d65.png)

report_timing:
![image](https://user-images.githubusercontent.com/118953929/210296824-fddcb1ac-1278-48f5-9e30-7f48a6185973.png)

after compile_ultra:

![image](https://user-images.githubusercontent.com/118953929/210296898-22747b46-682f-47a5-bd46-43d00ea769be.png)

</details>	

<details><summary><b> Lab 17 - seq optimizations </b></summary>

reading dff_constant1.v

![image](https://user-images.githubusercontent.com/118953929/210297111-41e69c34-b207-4fd2-9ac5-f12b595298ad.png)

read_verilog dff_const1.v\
link\
compile
	
write a foreach for a collection loop to get the cells;
	
![image](https://user-images.githubusercontent.com/118953929/210297668-b06ffda6-47c2-4d86-b985-76b2c1ac5dff.png)

get the ref_name for the cells:

![image](https://user-images.githubusercontent.com/118953929/210299288-a3280f2d-8cd4-47f9-a8c7-d59eeeac7665.png)

The schematic:
	
![image](https://user-images.githubusercontent.com/118953929/210299866-42283fad-21a4-4fef-bff5-f3d7052c760b.png)

read_verilog dff_const2.v\
link\
compile\
gui_start

The schematic:

![image](https://user-images.githubusercontent.com/118953929/210300353-0a4f0e2a-5e55-4a47-90b3-0ab4ce3daf7f.png)

read_verilog dff_const3.v\
link\
compile\
gui_start


The schematic: 

![image](https://user-images.githubusercontent.com/118953929/210300475-f5004be5-de0c-4033-a8e4-e0e7e8ce2f33.png)
	
Looking back at dff_const2.v:

read_verilog dff_const2.v
set compile_seqmap_propagate_constants false
	
	
**not optimized:

![image](https://user-images.githubusercontent.com/118953929/210300727-165537af-8600-4fd5-aca9-93c7f1025ecd.png)

read_verilog dff_const4.v\
link\
compile\
gui_start


The schematic:
	
![image](https://user-images.githubusercontent.com/118953929/210300987-9f96757d-417e-449f-bc35-f4674f7fa7d9.png)
	
read_verilog dff_const5.v\
link\
compile\
gui_start


The schematic:
	
![image](https://user-images.githubusercontent.com/118953929/210301105-48f49c96-2b9f-4ec0-9b55-df3eb841130c.png)

</details>
	

<details><summary><b> Lecture 13: Special Optimizations </b></summary>

$\fbox{Special Opt}$

- Retiming
	

![image](https://user-images.githubusercontent.com/118953929/210302428-6a4c7901-6a18-40aa-be83-b26e671e1a30.png)

the illustration of the retiming:

![image](https://user-images.githubusercontent.com/118953929/210302874-a66a65a2-28c7-4c68-8b2f-30a43b52fd45.png)

$\fbox{Boundary Optimization}$

![image](https://user-images.githubusercontent.com/118953929/210303253-ab555b34-7aea-433d-8c6e-43803e7c3f1d.png)
	
Optimization::( it was merged) 
	
![image](https://user-images.githubusercontent.com/118953929/210303343-0cd6fa54-ea67-4ffc-afde-959f750f4d2a.png)


**Take note: need to enable or not --> need to be very careful

Commands:
	
- set_boundary_optimization <design> < true| false>
	
M U L T I - C Y C L E PATHS 
	
- set_multicycle_path -setup 2 -to prod_reg [*]/D -through [all_inputs]

![image](https://user-images.githubusercontent.com/118953929/210304142-68c5944f-fedf-4ed9-93e9-f08115aaa53f.png)


**input A and B will load the data, and wait the sel to select, sel is basically the 1 cycle delay of the enable. SO, it can not be optimized into single path
	
F A L S E PATHS 
	
- Paths that are not valid for STA
	- set_false_path -from <> -to <>
	- set_false_path -through <>

![image](https://user-images.githubusercontent.com/118953929/210304588-3ec5988b-e06e-4561-9b16-df55f3b145cd.png)
![image](https://user-images.githubusercontent.com/118953929/210305039-9c1520a9-ad55-42ab-973c-a4ac036c6039.png)
	
External LOAD vs Internal LOAD

Commands:

- set_isolate_ports -type buffer [get_ports y]

![image](https://user-images.githubusercontent.com/118953929/210305712-ce10d41b-d27e-47d6-94d6-dc5e4ab9980f.png)
![image](https://user-images.githubusercontent.com/118953929/210305727-f657a68d-645e-4b84-bc82-71993450852e.png)

*internal path will not see the external load 
		
</details>

<details><summary><b> Lecture 14: How Paths are timed MCP? </b></summary>

H O W DC/STA tool checks timing ?

--single cycle path
	
![image](https://user-images.githubusercontent.com/118953929/210306683-99160365-1b08-4b41-919f-d131601ead00.png)

**Note: HOLD is always checked at the edge before setup
	
--Half cycle path
	
![image](https://user-images.githubusercontent.com/118953929/210307027-01ae91ea-798b-4fef-8eba-aee08309b74b.png)

**Note: HOLD will happen at edge before (VERY RELAXED) 
	
--multi-cycle path
	
![image](https://user-images.githubusercontent.com/118953929/210308130-51d6e4fb-5e2f-4174-a23a-dd1c1cc8b173.png)


**Prod_reg is getting loaded once in every 2 CYCLES only. 
	
	set_multicycle_path –setup 2 –from [all_inputs] –to (PROD_REG[]/D) <- endpoint edge moved forward
	set_multicycle_path –hold 1 –from [all_inputs] –to (PROD_REG[]/D) <- launch edge moved forward



</details>
	

<details><summary><b> Lab 18: Boundary Optimization </b></summary>

check_boundary.v content:
	
![image](https://user-images.githubusercontent.com/118953929/210309247-08603bfb-a5e6-43e1-8423-2368b3f17ed7.png)
	

reset_design\
read_verilog check_boundary.v\
link\
compile\
write -f ddc -out check_boundary.ddc
read_ddc check_boundary.ddc
	
The schematic:
![image](https://user-images.githubusercontent.com/118953929/210314464-507a8c54-9b67-4aac-9e28-a79e1bb3c362.png)

Now turn the u_im to false:
	
set_boundary_optimization u_im false\
compile_ultra

The schematic:
	
![image](https://user-images.githubusercontent.com/118953929/210315718-28e0ddc9-6a6a-4ca6-a0ba-3dbcbd914537.png)

</details>
	

<details><summary><b> Lab 19: Register Retiming </b></summary>

check_reg_retime.v

![image](https://user-images.githubusercontent.com/118953929/210316015-311c60ba-140a-4201-b0f0-fa212bb909c2.png)
![image](https://user-images.githubusercontent.com/118953929/210316238-1a7bb4ce-1bc0-4a0c-bc34-aedc076657ba.png)
![image](https://user-images.githubusercontent.com/118953929/210316349-6239906f-3376-4e1c-9486-4e1ee5ce65e1.png)


The schematic:

![image](https://user-images.githubusercontent.com/118953929/210316491-c3ede2a1-753e-4084-b349-bbe30ffc4e93.png)

create a tcl for the retiming:

![image](https://user-images.githubusercontent.com/118953929/210316751-311b5e42-9b14-4bde-a1d9-a06fb56f0b8c.png)

source the tcl\
report_timing:
	
![image](https://user-images.githubusercontent.com/118953929/210317108-f5bae39e-0cdb-455f-9ce1-d28c0ac69366.png)

Enable the retiming, can observe the schematic:
	
![image](https://user-images.githubusercontent.com/118953929/210317319-692a129e-d462-4407-933d-0f6532d4786d.png)
	
report_timing -from [all_inputs] -trans -cap -nosplit:

![image](https://user-images.githubusercontent.com/118953929/210317425-b07136f9-dc54-4f1d-9df4-f9bb0382dd49.png)
	

</details>
	

<details><summary><b> Lab 20: Isolating output ports </b></summary>

check_boundary.v

![image](https://user-images.githubusercontent.com/118953929/210326304-e4146688-6df8-4f76-a8a1-b8a2f8cd91c9.png)

set_isolate_ports -type buffer [all_outputs]\
compile_ultra

*the buffer is created:

![image](https://user-images.githubusercontent.com/118953929/210327069-a182e2d5-e1bc-4f32-a6a9-f66fa645a3b5.png)
	
reset_design\
read_verilog check_boundary.v\
link\
compile_ultra\
create_clock -per 5 -name myclk [get_ports clk]\
set_input_delay -max 2 [all_inputs] -clock myclk\
set_output_delay -max 2 [all_outputs] -clock myclk\
set_load -max 0.3 [all_outputs]\
report_timing

![image](https://user-images.githubusercontent.com/118953929/210327972-e01525eb-a581-4b32-93bb-814684dbe4a3.png)

report_timing -nosplit -inp -cap -trans -sig 4
	
![image](https://user-images.githubusercontent.com/118953929/210328023-320e8e97-5e15-4d37-aa31-a28f4e5845a0.png)
	

</details>
	

<details><summary><b> Lab 21: MultiCycle path </b></summary>

mcp_check.v
	
**a and b will be loaded only if there is valid:
![image](https://user-images.githubusercontent.com/118953929/210329327-ba1ea61a-17b6-49e5-bae3-fb948730ae22.png)

![image](https://user-images.githubusercontent.com/118953929/210330023-e1d682c8-3bef-4d95-b85c-ea43b2fdcb5f.png)

source the tcl\
report_timing
	
![image](https://user-images.githubusercontent.com/118953929/210330233-1780801a-418a-4d7d-b156-ba3937f88b54.png)

compile_ultra
report_timing

![image](https://user-images.githubusercontent.com/118953929/210330883-da88bd66-00d9-4f19-9aeb-47904c11dd76.png)

set_multicycle_path -setup 2 -to prod_reg[*]/D -from [all_inputs]
	
![image](https://user-images.githubusercontent.com/118953929/210331052-2a95e910-f781-487e-95b2-c34ecb520a69.png)
	
set_multicycle_path -hold 1 -from [all_inputs] -to prod_reg[*]/D <- * multiple bit register

![image](https://user-images.githubusercontent.com/118953929/210331697-1f9a725c-16d5-4d5f-87e1-a1fef66f73d8.png)

</details>
	

# &#x1F537; Day_10
	

<details><summary><b> Lecture Report Timing </b></summary>

$\fbox{Generate Timing Reports}$
	
	- report_timing -from DDF_A/clk
	- report_timing -from DDF_A/clk -to DDF_A/d
	- report_timing -fall_from DDF_A/clk
	- report_timing -rise_from DDF_b/clk
	- report_timing -delay_type min -to DDF_C/d
	- report_timing -delay_type min -through INV/a
	- report_timing -delay_type max -through AND/b
	- report_timing -rise_from DDF_b/clk -delay_type max -nets -cap -trans -sig 4
	

** default is delay_type max
	
Propagation delay:
	
	Propagation delay is the amount of time required for a signal to be received after it has been sent; it is caused by the time it takes for the signal to travel through a medium
	

![image](https://user-images.githubusercontent.com/118953929/210332925-4eb7740d-d465-4f5d-b273-e8bfd22f708f.png)

Timing paths - Further details
	
![image](https://user-images.githubusercontent.com/118953929/210336012-43be5a42-8cba-4013-9c65-3cc13401fcf7.png)
	
![image](https://user-images.githubusercontent.com/118953929/210337203-f283f648-b19d-49d5-9d1e-502bef70546e.png)

	
EG: 
	
** report_timing -delay_type max -to DFF_C/d
	
here:
clock period --> 5ns, and setup for DFF_C --> 0.5ns
Data at DFF_C needs to be stable by 4.5ns **(5-0.5)** --> Arrival time - required time
	
Max_paths and nworst path
	
***report_timing -to DFF_C/d -max_paths 2 <---- will report out 2
						
report_timing -max_paths 2 -nworst 2 <---- this will pick the worst of 2 out of 4 
	

</details>


<details><summary><b> Lab Report Timing </b></summary>

lab8_circuit_modified.v
	
![image](https://user-images.githubusercontent.com/118953929/210339169-9cbb2e5a-d5f7-4256-882a-1c5913eaee13.png)

source the lab_cons_modified.tcl

![image](https://user-images.githubusercontent.com/118953929/210339487-1114f589-24ec-4b7a-9632-8d18112e3bdb.png)
	
![image](https://user-images.githubusercontent.com/118953929/210339752-6d5dfc17-bba8-4d13-ab8c-d3290415b73d.png)

report_timing -sig 4 -nosplit -trans -cap -nets -inp -from IN_A > report1.rpt\
report_timing -sig 4 -nosplit -trans -cap -nets -inp -rise_from IN_A -to REGA_reg/D > report2.rpt


![image](https://user-images.githubusercontent.com/118953929/210340313-d6382cc8-faa5-4e5b-96b2-a2999a6dd4cb.png)
	
report_timing -delay min -from IN_A

![image](https://user-images.githubusercontent.com/118953929/210340757-6a220413-7a72-45da-ae61-dcf0d709f5eb.png)
	
![image](https://user-images.githubusercontent.com/118953929/210341134-1640d97c-095c-4fe0-8c88-f68c66aab244.png)
	

</details>


<details><summary><b> Lab Check timing, check design, set_max_capacitance </b></summary>
	
![image](https://user-images.githubusercontent.com/118953929/210341541-c7e9a694-380a-4087-963d-36edb93bd358.png)

check_timing
	
![image](https://user-images.githubusercontent.com/118953929/210341792-cfd3c491-a1f4-48f7-8e2b-94398b9072ac.png)

report_constraints
	
![image](https://user-images.githubusercontent.com/118953929/210342012-e2714a44-0c26-4a77-92e3-540c4f516358.png)

source lab8_cons.tcl and recheck timing and report constraints, observe the differents:
	
![image](https://user-images.githubusercontent.com/118953929/210342307-bbd52839-3028-4344-bc9f-d2c41957e815.png)
	
![image](https://user-images.githubusercontent.com/118953929/210342392-c98ddbfe-2e4a-49df-a92a-65e1c56c9f40.png)


modified the mux_generate.v into as follow:
	
![image](https://user-images.githubusercontent.com/118953929/210343112-340248b5-7ff9-40a9-9794-2f9a902daf5c.png)

![image](https://user-images.githubusercontent.com/118953929/210344068-64a8651b-da26-4f4b-b9b8-e48fc1bce9ed.png)

write -f verilog -out mux_generate_modified_net.v

![image](https://user-images.githubusercontent.com/118953929/210344439-c6a8e8b7-a289-4c88-82e9-6eac3519fa6e.png)

report_timing -net -cap
	
![image](https://user-images.githubusercontent.com/118953929/210344689-37ff6cf3-9188-4be8-8fd0-6c593157337b.png)
![image](https://user-images.githubusercontent.com/118953929/210344817-53abb53d-3f07-4a7e-a211-61fcf4f3a4c7.png)

reduce capacitance

![image](https://user-images.githubusercontent.com/118953929/210345009-339ca2bc-9b10-488b-93e5-29cfd393ff00.png)

compile_ultra

![image](https://user-images.githubusercontent.com/118953929/210345123-6662c3cc-9d3e-4dd8-a2cf-7573d697b944.png)

![image](https://user-images.githubusercontent.com/118953929/210345276-b7ddd232-97c7-476e-b97f-0aff90326dca.png)
	
report_timing

![image](https://user-images.githubusercontent.com/118953929/210345392-36a5d23a-1520-4874-9bd0-c8fb66d7b370.png)


![image](https://user-images.githubusercontent.com/118953929/210345626-b2ab44e4-9d66-46f2-a41a-79fdbf8e555b.png)
	
![image](https://user-images.githubusercontent.com/118953929/210345858-a5c7826d-46b3-44f0-a87d-66b05e89290b.png)

write -f ddc -out modified_net.v
read_ddc modified_net.v
	
![image](https://user-images.githubusercontent.com/118953929/210346099-fa740343-12ae-4f41-8945-cdb81b9b1fbb.png)

![image](https://user-images.githubusercontent.com/118953929/210346284-dcf197b4-36ef-4fde-97a6-26080c4a2507.png)

report_constraints
	
![image](https://user-images.githubusercontent.com/118953929/210346398-ca893f92-e9ff-4fd1-b307-f268560af28c.png)


</details>
	
# &#x1F537; Day_11
	
<details><summary><b> Lecture sessions </b></summary>

$\fbox{W H A T is SoC}$
	
SoC - SoC stands for System On Chip. It is a small integrated chip that contains all the required components and circuits of a particular system. The components of SoC include CPU, GPU, Memory, I/O devices, etc. SoC is used in various devices such as smartphones, Internet of Things appliances, tablets, and embedded system applications
	
	
	
- single die chip that has differents IP cores on it. These IPs could vary from completely DIGITAL to completely ANALOG
- the design of a SoC includes a central processing unit, memory, ports for input and outputs, secondary storage devices, and peripheral interfaces
- SoC with equivalent functionality will have increased $\colorbox{violet}{{\color{white}{performance}}}$ and reduced $\colorbox{violet}{{\color{white}{power}}}$ consumption as well as a smaller semiconductor die $\colorbox{violet}{{\color{white}{area}}}$


$\fbox{Type of SoC}$
	
- SoCs built around a micrcontroller
- SoCs built around a microprocessor, often found in cell phones
- Specialized application-specific integrated circuit SoCs designed for specific applications that $\colorbox{violet}{{\color{white}{DO NOT}}}$ fir into the above two 
	

$\fbox{Architecture ofSoC}$ - additional notes 
	
- SoC stands for System On Chip. It is a small integrated chip that contains all the required components and circuits of a particular system. The components of SoC include CPU, GPU, Memory, I/O devices, etc. 
- SoC is used in various devices such as smartphones, Internet of Things appliances, tablets, and embedded system applications.

![image](https://user-images.githubusercontent.com/118953929/210895027-aac905fe-efe3-407f-9865-5bd9e9f29e2a.png)
	
Processor:  It is the heart of SoC, usually SoC contains at least one or more than one coprocessor. It can be a microcontroller, microprocessor, or DSP. Most of the time DSP is used in every SoC as a processor.

DSP: DSP stands for Digital Signal Processor. It is included in SoC to perform signal processing operations such as data collection, data processing, etc. it is also used for the purpose of decoding the images.

Memory: Memory is used in SoC for the purpose of storage. It may be a volatile or non-volatile memory. Volatile memory includes RAM there are two types of RAM one is SRAM and another is DRAM. The non-volatile memory includes ROM.

Encoder/Decoder: Used for the purpose of interrupting information and converting it into codes.

Network Interface card: SoC has an internal interface or bus or network to connect all individual blocks. Basically, the Network interface card provides a connection of the network to the system.

GPU: GPU stands for Graphical Processing Unit, used in SoC to visualize the interface. GPU is specially designed to speed up the operations related to image calculations. The basic blocks of the GPU are the Bus interface, Power Management Unit, Video Processing unit, Graphics Memory Controller, Display interface, etc.

Peripheral devices: Externally connected devices/interfaces such as USB, HDMI, Wi-Fi, and Bluetooth are included in peripheral devices. This device is used in SoC to perform various operations.

UART: Universal Asynchronous Receiver Transmitter is included in SoC which is used to transmit or receive serial data. Voltage regulators, Oscillators, clocks, and ADC/DAC are also part of SoC

	
$\fbox{SoC flow design}$
	

![image](https://user-images.githubusercontent.com/118953929/210896144-00b800da-d5f7-4ef3-8b08-8bdb82aa0fae.png)
	

$\fbox{H O W are microchips made ?}$
	
- are made by building up layers of interconnected patterns on a silicon wafer.
	
$\fbox{Introduction to BabySoC}$
	
	
	
* Figure from lecture video:

![image](https://user-images.githubusercontent.com/118953929/210896467-33a87fea-cb93-406c-934f-953c5ce59283.png)
	
$\fbox{BabySoC Components}$
	
	
	- RVMYTH: RVMYTH core is a simple RISCV - basedCPU
	- PLL: A phase-locked loop or PLL is a control system that generates an output signal whose phase is related to the phase of an input signal. 
	- DAC: Adigital-to-analog converter or DAC is a system that converts a digital signal into ananalog signal.
	
$\fbox{Introduction to Modelling}$

	is the process of representing a model which includes its construction and working. This model is similar to a real system, which helps the analyst predict the effect of changes to the system. In other words, modelling is creating a model which represents a system including their properties. It is an act of building a model.
	
Short Additional notes:
	
$\fbox{Simulation is ?}$


- Simulation of a system is the operation of a model in terms of time or space, which helps analyze the performance of an existing or a proposed system. 
- In other words, simulation is the process of using a model to study the performance of a system. It is an act of using a model for simulation.
	
	
</details>

# &#x1F537; Day_12
	
<details><summary><b> Lecture sessions </b></summary>

$\fbox{Simulation and Modelling}$
	
Simulation plays an important role in the design of integrated circuits. Using simulation, a designer can determine both the functionality and the performance of a design before the expensive and time-consuming step of manufacture.


Modeling plays a significant role in the efficient simulation of VLSI circuits. By simplifying the models used to analyze these circuits, it is possible to perform transient analyses with reasonable accuracy at speeds of one or two orders of magnitude faster than in conventional circuit simulation programs

**Batch Mode**
	Note:
The runtime performance reduces if you use -debug,
-debug_all, or -debug_access(+<option>). Use these
options only when you require runtime debug abilities.

Differences between debug_pp and debug_access
	
![image](https://user-images.githubusercontent.com/118953929/211324284-341c884e-467e-4c79-a182-3b306cbc294d.png)



-debug_access option enables the dumping of the VPD and FSDB files for post-process debug, and enables reduced debug capabilities

-debug_access+all enables debug capabilities equal to -debug_all (except it does not apply capability inside cells and encrypted modules)
	




</details>
	

<details><summary><b> Lab activities </b></summary>

$\fbox{modelling RVMYTH(RISC-V)}$

![image](https://user-images.githubusercontent.com/118953929/210915373-872da35b-8f3d-4894-8e6d-4101449991cd.png)
![image](https://user-images.githubusercontent.com/118953929/210916272-f4831d0b-b125-457a-92e0-0472eb1eff39.png)
![image](https://user-images.githubusercontent.com/118953929/210924577-db7ef7b1-d2a5-4e04-9e0d-131e1d8f7ee4.png)

The simulation result:
	
![image](https://user-images.githubusercontent.com/118953929/210925718-e88a5bf4-a8cb-4611-a6fe-30cd7ee9ff96.png)
	
$\fbox{modelling DAC(RISC-V)}$

![image](https://user-images.githubusercontent.com/118953929/211228294-291f6168-ecd3-43a1-824b-b6739853da43.png)

tb code:
	
![image](https://user-images.githubusercontent.com/118953929/211228378-e026ef7b-e5a1-42bb-93e2-9539e805b64f.png)
	
![image](https://user-images.githubusercontent.com/118953929/211228496-8e01e9b4-e232-45a4-9d07-2c0fd0ac9814.png)
	
![image](https://user-images.githubusercontent.com/118953929/211228502-dd5a8390-f549-4c84-8ff5-c4c5abe24612.png)


$\fbox{modelling PLL}$

![image](https://user-images.githubusercontent.com/118953929/211298488-f979cef3-5e7f-41d0-a541-7a6b9c4aa499.png)
![image](https://user-images.githubusercontent.com/118953929/211298560-20ee4d1c-235f-464a-bf62-08c5cc7c6ae3.png)
![image](https://user-images.githubusercontent.com/118953929/211298596-2d1a456e-edd7-4790-8c75-01aa5b5cb860.png)

$\fbox{modelling risc_v and pll}$
	
![image](https://user-images.githubusercontent.com/118953929/211304672-c371300e-994b-4d54-bcd6-4d6a2d9aeb67.png)
![image](https://user-images.githubusercontent.com/118953929/211304842-8aadeaa4-e10a-4911-bfd4-451e7bb8152a.png)
![image](https://user-images.githubusercontent.com/118953929/211304872-6811bb14-9aa1-4528-8b93-19900acb6906.png)


$\fbox{modelling DAC and rvmyth}$
	
use 'real' without wire:
![image](https://user-images.githubusercontent.com/118953929/211309836-68935dc6-fbaf-41c9-bae6-b8b978f4fa74.png)
![image](https://user-images.githubusercontent.com/118953929/211311252-6603760b-8c1f-4821-b497-a8cc0820b28a.png)
![image](https://user-images.githubusercontent.com/118953929/211310945-b2eba314-7543-4a3f-956d-72a984bce842.png)

$\fbox{vsdbabysoc}$
	
![image](https://user-images.githubusercontent.com/118953929/211315652-b845cea4-584b-4aef-aa7e-b8d84679663d.png)
![image](https://user-images.githubusercontent.com/118953929/211319595-e255eaa0-da56-4049-b117-0db4af027e2a.png)
![image](https://user-images.githubusercontent.com/118953929/211319654-a6819370-6cc3-4cbb-89b9-d0d737ed18d2.png)

![image](https://user-images.githubusercontent.com/118953929/211319322-78415321-4bee-419d-90b8-2565a6140974.png)
	
</details>
	
# &#x1F537; Day_13
	
<details><summary><b> Lecture sessions </b></summary>

Pre-Synthesis vs Post-synthesis 
	
	Main idea:
	
	- Pre synthesis simulation: simulation done according to the logic that written. Reports only functionality
	- Post synthesis simulation/gate level simulation: simulation done after synthesis considering each and every gate delays into account. Reports the violations in both functionality and timing.
	- The basic difference is the post-synthesis one has access to the synthesized netlist information, the pre-synthesis doesn't.
	- Using the pre-synthesis option, enables you to see the netlist after the RTL elaboration. Whereas the post synthesis option takes the synthesized input as netlist


Additional notes:
	
- Pre layout netlist: This consists of the information of gate to gate connections according to the logic.

- Post layout netlist: This consists of the gate to gate and pin to pin connection of each gate including buffers.
	
	
	

</details>
	
<details><summary><b> Lab activities </b></summary>
	
![image](https://user-images.githubusercontent.com/118953929/211334771-1099d776-145a-4068-a1b7-a24990f76505.png)
![image](https://user-images.githubusercontent.com/118953929/211334870-16ddde60-7e72-442d-a0c2-b5635cc1688b.png)
![image](https://user-images.githubusercontent.com/118953929/211335892-0cf4f40b-4c37-43c9-8eb2-fccc319b2dc9.png)
![image](https://user-images.githubusercontent.com/118953929/211337498-d853625d-6cf0-4922-b4f2-927e988472c1.png)
![image](https://user-images.githubusercontent.com/118953929/211337569-c6367a8e-6d7c-4e13-8ea4-d3c0960d9cd8.png)

The synthesized code:
	
![image](https://user-images.githubusercontent.com/118953929/211337861-f9e784c3-c2f6-4371-aec7-1bb584a312de.png)

** Not able to proceed with the simulation so far, will update it later. 

</details>
	
# &#x1F537; Day_14
	
<details><summary><b> Lecture Notes </b></summary>
	
R E C A P: 
	

$\fbox{P V T}$

- PVT is the Process, Voltage, and Temperature. In order to make our chip to work after fabrication in all the possible conditions, we simulate it at different corners of process, voltage, and temperature. These conditions are called corners. All these three parameters directly affect the delay of the cell.
	
P R O C E S S:
	
- There are millions of transistors on the single-chip as we are going to lower nodes and all the transistors in a chip cannot have the same properties. Process variation is the deviation in parameters of the transistor during the fabrication.

- Process variation is different for different technologies but is more dominant in lower node technologies because transistors are in millions on the chip. Process variations are due to variations in the manufacturing conditions such as temperature, pressure, and dopant concentrations.  As a consequence, the different transistors have different lengths throughout the chip. This makes the different propagation delay everywhere in a chip because a smaller transistor is faster and therefore the propagation delay is smaller.

![image](https://user-images.githubusercontent.com/118953929/211852246-a1fd654d-b807-4349-b140-8baf53073c4d.png)
	
V O L T A G E:
	
- As we are going to the lower nodes the supply voltage for a chip is also going to less. Let’s say the chip is operating at 1.2V. So, there are chances that at certain instances of time this voltage may vary. It can go to 1.5V or 0.8V. To take care of this scenario, we consider voltage variation.

There are multiple reasons for voltage variation.

	- IR drop is caused by the current flow over the power grid network. 
	- Supply noise caused by parasitic inductance in combination with resistance and capacitance. when the current is flowing through parasitic inductance (L) it will causes the voltage bounce.
	
- Power is distributed to all transistors on the chip with the help of a power grid network. Throughout a chip, the power supply is not constant it will change with the placement of cells. The power grid network is made up of metals and metals have their own resistance and capacitance. So, there is a voltage drop along the power grid.

- The supply voltage reaching the power pins will not be the same for all standard cells and macros because of the resistance variation of the metals.
	
FOR EXAMPLE:

- let's say:
	
Consider there are two cells, one which is placed closer to the DC power source, and others placed far. As the interconnect length is more for the farther cell, it has more resistance and results in a higher IR drop, and it reduces the supply voltage reaching the farthest cell. As the voltage is less, this cell will take more delay to power on than the cell which is placed closer. If nearer cells get higher voltage then the cell is faster and hence the propagation delay is also reduced. That is the reason because of which, there is variation in delays across the transistors.

The delay of a cell is depending on the saturation current and the saturation current of a cell depends on the power supply. In this way, the power supply affects the propagation delay of a cell.

The self-inductance of a supply line contributes also to a voltage drop. For example, when a transistor is switching to high, it takes a current to charge up the output load. This time-varying current (for a short period of time) causes an opposite self-induced electromotive force. The amplitude of the voltage drop is given by V=L*dI/dt, where L is the self-inductance and I is the current through the line.

![image](https://user-images.githubusercontent.com/118953929/211854362-7b01268d-2136-4a82-8dd1-f11166c8562b.png)

T E M P E R A T U R E:
	
- The transistor density is not uniform throughout the chip. Some regions of the chip have higher density and higher switching, resulting in higher power dissipation and Some regions of the chip have lower density and lower switching, resulting in lower power dissipation Hence the junction temperature at these regions may be higher or lower depending upon the density of transistors. Because of the variation in temperature across the chip, it introduces different delays across all the transistors.

** When a chip is operating, the temperature can vary throughout the chip. This is due to the power dissipation in the MOS-transistors. The power consumption in the transistors is mainly due to switching, short-circuit, and leakage power consumption.
	

*** A higher temperature will decrease the threshold voltage. A lower threshold voltage means a higher current and therefore a better delay performance.
	
![image](https://user-images.githubusercontent.com/118953929/211855323-c17b62d3-bb1c-4e92-8aa8-674314485f28.png)


$\fbox{WNS AND TNS}$	
 
	
- Worst Negative Path(WNS) points to the path having the maximum negative slack.
- Total Negative Slack(TNS) gives the sum of all the negative slacks in the design.
	
***From the value of TNS, we can know the severity of the slack in total design and whether to proceed or not with the current design model.

***WNS slack can be negative or zero or positve.
	- If it is +ve, it means that there are no violations and it is giving the least of the positive slack. In this casee, TNS will be zero. 
	
</details>
	
<details><summary><b> Lab activities </b></summary>


- Get all the .lib files in the work directory:
git clone https://github.com/Geetima2021/vsdpcvrd.git
![image](https://user-images.githubusercontent.com/118953929/211857653-31abe17e-2ffb-4e56-8a5c-8e0216d49043.png)

> __WARNING!__  : you won't be able to read the lib file. WHY..? There are some errors. 
	
Delete the line from the .lib with the error stated. (REPEAT THIS FOR ALL THE .LIB) 
![image](https://user-images.githubusercontent.com/118953929/211857690-c990d5f8-3112-4e56-bca3-95c006289946.png)
	
After done editing the file, 
	
- Load lc_shell and read_lib, the write the lib into db:
	
![image](https://user-images.githubusercontent.com/118953929/211858677-0e9b5700-8a41-4820-8930-ea46e70f5c0c.png)
![image](https://user-images.githubusercontent.com/118953929/211858823-c558935b-f2de-4ec6-9360-11960e11b4d6.png)
![image](https://user-images.githubusercontent.com/118953929/211859291-49c15183-c24c-4eda-b159-98a9cdeec23b.png)
![image](https://user-images.githubusercontent.com/118953929/211859366-f49cda5d-c30f-4993-8ab7-1330d28fc7e8.png)

- Add all the .db file that had been converted into the ~/.synopsys_dc.setup to set for the target_library and link_library, separately:
	
- Make sure the link files are correct, separately, each:
![image](https://user-images.githubusercontent.com/118953929/212579297-cdae8d91-3fe7-40b7-a219-fc9382b821c4.png)


	
- read_verilog vsdbabysoc.v (current_design is clk_gate) incorrect
![image](https://user-images.githubusercontent.com/118953929/211861987-c82cbce2-4694-4049-a3d0-1599975f44d0.png)

- read_file {vsdbabysoc.v avsd_pll_1v8.v avsddac.v mythcore_test.v} -autoread -format verilog -top vsdbabysoc
![image](https://user-images.githubusercontent.com/118953929/211870687-4ba059dd-a31e-46c0-93c8-9c676f254486.png)

- get the in/o:
	
![image](https://user-images.githubusercontent.com/118953929/211870805-ac60873e-bfe3-463f-b677-97c9e28526db.png)

-link and compile, each time:
	
![image](https://user-images.githubusercontent.com/118953929/212579321-099e3494-5056-418e-88e1-19f00421af89.png)


Report_qor before constrainining:

![image](https://user-images.githubusercontent.com/118953929/211870972-b316b9de-9752-4854-b03a-e73606984362.png)

Constraints:
	
![image](https://user-images.githubusercontent.com/118953929/211871057-2e778107-d109-42d1-85ca-544d5ea5bf28.png)
	
Report_qor:

pasted one of db:
	
![image](https://user-images.githubusercontent.com/118953929/212579395-8e799ff1-6a20-4b15-8bf3-245c7e08dbe9.png)
	
summary:
	
	
![image](https://user-images.githubusercontent.com/118953929/212579890-f9d065df-87ed-4c2b-a81c-30488eccd650.png)
	
** the number doesnt look ok to me, will try with changing the constraint value., again



</details>

	
# &#x1F537; Day_15
	
<details><summary><b> Lecture : How to talk to computers 
	--> Introduction to QFN-48 Package, chip, pads, core, die and IPs </b></summary>
	
	
![image](https://user-images.githubusercontent.com/118953929/212797814-388f5725-e6a3-4622-90b0-625383c68a2a.png)

$\fbox{H O W is the chip is connected to the package ?}$

![image](https://user-images.githubusercontent.com/118953929/212799685-d7bee61d-32ba-470f-bbdd-2a2b111c3780.png)

$\fbox{I N S I D E the chip}$
	
![image](https://user-images.githubusercontent.com/118953929/212807090-56eaa46b-7dbd-472f-b29b-56ec9f1a5c2b.png)

EG: 

RISCV SoC

	
![image](https://user-images.githubusercontent.com/118953929/212810025-7f10447a-3cf8-4c32-b4ae-8f380e8104a2.png)
	

</details>

<details><summary><b> Lecture : How to talk to computers --> Introduction to RISC-V </b></summary>


$\fbox{RISC-V Instruction Set Architecture (ISA) }$
	

![image](https://user-images.githubusercontent.com/118953929/212811505-0a19d7ba-118f-40ad-8a27-a9e763cbe108.png)


**Additional take aways:
	
- An assembly language is a type of low-level programming language that is intended to communicate directly with a computer’s hardware. Unlike machine language, which consists of binary and hexadecimal characters, assembly languages are designed to be readable by humans
	
	MAIN POINTS:
	
	- An assembly language is a type of programming language that translates high-level languages into machine language.
	- It is a necessary bridge between software programs and their underlying hardware platforms.
	- Assembly language relies on language syntax, labels, operators, and directives to convert code into usable machine instruction.
	- Assembly language may pass through single-pass or multi-pass assemblers, each with specific uses and benefits.
	- Today, assemble languages are rarely written directly, although they are still used in some niche applications such as when performance requirements are particularly high.

	

</details>

<details><summary><b> Lecture : How to talk to computers --> From software Applications to Hardware </b></summary>
	

![image](https://user-images.githubusercontent.com/118953929/212911857-3e329b2f-13c6-4327-afd3-402096e22cfd.png)

	
</details>
	
<details><summary><b> SKY_L1 - Introduction to all components of open-source digital asic design </b></summary>

	
$\fbox{Open Source Digital Asic Design }$
	
ASIC 
- EDA tools 
	- Qflow
	- OpenROAD
	- OpenLANE
- RTL Designs
	- librecores.org
	- opencores.org
	- github.com
- PDK Data
	
W H A T is PDK ?
	
- PDK basically stands for Process Design Kit 
- Collection of files used to model a fabrication process for the EDA tools used to design an IC 
	
Eg:

OpenPDK SkyWater ( Real )
	
- The SkyWater Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which can be used to create manufacturable designs at SkyWater’s facility.

- As of May 2020, this repository is targeting the SKY130 process node. If the SKY130 process node release is successful then in the future more advanced technology nodes may become available.


</details>
	
<details><summary><b> SKY_L2 - Simplified RTL2GDS flow </b></summary>


$\fbox{Simplified RTL to GDSll Flow}$
	
![image](https://user-images.githubusercontent.com/118953929/212916119-3f6487ac-6c0a-472f-bf07-e5fca890cacd.png)
	
- Synthesis
- Floor/Power Planning
- Placement
- Clock Tree Synthesis
- Routing
- Sign off
	
SYNTHESIS:
	
- Converts RTL to a circuit out of components from the standard cell library (SCL)
- Standards cells have regular layout
- Each cells comes with different views/models 
	eg:
	- Electrical, HDL, SPICE, etc
	
FLOOR/POWER PLANNING:
	
- Chip Floor-planning 
	- Partition the chip die between different system building blocks and place the I/O pads
	
- Macro Floor-planning
	- Defines the dimensions, pin locations, rows definition, and routing tracks
	
- Power Planning
	- typically shift the power by power pads. 
	
PLACEMENT:
	
- Place the cells on the floorplan rows, alligned with the sites;
	- theoretically, should be place close to each other to reduce interconnect delays, and enable successful routing.
	- usually done in 2 steps;
		- Global
		- Detailed
	
CTS
	
- Create a clock distribution network
	- To deliver the clock to all sequential elements 
	- with minimum skew (zero is hard to achieve)
	- and in a good shape

ROUTE
	
- Implement the interconnect using the available metal layers
- Metal tracks form a routing grid
- Routing grid is huge
- Divide and Conquer
	- Global Routing: Generates routing guides
	- Detailed Routing: Uses the routing guides to implement the actual wiring
		
SIGN OFF

- Physical Verifications
	- Design Rules Checking (DRC)
	- Layout vs Schematic (LVS)
	
- Timing Verification
	- Static Timing Analysis (STA)
	
	
</details>
	
<details><summary><b> SKY_L3 - Introduction to OpenLANE and Strive Chipsets </b></summary>

$\fbox{Introducing OPENLANE}$
	
- Started as an Open-Source Flow for a True Open Source Tape-Out Experiment
- Strive is a family of open everything SoCs 
	- Open PDK, Open EDA, Open RTL
	
Strive SoC family
	
![image](https://user-images.githubusercontent.com/118953929/212922415-e9ae6732-9c44-47d1-a84f-ddc0dfa64390.png)


M A I N Goal:
- Produce a clean GDSll with no human intervention ( no-human-in-the-loop )
	- CLEAN means:
		- No LVS violations
		- No DRC violations
		- Timing Violations 
	
- Can be used to harden Macros and Chips 
	- Two modes of operation:
		- Autonomous or Interactive
	
- Design Space Exploration:
	- Find the best set of flow configurations
	
- Large number of design examples


</details>
	
<details><summary><b> SKY_L3 - Introduction to OpenLANE detailed ASIC design flow </b></summary>

_M a c r o Hardening Flow_:

![image](https://user-images.githubusercontent.com/118953929/212925732-7a0b43eb-6728-46f4-9b98-96f9be9a4b57.png)
	
	1) RTL Synthesis and STA
		- The design is synthesized into a gate-level netlist using yosys and static timing analysis is performed on the resulting netlist using OpenSTA
	2) Insertion of DFT structures
		- An open-source Design For Testability (DFT) toolchain, Fault, can optionally be used to modify the netlist, inserting scan chains and the necessary IO ports to scan and test the design after fabrication
	3) Physical Implementation
		- Advancing with the physical implementation, we note that most of the tools in this stage are used from within the OpenROAD application in combination with other tools, some of them are custom and based on the OpenDB infrastructure, while others are indpendent
	4) Post routing evaluation of results
		- DRC and LVS are then performed using magic and netgen. Antenna checking is performed by either OpenROAD’s ARC (Antenna Rule Checker) or using magic. Extraction of parasitics from the routed layout is then done using SPEF EXTRACTOR, followed by another round of static timing analysis to have more accurate timing reports that correspond to the actual physical layout.

	The final outputs of the flow, among various physical views and reports, are mainly GDSII and LEF views, which can be used in bigger designs



</details>
	
<details><summary><b> Get familiar to open-source EDA tools - SKY_L1 - OpenLANE directory in detail </b></summary>
	
![image](https://user-images.githubusercontent.com/118953929/212942090-379e8cd0-3311-40a1-a3c7-88de54d54e7c.png)
![image](https://user-images.githubusercontent.com/118953929/212942183-8a1399d3-029d-4b94-8590-83dcaabb6435.png)
![image](https://user-images.githubusercontent.com/118953929/212942298-37695fbf-bd41-4754-aab3-05abb8d3b321.png)
![image](https://user-images.githubusercontent.com/118953929/212942374-740c80c7-0425-491e-999a-c84d438774ac.png)
![image](https://user-images.githubusercontent.com/118953929/212942467-59ee491f-02e3-4b09-8c6a-995528cb519a.png)

</details>
	
<details><summary><b> Get familiar to open-source EDA tools - SKY_L2 - Design Preparation Step </b></summary>
	
![image](https://user-images.githubusercontent.com/118953929/212947848-0a680040-7114-4299-89b2-fd209ee1d2c8.png)
![image](https://user-images.githubusercontent.com/118953929/212947916-56a209ab-c429-4a7e-9d1a-9d1bd4232905.png)
![image](https://user-images.githubusercontent.com/118953929/212948017-1bda242e-5153-486a-90f2-ddfd36d28de4.png)
![image](https://user-images.githubusercontent.com/118953929/212948304-44a14a79-f4f5-4f0e-9591-14f47d8c59eb.png)

</details>
	
<details><summary><b> Get familiar to open-source EDA tools - SKY_L3 - Review files after design prep and run synthesis </b></summary>

![image](https://user-images.githubusercontent.com/118953929/212953648-16f68d70-c64b-411a-831e-68ed941301ff.png)

</details>
	
<details><summary><b> Get familiar to open-source EDA tools - SKY_L4 - OpenLANE Project Git Link Description </b></summary>

Reference links:
	
- https://github.com/efabless/openlane
- https://gitlab.com/gab13c/openlane-workshop
- https://github.com/efabless/OpenLane#openlane-design-stages
- https://github.com/efabless/OpenLane/blob/master/docs/source/advanced_readme.md
	
	

***RUN IN SEQUENCE:\
	run_synthesis\
	run_floorplan\
	run_placement\
	run_cts\
	run_routing\
	write_powered_verilog followed by set_netlist \
	::env(DESIGN_NAME).powered.v\
	run_magic\
	run_magic_spice_export\
	run_magic_drc\
	run_lvs\
	run_antenna_check

</details>
	
<details><summary><b> Get familiar to open-source EDA tools - SKY_L5 - Steps to characterize synthesis results </b></summary>
		
![image](https://user-images.githubusercontent.com/118953929/212957604-ebff835e-9f23-48ca-9d2d-6ffe08f3c78e.png)
![image](https://user-images.githubusercontent.com/118953929/212959719-449894d8-97ac-49f3-83ce-32a67a9bdca8.png)
![image](https://user-images.githubusercontent.com/118953929/212959770-e4485ae1-6a4b-4d06-8409-2f4c64efa2eb.png)
![image](https://user-images.githubusercontent.com/118953929/212960310-f5ad163d-2f00-4253-915b-3925ccf35af2.png)

</details>
	
	
# &#x1F537; Day_16
	
<details><summary><b> Chip Floor Planning considerations - SKY_L1 - Utilization factor and aspect ratio </b></summary>

$\fbox{HOW do we define Width and Height of Core and Die ?}$

![image](https://user-images.githubusercontent.com/118953929/212966415-64630003-c8ba-4708-8f08-f698798b284b.png)
![image](https://user-images.githubusercontent.com/118953929/212966504-053e534f-697c-4081-8116-366ebc474ff8.png)

Small R E C A P on die and core 
	
![image](https://user-images.githubusercontent.com/118953929/212966626-15394ea5-9577-40d4-8a14-40aed6c94eb9.png)

So now, place all the logical cells inside the 'core'

![image](https://user-images.githubusercontent.com/118953929/212967297-3af75f49-de2d-4f3a-bb16-0f4d61b1f1d8.png)

100 % utilization 
	
Utilization Factor = Area Ocupied by Netlist / Total Area of the core
	
	So, in our case:
	
	UF = (4 x 1 sq unit)/(2 unit x 2 unit)
	   = 4 sq unit/ 4 sq unit
	   = 1 
	
	--> Utilization Factor is 1 , which means --> core is completedly occupied, no any extra standard cells is allowed to add/ NOT POSSIBLE at all
	
****So, in real industry, we always go for 0.5 or 0.6 Utilization Factor ( more logical and realistic )

</details>
	
<details><summary><b> Chip Floor Planning considerations - SKY_L2 - Concept of pre-placed cells </b></summary>
	
Aspect ratio= Height/Width
	
![image](https://user-images.githubusercontent.com/118953929/212970023-896969e3-f07c-4212-954d-e2cbf38cdde2.png)

$\fbox{HOW do we define Locations of Pre-placed cells ?}$
	
![image](https://user-images.githubusercontent.com/118953929/212972143-ff56a183-2f16-44c2-8185-1220ee92c5ad.png)
![image](https://user-images.githubusercontent.com/118953929/212972189-ba984aa5-e42c-4bb4-98c6-cbf63e7630ad.png)
![image](https://user-images.githubusercontent.com/118953929/212972227-2fc5f4c5-bf8c-428e-8bc2-14ffd29d49f7.png)
	
Eg:

- Similarly, ip's available:
	
![image](https://user-images.githubusercontent.com/118953929/212972559-ee6daacc-0c30-4233-ada5-b88c48093c2f.png)
	
- The arrangement of these IP's in a chip is referred as FLOORPLANNING
- These IP's/blocks have user-defined location, hence are placed in chip before automated placement-and-routing and are called as _**pre-placed cells**_
- Automated placement and routing tools places the remaining logical cells in the design onto chip

</details>
	
<details><summary><b> Chip Floor Planning considerations - SKY_L3 - De-coupling capacitors </b></summary>
	
![image](https://user-images.githubusercontent.com/118953929/212974068-9ae552ee-335a-4ae3-9cdc-7cc6decd2397.png)
	
So now,
	
$\fbox{HOW do we surround pre-placed cells with Decoupling capacitors ?}$

Consider the amount of the switching current required for a complex circuit something like below:
	
![image](https://user-images.githubusercontent.com/118953929/212974477-b8e01cfc-78e5-4538-bea7-b81965f8e239.png)
	
1) Consider capacitance to be zero for the discussion. Rdd, Rss,Ldd and Lss are well defined values.
2) During switching operation, the circuit demands switching current eg, peak current
3) Now, due to the presence of Rdd, and Ldd, there will be a voltage drop across them anf the voltage at Node 'A' would be Vdd' instead of Vdd
	
Scenario:
	
- If Vdd' goes below the noise margin, due to Rdd and Ldd, the logic '1' at the output of the circuit wont be detected as logic '1' at the input of the circuit

Noise Margin summary:
Figure from lecture's video:
![image](https://user-images.githubusercontent.com/118953929/212976318-cd96a95c-69d9-4d38-ac5a-74a12bc1f666.png)

** For any signal to be considered as logic '0' and logic '1', it should be in the NM(L) and NM(H) ranges, respectively
	
S O L U T I O N 
	
: Add Decoupling Capacitors
	
- Addition of Decoupling Capacitor in parallel with the circuit 
- Everytime the circuit switches, it draws current from Cd, whereas, the RL network is used to replenish the charge into Cd
	
![image](https://user-images.githubusercontent.com/118953929/212977499-b1201d65-3d26-4e29-9d44-06ef3828c70e.png)

</details>
	
<details><summary><b> Chip Floor Planning considerations - SKY_L4 - Power Planning </b></summary>
	
$\fbox{HOW do we do Power Planning ?}$
	
![image](https://user-images.githubusercontent.com/118953929/212978098-9ec27062-da28-46aa-8ca2-86157b324197.png)
![image](https://user-images.githubusercontent.com/118953929/212978932-10c21dca-df8b-4c2e-bf5d-c0f4025980d0.png)
![image](https://user-images.githubusercontent.com/118953929/212979703-9e054c2f-1c25-4dfa-8dd8-b39efa9eac84.png)

This meant :
- all capacitors which were charged to 'V' volts will have to discharge to '0' volts through single 'Ground' tap point. 
- This will cause a bump in 'Ground' tap point. -- Ground Bounce
![image](https://user-images.githubusercontent.com/118953929/212979819-69a923ab-7d79-4d06-9e91-3d3a47ebfeaf.png)
- Also, all capacitors which were '0' volts will have to charge to 'V' volts through single 'Vdd' tap point. 
- This will cause lowering of the voltage at 'Vdd' tap point.
- The Voltage droop is happened. 

![image](https://user-images.githubusercontent.com/118953929/212980567-9329bb01-e882-4161-a6ee-0cc277adb860.png)

</details>

<details><summary><b> Chip Floor Planning considerations - SKY_L5 - Pin Placement and logical cell placement blockage </b></summary>

$\fbox{HOW do we do Pin Placement ?}$

![image](https://user-images.githubusercontent.com/118953929/213513844-4cdcd0c0-e4d5-41dd-8346-b6df511e0463.png)
![image](https://user-images.githubusercontent.com/118953929/213518348-f40b6bcb-ceb6-4cd2-94ef-9fd16e2c21eb.png)
	
</details>

<details><summary><b> Chip Floor Planning considerations - SKY_L6 - Steps to run floorplan using OpenLANE </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213522001-75c855b5-31fc-49b5-9991-589699936853.png)
![image](https://user-images.githubusercontent.com/118953929/213522037-cedf9d09-1b66-4ddd-ae96-753a737172c5.png)
![image](https://user-images.githubusercontent.com/118953929/213522149-bc7321c5-1876-4da8-8ff8-f2fe0293d750.png)
![image](https://user-images.githubusercontent.com/118953929/213522190-ce2c4950-b4aa-4506-bd07-d564f303ff27.png)
![image](https://user-images.githubusercontent.com/118953929/213522230-fb1ab5c9-0077-4b10-8834-89dbadddcb4b.png)


</details>

<details><summary><b> Chip Floor Planning considerations - SKY_L7 - Review floorplan files and steps to view floorplan </b></summary>
	
![image](https://user-images.githubusercontent.com/118953929/213527358-67b7b0a3-028a-4b19-bae0-31e3e3c44e84.png)
![image](https://user-images.githubusercontent.com/118953929/213527404-968b8e58-0616-4f66-be78-3c72f5589043.png)
![image](https://user-images.githubusercontent.com/118953929/213527455-42f92f16-69a2-447c-bd39-ed03415a7744.png)
![image](https://user-images.githubusercontent.com/118953929/213527595-e5032a89-288d-43ed-bc96-53e323c9b98d.png)


</details>

<details><summary><b> Chip Floor Planning considerations - SKY_L8 - Review floorplan layout in Magic </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213529963-dac83f08-8803-45e9-bd57-9b381b880e74.png)
![image](https://user-images.githubusercontent.com/118953929/213530001-c0f5f221-540b-4bd7-b34e-615ece09e8bf.png)
![image](https://user-images.githubusercontent.com/118953929/213530045-2d87fb15-176e-4a19-907d-3704ccd2fff9.png)

	
</details>

<details><summary><b> Library Binding and Placement - SKY_L1 - Netlist binding and initial place design </b></summary>

$\fbox{HOW do we do Placement and Routing ?}$
	
First, we must bind the netlist with physical cells

![image](https://user-images.githubusercontent.com/118953929/213533455-2259e9dd-80d5-47c6-85b3-65fc072204b4.png)
![image](https://user-images.githubusercontent.com/118953929/213533493-ad1fb6b9-7994-410e-a962-e4df35918142.png)
![image](https://user-images.githubusercontent.com/118953929/213533532-fed5a5af-5a1d-47ab-aea2-f562ae59d5de.png)
![image](https://user-images.githubusercontent.com/118953929/213533600-b227fa2e-cc90-44c5-9bf3-154e27e11313.png)

</details>

<details><summary><b> Library Binding and Placement - SKY_L2 - Optimize placement using estimated wire-length and capacitance </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213534733-0744067e-ec16-45af-9605-cea308bed7db.png)

OPTIMIZE PLACEMENT

- This is the stage where we estimate wire length and capacitance and, based on that, insert repeaters.
	
</details>
	
<details><summary><b> Library Binding and Placement - Final placement optimization </b></summary>


The placement happens for each stage of the FF condition:

Eg; for the 2nd stage:

![image](https://user-images.githubusercontent.com/118953929/213537358-511e1900-c3bf-4840-9ead-79c6d935bb23.png)


</details>
	
<details><summary><b> Library Binding and Placement - Need for libraries and characterization </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213540900-fd273e39-9b63-4b25-bce5-d0584ff5ca75.png)



</details>
	
<details><summary><b> Library Binding and Placement - Congestion aware placemnet using Replace </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213540804-b3d632c3-de22-48f4-b001-73862cf229fa.png)
![image](https://user-images.githubusercontent.com/118953929/213541184-e0f298ec-701a-4a2f-8a0f-9b92e12d5ea7.png)
![image](https://user-images.githubusercontent.com/118953929/213541205-9b80c7a8-4e08-4a4e-b78d-ed14d21f1954.png)
![image](https://user-images.githubusercontent.com/118953929/213541237-5a6eaf93-1324-4bf7-a142-a1d3d3d1c2ec.png)

</details>
	
<details><summary><b> Cell design and characterization flows - Inputs for cell design flow </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213543184-488cb0c5-bdf8-4ed5-afcc-65eaeac30fd2.png)
![image](https://user-images.githubusercontent.com/118953929/213543208-a4bfdff4-9a8e-4146-855f-66a35594f84e.png)
![image](https://user-images.githubusercontent.com/118953929/213543247-536f4c5a-6e18-4a72-97d8-79e25f3b344e.png)

	
</details>

<details><summary><b> Cell design and characterization flows - Circuit design step </b></summary>
![image](https://user-images.githubusercontent.com/118953929/213544288-7806aa54-ef2f-4864-8172-4ec58b190f82.png)
	
- Supply voltage --> noise margin level ( by top level)
- Metal layer --> certain lib built on certain metal layer
- Pin location --> user define
- Drawn gate-length --> user define
![image](https://user-images.githubusercontent.com/118953929/213544341-d5acc5b6-6560-4f2c-b458-e98829ff3b6b.png)

	
</details>
	
<details><summary><b> Cell design and characterization flows - Layout design step </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213545811-683299fa-ee68-4373-b5df-250849e1c68e.png)
![image](https://user-images.githubusercontent.com/118953929/213545926-0e958055-d8b2-44f2-a97e-5d9e8b4f1636.png)
![image](https://user-images.githubusercontent.com/118953929/213546404-a1c152d9-5cb4-4e2c-95be-91c23b3bdf02.png)

	
</details>
	
<details><summary><b> Cell design and characterization flows - Typical characterization flow </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213547150-314a0bd6-2ad7-4eb8-9397-9c834b2ae5a6.png)

Steps:
	- Read model file
	- Read extracted SPICE netlist
	- Define behaviour of buffer
	- Read sub circuit of inverter
	- Attach necessary power sources 
	- Apply stimulus
	- Provide commands
	

	
</details>

<details><summary><b> General timing characterization parameters - Timing threshold definition </b></summary>

![image](https://user-images.githubusercontent.com/118953929/213548260-64e1647a-cd5c-4b0a-8671-bc6f16413dd2.png)
![image](https://user-images.githubusercontent.com/118953929/213548311-7b691555-277b-473c-907f-469254a387ef.png)
![image](https://user-images.githubusercontent.com/118953929/213548360-502436ed-3999-489f-ac44-64b3efce05a0.png)
![image](https://user-images.githubusercontent.com/118953929/213548420-f9b1b6e4-ea76-40f5-8adc-93735a91063e.png)

** threshold -- 50% of the input
	


</details>

<details><summary><b> General timing characterization parameters - Propagation delay and transition time </b></summary>

H O W to calculate propagation delay?

![image](https://user-images.githubusercontent.com/118953929/213548611-c18b2f33-fa0a-42c3-935a-0befea7ede66.png)

Eg:
Here, it a positive delay:
![image](https://user-images.githubusercontent.com/118953929/213548794-f73eb31f-5040-4c5b-a9f5-5e57a73051fa.png)

So, as when the threhold point changes, it becomes negative delay
![image](https://user-images.githubusercontent.com/118953929/213548914-90bc7faf-71cd-494f-a53f-aec7f1176ea7.png)
	
H O W to calculate transition time?
	
![image](https://user-images.githubusercontent.com/118953929/213549068-c0b5c6ad-0f7a-4c0e-810a-21511c252b6f.png)
![image](https://user-images.githubusercontent.com/118953929/213549109-a99b0699-a960-4e04-9bd1-33634cd1fd4b.png)

Eg:
![image](https://user-images.githubusercontent.com/118953929/213549182-0171ad01-f8f8-4e76-85c4-dfb6755430e9.png)

</details>

# &#x1F537; Day_17

<details><summary><b> Lectures </b></summary>

</details>
	
<details><summary><b> LABS </b></summary>

![image](https://user-images.githubusercontent.com/118953929/215629834-8be51aab-588c-4609-ba36-af8a0a8f3597.png)

Inside openlane/configurations:

![image](https://user-images.githubusercontent.com/118953929/215629888-7d276006-2146-4f20-9998-e1ad990d6d60.png)
![image](https://user-images.githubusercontent.com/118953929/215629904-1052ef64-e7a7-410c-9661-aafb27c78add.png)

Set it in the run and rerun floorplan 

![image](https://user-images.githubusercontent.com/118953929/215629954-8b9f214a-c914-4771-af9e-d1e25d1c901c.png)
![image](https://user-images.githubusercontent.com/118953929/215629966-b144ddeb-f2b3-4854-8009-e510ae239d09.png)

Run magic full command and observe again:

![image](https://user-images.githubusercontent.com/118953929/215630003-20398a30-76c9-4cb9-bb3c-a488e09bc659.png)

Lab steps to git clone vsdstdcelldegin
	
(in openlance directory) git clone https://github.com/nickson-jose/vsdstdcelldesign.git
	
![image](https://user-images.githubusercontent.com/118953929/215630042-e5305e15-6d9b-4095-acaa-5764e20e271d.png)
![image](https://user-images.githubusercontent.com/118953929/215630052-3a8198b3-71ef-44ce-8be4-8f7d71a900a8.png)
![image](https://user-images.githubusercontent.com/118953929/215630063-6de8b185-7996-4169-84ae-5bc37b4c7592.png)

Copy tech file over 
![image](https://user-images.githubusercontent.com/118953929/215630084-ccf11d4c-c0eb-4788-ba00-33341973bab3.png)
	
Magic command:
	
![image](https://user-images.githubusercontent.com/118953929/215630215-95248be9-9fe9-45a7-8077-69c3536adbfa.png)
![image](https://user-images.githubusercontent.com/118953929/215630227-327220cd-625a-47d3-a7c6-cd403f064a63.png)

	
Introduction to Sky130 basic layers layout and LEF using inverter
	
![image](https://user-images.githubusercontent.com/118953929/215630245-007596cf-9cd0-4ab1-9a9f-edff0054b5a1.png)
![image](https://user-images.githubusercontent.com/118953929/215630264-ec957972-9d33-4c0d-a1ee-9d7375909fc5.png)

Press s 3 times to see connection:

![image](https://user-images.githubusercontent.com/118953929/215630286-9dd149c5-3465-4e90-b086-c02170104e15.png)

Steps to create std cell layout and extract spice netlist

![image](https://user-images.githubusercontent.com/118953929/215630320-0c6cfa11-df3d-4162-adf0-a59cb3794367.png)
![image](https://user-images.githubusercontent.com/118953929/215630334-68e315c3-6b36-4756-b02c-632ee3375f10.png)
DRC next error: zoom to the DRC area:

![image](https://user-images.githubusercontent.com/118953929/215630355-8b299efc-2c1a-4b37-a312-de10a3dd078c.png)
![image](https://user-images.githubusercontent.com/118953929/215630362-e64a8bba-9202-44cb-97d2-74e6d9f8a950.png)
![image](https://user-images.githubusercontent.com/118953929/215630369-7a01b7c8-9218-4b5d-ad13-031dee05af40.png)
![image](https://user-images.githubusercontent.com/118953929/215630378-c826605d-e55d-4b7c-85d8-9244418f3224.png)

	
Lab Steps to create final SPICE deck using Sky130 tech 
	
sky130_inv.spice

![image](https://user-images.githubusercontent.com/118953929/215630430-ca1615ba-1780-49f3-ada8-046ae949dfa9.png)
![image](https://user-images.githubusercontent.com/118953929/215630438-b282e270-cc46-4c8b-92a9-9c4de74dc196.png)

Pmos and nmos libs
	
![image](https://user-images.githubusercontent.com/118953929/215630472-6e07a040-5a6f-4634-a7ba-5f00a08723f4.png)

Nmos lib

![image](https://user-images.githubusercontent.com/118953929/215630530-f7733c29-fd5f-4329-92e5-baa99444781e.png)

	
Modified inv.spice

![image](https://user-images.githubusercontent.com/118953929/215630562-2a1b0635-114d-4598-8578-cd8e9d92e530.png)
	
Steps to characterize inverter using sky130 model files

![image](https://user-images.githubusercontent.com/118953929/215630598-aa910321-0a9d-4151-aeed-548bf0046a94.png)
	
Plot y vs time a
	
![image](https://user-images.githubusercontent.com/118953929/215631121-27c10b23-02b0-418c-9324-a769acc20634.png)

Rise/Fall/Delay Rise/Delay Fall value:

![image](https://user-images.githubusercontent.com/118953929/215630719-5b591e06-99e0-4d50-af4d-64208e6d584d.png)

![image](https://user-images.githubusercontent.com/118953929/215630733-0b5a6ee9-d9f8-4694-8235-87cdd111d9b7.png)

![image](https://user-images.githubusercontent.com/118953929/215630744-42869336-af48-465f-85e0-239a48f25db1.png)

![image](https://user-images.githubusercontent.com/118953929/215631242-950107d1-e7c0-47cd-bc0a-1347438e3e52.png)

	
Temperature used:

![image](https://user-images.githubusercontent.com/118953929/215631307-408736cf-6020-44c6-8a5a-9cf67194ec03.png)


Introduction to Sky130 pdk's and steps to download labs
	
![image](https://user-images.githubusercontent.com/118953929/215631353-8ebe48c7-4b3d-42f8-820a-2a9cfbc724e4.png)
![image](https://user-images.githubusercontent.com/118953929/215631365-79c9692e-fe23-41a9-af58-2622aebabdcb.png)
![image](https://user-images.githubusercontent.com/118953929/215631377-35e0b24f-34b9-41e0-add3-e601aad8eb1d.png)
![image](https://user-images.githubusercontent.com/118953929/215631388-24ac77ad-163e-4668-a0de-4b7c0fd2fff6.png)
![image](https://user-images.githubusercontent.com/118953929/215631404-13e09f10-3724-4073-a8d0-50e46fd22239.png)

magic -d XR
![image](https://user-images.githubusercontent.com/118953929/215631452-e07f393f-33f3-4b92-bc95-bc13a4e578a7.png)

![image](https://user-images.githubusercontent.com/118953929/215631467-9f39f350-7eb9-46e4-800c-97d915202ecb.png)

![image](https://user-images.githubusercontent.com/118953929/215631486-cfa03949-110b-4195-95d7-653b24bf407a.png)
	
Introduction to Magic and steps to load Sky130 tech-rules

![image](https://user-images.githubusercontent.com/118953929/215631534-7a248ece-a5fa-4506-9cb2-03a5c935d456.png)


Fix poly.9 error in Sky130 tech-file

![image](https://user-images.githubusercontent.com/118953929/215631589-3d203e6c-d758-4600-9efa-78af9afbead2.png)

![image](https://user-images.githubusercontent.com/118953929/215631612-e238d257-6b6e-44df-88e0-cd6ccbce25f5.png)

![image](https://user-images.githubusercontent.com/118953929/215631637-11f47afe-72a4-4ff6-8dea-5716db08a3c6.png)
	
![image](https://user-images.githubusercontent.com/118953929/215631663-b516bfea-3afc-4365-9332-f4300a25d073.png)

![image](https://user-images.githubusercontent.com/118953929/215631690-84491761-ca31-4b25-a8cd-c7240108c5db.png)
	
![image](https://user-images.githubusercontent.com/118953929/215631707-f4cd6fb7-3412-4295-a8cd-6352b1a23320.png)

![image](https://user-images.githubusercontent.com/118953929/215631727-8bf2f147-3ab0-4c70-8aad-918ba1a1c304.png)
	
Find missing or incorrect rules and fix them
	
![image](https://user-images.githubusercontent.com/118953929/215631770-70308368-53df-42a2-9ca7-9cf1287ac4a4.png)
	
![image](https://user-images.githubusercontent.com/118953929/215631787-812983f7-2b9a-4312-8291-fb041f1ad8d3.png)

	
</details>
	


# &#x1F537; Day_18
	
<details><summary><b> LABS </b></summary>

![image](https://user-images.githubusercontent.com/118953929/215631948-d378b7fd-cc13-441a-8b15-3d91b992c1c6.png)
![image](https://user-images.githubusercontent.com/118953929/215631955-f965fbf8-6214-4db9-8d3d-bda403c6992d.png)
![image](https://user-images.githubusercontent.com/118953929/215631967-909c2aae-6ce5-46ac-8dbf-54c93df7f784.png)
![image](https://user-images.githubusercontent.com/118953929/215631995-4e842e88-c12c-41a8-a5c0-a42a380a207a.png)
![image](https://user-images.githubusercontent.com/118953929/215632013-055cf8cf-e634-4c2e-9581-474b3832ba2d.png)
![image](https://user-images.githubusercontent.com/118953929/215632036-ff18c7f9-4046-4ea7-9b2c-32a8482bc150.png)
![image](https://user-images.githubusercontent.com/118953929/215632200-c97cc0ce-3af2-43a7-924c-3a2269c032a8.png)
![image](https://user-images.githubusercontent.com/118953929/215632222-0341097c-ee95-407e-9580-f7b009552067.png)
![image](https://user-images.githubusercontent.com/118953929/215632240-efbf8fee-65c7-4b5e-80b0-fa6015960a43.png)
	
Introduction to timing libs and steps to include new cell in synthesis

![image](https://user-images.githubusercontent.com/118953929/215632282-a563e7c4-da99-4b79-ad2b-a7a338454282.png)
![image](https://user-images.githubusercontent.com/118953929/215632294-c7edbe9e-5c22-4659-80a3-4d93454fa7ef.png)
![image](https://user-images.githubusercontent.com/118953929/215632405-1512e834-0d5a-4633-a778-44a406ed7266.png)
![image](https://user-images.githubusercontent.com/118953929/215632415-cb47683b-b520-4d29-ba85-920e739693d5.png)
![image](https://user-images.githubusercontent.com/118953929/215632434-9ba9ec9b-118d-4097-9563-52fd01e71816.png)
	
Steps to configure synthesis settings to fix slack and include vsdinv

![image](https://user-images.githubusercontent.com/118953929/215632467-2ec13a07-df84-4a6a-808a-5dacda2de605.png)
	
![image](https://user-images.githubusercontent.com/118953929/215632481-51a7bd7d-d181-433d-b44a-3cc134ee8c52.png)
	
Rerun synthesis and you will get 0 value

![image](https://user-images.githubusercontent.com/118953929/215632497-0761ed45-9a39-4700-9555-ab58ed092929.png)

![image](https://user-images.githubusercontent.com/118953929/215632518-9de7cf62-cb71-4680-af66-66e0b03c92f9.png)



</details>


	
# &#x1F537; Day_19

<details><summary><b> LECTURES </b></summary>

Routing and Design Rule Check (DRC) - Introduction to Maze Routing Lee's Algorithm


What is Lee's Algorithm?
- is one possible solution for maze routing problems. It always gives an optimal solution, if one exists, but is slow and requires large memory for dense layout.
	
How does it works?

The algorithm is a breadth-first based algorithm that uses queues to store the steps. It usually uses the following steps:
	

- Choose a starting point and add it to the queue.
- Add the valid neighboring cells to the queue.
- Remove the position you are on from the queue and continue to the next element.
- Repeat steps 2 and 3 until the queue is empty.
	
So , going deeper on the route stage

![image](https://user-images.githubusercontent.com/118953929/221397389-ef845648-6409-4216-b049-f31950569ac6.png)
![image](https://user-images.githubusercontent.com/118953929/221397416-68a738d8-7c8c-4a9e-9a12-c2849104d54d.png)

now that the routing occurs:
![image](https://user-images.githubusercontent.com/118953929/221397462-3aa65cc5-c2d6-426b-b5fa-c5a1401a7555.png)

Design Rule Checking
	
![image](https://user-images.githubusercontent.com/118953929/221398196-e62ddcc8-7e18-4283-926a-8caa021f1031.png)

Types of DRC :
	
![image](https://user-images.githubusercontent.com/118953929/221398277-77f1b8f3-fc60-48d7-95be-612c0ebbc926.png)
![image](https://user-images.githubusercontent.com/118953929/221398288-d77e1367-2122-435b-8150-f26b747223b2.png)
![image](https://user-images.githubusercontent.com/118953929/221398723-521a6551-7d7d-497e-a7de-9819c911d112.png)

Example of DRC:

![image](https://user-images.githubusercontent.com/118953929/221398765-0a30d272-b011-4692-a0f9-f45b7d174fe0.png)
![image](https://user-images.githubusercontent.com/118953929/221398791-c0176afc-e531-4bd3-9671-0baf8f5c29df.png)
![image](https://user-images.githubusercontent.com/118953929/221398800-74694d97-89a9-4506-be22-20b576f2b9df.png)

Parasitics Extraction:
	
![image](https://user-images.githubusercontent.com/118953929/221399069-844aa806-af9e-483a-b026-a686ac74b46d.png)
Path Components :
Din2_net : Wire/Net (SPEF : *D_NET)
▪Driver : Port “Din2” (SPEF : *P)
▪Driver Type : Not Specified (SPEF : *D)
▪Receiver :  Internal Pin “Buf1/a” (SPEF : *I)
▪Lumped Capacitance▪3 Distributed Resistance (SPEF : *RES)
▪3 Distributed Capacitance (SPEF : *CAP)

SPEF Equivalent 
*NAME_MAP
*1 Din2
*2 Din2_net
*D_NET *2 0.15
*CONN
*P *1 I
*I Buf1:a *L 0.15

Quick revision:
![image](https://user-images.githubusercontent.com/118953929/221399165-35d25751-6473-4f28-bd01-f95133aee36a.png)

	
</details>
	
	
# &#x1F537; Day_20
	
<details><summary><b> LECTURES </b></summary>

R E C A P:
	
PHYSICAL DESIGN FLOW:

- cardinal process of converting synthesized netlist, design curtailment and standard library to a layout as per the design rules provided by the foundry

![image](https://user-images.githubusercontent.com/118953929/217577150-af183779-eaeb-4383-a334-65300aa8052c.png)
![image](https://user-images.githubusercontent.com/118953929/217577281-97ad7567-c77e-414e-9864-e3635c3e70f6.png)


	
Files extantions:

- lib --> Technology Library source file. Technology libraries contain information about the characteristics and functions of each cell provided in a semiconductor vendor's library. Semiconductor vendors maintain and distribute the technology libraries.
- tf --> Vendor Technology File. This file contains technology-specific information such as the names, characteristics (physical and electrical) for each metal layer, and design rules. These information are required to route a design.
- *spef --> Standard Parasitic Exchange Format. File format to save parasitic information extracted by the place and route tool.
- *def --> Design Exchange Format. This format is often used in Cadence tools to represent physical layout. Synopsys tools normally use Milkyway format to save design.
- *.lef --> Library Exchange Format. Standard cells are often saved in this format. Cadence tools also often use this format. Synopsys tools normally use Milkyway format for standard cells.
- *mw( Milkyway database) --> The Milkyway database consists of libraries that contain information about your design. Libraries contain information about design cells, standard cells, macro cells, and so on. They contain physical descriptions, such as metal, diffusion, and polygon geometries. Libraries also contain logical information (functionality and timing characteristics) for every cell in the library. Finally, libraries contain technology information required for design and fabrication.
- db --> Technology Library. This is a compiled version of * lib in Synopsys database format.





</details>
	

<details><summary><b> LABS </b></summary>
	
![image](https://user-images.githubusercontent.com/118953929/217547784-68b189ad-e5a5-451f-a562-d95dfd5064c6.png)
![image](https://user-images.githubusercontent.com/118953929/217549754-909c2de5-759f-40d7-9cf1-f9e1f0142e7c.png)
Successfully read rvmyth
![image](https://user-images.githubusercontent.com/118953929/217549853-b9d752e9-3637-49f1-9a2d-e527e4e15448.png)
![image](https://user-images.githubusercontent.com/118953929/217550615-48cf3728-f6ca-42a3-9b7f-636c48fefd7a.png)
read library files
![image](https://user-images.githubusercontent.com/118953929/217571871-ac91b772-5070-4c21-a4c5-689875c7bde9.png)
	
![image](https://user-images.githubusercontent.com/118953929/217573102-47b7a426-1624-41ee-9901-2c8ced58ffd1.png)

read_lib for sky130 lib
![image](https://user-images.githubusercontent.com/118953929/217573237-983d9a57-7d4d-47e3-86a3-2fc55a2a99af.png)	

![image](https://user-images.githubusercontent.com/118953929/217572105-45cba9f7-96b9-4834-b745-fc3ad72c8983.png)

![image](https://user-images.githubusercontent.com/118953929/217578230-a553d133-b54e-45c9-ae32-d5d89edb81a5.png)
![image](https://user-images.githubusercontent.com/118953929/217578593-3154a00a-c1a2-441b-adc8-3f0817731bc1.png)

create_clocks, first, get the pins name for a correct one in your design
	
![image](https://user-images.githubusercontent.com/118953929/217591811-12c6a26d-a958-4392-9cc5-e59ac280a15e.png)
![image](https://user-images.githubusercontent.com/118953929/217591884-0b3612c3-a9db-4d0f-b581-be9e6550ee53.png)
![image](https://user-images.githubusercontent.com/118953929/217593708-2ef9112d-e3dd-424a-a3cc-3b3293d62094.png)

check_design and observe the warning( warnings are ok, without errors)
	
![image](https://user-images.githubusercontent.com/118953929/217594205-629a1fba-374d-4fe3-b6fb-b6dd2cf82726.png)
![image](https://user-images.githubusercontent.com/118953929/217594274-9d5e06b0-5bff-4e4e-888a-db796465aaff.png)
![image](https://user-images.githubusercontent.com/118953929/217599418-e3469e58-74aa-44bf-9111-e72b430d3d5c.png)
![image](https://user-images.githubusercontent.com/118953929/217599876-c83e4d5a-610f-453b-9ade-fce15706a335.png)
![image](https://user-images.githubusercontent.com/118953929/217599536-57142372-48db-4d95-8517-1ccea5c895c9.png)

Writing reports:
![image](https://user-images.githubusercontent.com/118953929/217601503-a81e06c4-75ff-414b-9257-ffdecb7bee2e.png)
![image](https://user-images.githubusercontent.com/118953929/217601565-6b5b7028-ff73-470d-9d34-72188de713bd.png)

Checking the reports:
	
Area and timing met:
![image](https://user-images.githubusercontent.com/118953929/217602279-6b77fb31-df36-4912-a45e-61016d4e90ff.png)

Power wise:
![image](https://user-images.githubusercontent.com/118953929/217602729-b2eccac9-816d-4bbe-a1aa-f2876cea45c5.png)

Schematic views:

![image](https://user-images.githubusercontent.com/118953929/217604138-db1f9422-e983-4d0d-b35d-ecd96c918002.png)

Overall view zooming in:
	
![image](https://user-images.githubusercontent.com/118953929/217604476-8d8b1366-779c-4131-a1bd-230bc0f8e37c.png)
![image](https://user-images.githubusercontent.com/118953929/217604542-cb5dea37-7c3b-42da-a3d8-a1e1f82f1d71.png)
![image](https://user-images.githubusercontent.com/118953929/217604638-e9011bfd-b81f-4f27-91d1-21ecce6b2d1a.png)
![image](https://user-images.githubusercontent.com/118953929/217604729-f75a65ac-124f-49ff-a14d-2783bada53b8.png)
![image](https://user-images.githubusercontent.com/118953929/217604808-9ffa68ee-e8c3-4e2a-b5b1-b99ec5d6bda6.png)
![image](https://user-images.githubusercontent.com/118953929/217605041-057091c7-724b-4cb8-b156-8834c6cb220c.png)


source top.tcl
	
![image](https://user-images.githubusercontent.com/118953929/218739356-17b71278-1555-4e73-a98f-f727a739fd21.png)
![image](https://user-images.githubusercontent.com/118953929/218739457-a9a4978e-297d-43ce-a8b8-549e2681e825.png)
![image](https://user-images.githubusercontent.com/118953929/218739561-2ed73710-e447-4ab7-b154-a94b7c7987d9.png)
![image](https://user-images.githubusercontent.com/118953929/218739632-0ea7aa1f-a6a6-40b0-81d7-4822401b0a44.png)

in icc2_shell

![image](https://user-images.githubusercontent.com/118953929/218741158-a40f34ae-b7b2-481d-8fee-c1ecbf82dba1.png)
![image](https://user-images.githubusercontent.com/118953929/218741081-ff751040-7426-486d-bfe3-050d7706834f.png)

Errors:
![image](https://user-images.githubusercontent.com/118953929/218790193-59fc3146-4051-4cd5-8058-d2cf61a0a55b.png)


	
the edits:
	
![image](https://user-images.githubusercontent.com/118953929/218789391-115130f8-2ead-4c05-982c-4c4265f28e11.png)
![image](https://user-images.githubusercontent.com/118953929/218789551-18349d82-8f1d-4307-8c9e-380d8d59b007.png)
	
grdgenxo -itf2TLUPlus -i /nfs/png/disks/png_mip_gen6p9ddr_0023/sepin/sd_training/new/new2/synopsys_ICC2flow_130nm/synopsys_skywater_flow_nominal/itf_files/skywater130.nominal.itf -o /nfs/png/disks/png_mip_gen6p9ddr_0023/sepin/sd_training/new/new2/synopsys_ICC2flow_130nm/synopsys_skywater_flow_nominal/itf_files/skywater130.nominal.tluplus

![image](https://user-images.githubusercontent.com/118953929/219232692-c1f4d3e0-0d4a-4bd0-830c-152fb03874ff.png)
![image](https://user-images.githubusercontent.com/118953929/219231086-a69de8ef-0b86-4893-9f05-876538930d38.png)
	
After done generating TLUPlus file, include inside this tcl below:
	
![image](https://user-images.githubusercontent.com/118953929/219395422-42765210-9bc6-4d82-ba4f-67c01ba0a42d.png)

Sourcing top.tcl again now
	
![image](https://user-images.githubusercontent.com/118953929/219407123-820af282-f86b-4535-8a8f-a048ce232e19.png)
![image](https://user-images.githubusercontent.com/118953929/219406861-d3893ede-56c6-44bc-9756-e0b229302609.png)
![image](https://user-images.githubusercontent.com/118953929/219412712-f2161039-7938-4c44-84ef-e77a1d768b77.png)

Floorplan view:
![image](https://user-images.githubusercontent.com/118953929/219413223-8fc62e34-66ca-4ef7-9cd1-f9e9133c4fe1.png)

Closed-up view:

Floorplan:
![image](https://user-images.githubusercontent.com/118953929/219413959-196917b8-061d-4fb5-9773-0ff69867749f.png)

Filler cells:
![image](https://user-images.githubusercontent.com/118953929/219415629-d0b88c7a-f2f6-4c1c-95d0-af46989933f4.png)
	
DAC
![image](https://user-images.githubusercontent.com/118953929/219413787-a93ce88d-a26a-45d3-a428-9809fe57ba21.png)
	
![image](https://user-images.githubusercontent.com/118953929/219420378-b73af34b-f690-44e1-8136-d31a97e9580b.png)

![image](https://user-images.githubusercontent.com/118953929/219421949-b422679f-fe52-4e0d-b403-c254e38b1bc8.png)
![image](https://user-images.githubusercontent.com/118953929/219422237-57fcb1c4-387c-4137-8426-6de8ae021711.png)

Total violations:
![image](https://user-images.githubusercontent.com/118953929/219424226-4ded56eb-82c4-47ee-980d-99c502d61819.png)
![image](https://user-images.githubusercontent.com/118953929/219424145-371861be-940b-4f1e-a83d-148f2c74ed73.png)

</details>
	

<details><summary><b> LABS - Experiment changing 7% utilization to 40% </b></summary>

Change from 7% to 40%

![image](https://user-images.githubusercontent.com/118953929/219425852-ed07c31e-9641-4317-8a11-9241fab18d9e.png)

After done, load gui again;

![image](https://user-images.githubusercontent.com/118953929/219429591-0b85fe42-d32d-40bd-bf9a-6557ae8d2c12.png)

Observe that the size is a lot more bigger (DAC)

Full floorplan:

![image](https://user-images.githubusercontent.com/118953929/219432652-6966993d-cfb8-44e2-b90f-84d2277b4899.png)
![image](https://user-images.githubusercontent.com/118953929/219432999-529da363-935f-4732-b322-7c0bff094086.png)

![image](https://user-images.githubusercontent.com/118953929/219433335-f819f93c-2e64-4304-8c53-d7b0025b6163.png)
![image](https://user-images.githubusercontent.com/118953929/219433505-61b76c32-219b-4332-88a1-e6b2512b5a77.png)
Violated slack is lesser
![image](https://user-images.githubusercontent.com/118953929/219433569-c812cb98-437b-4a26-a5ba-9f05e3fc51a3.png)
Violations is more lesser than before:
![image](https://user-images.githubusercontent.com/118953929/219434125-70ad4232-c033-4f20-8859-270e21d00f1a.png)



</details>
	
# &#x1F537; Day_21

<details><summary><b> LECTURE </b></summary>


PLACEMENT - simple word --> process of determine the location of standard cells

or in details:
	
- Placement is the process of finding a suitable physical location for each cell in the block.
Tool only determine the location of each standard cell on the die. 
- Placement does not just place the standard cell available in the synthesized netlist, it also optimized the design.
- The tool determines the location of each of the standard cell on the core.
	
Additional knowledge:
	
	
	checks before doing placement:
	
	After completion of floorplanning, power planning and placement of physical only cells Endcap cells and Tap cells, we check the base DRC and errors related to floorplanning like vertical spacing error, horizontal spacing error, min site row, vertical site row, and alignment. After inserting the tap cells, check to ensure that a standard cell peaceable area is protected by tap cells. Tap cells are placed correctly or not. Tap cells are typically used when most or all of the standard cells in the library contains no substrate or well taps. Generally, the design rule specifies the maximum distance allowed between every transistor in a standard cells and a well or substrate tap.
	Advanced nodes often requires the insertion of additional tap cells to manage the substrate and well noise. Before placing the standard cells we add boundary cells (Endcap cells) also, which are added to the ends of the cell rows and around the boundaries of objects such as core and hard macros and we checked that endcap cells are placed or not. After you have done the floorplanning i.e. created the core area, placed the macros and decided the power network structure of your design, it is time to let the tool do standard cell placement

	
</details>
	
<details><summary><b> LABS </b></summary>
	
Now that the placement stage will occurs:
	
![image](https://user-images.githubusercontent.com/118953929/219437313-631c4f9a-d629-49e8-a441-57252998d66d.png)
![image](https://user-images.githubusercontent.com/118953929/219438428-758c4d3b-63e2-4ffe-9cfe-ecbfe4157c85.png)


Timing estimation:

![image](https://user-images.githubusercontent.com/118953929/219437456-0d06131a-6422-471f-8654-6bb2a8d0a438.png)
	
![image](https://user-images.githubusercontent.com/118953929/219438219-0e8c5342-1d4d-48fa-bc7e-7702dbace8a3.png)
![image](https://user-images.githubusercontent.com/118953929/219438306-4c3743b5-e9c6-4062-8b13-9e5e6118ac8d.png)
	
Reports file generated under rpts_icc2 directory in the path:
vsdbabysoc.post_estimated_timing.rpt
	
![image](https://user-images.githubusercontent.com/118953929/219439729-0762e1b0-1eda-4b97-bb21-461d1b62d2c3.png)
![image](https://user-images.githubusercontent.com/118953929/219440002-0af6e677-acf5-45c2-a9c2-2bde62a27826.png)
	
vsdbabysoc.post_estimated_timing.qor.sum:
	
![image](https://user-images.githubusercontent.com/118953929/219440389-9befe0e5-7eb3-430f-8b86-da24337b6f2e.png)
	
vsdbabysoc.post_estimated_timing.qor
	
![image](https://user-images.githubusercontent.com/118953929/219440920-3f9baae0-dc1d-4b73-9a4b-e553d9741e54.png)
![image](https://user-images.githubusercontent.com/118953929/219440983-44403d5b-ccae-4eda-ae2f-cd4be03bc8f5.png)
	
check_design.pre_pin_placement:

![image](https://user-images.githubusercontent.com/118953929/219441506-44b7e7ef-0b5d-487e-b3b5-c91385d431bc.png)

report_port_placement.rpt:
![image](https://user-images.githubusercontent.com/118953929/219441745-e45627b8-b557-4bcc-9a98-90fcc9cc66d9.png)

	
</details>
	
# &#x1F537; Day_22

<details><summary><b> LECTURE </b></summary>

Clock Tree Synthesis
	
- is a technique for distributing the clock equally among all sequential parts of a VLSI design.
- The purpose of CTS is to reduce skew and delay. 

Inputs required for CTS:
- Detailed Placement database
- Buffers or inverters for creating the clock tree
- Latency target if delay and skew are supplied
- DRC clock tree (Max Tran, Max Cap, Max fanout, Max number of buffer levels)
	
Outputs for CTS:
- def 
- spef
- netlists 
	
Effects of CTS:
- clock buffers get added
- congestion get increased
- non-clock cells get relocated to less desirable places
- timing and maximum tran/cap violations take place
	
Limitations of CTS
- Latency
- skew
- Max Tran
- Max Cap
- Max fanout
- buffers and inverters

Example: 

![image](https://user-images.githubusercontent.com/118953929/218802102-7ec85ac9-a7b4-4589-9872-2b529354f036.png)

H-Tree
In this algorithm Clock routing takes place like the English letter H.\
It is an easy approach that is based on the equalization of wire length.\
In H tree-based approach the distance from the clock source points to each of the clock sink points are always the same.\
In H tree approached the tool trying to minimize skew by making interconnection to subunits equal in length.

This type of algorithm used for the scenario where all the clock terminal points are arranged in a symmetrical manner like as in gate array are arranged in FPGAs.
	
![image](https://user-images.githubusercontent.com/118953929/218802718-9efba76a-f6c8-4284-9007-295146d4b86a.png)

In this routing algorithm all the wires connected on the same metal layers, we don’t need to move horizontal to vertical or vertical to horizontal on two layers.
	
H tree do not produce corner sharper than 900 and no clock terminals in the H tree approach in close proximity like X tree.


Advantages:\
Exact zero skew in terms of distance (here we are ignoring parasitic delay) due to the symmetry of the H tree.\
Typically used for very special structures like top-level clock level distribution not for the entire clock then distributed to the different clock sinks.

Disadvantages:\
Blockages can spoil the symmetry of the H tree because sometimes blockages are present on the metal layers.\
Non-uniform sink location and varying sink capacitance also complicate the design of the H tree.

</details>
	
<details><summary><b> LABS </b></summary>

Place, CTS, Route:
	
![image](https://user-images.githubusercontent.com/118953929/219443077-b19f52da-f4e0-4a49-904d-8cb1db780be4.png)

Check the report of the check_legality--> check_legality.rpt

No violations
![image](https://user-images.githubusercontent.com/118953929/219443555-a6b868a7-4788-4f4f-87eb-1317fba16a3e.png)
![image](https://user-images.githubusercontent.com/118953929/219443624-18eae0c0-890a-408f-88bb-ff1f499b3e48.png)

check_clock_tree.rpt
	
Having one warning:

![image](https://user-images.githubusercontent.com/118953929/219443895-479dd7f0-73aa-403a-bc38-5dab7fb280b7.png)
	
Warnings detail:
![image](https://user-images.githubusercontent.com/118953929/219444137-a7f285dc-efab-4d58-a90b-b757b418a9aa.png)

Clock tree option reports:
![image](https://user-images.githubusercontent.com/118953929/219444315-8faf04ad-aef3-4f4a-9439-b8a985ce9fdb.png)
	
Legalize_placement:

![image](https://user-images.githubusercontent.com/118953929/219444844-d5db8866-0b06-45b4-8b2c-d288f8d1985d.png)
![image](https://user-images.githubusercontent.com/118953929/219444906-eb3efbd7-18ef-4d6a-a59a-561406c1a06c.png)
	
</details>
	
# &#x1F537; Day_23

<details><summary><b> LECTURE </b></summary>

Clock tree consume more than 50 % of dynamic power. The components of this power are:\
1) Power consumed by combinatorial logic whose values are changing on each clock edge\
2) Power consumed by flip-flops and\
3) The power consumed by the clock buffer tree in the design.



$\fbox{Clock Tree Synthesis (clock gating)}$
- Clock gating is one of the techniques used to save the dynamic power of clock elements in the design.

***Principle behind clock gating: The principle behind clock gating is to stop the clock of those sequential elements whose data is not toggling. RTL level code talks only about data transfer.
	
$\fbox{Routing}$

- Routing is the process of creating physical connections based on logical connectivity.
	
![image](https://user-images.githubusercontent.com/118953929/219449301-015c471e-88e3-4166-b849-3d0a0fc4b6af.png)
	
**Inputs and Outputs of Routing**
	
Inputs: 
- Netlist with location of blocks and locations of pins (CTS completed)
- Timing budget for critical net
- Technology File
- TLU + File
- SDC
	
Outputs:
- .gds
- .spef
- .sdc
	

W H A T to check before we do routing?
	
- Placement completed
- CTS completed
- Power and ground nets routed
- Estimated congestion - acceptable
- Estimated timing - (~0 ns slack)
- Estimated max cap/trans - NO violations
	
</details>
	
# &#x1F537; Day_24

<details><summary><b> LECTURE </b></summary>
	
$\fbox{ECO - Engineering Change Order}$

-  refers to a practice in the VLSI design flow to accommodate specification changes, to rectify functional errors, or to fix non-functional design requirements, such as timing and power, with minimal disturbance to the existing implementation, to save as much as possible the already-spent optimization efforts

VLSI design and ECO flows figure: 
(source:https://people.eecs.berkeley.edu/~alanmi/publications/other/date20_eco1.pdf)

![image](https://user-images.githubusercontent.com/118953929/219450985-f985a16c-57af-4fe7-84cb-74810eabe127.png)
	
	
So basically there are the following steps in each ECO cycle.

- Analysis of an issue on the latest database
- ECO generation for fixing the issue
- ECO Implementation on the analyzed database
- Save the database after ECO implementation for the next ECO cycle
	

</details>
	
<details><summary><b> LABS </b></summary>
	
	
![image](https://user-images.githubusercontent.com/118953929/219445995-f59454b0-8b6c-4c92-a5fe-e1f6357f3bdc.png)
![image](https://user-images.githubusercontent.com/118953929/219446129-eb74e396-1ef3-4f8f-b18f-71a181400950.png)
![image](https://user-images.githubusercontent.com/118953929/219446202-453a64d6-658a-4f5e-95e9-2601b19b70c3.png)

slack:
![image](https://user-images.githubusercontent.com/118953929/219446347-3349d985-9c52-4e84-9b06-5763f289a85b.png)

![image](https://user-images.githubusercontent.com/118953929/219446584-786ae5f6-0e92-4920-876e-c850f0ddf7bc.png)

		
</details>
	
# &#x1F537; Day_25

HAD BEEN COVERED IN PREVIOUS SESSION
	
# &#x1F537; Day_26

<details><summary><b> LECTURE </b></summary>

$\fbox{Electronic signal}$

a time-varying voltage that is also an electromagnetic wave carrying information, though it can take on other forms, such as current
	
TYPEs of electronics signals
	
Analog signal
- is time-varying and generally bound to a range (e.g. +12V to -12V), but there is an infinite number of values within that continuous range. 
- An analog signal uses a given property of the medium to convey the signal’s information, such as electricity moving through a wire. 
- In an electrical signal, the voltage, current, or frequency of the signal may be varied to represent the information
	
![image](https://user-images.githubusercontent.com/118953929/219452794-2bf40dc1-af5f-41b3-9e5d-dbab6d0ca7c7.png)

	
Digital Signal
	
- A digital signal is a signal that represents data as a sequence of discrete values. 
- A digital signal can only take on one value from a finite set of possible values at a given time. With digital signals, the physical quantity representing the information can be many things: 

	- Variable electric current or voltage\
	- Phase or polarization of an electromagnetic field\
	- Acoustic pressure\
	- The magnetization of a magnetic storage media
	
![image](https://user-images.githubusercontent.com/118953929/219453074-9e6b7452-e11b-4799-a390-08590099ce34.png)
	
$\fbox{W H A T are mixed-signal chips?}$

- that at least partially deal with input signals whose precise values matter

_**AMS - analog and mixed signal(digital and analog)**_
	
From lecture slide:
	
![image](https://user-images.githubusercontent.com/118953929/219453354-ff78de5e-247f-4410-9e74-a436a619ac0b.png)

![image](https://user-images.githubusercontent.com/118953929/219453540-c6fdd40d-23a2-4f11-9f00-68d66e029ceb.png)
	
$\fbox{W H A T are IP cores?}$
	
- consists of a block of logic or data that is used in a semiconductor chip. It is usually the intellectual property of a particular person or company. 
- IP cores are used when making a fieldprogrammable gate array (FPGA) or application-specific integrated circuit (ASIC).
- IP cores are created throughout the design process and can be turned into components for reuse.There are different categories for IP cores including **hard IP cores** and **soft IP cores**.
	- The soft IP core , can be customized during the physical design phase and mapped to any process technology.
	- A hard IP core is one that has the logic implementation and the physical implementation.
	

HOW it works in semiconductor industry?
	
![image](https://user-images.githubusercontent.com/118953929/219454263-0e1f2ee3-d586-4c02-876d-2952a2c80b73.png)

</details>
	
# &#x1F537; Day_27
	

<details><summary><b> LECTURE </b></summary>

$\fbox{Introduction to Crosstalk-Glitch and Delta delay}$
	
What is signal integrity and crosstalk?
	
- Signal integrity is the ability of an electrical signal to carry information reliably and resist the effects of high-frequency electromagnetic interference from nearby signals.

- Crosstalk is a type of noise signal that corrupts the actual signal while transmission through the communication medium.
	
Aggressor and victim nets
	
- a net that receives undesirable cross-coupling effects from a nearby net is called a victim net
- a net that causes these effects in a victim net is caleed an aggressor net
	
Crosstalk-Glitch

![image](https://user-images.githubusercontent.com/118953929/220734557-0962f4bf-6561-42f1-a25e-17e7bf88b2f2.png)

Performing Crosstalk delay analysis

- Enable PrimeTime SI  set_app_varsi_enable_analysistrue
- Back-annotate the design with cross-coupling capacitance information in a SPEF or GPD file  read_parasitics -keep_capacitive_coupling file_name.spf
	

Reporting Crosstalk Settings
	
To check your crosstalk settings:
•report_si_delay_analysis
•report_si_noise_analysis
•report_si_aggressor_exclusion
	
	
</details>
	
# &#x1F537; Day_28

<details><summary><b> LECTURE </b></summary>

LIVE SESSION:

$\fbox{Introduction to DRC and LVS}$

So from the Physical Design Flow Chart, now it's at $\mathcal{\textcolor{purple}{Physical Verification and Sign off stage}:
![image](https://user-images.githubusercontent.com/118953929/220624648-0bcfb347-afdf-44e9-a52f-6fc4352e72a4.png)

Design Rule Check (DRC)
- determine if the layout satisfies a set of rules required for manufacturing

Layout vc Schematic (LVS)
- Verifying the layout created is functionally same as the shcematic or netlist of the design
	
Antenna Rule Check (ARC)
- Process antenna effect or “plasma induced gate oxide damage” is a manufacturing effect.

Electrical Rule Check (ERC)
- Involves checking a design for all electrical connections that are considered dangerous
	
	
$\fbox{INTRODUCTION to SkyWater PDK}$

- joint project between Google and the SkyWater Technology Foundry, which provides a fully open source Process Design Kit (PDK), and its related resources

- PDK - Process Design Kit
- SKY130 - feature size of the process(130nm), where SKY refers to the manucturer ( SkyWater foundry )
	
![image](https://user-images.githubusercontent.com/118953929/220634606-6dc5fdd1-ca71-42a1-a9a8-923e78780fe3.png)

The SkyWater open PDK public repository contains the following:

- Documentation
- PDK Library and files
- Community

![image](https://user-images.githubusercontent.com/118953929/220631652-dcb4b05c-b0f0-4389-bd64-553397296bc8.png)

**NOTE: The "130" in SKY130 stands for the feature size, which is the length of smallest transistor that can be manufactured in the process.

![image](https://user-images.githubusercontent.com/118953929/220633393-30b09627-1bc2-446a-ba9b-60a4b6d8c58d.png)
	
$\fbox{Open Source PDK Tools}$
	
- open_pdks - a makefile based installer that takes files from SkyWater PDKs and then reformats them.
	
Tools: 
	
- Magic
- Klayout
- Openlane
- Xschem
- Netgen
- Ngspice
- IVerilog
- qflow
- IRSIM
- xcircuit

![image](https://user-images.githubusercontent.com/118953929/220639090-1497b827-e297-4b97-99c5-f476c9bdd974.png)

	Steps to install the Sky130 PDK
	- git clone https://github.com/RTimothyEdwards/open_pdks
	- cd open_pdks
	- configure --enable-sky130-pdk
	- make
	- sudo make install
	
	
$\fbox{Understanding the SkyWater PDK - Layers}$
	
![image](https://user-images.githubusercontent.com/118953929/220647512-ff502023-03db-4b4f-b6a4-03b714bda96a.png)
![image](https://user-images.githubusercontent.com/118953929/220654602-ccfbb917-2e3a-42c7-8fa1-cc87566947f9.png)
![image](https://user-images.githubusercontent.com/118953929/220656247-f42f3bad-bb7d-41cf-bfa5-1364d55ae7c6.png)
![image](https://user-images.githubusercontent.com/118953929/220656359-f9f1cb7d-93a2-41fd-a3c8-aa4ad33476ab.png)
![image](https://user-images.githubusercontent.com/118953929/220656721-b499540b-a38d-4007-a044-d0a8d6e92249.png)
![image](https://user-images.githubusercontent.com/118953929/220656873-8cbcd197-3bc4-4e57-a2b4-b823a38afc32.png)
![image](https://user-images.githubusercontent.com/118953929/220659723-395eb61f-a412-42b5-a34b-6eff16034ee0.png)
![image](https://user-images.githubusercontent.com/118953929/220659842-7cb0b4fd-4b25-47de-af04-cfde18ae58e1.png)
![image](https://user-images.githubusercontent.com/118953929/220659999-bc572cd2-59fe-4511-a248-3aa9cf1e770f.png)
![image](https://user-images.githubusercontent.com/118953929/220661220-62311514-6564-4153-aea3-7577585d66a8.png)

$\fbox{Understanding the SkyWater PDK - Devices}$
	
![image](https://user-images.githubusercontent.com/118953929/220661503-357ab4c1-168b-4978-99d2-e35163e95e6e.png)
![image](https://user-images.githubusercontent.com/118953929/220673116-c3626885-b196-422c-b0da-0f756351f33c.png)
![image](https://user-images.githubusercontent.com/118953929/220673242-386104d8-5552-41aa-8748-c4a864ec7717.png)
![image](https://user-images.githubusercontent.com/118953929/220684748-f0fc47db-85eb-4ae0-aaf7-c24253b7a007.png)
![image](https://user-images.githubusercontent.com/118953929/220684978-08cb78ef-dc30-4942-abd0-175fcca2da5d.png)
![image](https://user-images.githubusercontent.com/118953929/220685227-aee26eea-e824-4476-a8f7-028e523de0a3.png)
![image](https://user-images.githubusercontent.com/118953929/220686668-c29f31d8-adbd-4604-a09b-0447cda9512e.png)
![image](https://user-images.githubusercontent.com/118953929/220686825-1ee6ece5-7756-4984-816e-8debb45b6163.png)


$\fbox{Understanding the SkyWater PDK - Libraries}$
	
- should contain everything that user needs to work with
- 3 types of libraries:
	- Digital standard cells
	- I/O cells
	- Primitive devices and models
	
Digital standard cells
![image](https://user-images.githubusercontent.com/118953929/220694239-73dd748a-a9bc-4ab6-b9ae-d491c40404e3.png)

Naming convention:
sky130_vendor_library -type [_name]
	
![image](https://user-images.githubusercontent.com/118953929/220696830-04818663-5e75-42a8-a63c-39f615f1ebdf.png)
![image](https://user-images.githubusercontent.com/118953929/220697157-25165139-3661-4a14-a5ff-37b9e89e68da.png)
	
** double underscore --> separating library name and cell type
	

I/O cells
![image](https://user-images.githubusercontent.com/118953929/220698375-8d8f4584-9bf6-4c82-a0d5-3e88600ff4b8.png)
![image](https://user-images.githubusercontent.com/118953929/220698578-43905909-ae52-4952-89f5-325a6831f45d.png)

Primitive devices and models
![image](https://user-images.githubusercontent.com/118953929/220699321-c7743706-e675-4210-ade4-9d9a7505144d.png)
![image](https://user-images.githubusercontent.com/118953929/220700896-ab9bb4cc-d0e9-45b7-8310-bdea9d35d096.png)

Vertical Parallel Plate capacitor:
![image](https://user-images.githubusercontent.com/118953929/220708881-a605aac6-1165-4d5c-9bd4-b15c8b19fd3f.png)


$\fbox{OpenSource Tools and Flows}$
	
Example:
A simple manual design flow

1.Schematic --> export netlist(spice format) to ngspice(simulate) and generate magic
- xschem 
	- ngspice (analog simulation)
	- gaw (waveform viewing)
	
2.Layout
- import magic to initial layout 
![image](https://user-images.githubusercontent.com/118953929/220711085-30fa7cf4-bbb7-49a3-85f8-136bbd8bcd47.png)

3. LVS
from schematic --> export to netlist --> schematic capture
from layout --> export to netlist --> extraction

both imported to LVS(netgen) 


	
</details>
	
<details><summary><b> Labs </b></summary>

$\fbox{Tool installations and basic DRC/LVS design flow}$
	
CHECK TOOL INSTALLATIONS

- Magic: brings up a layout window and a console window that is a stock tcl interpreter used to run commands for layout and actions
	
- netgen: run Netgen using the command netgen in the terminal. Its console window is a stock tcl interpreter like magic as well

- Xschem: should bring up a schematics window. xschem has no seperate console window and uses the native command line terminal for tcl commands. Xschem can be run in batch mode with the command xschem --tcl filename.tcl -q.

- Ngspice: has its own prompt and runs its own set of interpreter commands that aren't based on tcl
	
CREATING SKY130 DEVICE LAYOUT IN MAGIC

![image](https://user-images.githubusercontent.com/118953929/220715251-12343c1d-6e23-4fc1-9bbe-ba0f93096fe4.png)
![image](https://user-images.githubusercontent.com/118953929/220716298-6e8f1e54-4b0b-4581-80ed-d6fea589a7eb.png)
![image](https://user-images.githubusercontent.com/118953929/220717152-5ac633f5-e000-4b7a-a388-a8697a45b97e.png)
Then, run xschem to load up the display:
	
![image](https://user-images.githubusercontent.com/118953929/220717914-828df447-2515-49ad-9436-54bd40ec7c81.png)

When you invoke magic, 2 windows will be popped up:
	
![image](https://user-images.githubusercontent.com/118953929/220719640-55c84fd4-b2f4-406b-8bfd-a217e44e4844.png)


	Magic shortcuts from videos:
	
	Left and right mouse buttons to adjust the cursor box
	Shift+Z to zoom out
	Middle mouse button/P to select a layer (also known as painting)
	E to erase whatever is present in the cursor box (can also be done ny clicking the middle mouse button on an empty part of the layout)
	V can be used to view the entire layout
	CTRL+P opens up the parameter options for the selected device
	S key can be used to select layers
	Typing the what command in the magic console gives information on the selected layer
	; key can be used to type commands in the magic console without moving between windows, until the Enter key is 	pressed
	I key can be used to select a device, and M key is used to move them

![image](https://user-images.githubusercontent.com/118953929/220720808-02549b3e-f0d6-413a-9eff-ccdc6627dec8.png)
![image](https://user-images.githubusercontent.com/118953929/220721737-ca18ed8b-d377-4254-817a-1ae71ff1f4e1.png)
No more rings, when you unchecked the ring box
	
![image](https://user-images.githubusercontent.com/118953929/220721954-4c2bc2aa-7db1-4481-80f7-d9b4ee651c14.png)
![image](https://user-images.githubusercontent.com/118953929/220722367-77a5fc6b-6f0e-47e7-88bc-18ab432f11e8.png)


CREATING SIMPLE SCHEMATIC IN XSCHEM
	
![image](https://user-images.githubusercontent.com/118953929/220731745-93b4ee34-cca8-4e3f-bd42-aee769756f7e.png)
![image](https://user-images.githubusercontent.com/118953929/220731849-e1eeeb4c-6aa1-4ee9-85ca-c9431d96bd73.png)

![image](https://user-images.githubusercontent.com/118953929/220731643-0365f8b8-fbec-4108-be10-50f5ca12ba57.png)
![image](https://user-images.githubusercontent.com/118953929/221194898-fa29e9c6-131c-495c-adca-3db4c02932b8.png)

	
CREATING SYMBOL AND EXPORTING SCHEMATIC IN XSCHEM
	
![image](https://user-images.githubusercontent.com/118953929/221197931-d8e7e6d9-f21c-48b7-9776-2d3330882e31.png)
![image](https://user-images.githubusercontent.com/118953929/221198543-45d4afce-992b-4a01-896b-067946641ff1.png)
the Plotting is not able to successfully generate
![image](https://user-images.githubusercontent.com/118953929/221199709-30e054ff-fbeb-4367-84f0-1bd708832d35.png)
	
	
IMPORTING SCHEMATIC TO LAYOUT AND INVERTER LAYOUT STPES

![image](https://user-images.githubusercontent.com/118953929/221211493-ef24a8a5-cf9c-4146-bfac-feacef8381f4.png)
you can move around by click "s" and "m" to select and move 
![image](https://user-images.githubusercontent.com/118953929/221211619-3d1e7bb1-7c10-4dc0-b44f-eefcd9e3f833.png)
	


	
</details>

<details><summary><b> LECTURE </b></summary>

$\fbox{OpenSource Tools and Flows}$	
	

![image](https://user-images.githubusercontent.com/118953929/221217181-914b249f-dd8e-4d2e-aa35-9a9e77dddc9d.png)
![image](https://user-images.githubusercontent.com/118953929/221217268-a61d1b39-0c75-4541-b103-17a567af0811.png)
![image](https://user-images.githubusercontent.com/118953929/221217699-4f6f480d-7d55-4b6f-a502-b834c61976dd.png)
![image](https://user-images.githubusercontent.com/118953929/221217778-5d7bbd8f-7b15-4c5e-b8fa-bf0f13b172af.png)
![image](https://user-images.githubusercontent.com/118953929/221217845-49d92009-fce7-4037-86a8-701a1e5be469.png)
![image](https://user-images.githubusercontent.com/118953929/221217883-3353c2c9-cc23-4ffa-801a-4d1f7b4d9c40.png)

![image](https://user-images.githubusercontent.com/118953929/221218013-7bb55689-ec04-41f9-90ba-89c038192dc3.png)
![image](https://user-images.githubusercontent.com/118953929/221218130-80e38bcc-aab0-4c26-aeea-8d8dead34502.png)
![image](https://user-images.githubusercontent.com/118953929/221218165-e90b9b0f-0201-408f-9b95-3c9dec35ffe4.png)
![image](https://user-images.githubusercontent.com/118953929/221218219-0a5b0422-6e7e-4e77-b16b-207904fed6e2.png)
![image](https://user-images.githubusercontent.com/118953929/221218327-91a88171-3257-4304-a1cf-0992a357330a.png)
![image](https://user-images.githubusercontent.com/118953929/221218414-5eb3e8f1-43f4-4e61-b6d5-4421940f5ddf.png)
![image](https://user-images.githubusercontent.com/118953929/221218476-774f8681-b9c9-4550-a2c3-fe3329bae2f3.png)
![image](https://user-images.githubusercontent.com/118953929/221218522-099aa891-c1c0-4079-a523-da9c994a55aa.png)
![image](https://user-images.githubusercontent.com/118953929/221218594-d66aea3c-e13c-4073-b033-f9d3da4d454f.png)
![image](https://user-images.githubusercontent.com/118953929/221218663-c8be61a3-6267-4e5f-a421-7c446d81195f.png)


	
</details>
	
<details><summary><b> LAB </b></summary>



![image](https://user-images.githubusercontent.com/118953929/221219609-48c627b2-4559-4c24-8772-63fc7c77e537.png)
![image](https://user-images.githubusercontent.com/118953929/221219897-060fed24-732a-4e7d-b8e3-7f153c59e1b0.png)
![image](https://user-images.githubusercontent.com/118953929/221222621-d0c8ef74-deb1-460f-b47a-780b078397e0.png)
![image](https://user-images.githubusercontent.com/118953929/221222671-f02b99ab-44f3-491c-b44d-5c506857f8f1.png)
![image](https://user-images.githubusercontent.com/118953929/221222935-99cc2be7-ff6f-4ce1-9bec-79bea58a3e48.png)
![image](https://user-images.githubusercontent.com/118953929/221223026-0e7ae876-e28b-4c71-95ee-8fb5a33a0bbe.png)
![image](https://user-images.githubusercontent.com/118953929/221223502-b2355b57-4e9f-4b7d-9b5e-e25c40531c69.png)
![image](https://user-images.githubusercontent.com/118953929/221223645-470b0ab1-c87c-455f-a927-aec9a5ab22b1.png)
![image](https://user-images.githubusercontent.com/118953929/221223984-869ddfee-d745-4d46-8519-675e7d460f1e.png)
![image](https://user-images.githubusercontent.com/118953929/221224108-963ccc09-d770-4fe4-8f57-bab3c3cb04dd.png)
![image](https://user-images.githubusercontent.com/118953929/221224300-c9cb6b70-7559-4122-863a-482476f67f1c.png)
![image](https://user-images.githubusercontent.com/118953929/221224538-d4c09bc1-4343-4464-aae6-d50090cb32bf.png)
![image](https://user-images.githubusercontent.com/118953929/221224824-74484e46-78a5-4126-b4f4-da48a0821b81.png)



![image](https://user-images.githubusercontent.com/118953929/221225279-6db43421-1b63-4e6a-bfa0-88705f6c4cb2.png)
![image](https://user-images.githubusercontent.com/118953929/221226956-468f3828-fd50-49b8-b733-04e5e0973677.png)
![image](https://user-images.githubusercontent.com/118953929/221228510-1ad538b8-8c75-4dd6-bbf9-16855b536940.png)
![image](https://user-images.githubusercontent.com/118953929/221228644-9e61f9b1-7c30-40c7-9522-b246b97e59ca.png)
![image](https://user-images.githubusercontent.com/118953929/221228841-dede137a-dcd2-4cd8-9818-baf4d2d35a49.png)
![image](https://user-images.githubusercontent.com/118953929/221229899-0e089798-aede-4876-9cf3-96a2ff771e1c.png)
![image](https://user-images.githubusercontent.com/118953929/221229839-1153ad8e-f454-4354-8512-af2530d32368.png)


	
![image](https://user-images.githubusercontent.com/118953929/221230729-c01df19a-ad39-441e-90a6-2db2d4ab5dab.png)
![image](https://user-images.githubusercontent.com/118953929/221231087-9a4799dd-dd83-46b5-8261-8a1297b0be9e.png)
![image](https://user-images.githubusercontent.com/118953929/221231867-6fef0840-234f-4e37-b2d5-598031200400.png)
![image](https://user-images.githubusercontent.com/118953929/221232536-b42fc46e-5f53-4be4-aad8-39c9371d2d8e.png)
![image](https://user-images.githubusercontent.com/118953929/221232689-50cfccf7-3a51-4df8-9bc4-ff79f1bbc1c3.png)
Magic cannot write abstraction view to gds , thats why its not load properly
![image](https://user-images.githubusercontent.com/118953929/221232865-3266b513-4700-4e69-af7a-1f16efe81505.png)
![image](https://user-images.githubusercontent.com/118953929/221232934-30e1fdbb-09fd-4d92-b93e-1ec471d0b479.png)
![image](https://user-images.githubusercontent.com/118953929/221233397-63b8b885-4680-4384-a547-4d0f7cb088c3.png)
![image](https://user-images.githubusercontent.com/118953929/221233698-2e3e58f2-c07e-4af2-b1c4-45a77802ea81.png)
![image](https://user-images.githubusercontent.com/118953929/221233754-e756a934-c3a8-41d0-8f32-601b71694360.png)
![image](https://user-images.githubusercontent.com/118953929/221233786-920b873e-46be-4567-b6b9-0ebcf8390cd5.png)


	
![image](https://user-images.githubusercontent.com/118953929/221235153-a0cfb120-bf81-4c99-892d-33f3687333aa.png)
![image](https://user-images.githubusercontent.com/118953929/221235317-a7d90619-4ed9-4533-98dd-b9d8fb25581b.png)
![image](https://user-images.githubusercontent.com/118953929/221235706-7839b4fd-ac3a-4557-b5f3-71ce1b6c1b64.png)
![image](https://user-images.githubusercontent.com/118953929/221235602-1e9ccd75-2dfa-4c73-aa25-bff58ec9191e.png)
load magic
	
![image](https://user-images.githubusercontent.com/118953929/221236046-a08466ab-10d2-4c1d-8c39-ffc0d9245272.png)
![image](https://user-images.githubusercontent.com/118953929/221236219-4591d4c0-3fc3-4f8c-82d5-6e99021b8543.png)
![image](https://user-images.githubusercontent.com/118953929/221236752-feae232d-86dd-45fb-afd3-e35c8d3a2229.png)
![image](https://user-images.githubusercontent.com/118953929/221236888-ad2a7d3f-1512-4ebb-878f-f2ff6ca20cc8.png)
![image](https://user-images.githubusercontent.com/118953929/221237538-6a348685-6826-4f57-80dc-5f2b6748e70a.png)

	
![image](https://user-images.githubusercontent.com/118953929/221239014-301e75b5-942d-471c-913c-b6623604c2c2.png)
Remove anything from the cell
![image](https://user-images.githubusercontent.com/118953929/221239079-93fc3747-2a28-46ae-9a84-cb387a0ac848.png)
![image](https://user-images.githubusercontent.com/118953929/221239403-f768e1cc-6373-4cd8-bf9a-2bb83f2832cb.png)

</details>
	
<details><summary><b>ALL LABS for DRC RULE</b></summary>
	
git clone the github link
![image](https://user-images.githubusercontent.com/118953929/221399452-5662aeb2-caa5-4154-9b44-ae44ca939f5f.png)
Run magic by ./run_magic command:
![image](https://user-images.githubusercontent.com/118953929/221399498-d646e140-080b-4049-aeba-b70c2c56ba33.png)
Open up exercise 1:
![image](https://user-images.githubusercontent.com/118953929/221399538-0704897b-e5aa-43c2-b458-a54a1f11da97.png)
![image](https://user-images.githubusercontent.com/118953929/221399556-c0f5dae2-a410-4fac-8ba3-6e44e7c1c650.png)
Moves the cursor to the area then click drc --> drc report
	
![image](https://user-images.githubusercontent.com/118953929/221399655-a4a46256-4868-45b0-bde9-9d958ed692ed.png)
So, its report out that the drc at the area is metal2 width < 0.14um
![image](https://user-images.githubusercontent.com/118953929/221399688-2fa0aa84-6b21-460f-ad1e-a8147db01baa.png)
![image](https://user-images.githubusercontent.com/118953929/221399827-ee530444-8b99-4c3e-9339-9e8194bfbb7c.png)
![image](https://user-images.githubusercontent.com/118953929/221399931-10dd4594-8160-4693-91e5-67d78f528145.png)
![image](https://user-images.githubusercontent.com/118953929/221400091-f4e31708-a64c-492b-a8b4-f4458ae4e457.png)
![image](https://user-images.githubusercontent.com/118953929/221400126-5ad38059-fd3d-454f-bbf5-f178806381d2.png)
![image](https://user-images.githubusercontent.com/118953929/221400165-951b7ca8-04ff-4afc-9ebf-8f0e82650c41.png)
![image](https://user-images.githubusercontent.com/118953929/221400175-1749802a-bf25-450a-b253-4f16318b2bd7.png)

Width spacing:
![image](https://user-images.githubusercontent.com/118953929/221400239-81c10a0b-6631-4030-8c49-00cbc3826034.png)
![image](https://user-images.githubusercontent.com/118953929/221400265-0cc1abfe-0c65-4c3f-96a0-6b7b1bd4c7fd.png)
![image](https://user-images.githubusercontent.com/118953929/221400508-fe1cc062-ce64-4161-89b0-08fea5f613c6.png)

								    
Via 
Stret it 
![image](https://user-images.githubusercontent.com/118953929/221400789-1d691aee-d645-4144-a638-4228e18457c2.png)
Get layer name:
![image](https://user-images.githubusercontent.com/118953929/221400895-1f836fa6-0123-4fe7-acd4-e60111fb5adb.png)
![image](https://user-images.githubusercontent.com/118953929/221401095-b9d48a7f-af93-44a5-861f-e2669b42758f.png)
The size of the box is actually getting a bit bigger
![image](https://user-images.githubusercontent.com/118953929/221401168-7a98e5a9-026f-433b-b48e-bdc017efc85e.png)
Holding the space bar on keyboard and playing around on the via , do cif see for more
![image](https://user-images.githubusercontent.com/118953929/221401314-85fe3536-e673-4301-83e8-2132cc5708bf.png)

Minimum area, minimum hole rule:
![image](https://user-images.githubusercontent.com/118953929/221401380-c967d219-1dd4-40db-a7e9-e2919d5bb7bc.png)
![image](https://user-images.githubusercontent.com/118953929/221401661-67e3a4fa-b6f7-4dda-89db-0f9917437326.png)
Erase of the drc, will no longer there:
![image](https://user-images.githubusercontent.com/118953929/221401708-a5f896ba-6470-49ca-9ac4-76fd07898729.png)

								    
Wells and Deep n-well
								    
Paint the nwell
![image](https://user-images.githubusercontent.com/118953929/221401985-222a0506-a6ba-4943-b589-ae89e4663fed.png)
![image](https://user-images.githubusercontent.com/118953929/221402102-4c044f6b-6ad1-4299-8848-ea51dfe9e198.png)
![image](https://user-images.githubusercontent.com/118953929/221402159-1ef07b10-9fc2-4cff-86b8-3dd7a7c2e728.png)
![image](https://user-images.githubusercontent.com/118953929/221402172-f5ef2acf-bfbc-4cbb-a03f-8d8f5b26a8e4.png)

Derived layers

![image](https://user-images.githubusercontent.com/118953929/221403019-e56cd689-6ad2-465f-a348-de60d110fb5a.png)
![image](https://user-images.githubusercontent.com/118953929/221403214-50588fed-d39e-454f-bff0-1d7c808c9c96.png)
![image](https://user-images.githubusercontent.com/118953929/221403226-e51de55a-5404-4862-8645-e9e34049919b.png)
![image](https://user-images.githubusercontent.com/118953929/221403239-d0c66b09-16bd-46e9-8a4d-4cbef43b8b93.png)
![image](https://user-images.githubusercontent.com/118953929/221403273-fc8ee5c7-2fef-40b4-862d-2534fde18b42.png)
![image](https://user-images.githubusercontent.com/118953929/221403302-af967edd-92da-42d8-a94b-8ec99cafa5de.png)
Doing for this:
![image](https://user-images.githubusercontent.com/118953929/221403623-1b00b160-a2c3-49d5-89ea-045da3da0d46.png)
![image](https://user-images.githubusercontent.com/118953929/221403614-1b881b56-9c14-4639-abde-ed0792b75a60.png)
								    
Doing cif see NPC- automated layer generation betwwen the 2 shapes:
![image](https://user-images.githubusercontent.com/118953929/221403675-77471277-2f24-4efe-b27b-657fe02d2725.png)

Paramterized and PDK services:
								    
![image](https://user-images.githubusercontent.com/118953929/221403748-02b20008-96bc-4e66-8670-9d2b25b3b488.png)
![image](https://user-images.githubusercontent.com/118953929/221404005-84103b28-d830-4b0f-baa0-9a18b3101ab3.png)
Painting the minumim area , as the error will no longer there
![image](https://user-images.githubusercontent.com/118953929/221404317-3fd6686a-b1c3-4637-b058-ab1cf4d447fa.png)
![image](https://user-images.githubusercontent.com/118953929/221404758-e121ceab-fb76-41fa-85ee-2a5657bc7c88.png)

								    
Unimplemented rule
![image](https://user-images.githubusercontent.com/118953929/221404804-505e82d5-5dcc-4a14-90e9-a7429a3a2907.png)
![image](https://user-images.githubusercontent.com/118953929/221404922-7639a183-99c4-4f7a-8d90-c0a3be12196a.png)
![image](https://user-images.githubusercontent.com/118953929/221405086-e42c5399-cb57-4440-9cdf-04d1c255dbea.png)
Notice that you can see the property even when you type for it:
![image](https://user-images.githubusercontent.com/118953929/221405125-eefb84d8-434e-41f7-a814-5edfd99f9e38.png)
![image](https://user-images.githubusercontent.com/118953929/221405185-553748d0-e8f0-43aa-af5a-91abdde5bbd8.png)
![image](https://user-images.githubusercontent.com/118953929/221405198-02955ff6-525d-415f-be76-38750c9c9d9f.png)
![image](https://user-images.githubusercontent.com/118953929/221405223-ff36fb88-2d86-443b-871c-7a90c3683ef0.png)
![image](https://user-images.githubusercontent.com/118953929/221405355-fdf27048-1621-49e5-9cc5-af87d4ddb77a.png)
![image](https://user-images.githubusercontent.com/118953929/221405369-6a79bd27-0031-4310-a1ea-f7fb65a5b7d7.png)
![image](https://user-images.githubusercontent.com/118953929/221405396-92bec639-7f83-44bd-badf-96f3413dca43.png)
gds read <gds seal file>
![image](https://user-images.githubusercontent.com/118953929/221405667-e39ee7c2-53f9-423a-968f-28e6db11ffd9.png)
![image](https://user-images.githubusercontent.com/118953929/221405679-2be6636b-8f3b-44f2-9ca2-b805e96cbda0.png)


Density rules:
![image](https://user-images.githubusercontent.com/118953929/221405725-06e9f6c6-0e9c-49e6-82d3-a7223a49ecb2.png)
![image](https://user-images.githubusercontent.com/118953929/221405765-c6190d2d-4f83-430f-88a6-669dbabea07e.png)
![image](https://user-images.githubusercontent.com/118953929/221405850-7bf8f1c8-e814-452a-abd5-b4390a8da09c.png)
do exercise_11.gds
![image](https://user-images.githubusercontent.com/118953929/221405918-7e6710fa-006b-440f-a45b-74042433c194.png)

![image](https://user-images.githubusercontent.com/118953929/221405906-56607c6b-a362-4983-82b7-13b6ecdfc888.png)
![image](https://user-images.githubusercontent.com/118953929/221406036-d3ba19d5-70f3-4c4c-946d-5e616d75ccc7.png)
![image](https://user-images.githubusercontent.com/118953929/221406237-fd5e5266-7c20-4793-8e10-d3646c513ccd.png)
![image](https://user-images.githubusercontent.com/118953929/221406281-da538d6e-48a8-4ea3-a125-1a7d0d960b6f.png)
![image](https://user-images.githubusercontent.com/118953929/221406298-e6ec7cf6-8bb5-4481-97c0-2376a72ad6f2.png)
![image](https://user-images.githubusercontent.com/118953929/221406330-ca8f2a3f-0862-4f88-92ea-e228bb61f150.png)
![image](https://user-images.githubusercontent.com/118953929/221406434-97cba18e-67a2-44a9-9be3-2d830402a68a.png)
![image](https://user-images.githubusercontent.com/118953929/221406697-f090af75-54f4-4c48-930b-188df6874c27.png)
![image](https://user-images.githubusercontent.com/118953929/221406723-96f04341-cf15-45df-a8b7-23a2e23c28be.png)
![image](https://user-images.githubusercontent.com/118953929/221406873-dc9d1e54-a73c-4f82-8035-9b86b1284612.png)
the zoom in pattern:
![image](https://user-images.githubusercontent.com/118953929/221406912-1bdbec96-4f29-4768-acf6-ab6898814d07.png)


</details>


	
