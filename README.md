# Ansible--CaseStudy
**Ansible for Configuration Management**

ANSIBLE CASE STUDY 

You are a Devops Engineer and the organization you are working on needs to set up two configuration management server groups. One for Apache another for Nginx. Being a Devops Engineer it is your task to deal with this configuration management issue. 
Let us see the tasks that you need to perform using Ansible. 
1. Create two Server Groups. One for Apache and another for Nginx.
2. Push two html files with their server information. 
Make sure that you don’t forget to start the services once the installation is done. Also send post installation messages for both the server groups. 
Using Ansible Roles accomplish the above the tasks. 
Also, once the Apache server configuration is done you need to install Java on that server group using ansible role in a playbook.

**Follow the below Steps to implement the requirments:**

**● Create a new deployment of ansible cluster of 5 nodes **

Step:1 Create 5 EC2 Instances (master, slave1, slave2, slave3 and slave4)

OS-> ubuntu

![Image](https://github.com/user-attachments/assets/1e89c91c-43a4-4a42-8484-e9f06af22879)

Step:2 Install Ansible

Open url:-  Installation Guide — Ansible Documentation (Contains Ansible installation guide)

![Image](https://github.com/user-attachments/assets/16cce222-8dd1-4e4a-b2fa-b0b2af365862)

Open Installing Ansible on Ubuntu

Run the following commands from Master Node

![Image](https://github.com/user-attachments/assets/b2de6797-1e5e-4923-a34e-c861d50dfd49)

![Image](https://github.com/user-attachments/assets/584ae900-f2f6-4df6-8f30-145e63f1b75e)

Step:3 Generate a keypair to establish connection between master and slave nodes
Run the command -> ssh-keygen (Master node)

![Image](https://github.com/user-attachments/assets/bc985f08-3640-4db5-bcce-88f69dddb09f)

Copy the public key generated

![Image](https://github.com/user-attachments/assets/4ed7d878-a663-4462-a674-0c95d6a999c4)

Open the .ssh/authorized_keys file and paste it (slave1,slave2,slave3 and slave4)

![Image](https://github.com/user-attachments/assets/6459264b-9c7b-4c51-a4e4-25e98b4aee46)
![Image](https://github.com/user-attachments/assets/1b07be9e-75e6-451d-9487-05be2c6324ec)

● Label 2 nodes as test and other 2 as prod 

Step:1 Edit the hosts file with the below data(private ip of slave machines)
Creating two groups test and prod

![Image](https://github.com/user-attachments/assets/9b4762fb-06da-4862-a1e4-3d185b6136b4)
![Image](https://github.com/user-attachments/assets/9812ac0b-094c-47f2-a29c-670a7339e048)
![Image](https://github.com/user-attachments/assets/606ba76f-0cbc-4219-a1a2-ee4efe0a6fe7)

