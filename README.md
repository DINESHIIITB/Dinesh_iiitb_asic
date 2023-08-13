# Dinesh_iiitb_asic


[Day 0](#day-0)

[Day 1](#day-1)

[Day 2](#day-2)

[Day 3](#day-3)

[Day 4](#day-4)


## Day 0

<details>
 <summary> Summary </summary>
	
I installed the needed tools.

</details>	
	
 <details>
 <summary> Yosys </summary>

### **YOSYS**

 I installed Yosys using the following commands:
```bash
git clone https://github.com/YosysHQ/yosys.git
cd yosys-master 
sudo apt install make 
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
make 
sudo make install
```
Below is the screenshot showing sucessful installation:

![Screenshot from 2023-07-31 09-58-15](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/3f61c7b7-3433-4971-91dc-dc036abd6afa)


</details>
<details>
    <summary>
    iverilog 
    </summary>

### **iVerilog**

I installed iverilog using the following command:
```
sudo apt-get install iverilog
```
Below is the screenshot showing successful launch:
	
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/f8c4f07e-8666-4cd9-ab5a-d8b110b8da0b)



</details>
<details>
<summary>
    gtkwave
</summary>

### **GTKWave**

I installed gtkwave using the following command:

```
sudo apt-get install gtkwave
```

Below is the screenshot showing successful launch
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/49a03a90-80f9-4a97-bec4-5153133ba204)
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/19e8e91c-9507-4839-bdb1-72bbe02bcf34)

</details>
<details>
<summary>
    Ngspice
</summary>


### **NgSpice**

 I downloaded the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory and unpacked it using the following commands:
 ```bash
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release
cd release
../configure  --with-x --with-readline=yes --disable-debug
make
sudo make install
 ```
Below is the screenshot showing sucessful installation:

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/37ee8c57-5007-4cc0-a046-9a4967a8e040)


</details>
 <details>
 <summary> OpenSTA </summary>

### **OpenSTA**

 I installed and built OpenSTA (including the needed packages) using the following commands:
 ```
sudo apt-get install cmake clang gcctcl swig bison flex
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake ..
make
```
Below is the screenshot showing sucessful installation:
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/7ca9dc6e-e1b7-4d38-bcd9-60796a902546)

</details>
 <details>
 <summary> magic </summary>

 
### **Magic**

 I installed magic using the following commands:
  ```bash
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev
 ```
 Below is the screenshot showing sucessful installation:

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/9d2ef33b-d50d-43ef-8a23-2dd8a45b9345)


</details>
 <details>
 <summary> Openlane
 </summary>


### **Openlane**

Prior to the installation of the OpenLane install the dependencies and packages using the command shown below :</br>
``` 
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
```
Docker Installation :</br>
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world

sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot 


# Check for installation
sudo docker run hello-world
```

**Steps to install OpenLane, PDKs and Tools**</br>
```
cd $HOME
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test
```
</details>

## Day-1



<details>
 <summary> Summary </summary>

This section shows how I simulated and synthesized a good_mux using iverilog and yosys respectively. iverilog generates from the RTL design and its testbench a value changing dump file (vcd). gtkwave is the tool used to plot the simulation results of the design. Yosys is a tool which synthesizes RTL designs into a netlist. It is also used to test the synthesized netlist when we provide it with a testbench.

</details>


<details>
 <summary> Steps to clone the repository </summary>

steps to clone the repository:
```bash
mkdir vlsi
cd vlsi
git clone https://github.com/kunalg123/vsdflow.git
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```

</details>	


<details>
 <summary> good_mux </summary>
The verilog codes for good_mux.v are taken from https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git

</details>

 <details>
 <summary> Simulation: iverilog and gtkwave </summary>

 
 I used the following commands to simulate and view the plots of the RTL design:
	
 ```bash
 iverilog <name verilog: good_mux.v> <name testbench: tb_good_mux.v>
 ./a.out
 gtkwave tb_good_mux.vcd
 ```
	
 Below is the screenshot of the gtkwave plots:
 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/7c4f28ad-dae6-41e0-a321-e3f71c1d2d9e)


		
I used the following commands to synthesize and view the design of the hierarchical multiple module:
		

 </details>

<details>
 <summary> Synthesis: Yosys </summary>
	
 In the directory of the verilog files, I used the following commands to synthesize and view the synthesized deisgn:
	
 ```bash
