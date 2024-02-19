1.	We use bitbucked as our source code repository and our target platform is openshift 
2.	We are using Jenkins for CI and argoCD for CD
3.	Whenever user commit his changes bitbucked webhook will trigger and below actions will take place
4.	First jenkins will check out the code
5.	As our source code is java we use Maven for code building and unit test framework for unit testing 
6.	We use sonar for code scanning , we are scanning the code in order to ensure the code is free from security vulnerabilities 
7.	In this stage we will create container Image 
8.	After the image is created we will scan the image for vulnerabilities
9.	Push the image to image registry
10.	We use the declarative Jenkins pipe lines for the above activities 
11.	We will update this image in k8’s manifest
12.	Again we will push this updated image to bitbucket repo , we will store then as helm charts or plain manifests 
13.	argoCD will continuously monitor this bitbucked repo , whenever you push the updated image it will immediately deploy it to openshift cluster .
