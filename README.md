## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Cybersec/Diagrams/ELKstackNetwork.JPG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  -Cybersec/Ansible

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network. 
   - Load balancers protect the Availability aspect of security, by directing traffic to the most stable server with the requested information. 	
	The advantage of having a jump box is security; being the only method of accessing the network means there is only one location that 			must be protected

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
   -What does Filebeat watch for? Filebeat watches for general or specific log events.
   -What does Metricbeat record? Metricbeat watches the metrics such as runtime on machines and also the processes running.

The configuration details of each machine may be found below.


| Name     | Function | IP Address             | Operating System |
|----------|----------|------------------------|------------------|
| Jump Box | Gateway  |Public: 20.124.176.203  | Linux            |
|          |          |Private: 10.1.0.4       |                  |
| Web-1    | Webserver|Private: 10.1.0.10      | Linux            |
| Web-2    | Webserver|Private: 10.1.0.11      | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- my Local Host workstation

Machines within the network can only be accessed by my local host workstation.
- Which machine did you allow to access your ELK VM? What was its IP address?
   - Jump Box at 20.124.176.203

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses      |
|-----------|---------------------|---------------------------|
| Jump Box  | Yes                 | my local host workstation |
| Web-1     | No                  | 10.1.0.4                  |
| Web-2     | No                  | 10.1.0.4                  |
| Elk Server| Yes                 | 10.1.0.4 and my local host|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
   -Using something like Ansible can save time configuring many machines at once or newly added machines automatically, while removing the           chance  of human error
 
The playbook implements the following tasks:
- Installing docker.io
- Installing Python3-pip
- Installing Docker through pip
- Increasing allowed virtual memory
- Using the increased memory
- Downloading and launching Docker ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/ELKDockerPS)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.1.0.10
- Web-2 10.1.0.11

We have installed the following Beats on these machines:
-Filebeats and Metricbeats

These Beats allow us to collect the following information from each machine:
- Filebeat collects log data such as audit logs and server logs and allows them to be displayed in an easily readable manner
- Metricbeat collects metrics of the machine, such as uptime, CPU and memory usage, load

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the hosts file to include the IP address of the machines you wish to update
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.





- _Which file is the playbook? Where do you copy it?_ 	
	
	The playbook file to install an ELK stack is called Install-elk.yml and must be copied to the /etc/ansible directory
	

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
	
	The hosts file must be updated with the IP address of each machine the playbooks are to be run on. You can specify which machine a 	 particular playbook is run on by adding them to the hosts file under different groupss and then specifying which group the playbook 	 will run on when writing the .yml file


- Which URL do you navigate to in order to check that the ELK server is running?
	
	http://20.112.88.109:5601/app/kibana#/home