yosys> read_liberty -lib <path to lib file>
yosys> read_verilog <path to verilog file>
yosys> synth -top <top_module_name>
yosys> abc -liberty <path to lib file>
yosys> show
 ```
In ABC step we need  to confirm the inputs ,outputs ,internal signals

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/bca8905e-0328-435f-a307-e6587a7e009f)

 Below is the screenshot of the synthesized design:
 
 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/0ff98c30-221b-45f5-93cb-4ddff06ef960)


 I used the following commands to generate the netlist:
 ```bash

 yosys> write_verilog -noattr <file_name_netlist.v>
 ```
 
 Below is the screenshot of the generated netlist:
 
 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/9e504712-1872-4e99-be94-ed7ba7e466f0)

 
</details>

## Day 2

### **Introduction to timing.libs**


<details>
 <summary> sky130_fd_sc_hd__tt_025C_1v80 </summary>

 The sky130_fd_sc_hd__tt_025C_1v80 name tells us that it is 130nm library and tt stands for typical, 025c is temperature,1v80 is voltage
 P-process
 V-volatge
 T-temperature
	
 ```bash
gvim  sky130_fd_sc_hd__tt_025C_1v80.lib

 ```
</details>


<details>
 <summary>multiple_modules </summary>
The verilog codes for good_mux.v are taken from https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git

</details>

 <details>
 <summary> Simulation: iverilog and gtkwave </summary>

 
 I used the following commands to simulate and view the plots of the RTL design:
	
 ```bash
 iverilog <name verilog:multiple_modules.v> <name testbench: tb_multiple_modules.v>
 ./a.out
 gtkwave tb_multiple_modules.vcd
 ```
 Below is the screenshot of the gtkwave plots:

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/0f00fc74-e11f-4cdc-b901-f3e574e0b773)

		
I used the following commands to synthesize and view the design of the hierarchical multiple module:
		

 </details>

<details>
 <summary> Synthesis: Yosys </summary>
	
 In the directory of the verilog files, I used the following commands to synthesize and view the synthesized deisgn:
	
 ```bash
yosys> read_liberty -lib <path to lib file>
yosys> read_verilog <path to verilog file>
yosys> synth -top <top_module_name>
yosys> abc -liberty <path to lib file>
yosys> show
 ```
The synth -top<top_module_name> gives the detail information about design hierarchy,submodules and that has shown below

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/bcf3784b-ee05-43d5-b2b1-4a3f0b4fc11c)

In ABC step we need  to confirm the inputs ,outputs ,internal signals

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/b92b2665-3da5-41f2-ac35-6e60c63cc30e)

After executing show command , we can see the hierarchical design that contains submodule 1 and submodule 2

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/68546208-4af6-460f-a0d3-9e1d20a8bf58)



I used the following commands to generate the netlist:
 
 ```bash

 yosys> write_verilog -noattr <file_name_netlist.v>
 yosys> !gvim multiple_modules_heir.v
 ```
 
 Below is the screenshot of the generated netlist:

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/e3346dc9-cf32-46f4-aabf-2b7a2dea5f75)


yosys flatten is used to write flat netlist
```bash
 yosys> flatten
 yosys> write_verilog -noattr multiple_modules_flat.v>
 yosys> !gvim multiple_modules_flat.v
 ```

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/c388013c-7f63-423f-be61-4c01008775c0)

Executing show command after flatten, we can see the hierarchical design that does not contains submodule 1 and submodule 2

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/338fcc42-0693-4113-9677-aee72499e24d)


submodule level synthesis
If we instantiate the same sub module so many times, then iit is not required to synthesise the same module every time so we use sub module level synthesis
If we have very big module then it is very difficult to synthesise the whole module so we synthesise sub modules 

sub module1

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/f8d27e0a-b8d3-4347-88ef-c6c021568349)

</details>


 <details>
 <summary> Asynchronous reset </summary>


![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/43b36e6b-5649-4d92-aac9-51aaa82de919)

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/411bae3a-1ea3-43ac-8167-f8a5fe2aed2a)

</details>

 <details>
 <summary> Asynchronous set </summary>
	 
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/f2e2a12e-637b-4d52-bd7e-be4b60a2892c)
	 
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/38af5112-fb5c-4bbf-a69e-033b22264eaa)

</details>

 <details>
 <summary> synchronous reset </summary>
	 
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/388ac745-efb7-4147-acaa-ead4acde6d9f)


![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/74f0e5ae-0864-4a31-a2eb-0788561c0621)

</details>

<details>
 <summary> Optimization 1  </summary>

	
 ### **Multiply by 2**
To perform multiplication we dont need hardware because we are adding zeores to lsb (2^n) n zeroes will be added to lsb adding zeroes can seen in the design and we confirm the same in netlist also. 

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/41f3eca2-a2b0-47a3-80b0-a719a071679e)

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/d792f082-8ee3-4b45-a4dc-12f56ea2ffd7)

</details>

<details>
 <summary> Optimization 2 </summary>
 

 ### **Multiply by 8**
 
 To perform multiplication we dont need hardware because we are adding zeores to lsb (2^n) n zeroes will be added to lsb adding zeroes can seen in the design and we confirm the same in netlist also. 
 
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/1b29a38d-e039-4090-9a7b-d607f8930c1c)

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/869032e6-1760-4a1a-9f4e-4e4c64017692)

</details>


## Day 3

**Combinational and Sequential Optimizations**
 
<details>
 <summary> Introducation </summary>

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/49a0095f-f330-47e6-b313-8c02940a1849)


![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/1cbbef40-d954-469a-88af-9e3bfa253dbf)

</details>


<details>
 <summary> Combinational logic Optimizations  </summary>
	
**opt_check**

 In the directory of the verilog files, I used the following commands to synthesize and view the synthesized deisgn:
	
 ```bash
