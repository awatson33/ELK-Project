# ELK-Project
ELK stack project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project Diagram](https://drive.google.com/file/d/1TaGyxzF1lfAMVu0dwpyjiqOlXGe-lavw/view?usp=sharing)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ELK-Project file may be used to install only certain pieces of it, such as Filebeat.

![/etc/ansible/install-elk.yml](https://drive.google.com/file/d/13iOd8zkIR63NfUnccIBv_QNLCDzR5Chf/view?usp=sharing)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.
- _Load balancers secure the network from DDoS attacks by shifting traffic between the servers. The advantage of having a jump box is to provide a user with access through one node that can be easily secured and monitored._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- _Filebeat monitors log files and collects log events and forwards them to either Elasticsearch or Logstash for indexing._
- _Metricbeat collects metrics and statistics from the operating system and forwards them to Elasticsearch or Logstash._

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.6   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.7   | Linux            |
| ELK-VM   | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _Home Public IP_

Machines within the network can only be accessed by SSH.
- _The Jump Box has access to the ELK VM. Jump Box IP: 10.0.0.6_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Home IP              |
| Web-1    | No                  | 10.0.0.6             |
| Web-2    | No                  | 10.0.0.6             |
| ELK-VM   | No                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _it allows the configuration tasks to be automated, which frees time to be spent on other project tasks._

The playbook implements the following tasks:
- _Install Docker.io_
- _Install Python pip_
- _Configure the target machine to use more memory_
- _Download and launch an ELK docker container module_
- _Enable docker service_

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker ps](https://drive.google.com/file/d/1g4lXolJea4wgL23JHesf86MxO2P1sVse/view?usp=sharing)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _Web-1: 10.0.0.5_
- _Web-2: 10.0.0.7_

We have installed the following Beats on these machines:
- _Filebeat and Metricbeat_

These Beats allow us to collect the following information from each machine:
- _Filebeat collects log data (e.g. system log host names and processes being run)_
- _Metricbeat collects the metrics/statistics from the operating system. (e.g. CPU usage, disk space, memory, and number of containers)_

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the filebeat configuration file to /etc/ansible/file folder.
- Update the /etc/ansible/hosts file to include webserver and elk server IP addresses
- Run the playbook, and navigate to http://10.1.0.4:5601/app/kibana to check that the installation worked as expected.
