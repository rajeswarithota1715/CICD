<pre>
apiVersion: v1
kind: Service
metadata:
  name: registration-service
  labels:
    app: regapp
spec:
  selector:
    app: regapp
  type: LoadBalancer
  ports:
    - port: 8080
      targetPort: 8080
      nodePort: 31200

  
</pre>

