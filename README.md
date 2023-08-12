# Dinesh_iiitb_asic


[Day 0](#day-0)

[Day 1](#day-1)

[Day 2](#day-2)



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


asyncres
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/43b36e6b-5649-4d92-aac9-51aaa82de919)

![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/411bae3a-1ea3-43ac-8167-f8a5fe2aed2a)


asyncset
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/f2e2a12e-637b-4d52-bd7e-be4b60a2892c)


![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/38af5112-fb5c-4bbf-a69e-033b22264eaa)


syncres
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/388ac745-efb7-4147-acaa-ead4acde6d9f)


![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/74f0e5ae-0864-4a31-a2eb-0788561c0621)



















