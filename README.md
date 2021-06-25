# Jaclyn-s_GitHub_Repository
Project 1: Elk Stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Documents/Cybersecurity-Bootcamp/Network_Topology.png]
Diagrams/Network_Topology.png
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

Ansible/my-playbook.yml
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting in-bound access to the network.
- Load balancers assist in increasing availability for applications by allocating loads across numerous machines.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Jumpbox as well as the system's internal network.
Filebeat monitors log files or specified locations in order collect data, which is then passed to Elasticsearch or Logstash._
Metricbeat records statistics and metrics regarding the operating system, as well as the services running on the server. It then delivers them to the output of your choosing. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web-1    | Container  | 10.0.0.5   | Linux            |
| Web-2    | Container  | 10.0.0.7   | Linux            |
| ELK-VM1  | ELK Server | 10.1.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
68.101.164.201

Machines within the network can only be accessed by my public IP address.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 68.101.164.201       |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Elk-VM1  | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main reasons why it is beneficial to use ansible to automate configuration are that it is open source and free of charge. In addition, using ansible simplifies the creation of software saving time and resources. 

The playbook implements the following tasks:
 
- Installion of docker.io and python3pip
- Expand the virtual memory
-Installation and downloads of dockers
-Direct dockers to launch upon each re-boot of the system


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Diagrams/Docker_PS.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1  10.0.0.5
- Web-2  10.0.0.7
We have installed the following Beats on these machines:
- Filebeat and Metricbeat were successfully installed on these machines.

These Beats allow us to collect the following information from each machine:
-  1. Filebeat is used to gather data regarding file location, as well as content. Using Kibana, one would expect to see the recent logs that Filebeat sent to Elasticsearch.
-  2. Metricbeat is used to gather metrics from the operating system. Using Kibana, one would expect to see data regarding the current services running. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the my-playbook.yml file to ansible control module.
- Update the hosts file to include the IP addresses of the web servers, as well as the ELK server.
- Run the playbook, and navigate to Kibana's Filebeat and Metricbeat sections to check that the installation worked as expected.


- _The playbook I created is titled "my-playbook.yml." When installing the playbook you must be in the /etc/ansible directory.
- _In order to update a designated machine on a playbook, it is required to edit the hosts file located within /etc/ansible to contain the public IP addresses associated with the each playbook. 
- _Which URL do you navigate to in order to check that the ELK server is running?
http://{your_elk_machine_IP}/app/kibana
