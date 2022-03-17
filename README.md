**Automated ELK Stack Deployment**

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/miguelyousif/ElkProject/blob/main/Images/Elk%20Diagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the configuration file may be used to install only certain pieces of it, such as Filebeat.

  [Install Elk Playbook](https://github.com/miguelyousif/ElkProject/blob/main/Ansible/Install%20Elk%20Playbook) - [Install VM with Docker](https://github.com/miguelyousif/ElkProject/blob/main/Ansible/Install%20Docker) - [Install Filebeat Playbook](https://github.com/miguelyousif/ElkProject/blob/main/Ansible/Install%20Filebeat) - [Install Metricbeat Playbook](https://github.com/miguelyousif/ElkProject/blob/main/Ansible/Install%20Metricbeat)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


**Description of the Topology**
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting exposing the backend servers directly to the external internet network.
Load Balancers contribute to the Availability aspect of security, which is in regards to the CIA (Confidentiality, Integrity, Availability) Triad through the support of network performance and redundancy. 
Jumpbox is used for System Administration and secured external network access. The advantage of a Jumpbox is the origination point for launching Administrative Tasks. This sets the Jumpbox as a Secure Admin Workstation. All admins that conduct any management tasks are required to connect to the Jumpbox this way. Jumpbox is configured for the restrictive access that provides a more secure environment for everyone.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the filesystem and system resources.
Filebeat watches for any log files or locations that are configured, collecting log events and forwarding them to the Elasticsearch or Logstash for indexing.
Metricbeat records the metric and statistical data from the operating system and from the running services on the host servers.

The configuration details of each machine may be found below.
![Chart 1](https://user-images.githubusercontent.com/94030092/158714342-0aad3e49-043a-4551-a313-9b613c91b76b.PNG)

**Access Policies**

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Whitelisted IP address: Admins personal IP address machines within the network can only be accessed via SSH.
Which machine did you allow to access your Elk VM? What was its IP address? JumpBoxProvisioner 10.0.0.4

A summary of the access policies in place can be found in the table below.

![Chart 2](https://user-images.githubusercontent.com/94030092/158714566-2ee8e08f-72ab-4942-9444-6173a4ed3f0b.PNG)


**Elk Configuration**

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because…
The main advantage is that Ansible brings automation of and simplification of repetitive, complex and tedious operations of a systems administrator.

The playbook implements the following tasks:
- Install: docker.io
- Install python3-pip
- Install docker module
- Increase Memory Use: sysctl -w vm.max_map_count=262144
- Download and Launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text](https://github.com/miguelyousif/ElkProject/blob/main/Images/761%20Elk.PNG)

**Target Machines & Beats**
This ELK Server is configured to monitor the following machines:

![Chart 3](https://user-images.githubusercontent.com/94030092/158714737-c7af4f7e-2030-4002-856f-ba8297373b85.PNG)


We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat is a lightweight shipper that forwards and centralizes log data. It monitors log files or locations that you specify, collects log events, and will forward them to either Elasticsearch or Logstash for indexing.
- Metricbeat collects metrics from the operating system and other services running on the server. Then it takes the metrics and stats it collected, and ships them to the output that you specify.

**Using the Playbook**
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
Copy the ansible_config.yml file to /etc/ansible directory.
Update the configuration file to include the private IP of the Elk-server to the Elasticsearch and Kibana sections listed.
Run the playbook, and navigate to http://[0.0.0.0]:5601/app/kibana to check that the installation worked as expected.
