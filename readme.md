
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
	
</details>
	
<details><summary><b> Lab 15: part2 - VCLK </b></summary>
	
</details>

