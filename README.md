# Dinesh_iiitb_asic


[Day 0](#day-0)



## Day 0

<details>
 <summary> Summary </summary>
	
I installed the needed tools.

</details>	
	
 <details>
 <summary> Yosys </summary>


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





