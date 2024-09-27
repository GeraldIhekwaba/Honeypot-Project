# Honeypot Project

## Overview
This project involves setting up a Cowrie honeypot, forwarding the logs to Splunk for monitoring and visualization.

## Prerequisites
1) **VM Setup**: For this project, I have set up a virtual lab consisting of a Linux-based honeypot system on a macOS system. The guest operating system is Debian 12, chosen for its widespread use and familiarity to potential attackers. The following VM configuration details have been implemented:

  -	VM Platform: VMware fusion
  -	Guest OS: Debian 12
  -	Network Configuaration: Bridged mode, allowing direct communication with the host network

2) **Software Tools**: Tools used to conduct and monitor the attack simulation, including log management and visualization:

  - Honeypot: Cowrie ,which is an interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interactions performed by the attacker. 
  - Terminal: The macOS terminal is a command-line interface used to interact with the system, run scripts, and execute commands on macOS.
  - Splunk Universal Forwarder: A lightweight agent used to collect and forward log data to a Splunk Enterprise instance.
  - Splunk Enterprise: A software platform for indexing, searching, and visualizing large volumes of machine-generated data.

## Setup/Configuration Instructions
#### Installation and Configuration of Cowrie
Before installing Cowrie, it’s necessary to configure the SSH service to listen on a different port, such as port 2222, rather than the default port 22. To do this, go to the SSH configuration file located at /etc/ssh/sshd_config, and modify the listening port. [(Click here to view the port change)](/Screenshots/sshconfiguration.png)
After making this adjustment, restart the SSH service by running "sudo systemctl restart ssh". You can verify that the new port is active by using the command nmap "your-ip-address" to check the open ports,[(Here's an image of the nmap results)](/Screenshots/ssh_nmap_scan.png).

Now that the SSH configuration is complete, you can proceed to install Cowrie. First, download and install the required dependencies for Cowrie [(View the dependencies installation)](/Screenshots/cowrie_dependencies.png). Once the dependencies are installed, create a new Cowrie user account with the password disabled. After creating the user, switch into the Cowrie user account. Next, clone the official Cowrie GitHub repository, and once the cloning process is complete [(Preview of the cowrie installation process)](Screenshots/cowrie_installation.png), navigate into the newly created Cowrie directory to continue with the setup.

Once inside, create a Python virtual environment, then activate it. After activation, proceed to install the necessary requirements.


