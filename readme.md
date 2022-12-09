**Contents:**

- [Day_0 : System/Tool Setup Check & GitHub ID creation](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#day_0)
- [Day_1 : Introduction to RTL verilog design and analysis](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#day_1)
- [Day_2 : Timing libs, hierarchical vs flat synthesis and efficient flop coding styles](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#day_2)
- [Day_3 : Combinational and sequential optimizations](https://github.com/somsunee/Intel-sd-training/blob/main/readme.md#day_3)
 
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

_CMOS (complementary metal-oxide-semiconductor) _
- has enabled massive scaling in a variety of semiconductor devices. Combining the CMOS process with VLSI has helped push packages to smaller levels while keeping costs reasonable

_FLOPS_ 
-Propagation delay - the time required for the input to be propagated to the output

_Glitch_
A glitch can be an issue if it propagates to the resultant logic or gets captured by a flip-flop. There can be two cases here:
**Synchronous timing paths:** (even has glitch) it will be within the limits of minimum and maximum delays permissible from one flip-flop to another
**Asynchronous timing paths:** if there is a glitch in the data path, it can get captured, hence, can cause issue. To prevent this, synchronizers are used and there are certain rules to be followed for asynchronous paths. 
![Screenshot 2022-12-07 201315](https://user-images.githubusercontent.com/118953929/206177613-9c92c340-9dd3-48f5-89bf-469067c00b85.jpg)


**_Labs:_**

_Lab 4:Introduction to dot lib_ 

a)
i) Open up sky*.lib file from lib 
![day2_lab4_1](https://user-images.githubusercontent.com/118953929/206072693-479941d2-ef25-4fb5-93ab-661817051570.jpg)
ii) Observe and understand the lib file.
- tt - typical
- 025C - tempertature\
***3 important things inside library, for the design to work\
PVT\
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

### Day_3

**_Notes:_**

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
	-State optimisation
	-Retiming
	-Sequential Logic Cloning(FloorPlan Aware Synthesis)
	


**SEQUENTIAL CONSTANT**

![photo1670590644 (3)](https://user-images.githubusercontent.com/118953929/206707788-c3a11f60-e003-4e6a-a66a-b1a2b0947df9.jpeg)
![photo1670590644 (4)](https://user-images.githubusercontent.com/118953929/206707783-005d1b87-bb49-41a6-8994-d9ec84d5448f.jpeg)


