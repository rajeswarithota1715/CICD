<pre>
  ---
  - name: "deploying web app to docker container"
    hosts: localhost
    connection: local
    tasks:

    - name: "stopping docker container"
      command: "docker stop regapp"


    - name: "deleting docker container"
      command: "docker rm regapp"


    - name: "building docker image"
      command: "docker build -t regapp:v1 ."
      args:
        chdir: /opt/docker

    - name: "tagging docker image"
      command: "docker tag regapp:v1 rajeswarithota1715/regapp:v1"

    - name: "push docker image to docker hub"
      command: "docker push rajeswarithota1715/regapp:v1"

    - name: "run the docker image"
      command: "docker run -d --name regapp -p 8090:8080 regapp:v1"

</pre>
