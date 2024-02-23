<pre>
apiVersion: apps/v1 
kind: Deployment
metadata:
  name: registration-deployment
spec:
  selector:
    matchLabels:
      app: regapp
  replicas: 2 # tells deployment to run 2 pods matching the template
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 1

  template:
    metadata:
      labels:
        app: regapp
    spec:
      containers:
      - name: registration-project
        image: rajeswarithota1715/regapp:v1
        imagePullPolicy: Always
        ports:
        - containerPort: 8080

  
</pre>
