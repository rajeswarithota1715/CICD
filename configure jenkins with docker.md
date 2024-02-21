How to deploy java web app in docker container ?

1.	Create a docker server 

  a. 	Create an EC2 instance

  b.	Login into EC2 instance


  c.	Sudo apt-get update 

  d.	Install docker in EC2 instance


    i.	apt install docker.io

2.	create tomcat container

  a.	write an docker file to create customised tomcat image

  b.	in docker file the first step should be pulling base image , then we need to copy the 

  c.	files from webapps.dist to webapps because the tomcat application will look into webapps for files but by default it will be in webapps.dist . if you don’t copy the files then you will get error . the 3rd step is copying the war files into container


    i.	FROM tomcat:latest

    ii.	RUN cp  -R /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps

    iii.	COPY ./*.war /usr/local/tomcat/webapps

3.	Jenkins will connect to docker server using username and password provided in global configurations and perform required actions 

  a.	Useradd dockeradmin

  b.	Passwd dockeradmin

  c.	Usermod -aG docker dockeradmin

4.	Add the “publish over SSH” plugin to Jenkins for transferring the war files from Jenkins server to tomcat server 

  a.	Jenkins>manage Jenkins>plugins>available>publich over SSH>install

  b.	Restart the Jenkins after the plugin installed

5.	Configure the Jenkins to use docker server

  a.	Jenkins>manage Jenkins>configure system>publish over SSH > add SSH > provide 

  b.	docker server details

6.	Create the new item

  a.	Click on new item

  b.	Select maven project

  c.	Provide git repo details

  d.	Provide maven goals

  e.	in post build actions you need to select "send build artifacts over SSH" there you 

  f.	need to select what are all the files you want to move and where you want to move .

7.	apply and save the configurations

8.	click on build now

9.	check the results
