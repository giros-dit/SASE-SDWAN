# VNX SD-WAN and SASE Scenario

## Acknowledgements

This work is a result of project [ECTICS](https://www.dit.upm.es/~giros/project/ectics/) (PID2019-105257RB-C21), funded by:

![financing-logo](doc/img/MICIU_AEI_w400.jpg)

## Overview

This project provides a comprehensive simulation environment for a Secure Access Service Edge (SASE) scenario, integrating Software-Defined Wide Area Network (SD-WAN) technologies and remote work models. Built using the Virtual Networks over Linux (VNX) framework, it enables the deployment and testing of advanced network configurations, including virtualized network functions, edge computing, and integrated security services.

![SCENARIO](https://github.com/ivalenzuelan/SASE-SDWAN/assets/125378917/aea11af9-6126-4f1e-89c5-f9612bde3a99)


## Features

- **SD-WAN Simulation:** Demonstrates the setup and management of a software-defined wide area network, offering insights into network optimization, application routing, and bandwidth management.
- **SASE Model Integration:** Integrates Secure Access Service Edge components, blending network and security functions to support dynamic, secure access to organizational resources.
- **Remote Work Connectivity:** Simulates remote work scenarios, showcasing how employees can securely connect to corporate resources from any location.
- **Advanced Network Configurations:** Utilizes Open vSwitch and VXLAN for network virtualization, alongside detailed routing and NAT configurations for realistic network topology simulation.

## Prerequisites

- Linux environment with support for LXC (Linux Containers).
- VNX Framework installed and properly configured ([VNX Installation Guide](http://web.dit.upm.es/vnxwiki/index.php/Docintro)).
- Basic understanding of networking concepts, SD-WAN, and SASE architectures.

## Installation

1. **Clone the Repository:**
   - `git clone [repository-url]`
   - Navigate to the project directory: `cd [project-directory]`

2. **Load the Scenario:**
   - Ensure the VNX daemon is running: `sudo vnx -v --daemon`
   - Load the scenario: `sudo vnx -f [scenario-file].xml --create`

3. **Start the Simulation:**
   - Execute the start command: `sudo vnx -f [scenario-file].xml --start`

## Configuration Details

This scenario includes multiple components:

- **LAN and WAN Networks:** Configured as virtual bridges and veth pairs for interconnectivity.
- **Host VMs (h11, h21, etc.):** Simulate end-user devices within the network.
- **Router VMs (r1, r2, etc.):** Facilitate routing between different network segments.
- **SD-WAN Edge Devices (sdedge1, sdedge2, etc.):** Implement SD-WAN functionalities.
- **NAT Devices (nat1, nat2, etc.):** Provide Internet connectivity and simulate external network access.
- **ISP:** Simulates Internet Service Provider for the scenario.

## Usage

Once the scenario is loaded and started, you can interact with each component using VNX commands or directly accessing the Linux Containers via `lxc-attach`. For specific interactions or to simulate network changes, refer to the VNX documentation.

## Troubleshooting

- Ensure all prerequisites are met and that VNX is correctly installed.
- Verify network configurations and interconnectivity between VMs if you encounter connectivity issues.
- Consult the VNX documentation for common issues and troubleshooting tips.

## Contributing

Contributions to enhance the scenario or documentation are welcome. Please submit pull requests or open issues with your suggestions and feedback.

## License

TFG Developed by Iñigo Valenzuela Nuñez with Carlos Mariano Lentisco Sánchez based on an SD-WAN practice scenario developed within the Communications Networking and within the Research Group on Networking and Virtualisation of Communication Services (GIROS) of the Department of Telematic Systems Engineering of the UPM

# SD-WAN Virtual Installation Guide

Virtualized installaion of SD-WAN Edge devices leveraging OpenFlow for network management.

## Overview

This virtual lab scenario demonstrates the integration of SD-WAN Edge devices within a network, aiming to encapsulate corporate traffic over a public IP network using SD-WAN technologies. The practice environment is built using VNX to deploy advanced network scenarios on Linux systems.

## Prerequisites

- **VirtualBox**: Free virtualization software for Linux, Windows, and macOS. [Download here](https://www.virtualbox.org/)
- **VNXSDNNFVLAB2020-v2.ova**: A pre-configured Virtual Machine (VM) for the SD-WAN practice. [Download link](http://idefix.dit.upm.es/download/vnx/vnx-vm/VNXSDNNFVLAB2020-v2.ova)

## Installation Instructions

### Step 1: VirtualBox Setup

1. Download and install VirtualBox from the official website.
2. Install the VM VirtualBox Extension Pack for additional features.

### Step 2: Import the Virtual Machine

1. Download the VNXSDNNFVLAB2020-v2.ova file to your local system.
2. In VirtualBox, go to **File > Import Appliance**. Select the downloaded `.ova` file and follow the prompts to import.

### Step 3: Starting the Virtual Machine

1. Once imported, select the VM in VirtualBox and click **Start**.
2. Inside the VM, you'll find shortcuts to essential tools such as a terminal, Firefox, and Wireshark on the desktop.

### Step 4: Scenario Setup

1. Use Firefox within the VM to download the SD-WAN scenario package: [sdw-p1.tgz](http://idefix.dit.upm.es/download/coit-sdw/sdw-p1.tgz).
2. Extract it to the desktop for easy access.
3. In the shared folder copy all the files that are in this repository.

### Step 5: Launching the Scenario

1. Open a terminal in the VM.
2. Gain root access: `sudo su`.
3. Navigate to the scenario directory: `cd /home/upm/Desktop/sdw-p1`.
4. Start the VNX scenario: `vnx -f sase_tfg.xml -t`.

### Step 6: Configuring the Scenario

1. Open each SDEDGE console.
2. Access the console with the credentials.
3. Excute the ./ryu-XX.sh (shell script in each machine).
4. Start the VNX scenario: `vnx -f sase_tfg.xml -t`.
5. Configure the *Snort* by opening a new sdedge0 terminal an executing the available `./snort-50.sh` and in other console the `sudo -i` and `./iniciaSnort.sh`


## Cleanup

To release the scenario and clean up resources, run: `vnx -f sase_tfg.xml -P`.



