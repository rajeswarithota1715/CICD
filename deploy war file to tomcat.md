Integrate tomcat with Jenkins

Manager Jenkins > plugins > available > deploy to container 

Add deployer user credentials to jenkins

Manager Jenkins > manage credentials > jenkins > global credentials >add credentials 

BuildAndDeploy

Provide git repo path

Provide maven goals (mvn clean install)

In post steps select deploy war/ear to a container

Provide the path to war file or **/*.war

Add container

Add credentials of tomcat

Provide tomcat url

Click on build now
