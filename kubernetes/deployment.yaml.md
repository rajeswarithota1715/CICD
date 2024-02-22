<pre>
  apiVersion: v1
  kind: Deployment
  metadata:
    name: registration application
    labels:
      app: regapp
 spec:
  replicas: 2
  selector:
    matchLabels:
      app: regapp
  template:
    metadata:
      name: registration app
      labels:
        app: regapp
  spec:
    containers:
    - name: regapp
      image:rajeswarithota1715/regapp
      imagePullPolicy: Always
      ports:
      - containerPort: 8080
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 1
  
  
</pre>
