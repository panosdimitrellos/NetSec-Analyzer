# WiFi-NID


![wifinid-small](https://github.com/panosdimitrellos/WiFi-NID/assets/34653518/0b17f762-e7b6-42cf-9dd2-dcf192bebcc2)
<p align="center">
<img src="https://img.shields.io/badge/GNU_bash-5.2.15-brightgreen?logo=gnu-bash&logoColor=white&style=flat" /> 
<img src="https://img.shields.io/badge/TShark%20(Wireshark)-4.0.3-blue?logo=wireshark&logoColor=white&style=flat"/>
<img src="https://img.shields.io/github/languages/code-size/panosdimitrellos/WiFi-NID?color=black"/>
<img src="https://img.shields.io/github/license/panosdimitrellos/WiFi-NID"/>
</p>

## About


WiFi-NID is a powerful Network Intrusion Detection tool written in Bash designed to detect various types of attacks in WiFi networks and networks in general. With WiFi-NID, you can capture live traffic and analyze captured files to identify potential security threats. This README provides an overview of the tool's features and instructions on how to use them effectively.
WiFi-NID offers an innovative approach to detecting malicious activity in WiFi networks, by focusing on WiFi specific attack features to identify attacks that originate from the 802.11 layer. As WiFi-NID operates at the edge of the WiFi network, it can be easily integrated as an add-on security mechanism and may be complementary to general IDS solutions that do not focus at the WiFi layer.
For more details about the tool, please refer to this paper: https://ieeexplore.ieee.org/document/10218077.

### Update:
I extended my initial implementation to increase the efficiency of detection using mathematical and statistical techniques in `detect_deauthentication_attacks.py`. This approach can also be applied to detect Disassociation Attacks, Authentication DoS, and Fake AP Beacon Flooding. 
More details can be found in the related journal paper here: https://www.itu.int/pub/S-JNL-VOL5.ISSUE1-2024-A07 

## Table of contents 

* [Installation](#installation)
* [Usage](#usage)
* [Supported features](#supported-features)
  * [Detection of Wireless Network Attacks](#detection-of-wireless-network-attacks)
  * [Detection of Network Attacks](#detection-of-network-attacks)
  * [Detection of Network Port Scanning](#detection-of-network-port-scanning)
  * [Detection of Host Discovery](#detection-of-host-discovery)
  * [Detection of Unauthorized Login Attempts](#detection-of-unauthorized-login-attempts)
* [Examples](#examples)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)

## Installation

To install WiFi-NID, follow these steps:

1. Clone the repository: `git clone https://github.com/panosdimitrellos/WiFi-NID.git`
2. Change to the project directory: `cd WiFi-NID`
3. Install the required dependencies: `bash install_required_packages.sh`
4. Ensure that the pcap file you want to analyze is in the same directory as the tool.

**Installation on Windows**

WiFI-NID is written in Bash, so to run it on Windows you can use a Unix-like environment.
Here is some popular options for Unix-like enviroments you could install and run the script.
   - Git Bash: Download and install Git from the official website: https://git-scm.com/.
   - Cygwin: Download and run the Cygwin installer from the official website: https://www.cygwin.com/.
   - Windows Subsystem for Linux (WSL): Follow the official Microsoft documentation to install WSL and choose a Linux distribution: https://docs.microsoft.com/en-us/windows/wsl/.

Note: Make sure the WiFI-NID has the execute permission. You can set the permission using `chmod +x wifinid.sh`.

## Usage 

Open a terminal and navigate to the WiFi-NID project directory.
1. Run the script: `bash wifinid.sh`
2. You will be presented with a menu. Select the appropriate options as instructed.
3. Depending on your selection, you may need to provide the pcap file to analyze or choose the type of attack to detect.
4. WiFi-NID will generate a detailed report based on the analysis of the pcap file and display it in the terminal.
5. Analyze already captured pcap files or capture live traffic and start analyzing them.

## Supported features

### Detection of Wireless Network Attacks

Using this option we can detect:
* **Deauthentication Attacks** - from tools like aireplay-ng, mdk3 and mdk4.
* **Disassociation Attacks** - from tools like mdk3 and mdk4.
* **Authentication DoSs** - from tools like mdk3 and mdk4.
* **Fake AP Beacon Flood** - from tools like mdk3 and mdk4.
* **WPS Bruteforce Attacks** - from tools like reaver and bully.

![image](https://github.com/panosdimitrellos/WiFi-NID/assets/34653518/9ee7e3f2-3759-4725-a7d1-5e9fd5662201)

### Detection of Network Attacks

Using this option we can detect:
* **ARP Poisoning** - from tools like arpspoof and ettercap.
* **ICMP Flood** - from tools like fping and hping.
* **VLAN Hopping** -  from tools like frogger and yersinia (future work).

![image](https://github.com/panosdimitrellos/WiFi-NID/assets/34653518/3bd0cc89-2007-4c34-b131-cfd3b839fec9)

### Detection of Network Port Scanning

Using this option we can detect:
* **TCP SYN Scan or Stealth Scan** - from tools like nmap.
* **TCP Xmass Scan** - from tools like nmap.
* **TCP Null Scan** - from tools like nmap.
* **TCP FIN Scan** - from tools like nmap.
* **TCP Connect() Scan** - from tools like nmap.
* **UDP Port Scan** - from tools like nmap.

![image](https://github.com/panosdimitrellos/WiFi-NID/assets/34653518/a3c759e3-0a24-408a-8647-10db447efbfb)

### Detection of Host Discovery

Using this option we can detect:
* **ARP Scanning** - from tools like arp-scan.
* **IP Protocol Scan** - from tools like nmap.
* **ICMP Ping Sweeps** - from tools like nmap.
* **TCP Ping Sweeps** - from tools like nmap.
* **UDP Ping Sweeps** - from tools like nmap.

![image](https://github.com/panosdimitrellos/WiFi-NID/assets/34653518/933201c1-4fce-4bad-99f1-7e10f2838a54)

### Detection of Unauthorized Login Attempts

This is an ongoing future work on WiFi-NID.

Using this option we can detect:
* **SSH Unauthorized Login Attempts**
* **FTP Unauthorized Login Attempts**
* **RDP Unauthorized Login Attempts**

![image](https://github.com/panosdimitrellos/WiFi-NID/assets/34653518/02b2dd77-8f63-44ac-ab11-096cb16af794)

## Examples

Here is an example of using WiFi-NID:

* Analyzing a captured pcap file (LAB.pcapng) for Deauthentication attacks:

![image](https://github.com/panosdimitrellos/WiFi-NID/assets/34653518/4412cc90-ddd4-41a3-8fc2-95d75eae36c6)
...
![image](https://github.com/panosdimitrellos/WiFi-NID/assets/34653518/56194de2-fc6a-434e-b060-63a08ab1ae09)

## Contributing

Contributions to WiFi-NID are welcome! If you have any improvements, bug fixes, or new features to propose, please submit a pull request

## License

Nothing for now.

## Contact

email: panosdimitrellos@gmail.com 
