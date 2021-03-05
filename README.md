## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Cybersecurityproject1/diagrams/ELK Network Diagram)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
- _TODO: What aspect of security do load balancers protect? Defends against denial of service attacks by shifting attack traffic from the coorporate server to the cloud server.
What is the advantage of a jump box? Requres admins to connect before performing  tasks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VMs on the network and watch system metrics.
- _TODO: What does Filebeat watch for?_ a lightweight shipper for forwarding and centralizing log data.
- _TODO: What does Metricbeat record?_ a lightweight shippe that allows your servers to periodically collect the metrics from the OS and services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web 1     | Web Server         | 10.0.0.5                   |  Linux                |
| Web 2    |   Web Server      |    10.0.0.6                 | Linux                 |
| ELK    | Monitoring         |            |   Linux               |
| DVWA2    |          |            |   Linux               |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- TODO: 24.30.83.239

Machines within the network can only be accessed by eaxh other.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ Web 1 and Web 2. 10.0.0.5 & 10.0.0.6

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              |24.30.83.239|
|    Web 1      |    No                 |          10.0.0.1-254            |
|    Web 2    | No                    |                10.0.0.1-254      |
|    Elk   | No                    |            10.0.0.1-254          |

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
 The main advantage of automatically configuring the ELK is that it saves time.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
The first step is to configure the elk VM with the docker
The second step is to install pip3 and the python docker module
The third step is to increase the memory 
The fourth step is to download and launch a docker elk container
The fifth step enables the docker on boot

- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Desktop/ELK_Screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _10.0.0.5 and 10.0.0.6

We have installed the following Beats on these machines:
Filebeat, Metricbeat, Packetbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat: Detects changes to the filing system which will collect apache logs
Metricbeat: detects changes in the system metrics. An example would be CPU usage. We will use it to detect failed SSH login attempts, failed sudo escalations, and manage CPU/RAM statistics.
Packetbeat collects the packets that pass throug the NIC and will be used to trace all activity on the network.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbooks file to Ansible control node.
- Update the hosts file to include the additional IP addresses
- Run the playbook, and navigate to Kibana  to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
CyberSecurityProject 

This is a collection of Linux and Ansible Scripts from my Cyber Class

Most of the scripts are used to configure cloud servers with different docker containers.

The final setup was 4 servers running DVWA containers along with a jump box and a server running an ELK stack container.
