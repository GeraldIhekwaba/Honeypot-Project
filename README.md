# Honeypot Project

## Overview
This project involves setting up a Cowrie honeypot, forwarding the logs to Splunk for monitoring and visualization.

## Prerequisites
1) **VM Setup**: For this project, I have set up a virtual lab consisting of a Linux-based honeypot system. The guest operating system is Debian 12, chosen for its widespread use and familiarity to potential attackers. The following VM configuration details have been implemented:

-	VM Platform: VMware fusion
-	Guest OS: Debian 12
-	Network Configuaration: Bridged mode, allowing direct communication with the host network
-	Honeypot: Cowrie ,which is an interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interactions performed by the attacker. 

2) **Software Tools**: Tools used to carry out the attack simulation and monitor the logs:

- Terminal: The macOS terminal was used as the primary interface for simulating attacks on the honeypot by initiating SSH connections to the target machine.
