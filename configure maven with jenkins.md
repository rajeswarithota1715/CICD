
Maven configuration:

Install maven in jenkins server  , follow maven official documentation for installing maven in jenkins server 

wget link-to-maven-package

tar -xvzf package-name

set up the ENV variables

edit .bash_profile which is available under user home directory

M2_HOME=/opt/maven

M2=/opt/maven/bin

JAVA_HOME=/usr/bin/jvm/java-11

PATH=$PATH:$HOME/BIN:$JAVA_HOME:$M2_HOME:$M2

Source .bash_profile


Now install maven plugin in Jenkins UI

Manage jenkins >available > maven integration

Provide JAVA and MAVEN home path

Maven Jenkins > global tool configuration
