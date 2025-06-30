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

**Step:1** Create 5 EC2 Instances (master, slave1, slave2, slave3 and slave4)

OS-> ubuntu

![Image](https://github.com/user-attachments/assets/1e89c91c-43a4-4a42-8484-e9f06af22879)

**Step:2** Install Ansible

Open url:-  Installation Guide — Ansible Documentation (Contains Ansible installation guide)

![Image](https://github.com/user-attachments/assets/16cce222-8dd1-4e4a-b2fa-b0b2af365862)

Open Installing Ansible on Ubuntu

Run the following commands from Master Node

![Image](https://github.com/user-attachments/assets/b2de6797-1e5e-4923-a34e-c861d50dfd49)

![Image](https://github.com/user-attachments/assets/584ae900-f2f6-4df6-8f30-145e63f1b75e)

**Step:3** Generate a keypair to establish connection between master and slave nodes

Run the command -> ssh-keygen (Master node)

![Image](https://github.com/user-attachments/assets/bc985f08-3640-4db5-bcce-88f69dddb09f)

Copy the public key generated

![Image](https://github.com/user-attachments/assets/4ed7d878-a663-4462-a674-0c95d6a999c4)

Open the .ssh/authorized_keys file and paste it (slave1,slave2,slave3 and slave4)

![Image](https://github.com/user-attachments/assets/6459264b-9c7b-4c51-a4e4-25e98b4aee46)
![Image](https://github.com/user-attachments/assets/1b07be9e-75e6-451d-9487-05be2c6324ec)

●** Label 2 nodes as test and other 2 as prod **

**Step:1** Edit the hosts file with the below data(private ip of slave machines)
Creating two groups test and prod

![Image](https://github.com/user-attachments/assets/9b4762fb-06da-4862-a1e4-3d185b6136b4)
![Image](https://github.com/user-attachments/assets/9812ac0b-094c-47f2-a29c-670a7339e048)
![Image](https://github.com/user-attachments/assets/606ba76f-0cbc-4219-a1a2-ee4efe0a6fe7)

**Step:2** ping slaves from master

Run the command-> ansible –m ping all

![Image](https://github.com/user-attachments/assets/bccb2464-b733-4781-b9ae-963e9d1e6663)

**Step:3** Create a role-> role-java 

![Image](https://github.com/user-attachments/assets/cdd9befa-357a-44c9-a778-c09b33fe057c)
![Image](https://github.com/user-attachments/assets/76cf0f30-a4b2-401a-8b0e-7d0529979a19)

Create a file install-java.yaml

![Image](https://github.com/user-attachments/assets/1cf29588-ae36-41bf-9c9b-7ef354ca9981)
![Image](https://github.com/user-attachments/assets/bdf895a1-2771-4d44-8b04-655aec0b15ee)
![Image](https://github.com/user-attachments/assets/ac182390-a5ca-4220-8842-50eeb5eb32b5)

Configure install-java.yaml in mail.yml

![Image](https://github.com/user-attachments/assets/64fd6d37-cd9a-4b11-a645-f671a1fab542)
![Image](https://github.com/user-attachments/assets/f77aeddc-1155-4690-bc1e-20d134e43425)
![Image](https://github.com/user-attachments/assets/ee232dd8-b922-4f91-bc6e-10d2fb95e313)

**Step:4** Create a role-> role-mysql

![Image](https://github.com/user-attachments/assets/a7995ea5-38a7-4a08-987a-f2a152a83b63)

Create a file install-mysql.yaml

![Image](https://github.com/user-attachments/assets/66e4503d-d620-4042-9bcb-f8ee00d81f39)
![Image](https://github.com/user-attachments/assets/93b25e02-2685-4470-b3b2-867d8d4e8591)
![Image](https://github.com/user-attachments/assets/c873c0e7-cce2-46b0-8618-7c70806a2657)

Configure install-mysql.yaml in mail.yml

![Image](https://github.com/user-attachments/assets/37bb76ec-27d6-400a-bdf3-5464855e62ec)
![Image](https://github.com/user-attachments/assets/bba6fa04-8932-4f28-a19a-42e917c0de99)

**Step:5** Create a playbook by including the roles role-java and role-mysql

![Image](https://github.com/user-attachments/assets/dab286bd-51fd-4519-a611-9122e3e6e80e)
![Image](https://github.com/user-attachments/assets/5121e003-fac1-4d58-984a-bd6eb0a03324)
![Image](https://github.com/user-attachments/assets/c4b9b06e-07aa-4cc6-ab12-e654cad4d0fa)

Check syntax error and execute the playbook

	ansible-playbook playbook5.yaml - -syntax-check

	ansible-playbook playbook5.yaml - -check

	ansible-playbook playbook5.yaml

![Image](https://github.com/user-attachments/assets/634505f3-b482-4ed7-9087-75f2866a5342)
![Image](https://github.com/user-attachments/assets/838e3db7-e5a2-4ba1-a127-07ba663888d4)

● Install java on test nodes 

Successfully installed java in test nodes(slave1 and slave2)

![Image](https://github.com/user-attachments/assets/6e5b5e07-6825-41ea-9975-b417795f1384)
![Image](https://github.com/user-attachments/assets/2af5e476-e3c5-489f-8a23-cdd932f6aa61)

● Install mysql-server on prod nodes 

Successfully installed mysql in prod nodes(slave3 and slave4)

![Image](https://github.com/user-attachments/assets/58a1ace1-1752-4e35-8a9b-cc9f23ae7b7e)
![Image](https://github.com/user-attachments/assets/7cf6c890-0944-40ed-a060-d987d5ad00b8)

