
**Contents:**

- [Day 0 : System/Tool Setup Check & GitHub ID creation](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_0)
- [Day 1 : Introduction to RTL verilog design and analysis](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_1)
- [Day 2 : Timing libs, hierarchical vs flat synthesis and efficient flop coding styles](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_2)
- [Day 3 : Combinational and sequential optimizations](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_3)
- [Day 4 : GLS,blocking vs non-blocking and synthesis-simulation mismtach](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_4)
- [Day 5 : DFT](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_5)
- [Day 6 : Introduction to Logic Synthesis](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#-day_6)
 
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
	

$\mathbb{\color{magenta}{SDC}}$ : Synopsys Design Constraints 
	- supplied to DC to _enable appropriate optimization_ suitable to archieve the best implementation 
	- design intent in terms of **timing, power** and **area** constraints.\
$\mathbb{\color{magenta}{.LIB}}$ : Design library (contains stamdard cells)\
$\mathbb{\color{magenta}{DB}}$ : same as .lib, but different format, in DC, we use .db\
$\mathbb{\color{magenta}{DDC}}$ : storing the design information. DC can write out and read in DDC\
$\mathbb{\color{magenta}{DESIGN}}$ : RTL files which has the behavioral model of the design

	


	

</details>




