# Cybersecurity-Ethanurie
This repository shows my Cybersecurity diagrams, scripts, playbooks, etc.
Two different projects have dedicated folders. The rest of the files relate to the project below.

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(Images/"Diagram of VM's".png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .txt file may be used to install only certain pieces of it, such as Filebeat.

  Playbooks.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
-Load balancing protects the availability of the asset, while the advantage of Jumpbox is a secure starting point and base that can be changed or transported.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the machine and system logs.

The configuration details of each machine may be found below.

| Name     |   Function   | IP Address |  Operating System   |
|----------|--------------|------------|---------------------|
| Jump Box |   Gateway    | 10.0.0.4   | Linux (ubuntu 18.04)|
| Elk      |  Monitoring  | 10.1.0.4   | Linux (ubuntu 18.04)|
| Web1     |Load Balancing| 10.0.0.7   | Linux (ubuntu 18.04)|
| Web2     |Load Balancing| 10.0.0.8   | Linux (ubuntu 18.04)|
| Web3     |Load Balancing| 10.0.0.6   | Linux (ubuntu 18.04)|
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the host machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 70.95.67.30

Machines within the network can only be accessed by Ansible.
- I used the Jumpbox machine to connect to ansible with the ip of 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |Yes(public IP w/ SSH)|     70.95.67.30      |
| Elk      |Yes(public Ip w/ SSH)|     70.95.67.30      |
| Web 1-3  |No(Load Balancer only fowards traffic)|    70.95.67.30 & 10.0.0.4    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Less human error + faster and ability to reproduce same results easily

The playbook implements the following tasks:
- Installs docker.io, python3-pip, & docker module
- Increases virtual memory to allow for everything to run properly
- Makes a docker container for elk and enables the start of docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/Elk-PS.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.6 10.0.0.7 10.0.0.8

We have installed the following Beats on these machines:
- Metric & File

These Beats allow us to collect the following information from each machine:
- Filebeat collects or observes system logs for change
- Metricbeat collects metric data like CPU usage, RAM usage, etc.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible.
- Update the hosts file to include your machines information, the desires locations, and the correct IPs
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.

Download the playbook curl http://futuregithublink --output name.the.file (Edit the playbook) Nano name.the.file (Run the playbook) ansible-playbook (playbookname).yml (Check its working) ssh username@IP-address
