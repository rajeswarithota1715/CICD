<pre>
  ---
  - name: create pods using deployment.yaml
    hosts: kubernetes
    become: true
    tasks:
    - name: create a deployment
      command: kubectl apply -f deployment.yaml
    - name: create a service
      command: kubectl apply -f service.yaml

</pre>
