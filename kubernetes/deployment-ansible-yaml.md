<pre>
  ---
  - name: create pods using deployment.yaml
    hosts: kubernetes
    tasks: 
    - name: create a deployment
      command: kubectl apply -f deployment.yml
 
    - name: update deployment with new pods if image updated in docker hub
      command: kubectl rollout restart deployment.v1.apps/XXXXX-deployment
</pre>
