# DDoS Attack Detection and Mitigation in SDN using Machine Learning
## DEMONSTRATION VIDEO LINK: [CLICK HERE]( https://drive.google.com/file/d/1VqVv_F0M-7--Cfk5W-j86Hxce5wvo6kB/view?usp=drive_link )
## Team Information
**Team Name:** FLY HIGH  
**Members:**
- Sony Jenith D – `dsony15@jnn.edu.in` (Leader)
- Prabhakar R - `rprabhakar40@jnn.edu.in`
- Kishori Sowmya G V - `skishori15@jnn.edu.in`
- Kaviya Priya M - `mkaviyapriya36@jnn.edu.in`
- Reshmashree N - `mreshmasree30@jnn.edu.in`

## Problem Statement
AI/ML for Networking or Network Security

## Project Overview
This project implements a DDoS attack detection and mitigation system in Software-Defined Networking (SDN) environments using machine learning. The system combines:
- Deep Belief Network and LSTM for feature detection
- Random Forest ML model for attack classification

## Key Components
1. **SDN Testbed**: Mininet for network emulation + Ryu controller
2. **Traffic Generation**: Simulated normal and DDoS traffic
3. **Detection**: Random Forest ML model
4. **Mitigation**: Automated response module in Ryu controller

## Architecture
![System Architecture](C:\Users\Hari\Pictures\Screenshots\Screenshot 2025-07-12 085836.png)

### SDN Layers:
1. **Application Layer**: Network management applications
2. **Control Layer**: Ryu SDN controller
3. **Infrastructure Layer**: Mininet virtual switches/hosts

## Dataset Features
- 22 columns × 1,048,576 rows
- Key features:
  - `ip_source`: Source IP address
  - `ip_dst`: Destination IP address
  - `icmp_type`: ICMP packet type
  - `flow_duration`: Flow duration time
  - `idle_time`: Connection idle time
  - `packet_count`: Number of packets
  - `label`: Classification (1=legitimate, 0=malicious)

## Implementation

### File Structure
    ```bash
    DDOS_ATTACK-main/
    │
    ├── README.md
    └── src/
    ├── mininet/ # Traffic generation scripts
    ├── Mitigation-KNN/ # Mitigation implementation
    ├── ml-models/ # Machine learning models
    └── SDN-Controller/ # Ryu controller components


### Module Breakdown
1. **ML Models** (DT, KNN, LR, NB, RF, SVM)
   - Random Forest showed best performance
   
2. **Traffic Control Module**
   - Collects and processes network flow data
   - Includes traffic generators for normal/DDoS traffic

3. **Detection Module**
   - Flow-based anomaly detection
   - Uses Random Forest classifier

4. **Mitigation Module**
   - Blocks malicious flows at source
   - Implements dynamic firewall rules

## Results
- Successful real-time detection and mitigation
- Random Forest outperformed other ML models
- Legitimate traffic unaffected during mitigation

## Conclusion
The implemented system effectively detects and mitigates DDoS attacks in SDN environments using machine learning, with Random Forest providing the most accurate classification. The framework maintains normal network operations while blocking malicious traffic.

## Installation Guide

### Prerequisites
1. Virtualization software:
   - [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or VMware
2. Virtual machines:
   - [Mininet-VM](https://github.com/mininet/mininet/releases/)
   - [Ubuntu](https://ubuntu.com/download/desktop)

### Setup Instructions
1. **RYU Controller Setup** (Ubuntu VM):
   ```bash
   # Install RYU controller
   git clone https://github.com/faucetsdn/ryu
   cd ryu
   pip install -r tools/pip-requires
   python setup.py install
2. Follow Steps which included in [setup-ryu](https://heltale.com/sdn/setting_up_ryu/)

### HOW TO RUN IT
1. **RYU-CONTROLLER COMMANDS**
   ```bash
   #check your IP address
   ifcongif
   # it should be something 198.162.XX.XX copy it
   # change working directory to controller folder
   cd controller

   # switch on the ryu-controller
   ryu-manager controller.py

2. **MININET-VM COMMANDS**
   ```bash
   # change working directory to mininet folder
   cd mininet

   # change controller ip address that you copied from ryu controller ip
   nano topology.py

   # run topology
   sudo python topology.py

3. **HPING COMMANDS FOR XTERM HOST (MININET)**
   ```bash
   # ICMP flood
   hping3 -1 -V -d 120 -w 64 -p 80 --rand-source --flood <target-IP>

   # SYN flood
   hping3 -S -V -d 120 -w 64 -p 80 --rand-source --flood <target-IP>

   # UDP flood
   hping3 -2 -V -d 120 -w 64 -p 80 --rand-source --flood <target-IP>

 ### CONTRIBUTORS

 Sony Jenith D (Team Lead)
 
 Prabhakar R

 Kishori Sowmya G V

 Kaviya Priya M

 Reshmashree N

