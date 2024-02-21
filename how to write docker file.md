FROM : To pull the basic image

RUN:  To execute commands

CMD: To provide defaults for an executing container

ENTRYPOINT: to configure a container that will run as a executable 

The difference between CMD and ENTRYPOINT is , we can overwrite CMD and we can't overwrite ENTRYPOINT

WORKDIR: to set the working directory ,likr cd in linux

COPY: To copy a directory from local machine to the docker container  

ADD: to copy files and folders from local machine to docker containers 

EXPOSE: informs docker that the container listens on the specified network ports at run time

ENV: to set the environment variables

EXAMPLES:

1.pull centos from dockerhub                        FROM: contos:latest

2.install java                                      RUN yum install java -y

3.create /opt/tomcat directory                      RUN mkdir /opt/tomcat

4.change working directory to /opt/tomcat           WORKDIR /opt/tomcat

5.download tomcat package                           ADD link  destination or RUN wget link destination

6.extract tar.gz file                               RUN tar -xvzf filename

7.rename to tomcat directory                        RUN mv source destination

8.tell to docker that it runs on port 8080          EXPOSE 8080

9.start tomcat service                              CMD ["/opt/tomcat/bin/catalina.sh" , "run"]

docker build -t filename
