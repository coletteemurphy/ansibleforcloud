# ansibleforcloud
Ansible project that configures google cloud vms and installs software 

## Requirements

Deploy a web application using the following restrictions: 

•	3 VM (2 web server and 1 database)

•	Install Python dependecies

•	Install Flask and Mysql in a distributed model

•	Install App from a Git repo (https://github.com/mmumshad/simple-webapp)

•	Run the services

•	Configure Load Balancer

•	Send email notification once deployment is completed.

Note: Mysql is listening by default on 127.0.0.1 update it on /etc/mysql/my.conf. As well as allow the Mysql user to connect from source IP or %

## Notes
  
Created 4 vms on google cloud  
Installed ansible on controller  
  
sudo apt-add-repository ppa:ansible/ansible  
sudo apt update  
sudo apt install ansible  
    
Created project1 with a simple inventory file, confirmed they were added ok  
ansible-inventory --list -y -i inventory.txt  
  
and confirmed can ping other 3 hosts  
ansible all -m ping -u root -i inventory.txt  
  
Checked which collections were already available by running  
ansible-galaxy collection list  
Things already installed that I could use include  
commmunity.mysql  
google.cloud (didn't use in previous version using VM but might be useful)  
  
Created project ansibleproject and created a basic playbook with logging of all vars using guidelines from https://zwischenzugs.com/2021/08/27/five-ansible-techniques-i-wish-id-known-earlier/

## Dynamic inventory
Decided to try to use a dynamic inventory. Check if there is a plugin for google cloud
ansible-doc -t inventory -l  
Might be able to use google.cloud.gcp_compute  
  
Followed instructions here https://github.com/cloudadvocate/google-cloud/tree/master/ansible-dynamic-inventory  
NB had to install pip3 on controller as a dependency for this and create service-account.json on google cloud console  
Then I ran ansible-inventory -i gcp.yml --graph to ensure the hosts and groups had been assigned correctly  

## Collections
Determine which collections can be used








