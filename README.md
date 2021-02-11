# ELKSTACK_DEPLOYMENT
The following documentation provides details of Project 1 at GWU Cyber Security Bootcamp.


  Description of Topology   |  ELK Configuration

  Access Administration     |  Implementation


  Description of Topology

   Objective: To create a monitored and load balanced instance of a DVWA network.
  Which will ensure the availability of the network and increase its overall efficiency. 

  Jump box: This provides a gateway to the network and provides an extra layer of security by decreasing exposure of the network to the internet.
  Load balancer: Increase the capacity and reliability of applications.
  ELK server: Integration of an ELK server provides the ability to monitor vulnerable VMs and log activity.
  Filebeat: Monitors changes of files on the VMs.
  Metricbeat: Monitors various activities such as downtime, ect.


  Machine List

  Red-Team-Jump-Box | Gateway        | 10.0.0.4<br/>
  Web-1             | DVWA Container | 10.0.0.5</br>
  Web-2             | DVWA Container | 10.0.0.6</br>
  ELK-Stack         | Linux Server   | 10.0.1.4<br/>


 Access Administration

 The sole gateway into the virtual network is provided by the jump box. The remainder of the network is unexposed to the internet. 

 Access Controls<br/>
 Name         |              Access<br/>
  Red-Team-Jump-Box.  |   Web-1 | Web-2 | ELK-Stack<br/>
  Web-1               |   Red-Team-Jump-Box | ELK-Stack<br/>
  Web-2               |   Red-Team-Jump-Box | ELK-Stack<br/>
  ELK-Stack           |   Web-1 | Web-2 | Red-Team-Jump-Box<br/>

  ELK Stack Configurations

The configuration of the ELK stack was obtainable through the creation of a docker container and the use of an ansible playbook (install-elk.yml). This mitigated some of the risks of misconfigurations that could potentially happen through manual setup.

  Install and configure the ELK Stack with docker
  Install docker.io
  Install pip3
  Download and launch ELK container

  This configures the ELK-Stack server to monitor Web-1 and Web-2.


  Implementation

  After configuration of the ansible on the gateway VM, use the following steps:

  1. Copy all playbooks into the “/ect/ansible/” directory
  
  2. Edit the correlating “host” group in the “/etc/ansible/hosts” file, with the IP addresses of the
  machines you would like to install your playbook and insert the following after each address “ansible_python_interpreter=/usr/bin/python3”.
  
  3. Run the playbook (example: ansible-playbook.yml), then run 'curl localhost/setup.php' to ensure the installation was successful
  
  4. To ensure the ELK server is running, navigate to “http://[ELK-Stack IP Address]:5601/app/kibana”

