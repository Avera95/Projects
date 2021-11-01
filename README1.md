## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._ filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_ Filebeat keeps track of your information 
- _TODO: What does Metricbeat record?_  Metricbeat collects metrics and statistics 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| VM1      |Server     |10.0.0.5   | Linux                 |
| VM1      |Server     |10.0.0.6   | Linux                 |
| ElkServer   |Server| 10.1.0.4      Linux             |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ public IP addresses from home

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ 52.160.37.157

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | no              |     |52.160.37.157
|Elk Server| no                    |20.57.178.28                     |
|Web-1     | no                    |10.0.0.4  ssh                    |
 web-2       no                     10.0.0.4  ssh
 LB          no                     40.78.125.160(via http)
 ### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ An advantage is you can place many commands in a playbook.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install: docker.io
- Install: python-pip3
- Install: docker python module 
- user more memory 
-  Download and Launch docker container:elk
- Enable service docker boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_ 10.0.0.5, 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed
-Elk Server 
-Web-1
-web-2

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- Filebeat-log events
- metricbeat: system metrics and system statistics
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.  curl  https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat >> /etc/ansible/filebeat-config.yml
- curl https://gist.githubusercontent.com/slape/58541585cc1886d2e26cd8be557ce04c/raw/0ce2c7e744c54513616966affb5e9d96f5e12f73/metricbeat >> /etc/ansible/metricbeat-config.yml

-Update the filebeat-config.yml and metricbeat-config.yml files




- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ Filebeat playbook: filebeat-playbook.yml - copy to /etc/ansible/roles
- _Which file do you update to make Ansible run the playbook on a specific machine?  Metricbeat playbook: metricbeat-playbook.yml - copy to /etc/ansible/roles                  
 How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ The hosts file needs to be modified in order to set machines in the correct groups (webserver) (elkserver). Once machines are in the correct group the playbook will install on group listed.
- _Which URL do you navigate to in order to check that the ELK server is running? http://20.57.178.28:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._