# Project-13-ELK-Stack
UofT CS Course: Contains Ansible, Bash Scripts, Network Diagrams 

The files in this repository were used to configure the network depicted below.

https://github.com/villafu5/UOFTCSPROJECT1/blob/main/Diagrams/Network%20Diagram%20with%20Elk.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  https://github.com/villafu5/UOFTCSPROJECT1/blob/main/Ansible/filebeat-playbook.txt

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box?
Load Balancers ensures availability and protects organizations from distributed denial-of-servive (DDos) attacks by distributing network traffic across multiple servers. Jump Box servers act as a single point of access to machines within the network, thus increasing security as incoming and outgoing traffic within the network can be monitored through a single focal point.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system logfiles and system usage.

- What does Filebeat watch for? 
Filebeat watches logfiles & log events 
- What does Metricbeat record? 
Metricbeat records CPU usage, memory usage, memory rss, as well as many other statistics for processes that are running on the system that is being monitored.

The configuration details of each machine may be found below.

| Name     | Function    | IP Address | Operating System |
|----------|-------------|------------|------------------|
| Jump Box | Gateway     | 10.0.0.4   | Linux            |
| Web1     | Server      | 10.0.0.5   | Linux            |
| Web2     | Server      | 10.0.0.6   | Linux            |
| ElkStack |Log Gathering| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox Provisioiner machine can accept connections from the Internet. Access to this machine is only llowed from the following IP addresses: my public ip address 178.89.0.0/16

Machines within the network can only be accessed by the JumpBox Provisioner.
The only machine that had access to the ELK VM was the Jump Box Provisioner with the IP address of 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 178.89.0.0/16        |
| Web 1 & 2| No                  | 10.0.0.4             |
| ElkStack | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible improves efficiency, management, and scalability by allowing you to manage all of your servers at once instead of managing each server one by one.

The playbook implements the following tasks:
- First you want to configure the Elk VM with Docker
- Secondly you want to install docker.io & python3-pip
- Third you want to install th docker module
- Lastly, you want to download the sebp/elk:761 image 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/villafu5/UOFTCSPROJECT1/blob/main/Diagrams/ELKSTACK/sebpelk761.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 & 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat System & Metricbeat Docker

These Beats allow us to collect the following information from each machine:
FileBeat collects log & file data which can be used to monitor and track any unusual behaviour. Filebeat will allow you to view syslog events from each individual host in real time.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the elk-playbook.yaml file to the ansible containers file.
- Update the ansibles hosts file to include [elk] as a group with its specific IP address. Meanwhile if you want to install Filebeat, you would need to specify the specific host that you want to install the service on, in this project it would be installed in the [webservers] host group which contains the two virtual machines that were created which were Web1 & Web2
- Run the playbook, and navigate to http://40.69.0.0/16:5601/app/kibana to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._# UOFTCSPROJECT1
CYBERSECURITY COURSE PROJECT 1
1. SSH into the JumpBox Provisioner (ssh username@jumpboxIP)
2. Start and then attach to your Ansible container (sudo docker start container "name of container" & then run sudo docker attach "name of container")
3. run nano /etc/ansible/hosts (edit this by adding [elk] as a group so that ansible can discover it and then connect to it)
4. cd /etc/ansible to create the yml file in order to install elk
5. touch install-elk.yml
The following yml scripts and config files can be seen in the link below: 
https://github.com/villafu5/UOFTCSPROJECT1/tree/main/Ansible