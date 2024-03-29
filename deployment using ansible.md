## deploying registration app to docker dontainer using ansible as deployment tool

1.	Setup EC2 instance
    - Create EC2 instance
  

Steup hostname

	Vi /etc/hostname
	
	Change the hostname
	
	Reboot machine to reflect the changes
	
Create ansadmin user
	
	Useradd ansadmin
	
	Passwd ansadmin
	
	Systemctl restart sshd

Add users to sudoers file

	Vi /etc/sudoers
	
	Add ansadmin user and provide all  priviliges
	
	Ansadmin ALL=(ALL)              NOPASSWORD:  ALL
	
Generate ssh keys
	
	Shh-keygen -t rsa
Enable passwordbased authetication
	Vi /etc/ssh/sshd_config
	
	Remove the comment for passwordAuthentication
	
Install ansible 
	
	For ansible python should be there

	Yum install ansible
	
	
Mnaage dockerhost with ansible

On docker hoost:

 create ansadmin user

	Useradd ansadmin
	
	Passwd ansadmin

Add ansadmin to sudoers files

	Vi /etc/sudoers
	
	Ansadmin ALL=(ALL)            NOPASSWORD:   ALL

Enable password based authentication

	Vi /etc/ssh/sshd_config
	
	Remove the comment for passwordAuthentication
	

On ansible server

Add docker host ip to hosts file

	Vi /etc/ansible/hosts
	
	Copy private ip of dockerhost
	

Copy docker host ansadmin public key to ansible server ansadmin authorised keys

	Su - ansadmin
	
	Cd .ssh
	
	Ssh-copy-id docker-ip

Test the connection

	ansible -i hosts.inv all -m ping
	
	
Integrate Ansible with Jenkins:

Create a user in ansible servr (ansadmin)

Install publish over SSH plugin
Add ansible server credentials to jenkins

	Dashboard>manage jenkins>configure system>publish over SSH>add>provide ansible details
	

Jenkins job:

Copy the war file to /opt/docker

Create docker directory in /opt in asnile server

Change the ownershio of docker directory

Install docker on ansible server

Add ansadmin to docker group

Usermod -aG docker ansadmin

Systemctl restart docker

Create Dockerfile

	FROM tomcat:latest
	
	RUN cp -r /usr/local/tomcat/webapps.dist /usr/local/tomcat/webapps
	
	COPY ./*.war /usr/local/tomcat/webapps
	
Docker build -t regapp:v2 .

Docker images

Docker run -d --name regapp -p 8081:808 regapp:v2


Using ansible to create containers:

Copy ansible ansadmin shh public key to ansible authorized_keys file

Add ansible server ip address to ansible /etc/ansible/hosts file

Login to docker hub in ansible server

Write ansible playbook

	---
	-   hosts: ansible
	
	  tasks: 
	
	  - name : create docker image
	
	     command: docker build -t regapp:v2 .
	
	     args:
	
		Chdir: /opt/docker
		
            - name: create tag to push image onto dockerhub

              command: docker tag image-name new-image-name

          -  name: push docker image to docker hu

             command: docker push image-name

Write another ansible or deploying app
<pre>
	---
	- Hosts: dockerhost
	
	Tasks:

	
	- Name: create image
	
	- Command: docker run -d --name regapp-server -p 8082:8080 dockerimage
</pre>


