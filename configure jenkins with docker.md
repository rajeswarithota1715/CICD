How to deploy java web app in docker container ?

1.	Create a docker server 

a.	Create an EC2 instance

b.	Login into EC2 instance


c.	Sudo apt-get update 

d.	Install docker in EC2 instance


i.	apt install docker.io

2.	create tomcat container

a.	write an docker file to create customised tomcat image

b.	in docker file the first step should be pulling base image , then we need to copy the 

c.	files from webapps.dist to webapps because the tomcat application will look into webapps for files but by default it will be in webapps.dist . if you don’t copy the files then you will get error . the 3rd step is copying the war files into container

d.	
i.	FROM tomcat:latest
ii.	
iii.	RUN cp  -R /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps
iv.	
v.	COPY ./*.war /usr/local/tomcat/webapps
vi.	
3.	Jenkins will connect to docker server using username and password provided in global configurations and perform required actions 
4.	
a.	Useradd dockeradmin
b.	
c.	Passwd dockeradmin
d.	
e.	Usermod -aG docker dockeradmin
f.	
5.	Add the “publish over SSH” plugin to Jenkins for transferring the war files from Jenkins server to tomcat server 
6.	
a.	Jenkins>manage Jenkins>plugins>available>publich over SSH>install
b.	
c.	Restart the Jenkins after the plugin installed
d.	
7.	Configure the Jenkins to use docker server
8.	
a.	Jenkins>manage Jenkins>configure system>publish over SSH > add SSH > provide 
b.	
c.	docker server details
d.	
9.	Create the new item
10.	
a.	Click on new item
b.	
c.	Select maven project
d.	
e.	Provide git repo details
f.	
g.	Provide maven goals
h.	
i.	in post build actions you need to select "send build artifacts over SSH" there you 
j.	
k.	need to select what are all the files you want to move and where you want to move .
l.	
11.	apply and save the configurations
12.	
13.	click on build now
14.	
15.	check the results
