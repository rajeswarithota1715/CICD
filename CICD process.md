1.	there is a developer who commit his code into SVC , how Jenkins will notify?
1.	There are multiple ways to trigger the pipeline , the most efficient way is to use webhook . take the webhook url from Jenkins and place it in github settings .
2.	You need to mention on which event this webhook will be triggered , it might pull request or commit or something else .
2.	When ever the event is triggered Jenkins pipeline will be created .
3.	The first step will be code build , if the build fails you can set up some alerts and email notifications . if the build successes then it will go to next stage 
4.	 Code scan , here we will scan the code for security vulnerabilities and compare with our company threshold . did it met our threshold or not , if it fails we will send email notification or some alerts , if it succeeded we will go to next step
5.	Creation of docker image (docker build)
6.	Push the docker image to image registry , this image will have new tag
7.	We use the declarative Jenkins pipe lines for the above activities 
8.	Use gitops tools for CD
9.	Deploy pod.yaml, deploy.yaml ,service and etc manifests in git repo
10.	Argo image updater will continuously monitor image registry and whenever there is a new update in the image it will update the manifests files 
11.	Argocd will continuously monitor this git repository , whenever there is change in the manifests it will deploy the new manifests to Kubernetes or openshift 
12.	Argocd will continuously compare the Kubernetes cluster with git repo , it will make sure both matching at all the time .
