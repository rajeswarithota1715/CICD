<pre>
  ---
  - name: "deploying web app to kubernetes cluster"
    hosts: localhost
    connection: local
    tasks:
  
    - name: "building docker image"
      command: "docker build -t regapp:v1 ."
      args:
        chdir: /opt/docker

    - name: "tagging docker image"
      command: "docker tag regapp:v1 rajeswarithota1715/regapp:v1"

    - name: "push docker image to docker hub"
      command: "docker push rajeswarithota1715/regapp:v1"
    
 
</pre>
