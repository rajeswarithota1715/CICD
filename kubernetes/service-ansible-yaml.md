<pre>
  ---
  - name: deploying service manifest
    hosts: kubernetes
    tasks:
    - name: "create a service"
      command: "kubectl -f reg-serive.yaml"
</pre>
