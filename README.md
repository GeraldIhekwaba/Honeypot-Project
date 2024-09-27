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
Before installing Cowrie, it’s necessary to configure the SSH service to listen on a different port, such as port 2222, rather than the default port 22. To do this, go to the SSH configuration file located at /etc/ssh/sshd_config, and modify the listening port. [_(Click here to view the port change)_](/Screenshots/sshconfiguration.png)
After making this adjustment, restart the SSH service by running "sudo systemctl restart ssh". You can verify that the new port is active by using the command nmap "your-ip-address" to check the open ports,[_(Here's an image of the nmap results)_](/Screenshots/ssh_nmap_scan.png).

Now that the SSH configuration is complete, you can proceed to install Cowrie. First, download and install the required dependencies for Cowrie [_(View the dependencies installation)_](/Screenshots/cowrie_dependencies.png). Once the dependencies are installed, create a new Cowrie user account with the password disabled. After creating the user, switch into the Cowrie user account. Next, clone the official Cowrie GitHub repository, and once the cloning process is complete [_(Preview of the cowrie installation process)_](Screenshots/cowrie_installation.png), navigate into the newly created Cowrie directory to continue with the setup.
Once inside, create a Python virtual environment, then activate it [_(Cowrie Virtualenv)_](/Screenshots/virtualenv.png). After activation, proceed to install the necessary requirements, by inputing "pip install -r requirements.txt" wait for a couple seconds then it should be fully installed.

Next, locate the cowrie.cfg.dist file. By default, Cowrie is installed with this template configuration file. To create a backup, make a copy of this file using the "cp" command and rename it to cowrie.cfg. The newly created cowrie.cfg will take precedence over the template configuration. Afterward, edit the cowrie.cfg file to configure Cowrie to listen on TCP port 22[_(Cowrie configuration)_](/Screenshots/cowriecfg_config.png).
Before starting Cowrie, it’s necessary to bind it to port 22 using authbind, since only privileged users can bind to ports below 1024. To do this, first install authbind if it’s not already available on your system. Then, grant Cowrie permission to bind to port 22 by running the following command[_(Authbind Cowrie to port 22)_](/Screenshots/authbind_cowrie.png).
This ensures Cowrie has the necessary permissions to bind to port 22 without needing elevated privileges. Once configured, you can proceed with starting Cowrie.

To start Cowrie, you can navigate to the bin directory where Cowrie is located and run the command directly. However, a more efficient way is to export the path to that bin file, allowing you to use Cowrie using simple commands like cowrie start, cowrie stop, or cowrie restart from anywhere in the account.
Instead of exporting the path every time you need to use Cowrie, you can add the exported path to the .bashrc configuration file. To do this, first, navigate to your home directory and run ls -a to display hidden files. Then, edit the .bashrc file and add the exported path command[_(Editing the .bashrc)_](/Screenshots/cowrie_bashrc.png). Save the changes, and finally, run "source ~/.bashrc" to apply the updated configuration. This will allow you to run Cowrie commands from anywhere within the user account without needing to manually export the path each time,with the path exported you can now start running Cowrie[_(Cowrie running successfully)_](/Screenshots/cowrie_running.png).

#### Setting up Splunk



