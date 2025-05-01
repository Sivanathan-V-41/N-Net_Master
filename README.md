![Version](https://img.shields.io/github/v/release/leondavi/N-Net)
![Contributors](https://img.shields.io/github/contributors/leondavi/N-Net)
![Issues](https://img.shields.io/github/issues/leondavi/N-Net)
[![Discord](https://shields.microej.com/discord/914616114204516393)](https://discord.gg/xwBTbzER)  
[![LinkedIn](https://img.shields.io/badge/Linkedin-%230077B5.svg?logo=linkedin&logoColor=white)](https://www.linkedin.com/company/nerlnet)
[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://www.youtube.com/channel/UCnnWPPKiHioTBy7Zq5shrQw)
[![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?logo=huggingface&logoColor=000)](https://huggingface.co/N-Net)

# N-Net

<p align="center">
  <img src="N-NetLogo.png" width="200" title="NerlNet">
</p>

N-Net is an open-source framework for research and deployment of distributed machine learning algorithms on IoT devices. It provides comprehensive insights into both edge devices that run neural network models and network performance and statistics. N-Net can simulate distributed ML clusters on a single or multiple machines and deploy these clusters, with minor changes, on various kinds of IoT devices.  

N-Net simplifies the setup of a distributed cluster that consists of many models on its edge, communication flow can be fully controlled and monitored, and N-Net's Python API allows users to manage and gather data from the distributed cluster throughout the experiment.  

N-Net library combines the following languages to achieve a stable and efficient distributed ML system framework:  
• The communication layer of N-Net is based on an Cowboy - an HTTP web server open-source library.  
• ML on the edge of the distributed cluster is based on OpenNN library, an open-source project of Cpp Neural Network library.  
• Management of N-Net cluster - An HTTP server of Flask communicates with N-Net's main server to control the cluster's entities.  

![image](https://user-images.githubusercontent.com/18975070/144730156-5bd03ad7-fc5f-45e9-8b4e-62d582af2200.png) 
![image](https://user-images.githubusercontent.com/18975070/144730182-c535b20a-a5f9-4d4f-8632-77d49732f17f.png) 
![image](https://user-images.githubusercontent.com/18975070/144730189-4bad4fba-e559-45a6-b163-d3e5d7d87e1f.png) 
![image](https://user-images.githubusercontent.com/18975070/144730205-5a665819-4be0-40aa-88e5-868ba99aab17.png)
 
### N-Net cluster is defined by three configuration files (Json files):
- Distributed Configuration that defines entities of N-Net: Source, Router, Client.
  - A client is a host of workers. A worker is a NN model that can move between phases of train and predict.
  - Source generates data streams that are sent to workers.
  - Router controls the data flow through N-Net cluster.

### References and libraries:
- [OpenNN](https://www.opennn.net/), an open-source neural networks library for machine learning.   
- [Cowboy](https://github.com/ninenines/cowboy) an HTTP server for Erlang/OTP.  
- [NIFPP](https://github.com/goertzenator/nifpp) C++11 Wrapper for Erlang NIF API.   
- [Rebar3](https://github.com/erlang/rebar3), an Erlang tool that makes it easy to create, develop, and release Erlang libraries, applications, and systems in a repeatable manner.
- [Simple Cpp Logger](https://github.com/nadrino/simple-cpp-logger), simple cpp logger headers-only implementation.

N-Net is developed by David Leon, Dr. Yehuda Ben-Shimol, and the community of N-Net open-source contributors.  
Academic researchers can use N-Net for free, provided they cite this repository.  

### N-Net Architecture Example:
![N-Net Architecture](https://user-images.githubusercontent.com/18975070/141692829-f0cdca7d-96d1-43b0-920a-5821a14242f7.jpg)

# Build and Run N-Net:
Recommended cmake version 3.26   
Minimum erlang version otp 25 (Tested 24,25,26)   
Minimum gcc/g++ version 10.3.0   

### On every device that hosts N-Net cluster entities, do the following steps:

1. Clone this repository with its subomdules ```git clone --recurse-submodules <link to this repo> N-Net```  
2. Run ```sudo ./N-NetInstall.sh```  
  2.1 With argument -i script builds and installs Erlang (OTP 25), and CMake from source.
      (validate that erlang is not installed before executing installation from source)  
  2.2 On successful installation, N-Net directory is accessible  
      via the following path: ```/usr/local/lib/nerlnet-lib```
3. Run ```./N-NetBuild.sh```
4. Test N-Net by running: ```./tests/N-NetFullFlowTest.sh```
5. [Nerlplanner](https://github.com/leondavi/N-Net/wiki/NerlPlanner) is a N-Net tool to generate required jsons files to setup a distributed system of N-Net.  
To use NerlPlanner execute ```./NerlPlanner.sh```.  
Create json files of distributed configurations, connection map and experiment flow as follows:  
- dc_\<any name\>.json  
- conn_\<any name\>.json  
- exp_\<any name\>.json       
6. Run ```./N-NetRun.sh```.
7. On API-Server device, Start Jupyter NB with ```./N-NetJupyterLaunch.sh``` and follow ApiServerInstance.help() and [examples](https://github.com/leondavi/N-Net/tree/master/examples).

## Python API and Jupyter-lab (For Api-Server): 
Minimum Python version: 3.8  
  
Communication with N-Net is done through a simple python API that can be easily used through Jupyter notebook.       
The API allows the user to collect statistics insights of a distributed machine learning network:   
Number of messages, throughput, loss, predictions, models performance, etc.  

### Instructions
1. Open a jupyter lab environment using ```./N-NetJupyterLaunch.sh -d <experiment_direcotry>```  
1.1    Use -h to see the help menu of N-NetJupyterLaunch.sh script.  
1.2    If --no-venv option is selected then required modules can be read from ```src_py/requirements.txt```.  
3. Read the instructions of importing Api-Server within the generated readme.md file inside <experiment_directory> folder. 
4. Follow the [Example Notebook](https://github.com/leondavi/N-Net/blob/master/examples/example_run.ipynb)

### Distributed ML on The Edge
Distributed ML on the edge - A new evolution step of AI.  

https://github.com/leondavi/N-Net/assets/18975070/15a3957a-3fd6-4fb2-a365-7e1578468298  

## Gratitudes
<h3 align="center">Microsoft Azure</h1>
<p align="center"> <img src="https://github.com/leondavi/N-Net/assets/18975070/d3255b30-ae3b-46fd-a87f-6c1ec7ae231b" width="50" title="Microsoft Azure Sponsorship"></p>  
<p align="center"> A grant of Azure credits as part of Microsoft’s Azure credits for open source projects program (2024-2025).</p>  
<h3 align="center">Amazon AWS</h1>
<p align="center"> <img src="https://github.com/leondavi/N-Net/assets/18975070/5fe285fd-43c9-4de8-a619-5ebaace33b29" width="50" title="Amazon AWS Sponsorship"></p>  

<p align="center"> A grant of AWS credits as part of AWSOpen program for open source projects (2024).</p>


---

### 📚 Table of Contents  
- [About N-Net](#n-net)  
- [Key Features](#key-features)  
- [System Architecture](#n-net-architecture-example)  
- [Getting Started](#build-and-run-n-net)  
- [Python API & Jupyter Support](#python-api-and-jupyter-lab-for-api-server)  
- [Configuration Files](#n-net-cluster-is-defined-by-three-configuration-files-json-files)  
- [References](#references-and-libraries)  
- [Distributed ML on the Edge](#distributed-ml-on-the-edge)  
- [Gratitudes](#gratitudes)  
- [License](#license)  
- [Acknowledgments](#acknowledgments)

---

### 🔑 Key Features

- 💻 **Distributed ML on IoT Devices**  
  Simulate and deploy neural networks across multiple edge devices.

- 🌐 **Real-Time Communication Layer**  
  Powered by Erlang's Cowboy HTTP server for stable, lightweight performance.

- 🧠 **Edge Inference and Training**  
  OpenNN-backed neural networks allow both training and prediction phases on the edge.

- 📊 **Metrics & Monitoring**  
  View throughput, loss, predictions, and other metrics via Jupyter-based dashboards.

- ⚙️ **Flexible Configuration**  
  Use JSON to define your distributed system architecture with fine-grained control over sources, routers, and clients.

---

### 🧾 License

N-Net is released under the MIT License. See the [LICENSE](LICENSE) file for more information.

---

### 🙌 Acknowledgments

N-Net is the result of collaborative efforts by researchers, engineers, and contributors who believe in open-source distributed AI. Special thanks to:
- David Leon
- Dr. Yehuda Ben-Shimol
- The open-source community of N-Net

---

### 🖋️ Generated by

> 📄 **This README file was compiled and enriched by [Sivanathan]**, with the aim of supporting the N-Net community and improving developer onboarding.

