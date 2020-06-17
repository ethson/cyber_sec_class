## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(Diagrams/ElkArchitecture.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the `Ansible/filebeat-playbook.yml` file may be used to install only certain pieces of it, such as Filebeat.


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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system logs and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.1.4   | Linux            |
| DVWA     | Web App  | 10.0.1.7   | Linux            |
| DVWA     | Web App  | 10.0.1.8   | Linux            |
| ELK      | Kibana   | 10.0.1.9   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
**_YOUR PUBLIC IP_**

Machines within the network can only be accessed by Jump Box machine, 10.0.1.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | PUBLIC IP, Jump Box  |
| DVWA     | No                  | Jump Box, ELK, LB    |
| LB       | Yes                 | PUBLIC IP            |
| ELK      | Yes                 | PUBLIC IP, Jump Box  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it ensures consistency and removes human error. It's also very fast.

The playbook implements the following tasks:
Download Filebeat
Install Filebeat
Add filebeat-config.yml to the etc/filebeat of the machine to be monitored
Enable and Configure System module for filebeat
Set-up Filebeat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
!(Images/elk_sepb_install.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
DVWA's: 10.0.1.7, 10.0.1.8

We have installed the following Beats on these machines:
FileBeat

These Beats allow us to collect the following information from each machine:
Filebeat collects system logs, an example of these would be ssh logins

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node (Jump Box) and follow the steps below:
- Copy the (Ansible/elk.yml) file to /etc/ansible/roles/
- Update the hosts file to include the elkservers
- Run the playbook, and navigate to **_ELK PUBLIC IP_**:5601 to check that the installation worked as expected.

