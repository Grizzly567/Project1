## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1ZuDMC7MvGKiwZ51_t0Jm4qL3uQmGUU1w/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook file may be used to install only certain pieces of it, such as Filebeat.

[Metricbeat-playbook.txt](https://github.com/Grizzly567/Project1/files/7013428/Metricbeat-playbook.txt)

[filebeat-playbook.txt](https://github.com/Grizzly567/Project1/files/7013429/filebeat-playbook.txt)

[install-elk-yml.txt](https://github.com/Grizzly567/Project1/files/7031049/install-elk-yml.txt)



This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored 
- How to Use the Ansible Build


Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting malicious traffic to the network.
The off-loading function of a load balancer defends an organization against distributed denial-of-service (DDoS) attacks.
A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| web-1    | Domain   | 10.0.0.8   | Linux            |
| web-2    | Domain   | 10.0.0.9   | Linux            |
| web-3    | Domain   | 10.0.0.10  | Linux            |
| ElkStack | Database | 10.1.0.4   | Linux            |


The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My computers public ip address.

Machines within the network can only be accessed by The Jump Box machine.
The Elk Vm is also accessed within the jump box vm, the elk stack internal ip address will be 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible |       Allowed IP Addresses     |
|----------|---------------------|--------------------------------|
| Jump Box | No                  | Your local machine public ip   |
| Web-1    | No                  | 10.0.0.1                       |
| Web-2    | No                  | 10.0.0.1                       |
| ElkStack | No                  | Your local machine public ip   |


Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
It allows IT administrators to automate away the drudgery from their daily tasks.

The playbook implements the following tasks:
Install docker.
Install python3.
Install the docker module.
Downlooad and launch the elk container iwht publiished ports.
Enabling the systemMD to restart on boot.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
[Docker ps output](https://user-images.githubusercontent.com/79630983/130306470-0c17216c-665a-43f5-94a2-debf1ff41163.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.8
10.0.0.9
10.0.0.10

We have installed the following Beats on these machines:
Filebeat & Metricbeat 

These Beats allow us to collect the following information from each machine:
Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. 
Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/filebeat/filebeat.yml .
- Update the playbook file to include the ansible local copy function.
- Run the playbook, and navigate to /etc/filebeat/ to check that the installation worked as expected.

Navigate back to the Filebeat installation page on the ELK server GUI.
On the same page, scroll to Step 5: Module Status and click Check Data.
Scroll to the bottom of the page and click Verify Incoming Data.
If your configuration is successful you will get a message like this for both metricbeat and filebeat.
![Kibana Data Recieval](https://user-images.githubusercontent.com/79630983/130306749-656de5fb-00bb-43c8-91e2-51492fe2602a.PNG)
