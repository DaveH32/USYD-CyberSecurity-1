# USYD-CyberSecurity-1
# CYBER-Project-1
USYD CyberSecurity Bootcamp Project 1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Network Diagram: diagrams/network

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

 	This document contains the following details:
 	Description of the Topology
 	Access Policies
 	ELK Configuration
 	Beats in Use
 	Machines Being Monitored
 	How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible ,reliable _____, in addition to restricting access to the network.

- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?

The off-loading function of a load balancer defends the organization against distributed denial-of-service attacks. It does this by shifting traffic from the corporate server to a public cloud provider.

A jump box is a secure computer that all on the network that accesses and manages all the devices in a different zone of security. They provide transparent management of devices on the DMZ once a management session has been established. It acts as a single audit point for traffic and also a singe place where user accounts can be managed.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _logs____ and system ___traffic__.
- _TODO: What does Filebeat watch for?_: Monitors log files for changes and log events 
- _TODO: What does Metricbeat record?_: Collect metrics from the system and services running on a server 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name    	| Function    	| IP address 	| OS                 	|
|---------	|-------------	|------------	|--------------------	|
| Jumpbox 	| Web-gateway 	| 10.0.0.4   	| Ubuntu Linux 18.04 	|
| Web-1   	| Web-server  	| 10.0.0.5   	| Ubuntu Linux 18.04 	|
| Web-2   	| Web-Server  	| 10.0.0.6   	| Ubuntu Linux 18.04 	|
| ELK     	| ELK server  	| 10.1.0.4   	| Ubuntu Linux 18.04 	|


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _jumpbox____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

52.188.65.178

Machines within the network can only be accessed by jumpbox_____.

- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ Jumpbox 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     	| Physicalle accessible 	| IP address                              	|
|----------	|-----------------------	|-----------------------------------------	|
| Jump-Box 	| Yes                   	| 52.188.65.178 via ssh                   	|
| Web-1    	| No                    	| 10.0.0.5 accessible port 80             	|
| Web-2    	| No                    	| 10.0.0.6 accessible port 80             	|
| ELK      	| No                    	| ssh from jumpbox ,Kibana http port 5601 	|


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because

- _TODO: What is the main advantage of automating configuration with Ansible?_
It serves as a useful automation tool in deploying docker instances on multiple machines in a repeatable fashion.

The playbook implements the following tasks:

- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

 	Install docker.io
 	Download DVWA
 	Download ansible docker container
 	Start ansible container  @objectiveGoodall
 	Attach a bash shell to container
 	Create ansible install-elk playbook
 	Run ansible playbook


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Diagrams/Verification
 
![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
: 10.0.0.4 10.0.0.5 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Filebeat: Filebeat is a lightweight shipper for forwarding and centralized log data. It is installed as an agent on servers and monitors the log files or locations that are specified, collects log events and forwards them to Elasticsearch. 

Metricbeat:Metricbeat is also a lightweight agent that can be installed on target servers to periodically collect metric data from the target servers. This could include operating system metrics such as CPU, memory or data related to services or processes running on that server. It can also be used to monitor other beats and the ELK stack itself. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __ansible.cfg___ file to _/etc/ansible____.
- Update the ___ansible.cfg__ file to include...the private ip of the ELK server In the elesticsearch and Kibana sections.
- Run the playbook, and navigate to http://publicIPELK:5601/app/Kibana____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it ?_filebeat-playbook.yml and metricbeat-playbook.yml copied to /etc/ansible/roles
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_hosts file.cfg the private ip of the machine to which ELK and Filebeats should be installed on should be updated in the /etc/ansible file.
- _Which URL do you navigate to in order to check that the ELK server is running? http://publicIPELK:5601/app/Kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
    

