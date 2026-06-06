# pfSense Firewall Security Lab

## Overview

This project demonstrates the deployment of a pfSense-based network security lab using VirtualBox. The lab simulates a real-world network environment with segmented WAN and LAN networks, an Ubuntu web server, and a Kali Linux attacker machine. Security testing was performed by launching ICMP flood attacks using hping3, monitoring traffic with Wireshark, and mitigating attacks through pfSense firewall rules.

## Lab Architecture

```text
Kali Linux (Attacker)
192.168.1.20
        |
        |
   pfSense WAN
   192.168.1.18
        |
   pfSense LAN
   10.10.10.1
        |
        |
Ubuntu Server (Victim)
10.10.10.100
```

## Technologies Used

* pfSense CE 2.7.2
* VirtualBox
* Kali Linux
* Ubuntu Desktop
* Apache2 Web Server
* Wireshark
* hping3

## Features

* Multi-zone network segmentation (WAN/LAN)
* DHCP configuration and routing
* Firewall rule creation and management
* Apache web server deployment
* ICMP DoS attack simulation
* Packet capture and traffic analysis
* Firewall log monitoring
* Attack mitigation and verification

## Configuration

### pfSense

* WAN Interface: DHCP (192.168.1.18)
* LAN Interface: 10.10.10.1/24
* DHCP Range: 10.10.10.100 - 10.10.10.199

### Ubuntu Victim

* IP Address: 10.10.10.100
* Apache2 Web Server Installed

### Kali Linux Attacker

* IP Address: 192.168.1.20
* hping3 Installed

## Attack Simulation

### Verify Connectivity

```bash
ping 10.10.10.100
```

### Launch ICMP Flood Attack

```bash
sudo hping3 -1 --flood 10.10.10.100
```

### Monitor Traffic

```bash
sudo wireshark
```

Apply filter:

```text
icmp
```

## Mitigation

A firewall rule was created on pfSense to block traffic from the Kali attacker machine.

### Firewall Rule

```text
Action: Block
Source: 192.168.1.20
Destination: 10.10.10.100
Protocol: Any
Logging: Enabled
```

## Results

* Successfully simulated ICMP flood attacks using hping3.
* Captured malicious traffic using Wireshark.
* Implemented firewall rules to block attack traffic.
* Verified blocked packets through pfSense firewall logs.
* Demonstrated attack detection and mitigation in a controlled environment.

## Skills Demonstrated

* Firewall Administration
* Network Security
* Packet Analysis
* Traffic Monitoring
* Routing and Switching
* DHCP Configuration
* Security Monitoring
* Incident Detection
* Attack Simulation
* Log Analysis


## Screenshots

### Wazuh Dashboard
![Wazuh Dashboard](screenshots/wazuh1.jpg)

### Active Agents
![Active Agents](screenshots/wazuh2.jpg)

### Security Alerts
![Security Alerts](screenshots/wazuh3.jpg)

## Author

Parthiv Lalakiya
Cybersecurity & SOC Analyst Enthusiast