ls *opt_check*
yosys> read_liberty -lib <path to lib file>
yosys> read_verilog <path to verilog file>
yosys> synth -top <top_module_name>
yosys> opt_clean -purge
yosys> abc -liberty <path to lib file>
yosys> show
 ```
ls opt_check is used to find out what are the opt check files we are using.
opt_clean -purge is used to removes unused wires and cells. Expecting and gate and we got and gate.



![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/70f250d4-6ff0-4359-87c6-ad3f8daa5a4d)



**opt_check2**

Repeat the above following steps .Expecting OR gate and got OR gate

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/3ffb8f3d-01fc-4cc5-86bf-aac06cfa95b3)

**opt_check3**

Repeat the above following steps .Expecting 3 input and gate and got 3 input and gate.

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/f18c0591-1567-47e7-8598-f26fa50ba86b)


**opt_check4**

Repeat the above following steps .Expecting xnor between a and c input and got xnor gate.

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/8f8b9d85-71b5-4adf-9b93-bf06b8c735e1)

**multiple_module_opt**

Repeat the above following steps  and use flatten command before the opt_clean -purge

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/aabc0f09-4c21-4a55-9205-47381ac107e1)

**multiple_module_opt2**

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/c4a2878e-9357-4e73-bf7f-3f68dc92c8dd)

</details>




<details>
 <summary> Sequential logic Optimizations  </summary>
 
 **dff_const1**
These are the sequential files using ,to display these sequential files,we need to give command in the directory of the verilog files
```
ls *dff*const*
```

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/70bfff7a-143b-48c8-adc4-dd39a8e80d85)

I used the following commands to simulate and view the plots of the RTL design:
	
 ```bash
 iverilog dff_const1.v tb_dff_const1.v
 ./a.out
 gtkwave tb_dff_const1.vcd
 ```
The wave form clearly tells that it doesnt work like a inverter, the change in output will happen only at rsing edge of clock

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/33c1b13d-f6b6-42ec-9a51-2a8648e409a1)

In the directory of the verilog files, I used the following commands to synthesize and view the synthesized deisgn:
	
 ```bash
yosys> read_liberty -lib <path to lib file>
yosys> read_verilog <path to verilog file>
yosys> synth -top <top_module_name>
yosys> dfflibmap -liberty ../lib/<path to the file>
yosys> abc -liberty <path to lib file>
yosys> show
 ```
In statistics s_dff_ppo has got 1.i,e there is one dflipflop. The commmand dfflibmap is used to tell the synthesizer, what library has to be picked

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/32bd35b3-a3d6-4f86-9a5f-78c0adfa4c71)

 
 **dff_const2**

 I used the following commands to simulate and view the plots of the RTL design:
	
 ```bash
 iverilog dff_const2.v tb_dff_const2.v
 ./a.out
 gtkwave tb_dff_const2.vcd
 ```
In this circuit output is always 1,regardless of input

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/3fcc9225-eb7e-4807-8163-11835f7b7e74)

In the directory of the verilog files, I used the following commands to synthesize and view the synthesized deisgn,The commmand dfflibmap is used to tell the synthesizer, what library has to be picked
	
 ```bash
