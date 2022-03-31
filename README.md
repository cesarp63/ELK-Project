## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.  
![Network Diagram](https://github.com/cesarp63/ELK-Project/blob/ee1223cee294c57a4f4a0f33e3f286f1cd2a4e22/Project%20Diagram%20.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the **YAML** file may be used to install only certain pieces of it, such as Filebeat.


![Filebeat-Configuration](https://github.com/cesarp63/ELK-Project/blob/f4ebe9142a4fbe1ce80e7cec9e26a8f3ea3553eb/CONFIG%20FOLDER/filebeat-configuration.yml)


![Filebeat-Playbook](https://github.com/cesarp63/ELK-Project/blob/f4ebe9142a4fbe1ce80e7cec9e26a8f3ea3553eb/CONFIG%20FOLDER/filebeat-playbook.yml)


![Metricbeat-Configutation](https://github.com/cesarp63/ELK-Project/blob/f4ebe9142a4fbe1ce80e7cec9e26a8f3ea3553eb/CONFIG%20FOLDER/metricbeat-configuration.yml)


![Metric-Playbook](https://github.com/cesarp63/ELK-Project/blob/f4ebe9142a4fbe1ce80e7cec9e26a8f3ea3553eb/CONFIG%20FOLDER/metricbeat-playbook.yml)


![Elk](https://github.com/cesarp63/ELK-Project/blob/679022265d3d93b92c46ed09e9f13a9963280522/CONFIG%20FOLDER/install-elk.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly **available**, in addition to restricting **inbound access** to the network.
 What aspect of security do load balancers protect? 
**A load balancer protects azure resources within our virtual network. They protect the system from DDos attacks.** 

What is the advantage of a jump box?
**The advantage of a jump box is that it improves the security aspect. It will protect all virtual machines from being exposed to the public network.** 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **filesystem** and system **metric**.
- What does Filebeat watch for? **Filebeat watches for changes in logs and files.**

- What does Metricbeat record? **It records machine metrics and stats.**

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 13.67.232.43,10.0.0.4   |Linux|
| Web-1    | DVWA     | 10.0.0.5                |Linux|
| Web-2    | DVWA     | 10.0.0.6                |Linux|
|Project-VM| Kibana   | 10.1.0.4                |Linux|
|Red-Teamlb| load Ba  | 23.99.15.28             |Linux|

### Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the **Jump Box** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
**172.15.78.50, it would be my home network public IP.**
Machines within the network can only be accessed by **SSH.**
Which machine did you allow to access your ELK VM? What was its IP address?
**Jump box  13.67.232.43**
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses   |
|----------|---------------------|------------------------|
| Jump Box | no                  |172.15.78.50,User Pub IP|
| Web-1    | Yes                 |any                     |
| Web-2    | Yes                 |any                     |
| ELK-VM   | Yes                 |User Pub IP, 10.1.0.4   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous **because it would let us access our container faster and help us have a consistent connection. This avoids any human error that can occur by performing the configuration manually.** 

The playbook implements the following tasks:
**First Step: ssh to my Jump-box-provisioner (ssh sysadmin@13.67.232.43)
Second step: It is to run my ansible container. sudo docker ps, sudo docker start interesting_booth and sudo docker attach interesting_booth
Third Step: cd to /etc/ansible/roles. I created the Elk playbook (Elk_playbook.yml)
Fourth Step: I ran the Elk_playbook.yml in the same directory
Fifth Step: Now I ssh to my Project-VM to check if the server is running**


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Sudo Docker PS](https://github.com/cesarp63/ELK-Project/blob/d7d9198ca959a19bd17ccc7de4b08594e770b2f0/Pictures/dock-ps-elk-output.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- **Web-1 (10.0.0.5)**
- **Web-2 (10.0.0.6)**


We have installed the following Beats on these machines:
- **Filebeat**
- **Metricbeat**
These Beats allow us to collect the following information from each machine:
- **filebeat will monitor logs and collect data logs. It will display output directly to elasticsearch or logstash.** 
- **metricbeat collects metrics and statistic.The data output is collected by the operating system and services running in the server.**


![Filebeat-Configuration](https://github.com/cesarp63/ELK-Project/blob/f4ebe9142a4fbe1ce80e7cec9e26a8f3ea3553eb/CONFIG%20FOLDER/filebeat-configuration.yml)


![Filebeat-Playbook](https://github.com/cesarp63/ELK-Project/blob/f4ebe9142a4fbe1ce80e7cec9e26a8f3ea3553eb/CONFIG%20FOLDER/filebeat-playbook.yml)


![Metricbeat-Configutation](https://github.com/cesarp63/ELK-Project/blob/f4ebe9142a4fbe1ce80e7cec9e26a8f3ea3553eb/CONFIG%20FOLDER/metricbeat-configuration.yml)


![Metric-Playbook](https://github.com/cesarp63/ELK-Project/blob/f4ebe9142a4fbe1ce80e7cec9e26a8f3ea3553eb/CONFIG%20FOLDER/metricbeat-playbook.yml)



### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the **install-elk.yml** file to **/etc/ansible**.
- Update the **/etc/ansible/hosts** file to include **the ELK server (and the webservers)**
- Run the playbook, and navigate to **http://20.213.143.66:5601/app/kibana#** to check that the installation worked as expected.


- Which file is the playbook? Where do you copy it? **/etc/ansible/install-elk.yml**
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? **/etc/ansible/hosts**
- _Which URL do you navigate to in order to check that the ELK server is running? **http://20.213.143.66:5601/app/kibana#/home**

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
