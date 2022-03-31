# ELK-Project
Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.
Note: The following image link needs to be updated. Replace diagram_filename.png Project Diagram .png .

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.
TODO: Enter the playbook file.
This document contains the following details:
Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
 What aspect of security do load balancers protect? 
A load balancer protects azure resources within our virtual network. They protect the system from DDos attacks. 
What is the advantage of a jump box?
The advantage of a jump box is that it improves the security aspect. It will protect all virtual machines from being exposed to the public network. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file and system metric
 What does Filebeat watch for?
Filebeat watches for changes in logs and files. 
What does Metricbeat record?
It records machine metrics and stats. 
The configuration details of each machine may be found below. Note: Use the Markdown Table Generator to add/remove values from the table.



|     Name        |  Function |  IP Address             | Operating System    
---------------------------------------------------------------------------
|    Jump-Box     | Gateway     |13.67.232.43, 10.0.0.4 |  linux
|     web-1       | Web Server  |10.0.0.5               |  linux 
|     web-2       | Web Server  | 10.0.0.6              |  linux
|  Load Balancer  | Dvwa        | 23.99.15.28           |  linux
|    Project VM   | Gateway     | 10.1.0.4              |  linux






Access Policies
The machines on the internal network are not exposed to the public Internet.
Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
172.15.78.50, it would be my home network public IP.
Machines within the network can only be accessed by SSH.
Which machine did you allow to access your ELK VM? What was its IP address?

|     Name        |  Publicly Accessible |  IP Address             | Operating System    
---------------------------------------------------------------------------------------
| Jump-Box        | Gateway               |13.67.232.43, 10.0.0.4 |  linux
|     web-1       | Web Server            |10.0.0.5               |  linux 
|     web-2       | Web Server            | 10.0.0.6              |  linux
|  Load Balancer  | Dvwa                  | 23.99.15.28           |  linux
|    Project VM   | Gateway               | 10.1.0.4              |  linux



Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it would let us access our container faster and help us have a consistent connection. This avoids any human error that can occur by performing the configuration manually. 

The playbook implements the following tasks:
First Step: ssh to my Jump-box-provisioner (ssh sysadmin@13.67.232.43)
Second step: It is to run my ansible container. sudo docker ps, sudo docker start interesting_booth and sudo docker attach interesting_booth
             Third Step: cd to /etc/ansible/roles. I created the Elk playbook (Elk_playbook.yml)
             Fourth Step: I ran the Elk_playbook.yml in the same directory
             Fifth Step: Now I ssh to my Project-VM to check if the server is 

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Note: The following image link needs to be updated. Replace docker_ps_output.png with the name of your screenshot image file.

Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.5
Web-2 10.0.0.6

We have installed the following Beats on these machines:
Filebeat
Metricbeat
These Beats allow us to collect the following information from each machine:
filebeat will monitor logs and collect data logs. It will display output directly to elasticsearch or logstash. 
metricbeat collects metrics and statistic.The data output is collected by the operating system and services running in the server.
Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:
Copy the install-elk.yml  file to /etc/ansible
Update the _____ file to include...
Run the playbook, and navigate to check that the installation worked as expected.
TODO: Answer the following questions to fill in the blanks:
Which file is the playbook? Where do you copy it?
/etc/ansible/file/filebeat-configuration.yml
Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
/etc/ansible/hosts


_Which URL do you navigate to in order to check that the ELK server is running?
As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.
