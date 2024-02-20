Deploy artifacts on tomcat server:

Create new instance for tomcat application

Install java-openjdk-11

Download latest version of tomcat from official tomcat website

Tar -xvzf tomcat-file

Goto bin

./startup.sh

Access the tomcat ip:8080

Edit the context.xml to access the tomcat from outside of this server

Comment the allow field

Restart tomcat , the below files will be available in /opt/tomcat/bin

./shutdown.sh

./startup.sh

Edit the tomcat-users.xml to add some users from server

./shutdown.sh

./startup.sh
