# Honeypot Project

## Overview
This project involves setting up a Cowrie honeypot, forwarding the logs to Splunk for monitoring and visualization.

## Prerequisites
1) **VM Setup**: For this project, I have set up a virtual lab consisting of a Linux-based honeypot system on a macOS system. The guest operating system is Debian 12, chosen for its widespread use and familiarity to potential attackers. The following VM configuration details have been implemented:

  -	VM Platform: VMware fusion
  -	Guest OS: Debian 12
  -	Network Configuaration: Bridged mode, allowing direct communication with the host network

2) **Software Tools**: Tools used to conduct and monitor the attack simulation, including log management and visualization:

  - Terminal: The macOS terminal is a command-line interface used to interact with the system, run scripts, and execute commands on macOS.
  - Splunk Universal Forwarder: A lightweight agent used to collect and forward log data to a Splunk Enterprise instance.
  - Splunk Enterprise: A software platform for indexing, searching, and visualizing large volumes of machine-generated data.
  - Honeypot: Cowrie ,which is an interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interactions performed by the attacker. 