yosys> read_liberty -lib <path to lib file>
yosys> read_verilog <path to verilog file>
yosys> synth -top <top_module_name>
yosys> dfflibmap -liberty ../lib/<path to the file>
yosys> abc -liberty <path to lib file>
yosys> show
 ```

In statistics there is no dfliplfop and the design was matching with the statistics.we got the design as we expected, output is always one.

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/0e498cf0-1cd8-46c9-bd55-a3ac21aff22f)


 **dff_const3**


 I used the above commands of iverilog to simulate and view the plots of the RTL design:

 we got the output as what we understood from the code ,except for one clock cycle the output is always on,
 
 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/fd0cef7c-5d70-45c6-ac22-0309464852eb)

 In the directory of the verilog files, I used the above commands to synthesize and view the synthesized deisgn,The commmand dfflibmap is used to tell the synthesizer, what library has to be picked. and we can see from the statistics the both flipflops are present and there no optimization has done to circuit.
 
 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/bbbbc629-687d-45cc-8b44-9cf3ed1a31a4)

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/65eb3267-a96d-41cc-abb6-a8ae7e917e15)


 **dff_const4**

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/8b960c55-175c-49d1-af03-524bcb8f45e5)


 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/d1612b3a-b429-4683-956e-f58a70f3c4aa)
 
 **dff_const5**

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/1829e027-bac9-48f2-8483-e8aac981089a)


 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/83c50943-f602-46db-b32e-36d5d3e46cd3)

</details>
 
<details>
 <summary> Sequential logic Optimizations of unused ports  </summary>


In the directory of the verilog files, I used the above commands to synthesize and view the synthesized deisgn,according the verilog code its a 3 bit counter ,so we require 3 flip flops ,but if we see the statisctics and netllist design there is only on eflip flop.for getiing the output we are using one flip flop thats why the other two flopsgot optimized .
 
 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/7b3e8754-6c91-472b-b68b-8f04d3b3decb)


 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/f1a248ec-b350-4960-8290-7f2279751828)

before we are using one bit of the output ,now we changed the code to use all three bits and verifying the design is using three flip flops are not, as we expected the other two flops are not getting optimized.

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/51717449-62ca-4467-af35-095889cf2d24)
 

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/db22b6e6-e903-4803-a0c8-69400d96294b)

 </details>
 
## Day 4

<details>
 <summary> GLS,Synthesis simulation mismatches </summary>
	
GLS-Running the testbench with netlist as design under test,Normally we use RTL code to run the testbench.
* Netlist is logically same as RTL code ,so we will be getting the same output. 



 <img src="https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/e6ecbc49-2419-4748-8b83-ec662f178f9e" alt="Image" width="500" height="400">
 
 ### synthesis simulation mismatch

 	Synthesis simulation mismatch happens bacuse of these three reasons
  1. Missing sensitivity list
  2. Wrong usage of blocking and non blocking assignments
  3. Nonstandard verilog coding

* always@(*)---> always will be evaluated when anysignal changes.
* always@(signal)---->always block get evaluated when there is any change inthat signal.The change in the inputs doesnt affect the output if signal is not changing at that point ,so this  error is considered as missing sensitivity list.
 
 ### Blocking and non blocking statements

- '='---> Blocking
	- used inside always block
	- executes the statements in order

- '<='---> Non Blocking
	- used inside always block
 	- executes all the RHS first then assigns it to LHS
 	- parallel evaluation
 
### Caveats with Blocking statements

example 1:

| ![Image 1](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/670eedb6-5019-49a2-bab6-b5f33d6b8436) | ![Image 2](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/f35dfcaf-86b4-41d5-8d16-3f0ec87c82e5) |
|:---:|:---:|
| two flops will be created | only one flop will be created ,i.e q is assigned d  |

- while using blocking statements we should be careful ,wrong order changes the circuit and give wrong output.In the above circuit if we use non blocking assignment, order doesnt matter  because RHS executes first and assignes to LHS so it wikkl create two memory locations,tow flops will be created
 </details>

<details>
 <summary> Synthesis simulation mismatche </summary>
	
 I used the commands of iverilog to simulate and view the plots of the RTL design:

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/98d0077e-6b8e-4f36-95b9-dd2ab6a574d1)

 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/aaf4644c-3ff2-41f9-b5e4-d816e68f406f)

```
iverilog ../my_lib/verilog_model/primitives.v  ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
```


 ![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/9b90e624-c6c2-4dee-9f90-39f7c3d95e37)


 ![Screenshot from 2023-08-13 20-54-29](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/57455898-656f-4af4-9e19-0404390bcf2d)


 ![Screenshot from 2023-08-13 21-01-03](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/92ec0d8c-7126-4165-9eef-46f562d5b6e8)

 ![Screenshot from 2023-08-13 21-05-16](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/7776bf7f-a132-409e-83d2-9904b722285e)


 ![Screenshot from 2023-08-13 21-08-00](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/71506a3f-4dc0-4344-987f-70cf1338f68c)


![Screenshot from 2023-08-13 21-12-09](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/279fc08a-634f-41e9-8d48-c3ec0960e3de)


![Screenshot from 2023-08-13 21-15-29](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/eb7371e9-f53a-44e6-8816-9eb9e78172a9)














   




 

  


 

 







 

 

 







 








































